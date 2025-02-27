# [Estendibilità del debugger di Visual Studio](visual-studio-debugger-extensibility.md)
# [Scelta di una strategia di implementazione del motore di debug](choosing-a-debug-engine-implementation-strategy.md)
# [Creazione di un motore di debug personalizzato](creating-a-custom-debug-engine.md)
## [Registrazione di un motore di debug personalizzato](registering-a-custom-debug-engine.md)
## [Abilitazione di un programma da sottoporre a debug](enabling-a-program-to-be-debugged.md)
### [Recupero di una porta](getting-a-port.md)
### [Registrazione del programma](registering-the-program.md)
### [Collegamento al programma](attaching-to-the-program.md)
### [Collegamento basato su avvio](launch-based-attachment.md)
### [Invio degli eventi richiesti](sending-the-required-events.md)
## [Controllo dell'esecuzione e valutazione dello stato](execution-control-and-state-evaluation.md)
### [Controllo del programma](program-control.md)
### [Metodi correlati al punto di interruzione](breakpoint-related-methods.md)
### [Valutazione dello stack di chiamate](call-stack-evaluation.md)
### [Valutazione dell'espressione](expression-evaluation-visual-studio-debugging-sdk.md)
### [Eventi di controllo](control-events.md)
## [Invio di eventi](sending-events.md)
### [Origini evento](event-sources-visual-studio-sdk.md)
### [Tipi di evento supportati](supported-event-types.md)
### [Descrizioni di eventi](event-descriptions.md)
## [Terminazione e scollegamento](termination-and-detaching.md)
## [Chiamata degli eventi del debugger](calling-debugger-events.md)
### [Collegamento e scollegamento da un programma](attaching-and-detaching-to-a-program.md)
### [Avvio del debugger](launching-the-debugger.md)
### [Terminazione di un programma](terminating-a-program.md)
### [Creazione di un punto di interruzione](creating-a-breakpoint.md)
### [Associazione o disassociazione di un punto di interruzione](when-a-breakpoint-binds-or-becomes-unbound.md)
### [Errori dei punti di interruzione](breakpoint-errors.md)
### [Raggiungimento di un punto di interruzione](hitting-a-breakpoint.md)
### [Eliminazione di un punto di interruzione](deleting-a-breakpoint.md)
### [Attivazione della modalità di interruzione](entering-break-mode.md)
### [Esecuzione di istruzioni in modalità di interruzione](stepping-in-break-mode.md)
### [Valutazione delle espressioni in modalità di interruzione](expression-evaluation-in-break-mode.md)
### [Gestione delle eccezioni](exception-handling-visual-studio-sdk.md)
## [Procedura: Eseguire il debug di un motore di debug personalizzato](how-to-debug-a-custom-debug-engine.md)
# [Introduzione](getting-started-with-debugger-extensibility.md)
## [Guida di orientamento per l'estensione del debugger](roadmap-for-extending-the-debugger.md)
## [Componenti del debugger](debugger-components.md)
### [Pacchetto di debug](debug-package.md)
### [Gestione del debug dei processi](process-debug-manager.md)
### [Gestione del debug delle sessioni](session-debug-manager.md)
### [Motore di debug](debug-engine.md)
### [Modalità operative](operational-modes.md)
### [Analizzatore di espressioni](expression-evaluator.md)
### [Provider di simboli](symbol-provider.md)
### [Visualizzatore di tipi e visualizzatore personalizzato](type-visualizer-and-custom-viewer.md)
## [Concetti relativi al debugger](debugger-concepts.md)
### [Sessione di debug](debug-session.md)
### [Server](servers-visual-studio-sdk.md)
### [Fornitori di porte](port-suppliers.md)
### [Porte](ports.md)
### [Processi](processes.md)
### [Nodi di programma](program-nodes.md)
### [Programmi](programs.md)
### [Thread](threads.md)
### [Stack frame](stack-frames.md)
### [Moduli](modules.md)
### [Punti di interruzione](breakpoints-visual-studio-sdk.md)
## [Contesti del debugger](debugger-contexts.md)
### [Contesto del codice](code-context.md)
### [Posizione nel documento](document-position.md)
### [Contesto del documento](document-context.md)
### [Contesto di valutazione delle espressioni](expression-evaluation-context.md)
## [Attività di debug](debugging-tasks.md)
### [Problemi di sicurezza](security-issues.md)
### [Avvio di un programma](launching-a-program.md)
#### [Notifica della porta](notifying-the-port.md)
#### [Collegamento dopo un avvio](attaching-after-a-launch.md)
### [Collegamento diretto a un programma](attaching-directly-to-a-program.md)
### [Invio degli eventi di avvio dopo un avvio](sending-startup-events-after-a-launch.md)
### [Controllo dell'esecuzione](control-of-execution.md)
### [Associazione di punti di interruzione](binding-breakpoints.md)
### [Valutazione di espressioni](evaluating-expressions.md)
### [Visualizzazione di tipi e dati](visualizing-and-viewing-data.md)
# [Scrittura di un analizzatore di espressioni CLR](writing-a-common-language-runtime-expression-evaluator.md)
## [Common Language Runtime e valutazione delle espressioni](common-language-runtime-and-expression-evaluation.md)
## [Architettura dell'analizzatore di espressioni](expression-evaluator-architecture.md)
### [Contesto di valutazione](evaluation-context.md)
### [Interfacce dell'analizzatore di espressioni chiave](key-expression-evaluator-interfaces.md)
## [Registrazione di un analizzatore di espressioni](registering-an-expression-evaluator.md)
## [Implementazione di un analizzatore di espressioni](implementing-an-expression-evaluator.md)
### [Strategia di implementazione di un analizzatore di espressioni](expression-evaluator-implementation-strategy.md)
## [Visualizzazione di variabili locali](displaying-locals.md)
### [Implementazione di esempio di variabili locali](sample-implementation-of-locals.md)
#### [Implementazione di GetMethodProperty](implementing-getmethodproperty.md)
#### [Enumerazione di variabili locali](enumerating-locals.md)
#### [Recupero delle proprietà locali](getting-local-properties.md)
#### [Recupero dei valori locali](getting-local-values.md)
#### [Valutazione di variabili locali](evaluating-locals.md)
## [Valutazione di un'espressione della finestra Espressioni di controllo](evaluating-a-watch-window-expression.md)
### [Implementazione di esempio di valutazione delle espressioni](sample-implementation-of-expression-evaluation.md)
### [Valutazione di un'espressione di controllo](evaluating-a-watch-expression.md)
## [Modifica del valore di una variabile locale](changing-the-value-of-a-local.md)
### [Implementazione di esempio di modifica dei valori](sample-implementation-of-changing-values.md)
## [Implementazione di visualizzatori di tipi e visualizzatori personalizzati](implementing-type-visualizers-and-custom-viewers.md)
# [Implementazione di un fornitore di porte](implementing-a-port-supplier.md)
## [Implementazione e registrazione di un fornitore di porte](implementing-and-registering-a-port-supplier.md)
## [Interfacce obbligatorie dei fornitori di porte](required-port-supplier-interfaces.md)
# [Elementi interni delle estensioni parallele per .NET Framework](parallel-extension-internals-for-the-dotnet-framework.md)
## [Classe Task](task-class-internal-members.md)
### [Campo m_action](m-action-field.md)
### [Campo m_contingentProperties](m-contingentproperties-field.md)
### [Campo m_parent](m-parent-field.md)
### [Campo m_stateFlags](m-stateflags-field.md)
### [Campo m_stateObject](m-stateobject-field.md)
### [Campo m_taskId](m-taskid-field.md)
### [Campo s_taskIdCounter](s-taskidcounter-field.md)
### [Campo TASK_STATE_CANCELED](task-state-canceled-field.md)
### [Campo TASK_STATE_EXECUTED](task-state-executed-field.md)
### [Campo TASK_STATE_FAULTED](task-state-faulted-field.md)
### [Campo TASK_STATE_RAN_TO_COMPLETION](task-state-ran-to-completion-field.md)
### [Campo TASK_STATE_WAITING_ON_CHILDREN](task-state-waiting-on-children-field.md)
### [Metodo SetNotificationForWaitCompletion](setnotificationforwaitcompletion-method.md)
### [Metodo NotifyDebuggerOfWaitCompletion](notifydebuggerofwaitcompletion-method.md)
## [Classe TaskScheduler](taskscheduler-class-internal-members.md)
### [Metodo GetScheduledTasksForDebugger](getscheduledtasksfordebugger-method.md)
### [Metodo GetTaskSchedulersForDebugger](gettaskschedulersfordebugger-method.md)
## [Classe ContingentProperties](contingentproperties-class-internal-members.md)
### [Campo m_children](m-children-field.md)
## [Struttura AsyncTaskMethodBuilder](asynctaskmethodbuilder-structure-internal-members.md)
### [Proprietà ObjectIdForDebugger](asynctaskmethodbuilder-objectidfordebugger-property.md)
### [Campo m_builder](asynctaskmethodbuilder-m-builder-field.md)
## [AsyncTaskMethodBuilder\<TResult> Structure](asynctaskmethodbuilder-tresult-structure-internal-members.md)
### [Proprietà ObjectIdForDebugger](asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)
### [Campo m_task](asynctaskmethodbuilder-tresult-m-task-field.md)
## [Struttura AsyncVoidMethodBuilder](asyncvoidmethodbuilder-structure-internal-members.md)
### [Proprietà ObjectIdForDebugger](asyncvoidmethodbuilder-objectidfordebugger-property.md)
### [Campo m_objectIdForDebugger](asyncvoidmethodbuilder-m-objectidfordebugger-field.md)
# [Riferimento](reference/reference-visual-studio-debugging-apis.md)
# [Esempi](visual-studio-debugging-samples.md)
