---
title: Personalizzare il pacchetto di soluzione SharePoint tramite le destinazioni di MSBuild
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71665f6ccf22ace264ff39831521538a335aed93
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401504"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Procedura: Personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild
  Tramite le destinazioni di MSBuild al prompt, è possibile personalizzare come Visual Studio crea il file di pacchetto di SharePoint (*wsp*). Ad esempio è possibile personalizzare le proprietà di MSBuild per modificare la directory intermedia dei pacchetti e i gruppi di elementi di MSBuild con cui si specificano i file enumerati.

## <a name="customize-and-run-msbuild-targets"></a>Personalizzare ed eseguire le destinazioni di MSBuild
 Se si personalizzano le destinazioni di BeforeLayout e AfterLayout, è possibile eseguire le attività prima del layout del pacchetto, ad esempio aggiungendo, rimuovendo o modificando i file che verranno inclusi nel pacchetto.

#### <a name="to-customize-the-beforelayout-target"></a>Per personalizzare la destinazione di BeforeLayout

1. Aprire un editor, ad esempio Blocco note, quindi aggiungere il codice riportato di seguito.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    In questo esempio viene visualizzato un messaggio prima della creazione del pacchetto di questa destinazione.

2. Denominare il file **CustomLayout**e quindi salvare il file nella cartella del progetto SharePoint.

3. Aprire il progetto, aprire il menu di scelta rapida e quindi scegliere **Scarica progetto**.

4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto e quindi scegliere **Edit** *\<ProjectName > vbproj* o **modifica** *\<NomeProgetto > csproj*.

5. Dopo la riga `Import` verso la fine del file di progetto, aggiungere la seguente riga.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Salva e chiudi il file di progetto.

7. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto e quindi scegliere **Ricarica progetto**.

   Quando si pubblica il progetto, il messaggio viene visualizzato nell'output prima che inizi la creazione del pacchetto.

#### <a name="to-customize-the-afterlayout-target"></a>Per personalizzare la destinazione di AfterLayout

1. Nella barra dei menu, scegliere **File** > **Open** > **File**.

2. Nel **Apri File** della finestra di dialogo passare alla cartella del progetto, scegliere il file CustomLayout e quindi scegliere il **Open** pulsante.

3. Prima del tag `</Project>` aggiungere il codice seguente:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    In questo esempio viene visualizzato un messaggio dopo la creazione del pacchetto di questa destinazione.

4. Salvare e chiudere il file di destinazioni.

5. Riavviare Visual Studio, quindi aprire il progetto.

   Quando si pubblica il progetto, il messaggio di BeforeLayout viene visualizzato prima che inizi la creazione del pacchetto e il messaggio di AfterLayout viene visualizzato al termine della creazione del pacchetto.

## <a name="see-also"></a>Vedere anche
- [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
