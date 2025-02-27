---
title: Aggiunta di una barra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12fcf63c09d805f23fcbf0d041ab41ede7f85f32
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352354"
---
# <a name="add-a-toolbar"></a>Aggiungere una barra degli strumenti
Questa procedura dettagliata viene illustrato come aggiungere una barra degli strumenti all'IDE di Visual Studio.

 Una barra degli strumenti è visualizzata una striscia orizzontale o verticale che contiene i pulsanti associati a comandi. A seconda della relativa implementazione, una barra degli strumenti nell'IDE possibile riposizionare, ancorato a qualsiasi lato della finestra IDE principale o rendere essere davanti altre finestre.

 Inoltre, gli utenti possono aggiungere comandi a una barra degli strumenti o rimuoverli da esso tramite il **Personalizza** nella finestra di dialogo. In genere, le barre degli strumenti in VSPackage sono personalizzabili dall'utente. L'IDE gestisce tutte le personalizzazioni e il pacchetto VSPackage risponde ai comandi. Il pacchetto VSPackage non è necessario sapere dove è situato fisicamente un comando.

 Per altre informazioni sui menu, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Creare un'estensione con una barra degli strumenti
 Creare un progetto VSIX denominato `IDEToolbar`. Aggiungere un modello di elemento di comando di menu denominato **ToolbarTestCommand**. Per informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Creare una barra degli strumenti per l'IDE

1. Nelle *ToolbarTestCommandPackage.vsct*, cercare la sezione di simboli. Nell'elemento GuidSymbol denominato guidToolbarTestCommandPackageCmdSet, aggiungere le dichiarazioni per una barra degli strumenti e un gruppo della barra degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Nella parte superiore della sezione di comandi, creare una sezione di menu. Aggiungere un elemento Menu con la sezione di menu per definire la barra degli strumenti.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Le barre degli strumenti non possono essere annidati, come sottomenu. Pertanto, non è necessario assegnare un gruppo padre. Inoltre, non è necessario impostare la priorità, perché l'utente può spostare barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti è definita a livello di codice, ma le successive modifiche dall'utente vengono rese persistenti.

3. Nel [gruppi](../extensibility/groups-element.md) sezione, dopo la voce di gruppo esistente, definire una [gruppo](../extensibility/group-element.md) elemento per contenere i comandi per la barra degli strumenti.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Visualizzare il pulsante sulla barra degli strumenti. Nella sezione pulsanti, sostituire il blocco padre nel pulsante alla barra degli strumenti. Il blocco pulsante risultante dovrebbe essere simile al seguente:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Per impostazione predefinita, se una barra degli strumenti non dispone di alcun comando, non visualizzato.

5. Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.

6. Fare clic sulla barra dei menu di Visual Studio per ottenere l'elenco delle barre degli strumenti. Selezionare **sulla barra degli strumenti di Test**.

7. Si noterà ora la barra degli strumenti ridotta a icona a destra della scheda Cerca nei icona dei file. Quando si fa clic sull'icona, si dovrebbe essere una finestra di messaggio con la dicitura **ToolbarTestCommandPackage. Inside IDEToolbar.ToolbarTestCommand.MenuItemCallback()** .

## <a name="see-also"></a>Vedere anche
- [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)