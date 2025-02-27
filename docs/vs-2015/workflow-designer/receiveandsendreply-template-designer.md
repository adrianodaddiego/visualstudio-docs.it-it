---
title: Progettazione del modello ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9de3e8446250829d431dcbf33b14effd607ab545
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802425"
---
# <a name="receiveandsendreply-template-designer"></a>Finestra di progettazione del modello ReceiveAndSendReply
Il **ReceiveAndSendReply** modello viene utilizzato per creare una coppia di preconfigurati <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> attività all'interno di un <xref:System.Activities.Statements.Sequence> attività correlate come parte di uno scambio di messaggi di richiesta/risposta modello sul server.  

## <a name="the-receiveandsendreply-template"></a>Modello ReceiveAndSendReply  
 Aggiunta **ReceiveAndSendReply** modello effettua tre operazioni oltre alla creazione di <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> attività con un <xref:System.Activities.Statements.Sequence> attività:  

1. Configurazione delle proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Receive>.  

2. Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.  

3. Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.  

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilizzo della finestra di progettazione del modello ReceiveAndSendReply  
 Il **ReceiveAndSendReply** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**  scheda nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  

 Il **ReceiveAndSendReply** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque vengono posizionate le attività in genere. Ciò consente di creare un <xref:System.ServiceModel.Activities.Receive> attività che può essere configurato con il **inviare** ActivityDesigner e un correlato <xref:System.ServiceModel.Activities.SendReply> che può essere configurato con la finestra di progettazione SendReplyToReceive.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando il **Receive** finestra di progettazione per configurare il <xref:System.ServiceModel.Activities.Receive> attività, vedere il [ricezione](../workflow-designer/receive-activity-designer.md) argomento.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando il **SendReplyToReceive** finestra di progettazione per configurare il <xref:System.ServiceModel.Activities.SendReply> attività, vedere la sezione seguente.  

### <a name="properties-of-sendreply"></a>Proprietà di SendReply  
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  

|                               Nome proprietà                                | Obbligatorio |                                                                                                                                                                                                                                                                                                                                                      Utilizzo                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>. Il valore predefinito è SendReplyToReceive.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>. Questa proprietà non deve essere **null**. Le attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> sono usate insieme sul server per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificarla in quanto viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> dalla quale è stata creata l'attività <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante puntini di sospensione accanto al **contenuto** campo nella griglia delle proprietà oppure facendo clic di **definire...** pulsante accanto il **contenuti** etichetta nel **ricezione** superficie dell'ActivityDesigner. Entrambi visualizzano la **definizione del contenuto** finestra di dialogo. [!INCLUDE[crabout](../includes/crabout-md.md)] come usare questa casella, vedere la [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) argomento.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> proprietà nella griglia delle proprietà per aprire la **Aggiungi inizializzatori di correlazione** nella finestra di dialogo. [!INCLUDE[crabout](../includes/crabout-md.md)] utilizzo di questa casella, vedere la [finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md) argomento.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Specifica l'intestazione Action del messaggio. Se non viene impostata esplicitamente, assume il valore predefinito:<br /><br /> <strong>https://tempuri.org/{service spazio dei nomi del contratto} / {nome del contratto di servizio} / {nome dell'operazione}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta. Il valore predefinito è **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Vedere anche  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)