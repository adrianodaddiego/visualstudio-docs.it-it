---
title: 'Procedura dettagliata: Uso della gerarchia XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3cf836ed59dadba71314aa38cd4d2907bee384a6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808159"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Procedura dettagliata: Usare gerarchia XSLT

Lo strumento di gerarchia XSLT semplifica molte attività di sviluppo XML. Un foglio di stile XSLT spesso usa istruzioni `includes` e `imports`. La compilazione viene avviata dal foglio di stile principale, ma quando viene visualizzato un errore come risultato della compilazione di un foglio di stile XSLT, è possibile che l'errore provenga da un'origine diversa dal foglio di stile principale. È possibile che la correzione dell'errore o la modifica del foglio di stile richieda accesso ai fogli di stile inclusi o importati. Scorrendo il foglio di stile nel debugger è possibile che vengano visualizzati i fogli di stile inclusi e importati ed è necessario aggiungere un punto di interruzione in una determinata posizione di uno o più fogli di stile inclusi.

Un altro scenario in cui può essere utile lo strumento di gerarchia XSLT è l'inserimento di punti di interruzione sulle regole del modello incorporato. Le regole del modello sono modelli speciali generati per ogni modalità del foglio di stile e sono chiamate da `xsl:apply-templates` quando nessun altro modello corrisponde al nodo. Per implementare il debug nelle regole dei modelli incorporati, il debugger XSLT genera il file con le regole nella cartella temporanea e le compila insieme al foglio di stile principale. Senza eseguire istruzioni di codice da alcuni `xsl:apply-template`, può essere difficile individuare i fogli di stile inclusi nel foglio di stile principale o trovare e aprire il foglio di stile con le regole del modello incorporate.

Nell'esempio riportato in questo argomento viene dimostrata l'esecuzione del debug in un foglio di stile a cui si fa riferimento.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Per eseguire il debug in un foglio di stile di riferimento

1. Aprire un documento XML in Visual Studio. Questo esempio Usa il documento seguente:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Aggiungere il codice seguente *xslinclude. xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3. Aggiungere il codice seguente *xslinclude. xsl* file:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4. Aggiungere un punto di interruzione dell'istruzione `<xsl:include href="xslincludefile.xsl" />`.

5. Avviare il debug.

6. Quando il debugger si arresta in corrispondenza l'istruzione `<xsl:include href="xslincludefile.xsl" />`, premere la **Esegui istruzione** pulsante. Il debug può proseguire nel foglio di stile di riferimento. La gerarchia è visibile e nella finestra di progettazione viene visualizzato il percorso corretto.

## <a name="see-also"></a>Vedere anche

- [Profiler XSLT](../xml-tools/xslt-profiler.md)