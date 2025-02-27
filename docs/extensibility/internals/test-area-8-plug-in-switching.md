---
title: 'Area di test 8: Cambio di plug-in | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6af0a0333131697526d1ffcc8394f7bfe81ca6b4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327804"
---
# <a name="test-area-8-plug-in-switching"></a>Area di test 8: Cambio di plug-in
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) è l'interfaccia utente (UI) per modificare il controllo del codice sorgente corrente del plug-in. Questa area di test fornisce i test case per il processo di selezione plug-in da usare per la soluzione controllo del codice sorgente che.

## <a name="command-menu-access"></a>Accesso a comandi di Menu
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nei test case vengono usati percorsi di menu ambiente di sviluppo integrato.

- Controllo origine corrente del plug-in: **Gli strumenti** -> **opzioni** -> **controllo del codice sorgente** -> **Selezione plug-in**.

- Modificare l'origine dell'associazione di controllo: **File** -> **controllo del codice sorgente** -> **Modifica controllo del codice sorgente**...

## <a name="common-expected-behavior"></a>Comportamento previsto comune
 Il plug-in per una soluzione di controllo del codice sorgente è possibile modificare senza uscire da Visual Studio o il ricaricamento della soluzione. Inoltre, il controllo del codice sorgente corrente del plug-in modifica automaticamente a quella usata da una soluzione quando tale soluzione è caricata.

## <a name="test-cases"></a>Test case
 Di seguito sono specifici test case per l'area di test di commutazione del plug-in.

### <a name="case-8a-automatic-change"></a>Case 8a: Modifiche automatico

#### <a name="expected-behavior"></a>Comportamento previsto
 Quando un utente viene caricata una soluzione che si trova sotto controllo del codice sorgente, la soluzione viene automaticamente caricata e il plug-in del controllo del codice sorgente appropriato viene selezionata come corrente.

| Operazione | Passi del test | Per verificare i risultati previsti |
| - | - | - |
| Modifica del plug-in controllo origine automatica | 1.  Selezionare plug-nel test come corrente (**degli strumenti** -> **opzioni** -> **controllo del codice sorgente** -> **plug-in Selezione**.)<br />2.  Creare un nuovo progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Selezionare un altro plug-in (ad esempio, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Accettare scaricamento soluzione richiesta.<br />6.  Riaprire la soluzione dal disco. | Soluzione è aperta.<br /><br /> Plug-in sottoposta a test è il controllo del codice sorgente corrente del plug-in. |

### <a name="case-8b-solution-based-change"></a>Case 8b: Modifica basati su soluzioni

#### <a name="expected-behavior"></a>Comportamento previsto
 La soluzione può avere il controllo del codice sorgente associato del plug-in modificato.

| Operazione | Passi del test | Per verificare i risultati previsti |
|----------------------------------| - | - |
| Modifica del plug-in per una soluzione | 1.  Selezionare plug-nel test come corrente (**degli strumenti** -> **opzioni** -> **controllo del codice sorgente** -> **plug-in Selezione**).<br />2.  Creare un nuovo progetto e soluzione.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Dissociare la soluzione dal controllo del codice sorgente (usando il **Modifica controllo del codice sorgente** nella finestra di dialogo).<br />5.  Selezionare un altro plug-in (ad esempio, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Ricaricare la soluzione dal disco se scaricato.<br />7.  Aggiungere la soluzione al controllo del codice sorgente.<br />8.  Dissociare la soluzione dal controllo del codice sorgente (tramite **Modifica controllo del codice sorgente** nella finestra di dialogo).<br />9. Selezione plug-in sottoposta a test nuovamente.<br />10. Ricaricare la soluzione dal disco se scaricato.<br />11. Associare la soluzione nel percorso originale (tramite il **Modifica controllo del codice sorgente** nella finestra di dialogo). | Soluzione viene aggiunta al controllo del codice sorgente usando il plug-in. |

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)