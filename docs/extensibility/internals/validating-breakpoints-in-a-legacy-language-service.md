---
title: La convalida dei punti di interruzione in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 177b0bb3fddebab6518a851bf8ce4c4d34d43897
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324567"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Convalida dei punti di interruzione in un servizio di linguaggio legacy
Un punto di interruzione indica che l'esecuzione del programma deve essere interrotta in un particolare punto mentre è in esecuzione in un debugger. Un utente può inserire un punto di interruzione su una qualsiasi riga nel file di origine, poiché l'editor non dispone di alcuna conoscenza di ciò che costituisce una posizione valida per un punto di interruzione. Quando il debugger viene avviato, tutti i punti di interruzione contrassegnate (denominati in sospeso i punti di interruzione) sono associati nella posizione appropriata nel programma in esecuzione. Allo stesso tempo che i punti di interruzione vengono convalidate per assicurarsi che fungono da indicatore percorsi di codice valido. Ad esempio, un punto di interruzione in un commento non è valido, perché non è presente codice in tale posizione nel codice sorgente. Il debugger disabilita i punti di interruzione non validi.

 Poiché il servizio di linguaggio conosce il codice sorgente viene visualizzato, è possibile convalidare i punti di interruzione prima che il debugger viene avviato. È possibile eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> per restituire un intervallo che specifica un percorso valido per un punto di interruzione. La posizione del punto di interruzione viene comunque convalidata quando il debugger viene avviato, ma l'utente viene informato di punti di interruzione non validi senza attendere che il debugger deve caricare.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementazione del supporto per la convalida dei punti di interruzione

- Il <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo è data la posizione del punto di interruzione. L'implementazione deve decidere se il percorso sia valido e indicare questo restituendo un intervallo di testo che identifica il codice associato la posizione di riga del punto di interruzione.

- Restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> se il percorso sia valido, o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> se non è valido.

- Se il punto di interruzione è valido e il punto di interruzione viene evidenziato l'intervallo di testo.

- Se il punto di interruzione non è valido, un messaggio di errore viene visualizzato nella barra di stato.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo che chiama il parser per ottenere l'intervallo di codice (se presente) in corrispondenza della posizione specificata.

 Questo esempio si presuppone che sia stato aggiunto un `GetCodeSpan` metodo per il <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe che convalida l'intervallo di testo e restituisce `true` se è un percorso valido punto di interruzione.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>Vedere anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)