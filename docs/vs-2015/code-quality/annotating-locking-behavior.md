---
title: Annotazione del comportamento di blocco | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 66c4aafb380d50ec0faafce931b8ce73e5138e6f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052389"
---
# <a name="annotating-locking-behavior"></a>Annotazione del comportamento di blocco
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per evitare i bug di concorrenza in un programma multithread, seguire sempre un'appropriata disciplina di blocco e utilizzare le annotazioni SAL.  
  
 I bug di concorrenza sono notoriamente difficili da riprodurre, diagnosticare e sottoporre al debug perché sono non deterministici. Ragionare sull'interfoliazione dei thread è difficile idealmente e quindi praticamente quando si progetta un corpo di codice che dispone di più di un thread. Pertanto, è consigliabile seguire una disciplina di blocco nei programmi multithread. Ad esempio, obbedendo a un ordine di blocco mentre si acquisiscono molteplici blocchi aiuta ad evitare deadlock e acquisendo correttamente la guardia del blocco prima di accedere ad una risorsa condivisa aiuta a impedire una race condition.  
  
 Sfortunatamente, queste regole di blocco in apparenza semplici sono sorprendentemente difficili da utilizzare nella pratica. Una limitazione fondamentale in linguaggi di programmazione e i compilatori di oggi è che non direttamente supportano la specifica e analisi dei requisiti di concorrenza. I programmatori devono fare affidamento sui commenti informali del codice per esprime le intenzioni su come utilizzare i blocchi.  
  
 Le annotazioni di concorrenza SAL sono progettate per specificare gli effetti collaterali del blocco, la responsabilità del blocco, la tutela di dati, la gerarchia d'ordine e altri comportamenti previsti del blocco. Creando regole implicite esplicite, le annotazioni di concorrenza SAL forniscono un metodo coerente per documentare come il codice utilizza le regole di blocco. Le annotazioni di concorrenza migliorano anche la capacità degli strumenti di analisi del codice di trovare race condition, deadlock, operazioni di sincronizzazione non corrispondenti e altri difficili errori di concorrenza.  
  
## <a name="general-guidelines"></a>Indicazioni generali  
 Utilizzando le annotazioni è possibile indicare i contratti impliciti nelle definizioni di funzione tra le implementazioni (chiamati) e i client (chiamanti) ed esprimere invarianti e altre proprietà del programma che possono migliorare ulteriormente l'analisi.  
  
 SAL supporta molti tipi diversi di primitive di blocco, come ad esempio le sezioni critiche, i mutex, gli spinlock e altri oggetti risorsa. Le annotazioni di concorrenza molti hanno un'espressione di blocco come parametro. Per convenzione, un blocco è identificato dall'espressione del percorso dell'oggetto sottostante di blocco.  
  
 Alcune regole sulla proprietà dei thread da tenere in considerazione:  
  
- Gli spinlock sono blocchi non contati che dispongono della proprietà dei thread.  
  
- I mutex e le sezioni critiche sono blocchi contati che dispongono della proprietà dei thread.  
  
- I semafori e gli eventi sono considerati blocchi contati che non che dispongono della proprietà dei thread.  
  
## <a name="locking-annotations"></a>Annotazioni di bloccante  
 Nella tabella seguente sono elencate le annotazioni di bloccante.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione incrementando di uno il conteggio dei blocchi esclusivi dell'oggetto di blocco denominato da `expr`.|  
