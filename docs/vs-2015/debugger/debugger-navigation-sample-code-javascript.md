---
title: Il debugger di codice di esempio di navigazione (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 4e2d1346-91d6-4935-9e70-130e369a4cb7
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6102fd8eace3db19e44a0214ce7ce98278b53eea
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964316"
---
# <a name="debugger-navigation-sample-code-javascript"></a>Codice di esempio della navigazione del debugger (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il codice in questo argomento è il file di esempio per la [controllare l'esecuzione in una sessione di debug (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) argomento.  
  
## <a name="defaultjs-sample-code"></a>codice di esempio default. js  
  
```javascript  
// For an introduction to the Blank template, see the following documentation:  
// http://go.microsoft.com/fwlink/?LinkId=232509  
(function () {  
    "use strict";  
  
    var app = WinJS.Application;  
  
    app.onactivated = function (eventObject) {  
        if (eventObject.detail.kind === Windows.ApplicationModel.Activation.ActivationKind.launch) {  
            if (eventObject.detail.previousExecutionState !== Windows.ApplicationModel.Activation.ApplicationExecutionState.terminated) {  
                // TODO: This application has been newly launched. Initialize   
                // your application here.  
            } else {  
                // TODO: This application has been reactivated from suspension.   
                // Restore application state here.  
            }  
            WinJS.UI.processAll();  
  
        }  
    };  
  
    app.oncheckpoint = function (eventObject) {  
        // TODO: This application is about to be suspended. Save any state  
        // that needs to persist across suspensions here. You might use the   
        // WinJS.Application.sessionState object, which is automatically  
        // saved and restored across suspension. If you need to complete an  
        // asynchronous operation before your application is suspended, call  
        // eventObject.setPromise().   
    };  
  
    app.start();  
    var callTrack = "module function";  
    example1();  
  
    function example1()  
    {  
        var a = 1;  
        var b = 2;  
        callTrack += "->example1";  
        return a + b;  
    }  
  
    function example2()  
    {  
        var a = 3;  
        callTrack += "->example2 ";  
        var x = example2_a();  
        var y = example2_a();  
        var z = example2_b();  
    }  
  
    function example2_a()  
    {  
        var b = 3;  
        callTrack += "->example2_a ";  
        return b;  
    }  
  
    function example2_b()  
    {  
        var c = 3;  
        callTrack += "->example2_b ";  
        return c;  
    }  
  
    function example3() {  
        var s = "";  
        for (var i = 0; i < 1000; i++) {  
            s += i.toString() + "\n";  
        }  
        callTrack += "->example3 ";  
        return 1;  
  
    }  
  
    function example4() {  
        var b = 4;  
        var a = example4_a(2);  
        callTrack += "->example4";  
        var multiplyByA = multiClosure(a);  
        a = 20;  
        var x = multiplyByA(b);  
        return x;  
    }  
  
    function example4_a(x) {  
        var y = 2;  
        return x + y;  
    }  
  
    function multiClosure(num) {  
        var a = num;  
        function multiplyXby(b) {  
            callTrack += "->multiplyXby";  
            return a * b;  
        }  
        return multiplyXby;  
    }  
  
    function example5() {  
         var a = 1;  
         callTrack += "->example5";  
         a += example5_a();  
         return a;  
     }  
  
     function example5_a() {  
         var a = 1;  
         callTrack += "->example5_a";  
         a += example5_b();  
         return a;  
     }  
  
     function example5_b() {  
         var a = 1;  
         callTrack += "->example5_b";  
         a += example5_c();  
         return a;  
     }  
  
     function example5_c() {  
         var a = 1;  
         callTrack += "->example5_c";  
         a += example5_d();  
         return a;  
     }  
  
     function example5_d() {  
         var a = 1;  
         callTrack += "->example5_d";  
         a += example5_e();  
         return a;  
     }  
  
     function example5_e() {  
         var a = 1;  
         callTrack += "->example5_e";  
         return a;  
     }  
  
 })();  
  
```
