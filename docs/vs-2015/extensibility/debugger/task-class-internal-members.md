---
title: Classe Task - membri interni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 200b35e60d3d468a934565959629298e6c6f04bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970240"
---
# <a name="task-class---internal-members"></a>Classe Task - Membri interni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni del <xref:System.Threading.Tasks.Task?displayProperty=fullName> classi che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere il <xref:System.Threading.Tasks.Task> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Membri  
  
### <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto usato come destinazione un punto di interruzione dal debugger.|  
  
### <a name="fields"></a>Campi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice da eseguire nel <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Archivia le proprietà aggiuntive del <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Il campo sottostante per il <xref:System.Threading.Tasks.Task?displayProperty=fullName> proprietà padre.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia le informazioni sullo stato corrente del <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno usati dall'azione.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Il campo sottostante per il <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> proprietà.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|L'identificatore successivo disponibile per un <xref:System.Threading.Tasks.Task> oggetto.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima che ha raggiunto lo stato di esecuzione o che l'attività ha confermato l'annullamento relativi e completata senza eccezioni.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica che l'attività è in esecuzione.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica che l'attività completata a causa di un'eccezione non gestita.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica che l'attività completata correttamente l'esecuzione.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica che l'attività ha terminato l'esecuzione del delegato e in modo implicito è in attesa di completamento delle attività figlio collegate.|  
  
## <a name="remarks"></a>Note  
 I seguenti metodi interni sono utili per un motore di debugger perché fungono da indicatore all'ingresso di <xref:System.Threading.Tasks.Task> l'esecuzione di codice:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
