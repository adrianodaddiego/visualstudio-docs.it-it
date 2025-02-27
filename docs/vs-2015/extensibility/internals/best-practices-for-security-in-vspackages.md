---
title: Procedure consigliate per la sicurezza nei pacchetti VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697275"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedure consigliate per la sicurezza nei pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per installare il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] nel computer, è necessario essere in esecuzione in un contesto con credenziali amministrative. Unità di base di sicurezza e la distribuzione di un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] applicazione è il [VSPackage](../../extensibility/internals/vspackages.md). Un pacchetto VSPackage deve essere registrato utilizzando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], che richiede credenziali amministrative.  
  
 Gli amministratori hanno autorizzazioni complete per scrivere il Registro di sistema e file system e per eseguire qualsiasi codice. È necessario disporre delle autorizzazioni sviluppare, distribuire o installare un pacchetto VSPackage.  
  
 Non appena è installato, un pacchetto VSPackage è completamente attendibile. A causa di questo livello elevato di autorizzazione associata a un pacchetto VSPackage, è possibile installare inavvertitamente un VSPackage contenente dannosi.  
  
 Gli utenti devono assicurarsi che installano i pacchetti VSPackage solo da fonti attendibili. Società di sviluppo di VSPackages fortemente consigliabile assegnare un nome e firmarli, per assicurare che l'utente che manomissioni non è consentita. Società di sviluppo di VSPackages deve esaminare le dipendenze esterne, ad esempio servizi web e l'installazione remota, valutare e correggere eventuali problemi di sicurezza.  
  
 Per altre informazioni, vedere proteggere le linee guida di codifica per .NET Framework ([https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza componenti aggiuntivi](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Sicurezza DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