|`_Acquires_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione incrementando di uno il conteggio dei blocchi dell'oggetto di blocco denominato da `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Il blocco denominato da `expr` viene acquisito.  Viene restituito un errore se il blocco è già utilizzato.|  
|`_Acquires_shared_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione incrementando di uno il conteggio dei blocchi condivisi dell'oggetto di blocco denominato da `expr`.|  
|`_Create_lock_level_(name)`|Un'istruzione che dichiara il simbolo `name` come un livello di blocco in modo che possa essere utilizzato nelle annotazioni `_Has_Lock_level_` e `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Annota un qualsiasi oggetto per perfezionare le informazioni sul tipo di un oggetto risorsa. In alcuni casi viene utilizzato un tipo comune per diversi tipi di risorse e il tipo di overload non è sufficiente per distinguere i requisiti di semantici tra varie risorse. Di seguito è riportato un elenco di parametri `kind` predefiniti:<br /><br /> `_Lock_kind_mutex_`<br /> ID tipo di blocco per i mutex.<br /><br /> `_Lock_kind_event_`<br /> ID tipo di blocco per gli eventi.<br /><br /> `_Lock_kind_semaphore_`<br /> ID tipo di blocco per i semafori.<br /><br /> `_Lock_kind_spin_lock_`<br /> ID tipo di blocco per SpinLock.<br /><br /> `_Lock_kind_critical_section_`<br /> ID tipo di blocco per le sezioni critiche.|  
|`_Has_lock_level_(name)`|Annota un oggetto di blocco e lo fornisce al livello di blocco `name`.|  
|`_Lock_level_order_(name1, name2)`|Un'istruzione che fornisce il blocco di ordinamento tra `name1` e `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Annota una funzione e indica che lo stato successivo dei due blocchi `expr1` e `expr2`, verrà considerato come se fosse lo stesso oggetto di blocco.|  
|`_Releases_exclusive_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione riducendo di uno il conteggio dei blocchi esclusivi dell'oggetto di blocco denominato da `expr`.|  
|`_Releases_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione riducendo di uno il conteggio dei blocchi dell'oggetto di blocco denominato da `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Il blocco denominato da `expr` viene rilasciato. Viene restituito un errore se il blocco non è attualmente utilizzato.|  
|`_Releases_shared_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione riducendo di uno il conteggio dei blocchi condivisi dell'oggetto di blocco denominato da `expr`.|  
|`_Requires_lock_held_(expr)`|Annota una funzione e indica che nello stato precedente il conteggio dei blocchi dell'oggetto denominato da `expr` è di almeno uno.|  
|`_Requires_lock_not_held_(expr)`|Annota una funzione e indica che nello stato precedente il conteggio del blocco dell'oggetto denominato da `expr` è zero.|  
|`_Requires_no_locks_held_`|Annota una funzione e indica che il conteggio del blocco è zero in tutti i blocchi noti al controllore.|  
|`_Requires_shared_lock_held_(expr)`|Annota una funzione e indica che nello stato precedente il conteggio dei blocchi condivisi dell'oggetto denominato da `expr` è di almeno uno.|  
|`_Requires_exclusive_lock_held_(expr)`|Annota una funzione e indica che nello stato precedente il conteggio dei blocchi esclusivi dell'oggetto denominato da `expr` è di almeno uno.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Intrinseci SAL per oggetti di blocco non esposti  
 Alcuni oggetti di blocco non sono esposte dall'implementazione delle funzioni di blocco associate.  Nella tabella seguente sono elencate le variabili intrinseche SAL che abilitano le annotazioni sulle funzioni che operano sugli oggetti di blocco non esposti.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Viene descritto lo spin lock di annullamento.|  
|`_Global_critical_region_`|Viene descritta l'area critica.|  
|`_Global_interlock_`|Vengono descritte le operazioni con interlock.|  
|`_Global_priority_region_`|Viene descritta la regione di prioritaria.|  
  
## <a name="shared-data-access-annotations"></a>Annotazioni dei dati condivisa per l'accesso  
 Nella tabella seguente sono elencate le annotazioni per l'accesso ai dati condivisi.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Annota una variabile e indica se la variabile è accessibile, il conteggio dei blocchi dell'oggetto di blocco denominato da `expr` è di almeno uno.|  
|`_Interlocked_`|Annota una variabile ed è equivalente a `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Il parametro della funzione con annotazioni è l'operando di destinazione di una delle varie funzioni Interlocked.  Tali operandi devono avere le proprietà aggiuntive specifiche.|  
|`_Write_guarded_by_(expr)`|Annota una variabile e indica se la variabile è modificata, il conteggio dei blocchi dell'oggetto di blocco denominato da `expr` è di almeno uno.|  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle annotazioni SAL per ridurre i difetti del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento (funzione)](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Specificare quando e dove applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Esempi e procedure consigliate](../code-quality/best-practices-and-examples-sal.md)   
 [Blog del Team di analisi del codice](http://go.microsoft.com/fwlink/p/?LinkId=251197)
