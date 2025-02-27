---
title: 'CA1063: Implementare IDisposable correttamente'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f1b2c5b447d796ddd2098a6500b6094478fcd8b9
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842000"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementare IDisposable correttamente

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Il <xref:System.IDisposable?displayProperty=nameWithType> interfaccia non è implementata correttamente. Possibili cause sono:

- <xref:System.IDisposable> reimplementato nella classe.

- Finalizzare è reoverridden.

- Viene eseguito l'override di Dispose ().

- Non è pubblico, il metodo Dispose () [sealed](/dotnet/csharp/language-reference/keywords/sealed), o denominati **Dispose**.

- Dispose (bool) non è protetto, virtuale o non sealed.

- Nei tipi non sealed, Dispose () devono chiamare Dispose (true).

- Per i tipi unsealed, l'implementazione di Finalize non chiama Dispose (bool) o il finalizzatore della classe base.

Violazione di uno di questi modelli Attiva avviso CA1063.

Ogni tipo non sealed che dichiara e implementa la <xref:System.IDisposable> interfaccia deve fornire il proprio `protected virtual void Dispose(bool)` (metodo). `Dispose()` deve chiamare `Dipose(true)`, e deve chiamare il finalizzatore `Dispose(false)`. Se si crea un tipo non sealed che dichiara e implementa la <xref:System.IDisposable> interfaccia, è necessario definire `Dispose(bool)` e chiamarlo. Per altre informazioni, vedere [pulire le risorse non gestite (Guida per .NET)](/dotnet/standard/garbage-collection/unmanaged) e [criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

Per impostazione predefinita, questa regola cerca solo tipi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Tutti i <xref:System.IDisposable> i tipi devono implementare le [criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern) correttamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Esaminare il codice e determinare quale delle seguenti soluzioni risolverà questa violazione:

- Rimuovere <xref:System.IDisposable> nell'elenco delle interfacce implementate dal tipo di ed eseguire l'override dell'implementazione Dispose della classe base.

- Rimuovere il finalizzatore dal tipo specificato, eseguire l'override di Dispose (bool disposing) e inserire la logica di finalizzazione nel percorso del codice dove 'disposing' è false.

- Eseguire l'override di Dispose (bool disposing) e inserire la logica di dispose nel percorso del codice dove 'disposing' è true.

- Assicurarsi che sia dichiarato come pubblico Dispose () e [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Rinominare il metodo dispose **Dispose** e assicurarsi che sia dichiarato come pubblico e [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Assicurarsi che che Dispose (bool) sia dichiarato come protected, virtual e unsealed.

- Modificare Dispose () in modo che chiami Dispose (true), quindi chiama <xref:System.GC.SuppressFinalize%2A> sull'istanza dell'oggetto corrente (`this`, o `Me` in Visual Basic) e poi restituisce.

- Modificare il finalizzatore, in modo che chiami Dispose (false) e quindi restituisce.

- Se si crea un tipo non sealed che dichiara e implementa la <xref:System.IDisposable> l'interfaccia, assicurarsi che l'implementazione di <xref:System.IDisposable> segue il modello che è descritti in precedenza in questa sezione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Esempio di pseudocodice

Il pseudo-codice seguente viene fornito un esempio generale di come Dispose (bool) deve essere implementata in una classe che usa gestita e le risorse native.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Elimina modello (linee guida di progettazione framework)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Pulire le risorse non gestite (Guida per .NET)](/dotnet/standard/garbage-collection/unmanaged)