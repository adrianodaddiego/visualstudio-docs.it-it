---
title: Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703777"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento illustra gli errori di MSBuild che possono verificarsi a causa di problemi di riferimento e indica in che modo è possibile risolvere tali errori.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>È stato fatto riferimento a un progetto o a un assembly destinato a una versione diversa di .NET Framework  
 È possibile creare applicazioni che fanno riferimento a progetti o assembly destinati a versioni diverse di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. È ad esempio possibile creare un'applicazione destinata al profilo client per [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ma che fa riferimento a un assembly destinato a .NET Framework 2.0. Se tuttavia si crea un progetto destinato a una versione precedente di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], non è possibile impostare in tale progetto un riferimento a un progetto o a un assembly destinato al profilo client per [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o per [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] stesso. Per correggere l'errore, assicurarsi che l'applicazione abbia come destinazione profili compatibili con il profilo di destinazione dei progetti o degli assembly a cui fa riferimento.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Come nuova destinazione di un progetto è stata definita una versione diversa di .NET Framework  
 Se si modifica la versione di destinazione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] per l'applicazione, Visual Studio modifica alcuni dei riferimenti. Può tuttavia essere necessario aggiornarne altri in modo manuale. Ad esempio, uno degli errori descritti in precedenza può verificarsi se si modifica un'applicazione in modo che abbia come destinazione [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] e tale applicazione dispone di risorse o impostazioni basate su profilo client per [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)].  
  
 Per ovviare alle impostazioni, aprire **Esplora soluzioni**, scegliere **Mostra tutti i file** e quindi modificare il file app.config nell'editor XML di Visual Studio. Nelle impostazioni modificare la versione in modo che corrisponda alle versione corretta di .NET Framework. È ad esempio possibile modificare l'impostazione della versione da 4.0.0.0 a 2.0.0.0. Analogamente, per un'applicazione che ha aggiunto risorse, aprire **Esplora soluzioni**, scegliere il pulsante **Mostra tutti i file**, espandere **Progetti** (Visual Basic) o **Proprietà** (C#) e quindi modificare il file Resources.resx nell'editor XML di Visual Studio. Modificare l'impostazione della versione da 4.0.0.0 a 2.0.0.0.  
  
 Se l'applicazione dispone di risorse, come icone o bitmap, o di impostazioni, come stringhe di connessione dati, per correggere l'errore è anche possibile rimuovere tutti gli elementi nella pagina **Impostazioni**  di **Creazione progetti** e quindi aggiungere di nuovo le impostazioni necessarie.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Come nuova destinazione di un progetto è stata definita una versione diversa di .NET Framework e non è possibile risolvere i riferimenti  
 Se come nuova destinazione di un progetto è stata definita una versione diversa di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], in alcuni casi è possibile che i riferimenti non vengano risolti correttamente. I riferimenti espliciti completi agli assembly generano spesso questo problema. È tuttavia possibile correggere l'errore rimuovendo i riferimenti non risolti e quindi aggiungendoli di nuovo al progetto. In alternativa, è possibile modificare il file di progetto per sostituire i riferimenti. Rimuovere innanzitutto i riferimenti nel formato seguente:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Sostituirli quindi con il formato semplice seguente:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> Dopo aver chiuso e riaperto il progetto, è necessario ricompilarlo per verificare che tutti i riferimenti vengano risolti correttamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Profilo client .NET Framework](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)
