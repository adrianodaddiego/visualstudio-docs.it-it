---
title: GUID e ID dei menu di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26171ae9f4464c3b8b63762d92e9a91d5a4b8420
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329110"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Menu GUID e ID di Visual Studio
Questo articolo enumera i valori GUID e ID dei menu e gruppi sulla barra dei menu di Visual Studio. Questi valori sono definiti nella *vsct* i file che vengono installati come parte di Visual Studio SDK. Per altre informazioni, vedere [definiti dall'IDE comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Per altre informazioni su come utilizzare gli oggetti ambiente di sviluppo (IDE) di sviluppo integrato che sono definiti in *vsct* i file, vedere [estendono i menu e comandi](../../extensibility/extending-menus-and-commands.md).

 I menu e gruppi sulla barra dei menu di Visual Studio utilizzano il GUID `guidSHLMainMenu`. Il menu della barra di se stesso ha un ID di `IDM_VS_TOOL_MAINMENU`.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppi nella barra dei menu di Visual Studio
 Per aggiungere un menu alla barra dei menu, impostare uno di questi gruppi come relativo elemento padre.

|Raggruppa|Id|
|-----------|--------|
|File/Modifica/visualizzazione|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|Progetto|IDG_VS_MM_PROJECT|
|Compilazione|IDG_VS_MM_BUILDDEBUGRUN|
|Formato/Tools|IDG_VS_MM_TOOLSADDINS|
|Window/Help/Community|IDG_VS_MM_WINDOWHELP|
|Componenti aggiuntivi|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu nella barra dei menu di Visual Studio
 Per aggiungere un gruppo a un menu di Visual Studio esistente, impostare una delle seguenti menu come elemento padre. Sottomenu non sono inclusi in questo elenco.

|Menu|Id|
|----------|--------|
|File|IDM_VS_MENU_FILE|
|Edit|IDM_VS_MENU_EDIT|
|Visualizza|IDM_VS_MENU_VIEW|
|Refactoring del codice|IDM_VS_MENU_REFACTORING|
|Progetto|IDM_VS_MENU_PROJECT|
|Compilazione|IDM_VS_MENU_BUILD|
|Formato|IDM_VS_MENU_FORMAT|
|Strumenti|IDM_VS_MENU_TOOLS|
|Estensioni|IDM_VS_MENU_EXTENSIONS|
|Finestra|IDM_VS_MENU_WINDOW|
|Componenti aggiuntivi|IDM_VS_MENU_ADDINS|
|Community|IDM_VS_MENU_COMMUNITY|
|?|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Gruppi nei menu di Visual Studio
 Di seguito vengono elencati mostrano i gruppi che derivano direttamente dal menu nella barra dei menu di Visual Studio. Il modo più rapido per aggiungere un comando a un menu di Visual Studio consiste nell'impostare uno di questi gruppi come elemento padre. In questa sezione non vengono visualizzati i gruppi che discendono dagli sottomenu.

### <a name="file-menu-groups"></a>Gruppi di menu file

|Raggruppa|Id|
|-----------|--------|
|Nuovo/Apri|IDG_VS_FILE_FILE|
|Aggiunta|IDG_VS_FILE_ADD|
|Soluzione|IDG_VS_FILE_SOLUTION|
|Varie|IDG_VS_FILE_MISC|
|Salva|IDG_VS_FILE_SAVE|
|Rinomina|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Print|IDG_VS_FILE_PRINT|
|Usati di recente|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Esci|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Modificare i gruppi di menu

|Raggruppa|Id|
|-----------|--------|
|Annullamento/ripristino|IDG_VS_EDIT_UNDOREDO|
|Le operazioni Taglia/Copia/Incolla|IDG_VS_EDIT_CUTCOPY|
|Seleziona|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|Oggetti|IDG_VS_EDIT_OBJECTS|
|Verbi OLE|IDG_VS_EDIT_OLEVERBS|
|Comando anche|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Effettuare il refactoring di gruppi di menu

|Raggruppa|Id|
|-----------|--------|
|Comuni|IDG_REFACTORING_COMMON|
|Avanzate|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Visualizzare i gruppi di menu

|Raggruppa|Id|
|-----------|--------|
|Codice del modulo|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definire le visualizzazioni|IDG_VS_VIEW_DEFINEVIEWS|
|WINDOWS|IDG_VS_VIEW_WINDOWS|
|Definire l'architettura di Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Windows dell'organizzazione|IDG_VS_VIEW_ORG_WINDOWS|
|Browser di codice|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Barre degli strumenti|IDG_VS_VIEW_TOOLBARS|
|Simboli|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Passare|IDG_VS_VIEW_NAVIGATE|
|Passare di piccole dimensioni|IDG_VS_VIEW_SMALLNAVIGATE|
|Visualizzatore oggetti|IDG_VS_VIEW_OBJBRWSR|
|Comando anche|IDG_VS_VIEW_COMMANDWELL|
|Pagine delle proprietà|IDG_VS_VIEW_PROPPAGES|
|Aggiorna|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Gruppi di menu progetto

|Raggruppa|Id|
|-----------|--------|
|Varie aggiungere|IDG_VS_PROJ_MISCADD|
|Aggiunta|IDG_VS_PROJ_ADD|
|Cartella|IDG_VS_PROJ_FOLDER|
|Scaricamento/ricaricamento|IDG_VS_PROJ_UNLOADRELOAD|
|Riferimenti|IDG_VS_PROJ_REFERENCE|
|Opzioni|IDG_VS_PROJ_OPTIONS|
|Impostazioni|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Creare gruppi di menu

|Raggruppa|Id|
|-----------|--------|
|Soluzione|IDG_VS_BUILD_SOLUTION|
|Selection|IDG_VS_BUILD_SELECTION|
|Ottimizzazione GPO|IDG_VS_PGO_SELECTION|
|Varie|IDG_VS_BUILD_MISC|
|Annulla|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Gruppi di menu Strumenti

|Raggruppa|Id|
|-----------|--------|
|Riga di comando|IDG_VS_TOOLS_CMDLINE|
|Frammenti di codice|IDG_VS_TOOLS_SNIPPETS|
|Subset di oggetti|IDG_VS_TOOLS_OBJSUBSET|
|Opzioni|IDG_VS_TOOLS_OPTIONS|
|Gli altri 2|IDG_VS_TOOLS_OTHER2|
|Strumenti esterni|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizzazioni esterne|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Gruppi di menu finestra

|Raggruppa|Id|
|-----------|--------|
|Nuovo|IDG_VS_WINDOW_NEW|
|Dock/di chiusura|IDG_VS_DOCKCLOSE|
|Dock/Nascondi|IDG_VS_DOCKHIDE|
|Disponi|IDG_VS_WINDOW_ARRANGE|
|Navigazione|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Gruppi di menu della Guida

|Raggruppa|Id|
|-----------|--------|
|Esempi|IDG_VS_HELP_SAMPLES|
|Supporto|IDG_VS_HELP_SUPPORT|
|Informazioni su|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Sottomenu del menu di Visual Studio
 La gerarchia seguente viene illustrato i sottomenu che sono associati i menu nella barra dei menu di Visual Studio. Perché solo un gruppo può avere un menu come relativo elemento padre, ogni sottomenu deve derivano da un gruppo in un menu, anziché direttamente dal menu di scelta. Per altre informazioni sulla relazione tra i menu, gruppi e i sottomenu, vedere [aggiungere un sottomenu a un menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> I nomi dei menu nella barra dei menu di Visual Studio non vengono visualizzati separatamente nella gerarchia perché questi possono essere dedotti dalla convenzione di denominazione per i gruppi nell'IDE, come indicato di seguito: *IDG_VS_\<nome del Menu\>_\<nome gruppo\>* .

|Gruppo padre|Submenu|Gruppi figlio|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1...6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Vedere anche
- [Barre degli strumenti GUID e ID di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Comandi i GUID e ID di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [File di Visual Studio comando table (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
