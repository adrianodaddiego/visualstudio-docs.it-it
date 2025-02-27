---
title: È stato selezionato un oggetto di database da un provider di database non supportata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d2812e316d17c347341e97ec9594162a2252e4d0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688227"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) supporta solo il Provider di dati .NET Framework per SQL Server (<xref:System.Data.SqlClient>). Anche se è possibile fare clic su **OK** e continuare a usare gli oggetti di provider del database non supportati, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.  
  
> [!NOTE]
> Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Fare clic su **OK** per continuare a progettare le classi di entità con mapping alla connessione che usa il provider del database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.  
  
     -oppure-  
  
- Fare clic su **Annulla**.  
  
     L'azione viene interrotta. Creare o usare una connessione dati che si avvale del provider .NET Framework per SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Provider di dati .NET Framework](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   