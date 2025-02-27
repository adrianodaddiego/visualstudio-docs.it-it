---
title: Aggiungere comandi e movimenti ai diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea106d98dbd18f224e7f2a9d95734eff591dfc2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476662"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Aggiungere comandi e movimenti ai diagrammi delle dipendenze

È possibile definire comandi di menu di scelta rapida e gestori movimenti nei diagrammi delle dipendenze in Visual Studio. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) che è possibile distribuire ad altri utenti di Visual Studio.

Se si vuole, è possibile definire gestori comandi e movimenti diversi nello stesso progetto di Visual Studio. È anche possibile combinare più progetti di questo tipo in un progetto VSIX. Ad esempio, è possibile definire un unico progetto VSIX contenente comandi di livello e un linguaggio specifico di dominio.

> [!NOTE]
> È anche possibile personalizzare la convalida dell'architettura, in origine degli utenti che verrà confrontato con i diagrammi delle dipendenze. È consigliabile definire la convalida dell'architettura in un progetto di Visual Studio separato. È possibile aggiungerlo allo stesso progetto VSIX come per le altre estensioni. Per altre informazioni, vedere [aggiungere la convalida architettura personalizzati a diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Requisiti

Vedere [Requisiti](../modeling/extend-layer-diagrams.md#requirements).

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Definire un comando o movimento in un nuovo progetto VSIX

Il modo più rapido per creare un'estensione è usare il modello di progetto. In questo modo il codice e il manifesto VSIX vengono inseriti nello stesso progetto.

1. Creare una nuova **estensione di comando Progettazione livelli** oppure **estensione di movimento Progettazione livelli** progetto.

   Il modello crea un progetto che contiene un piccolo esempio funzionante.

2. Per testare l'estensione, premere **Ctrl**+**F5** oppure **F5**.

    Avvia un'istanza sperimentale di Visual Studio. In questo caso, creare un diagramma delle dipendenze. L'estensione di comando o di movimento dovrebbe funzionare in questo diagramma.

3. Chiudere l'istanza sperimentale e modificare il codice di esempio.

4. È possibile aggiungere più gestori comandi o movimenti allo stesso progetto. Per altre informazioni vedere una delle sezioni seguenti:

    [Definizione di un comando di menu](#command)

    [Definizione di un gestore movimenti](#gesture)

::: moniker range="vs-2017"

5. Per installare l'estensione nell'istanza principale di Visual Studio o in un altro computer, trovare il *VSIX* del file nei *bin* directory. Copiare il file nel computer in cui si vuole installare l'estensione e fare doppio clic sul file stesso. Per disinstallare l'estensione, scegliere **estensioni e aggiornamenti** nel **Tools** menu.

::: moniker-end

::: moniker range=">=vs-2019"

5. Per installare l'estensione nell'istanza principale di Visual Studio o in un altro computer, trovare il *VSIX* del file nei *bin* directory. Copiare il file nel computer in cui si vuole installare l'estensione e fare doppio clic sul file stesso. Per disinstallare l'estensione, scegliere **gestire le estensioni** nel **estensioni** menu.

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Aggiungere un comando o movimento a un progetto VSIX separato

Se si vuole creare un progetto VSIX contenente comandi, validator dei livelli e altre estensioni, è consigliabile creare un unico progetto per definire l'estensione VSIX e progetti separati per i gestori.

1. Creare un nuovo progetto **Libreria di classi**. Questo progetto conterrà le classi del gestore comandi o movimenti.

   > [!NOTE]
   > È possibile definire più classi dei gestori comandi o movimenti in una stessa libreria di classi, ma è consigliabile definire le classi per la convalida dei livelli in una libreria di classi distinta.

2. Aggiungere o creare un progetto VSIX nella soluzione. Un progetto VSIX contiene un file denominato **vsixmanifest**.

3. Nelle **Esplora soluzioni**, fare clic sul progetto VSIX e scegliere **imposta come progetto di avvio**.

4. In **source.extension.vsixmanifest**, in **Asset**, aggiungere il progetto di gestore comandi o movimenti come componente MEF.

    1. Nella scheda **Asset**scegliere **Nuovo**.

    2. In **Tipo**selezionare **Microsoft.VisualStudio.MefComponent**.

    3. In **Origine**selezionare **Progetto nella soluzione corrente** e selezionare il nome del progetto del gestore comandi o movimenti.

    4. Salvare il file.

5. Tornare al progetto di gestore comandi o movimenti e aggiungere i riferimenti di progetto seguenti:

   |**Riferimento**|**Operazioni consentite**|
   |-|-|
   |Programmi\Microsoft Visual Studio [versione]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Creare e modificare livelli|
   |Microsoft.VisualStudio.Uml.Interfaces|Creare e modificare livelli|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modificare forme nei diagrammi|
   |System.ComponentModel.Composition|Definire i componenti mediante Managed Extensibility Framework (MEF).|
   |Microsoft.VisualStudio.Modeling.Sdk.[versione]|Definire le estensioni di modellazione|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versione]|Aggiornare forme e diagrammi|

6. Modificare il file di classe nel progetto di libreria di classi C# contenente il codice per l'estensione. Per altre informazioni vedere una delle sezioni seguenti:

     [Definizione di un comando di menu](#command)

     [Definizione di un gestore movimenti](#gesture)

7. Per testare la funzionalità, premere **Ctrl**+**F5** oppure **F5**.

   Viene aperta un'istanza sperimentale di Visual Studio. In questo caso, creare o aprire un diagramma delle dipendenze.

8. Per installare l'estensione VSIX nell'istanza principale di Visual Studio o in un altro computer, trovare il **VSIX** del file nei **bin** directory del progetto VSIX. Copiare il file nel computer in cui si vuole installare il progetto VSIX. Fare doppio clic sul file VSIX in Esplora File.

## <a name="command"></a> Definizione di un comando di menu

È possibile aggiungere altre definizioni dei comandi di menu a un progetto di comandi o movimenti esistente. Ogni comando viene definito da una classe che ha le caratteristiche seguenti:

- La classe viene dichiarata nel modo seguente:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Lo spazio dei nomi e il nome della classe sono irrilevanti.

- I metodi che implementano `ICommandExtension` sono i seguenti:

  - `string Text {get;}` : etichetta visualizzata nel menu.

  - `void QueryStatus(IMenuCommand command)` : viene chiamato quando l'utente fa clic con il pulsante destro del mouse sul diagramma e determina se il comando deve essere visibile e abilitato per la selezione corrente dell'utente.

  - `void Execute(IMenuCommand command)` : viene chiamato quando l'utente seleziona il comando.

- Per determinare la selezione corrente, è possibile importare `IDiagramContext`:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Per aggiungere un nuovo comando, creare un nuovo file di codice che contiene l'esempio riportato di seguito. Quindi, testarlo e modificarlo.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="gesture"></a> Definizione di un gestore movimenti

Un gestore movimenti risponde quando l'utente trascina elementi nel diagramma delle dipendenze e quando l'utente fa doppio clic in qualsiasi punto nel diagramma.

È possibile aggiungere al progetto VSIX del gestore comandi o movimenti esistente un file di codice che definisce un gestore movimenti:

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

Per quanto riguarda i gestori movimenti tenere presente quanto segue:

- I membri di `IGestureExtension` sono:

     **OnDoubleClick** : viene chiamato quando l'utente fa doppio clic in qualsiasi punto del diagramma.

     **CanDragDrop** : viene chiamato ripetutamente quando l'utente sposta il mouse durante il trascinamento di un elemento nel diagramma. Deve operare rapidamente.

     **OnDragDrop** : viene chiamato quando l'utente rilascia un elemento nel diagramma.

- Il primo argomento per ogni metodo è un `IShape`, da cui è possibile ottenere l'elemento del livello. Ad esempio:

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- I gestori per alcuni tipi di elemento trascinato sono già definiti. Ad esempio, l'utente può trascinare elementi da Esplora soluzioni in un diagramma di dipendenza. Non è possibile definire un gestore del trascinamento per questi tipi di elemento. In questi casi, i metodi `DragDrop` non verranno richiamati.

## <a name="see-also"></a>Vedere anche

- [Aggiungere strumenti di convalida dell'architettura personalizzati ai diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
