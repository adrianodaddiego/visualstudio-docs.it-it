---
title: Accesso negato | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9563cafa4895f89253b4073d788240806a86fa2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561078"
---
# <a name="access-is-denied"></a>Accesso negato
Uno script ha cercato di accedere ai dati da un'origine diversa dall'host della pagina corrente. I criteri di corrispondenza dell'origine seguiti da Internet Explorer e da altri browser consentono agli script di accedere ai dati solo da origini con lo stesso schema, host e porta dell'URL della pagina corrente.  
  
 Ad esempio, se la pagina corrente è `https://employees.mycompany.com`, è possibile accedere ai dati dagli URL seguenti:  
  
- `http://data.contoso.com`, perché Usa HTTP anziché HTTPS.  
  
- `https://somedatasource.com`, perché è un dominio diverso.  
  
- `https://employees.mycompany.com:8888`, perché usa una porta diversa.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Controllare se l'API che si sta cercando di chiamare supporta JSONP o CORS, due approcci che consentono lo scripting tra le origini in modo sicuro.  
  
- Se si sta cercando di chiamare un'API REST, effettuare il refactoring di questa chiamata al codice lato server, quindi esporre un nuovo endpoint REST per gli script lato client.  
  
     Per altre informazioni, cercare la documentazione online relativa ai criteri di corrispondenza dell'origine, a JSONP e a CORS.
