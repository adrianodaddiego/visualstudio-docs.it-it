---
title: Preparazione di estensioni per la distribuzione di Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694599"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparazione di estensioni per la distribuzione di Windows Installer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione di file MSI. Questo documento illustra come preparare un progetto di cui l'output predefinito è un pacchetto VSIX per l'inclusione in un progetto di installazione.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparazione di un progetto di estensione per la distribuzione di Windows Installer  
 Eseguire questi passaggi in nuovi progetti di estensione prima di aggiungere a un progetto di installazione.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows Installer  
  
1. Creare un pacchetto VSPackage, del componente MEF, dell'area di controllo dell'Editor o altro tipo di progetto di estendibilità che include un manifesto VSIX.  
  
2. Aprire il manifesto VSIX nell'editor del codice.  
  
3. Impostare l'elemento InstalledByMsi del manifesto VSIX per `true`. Per altre informazioni sul manifesto VSIX, vedere [riferimenti su VSIX Extension Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Ciò impedisce che il programma di installazione VSIX provi a installare il componente.  
  
4. Fare clic sul progetto in **Esplora soluzioni** e fare clic su **proprietà**.  
  
5. Selezionare il **VSIX** scheda.  
  
6. Selezionare la casella **contenuto VSIX copia nel percorso seguente** e digitare il percorso in cui il progetto di installazione verrà prelevati i file.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>L'estrazione dei file da un pacchetto VSIX esistente  
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non è i file di origine.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Estrarre i file da un pacchetto VSIX esistente  
  
1. Rinominare il. File VSIX che contiene l'estensione dal *nomefile*VSIX a *filename*con estensione zip.  
  
2. Copiare il contenuto del file con estensione zip in una directory.  
  
3. Eliminare il file [Content_types] XML dalla directory.  
  
4. Modificare il manifesto VSIX, come illustrato nella procedura precedente.  
  
5. Aggiungere i file rimanenti al progetto di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di programma di installazione di Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procedura dettagliata: Creazione di un'azione personalizzata](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
