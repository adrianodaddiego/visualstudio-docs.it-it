---
title: Debug del codice di esempio HTML e CSS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 10fda5038ab1c69a27e79406167c69adcc560658
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563474"
---
# <a name="debug-html-and-css-sample-code"></a>Eseguire il debug del codice di esempio HTML e CSS

Il codice in questo argomento è il file di esempio per [Guida introduttiva: Debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md). Gli errori presenti nella guida introduttiva, in base alla progettazione, vengono corretti in questa versione del codice.

## <a name="sample-code"></a>Codice di esempio
Il codice HTML seguente viene usato nel tag \<body> della guida introduttiva.

```html
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"
         style="display:none">
    <div class="fixedItem" >
        <img src="#" data-win-bind="src: flipImg" />
    </div>
</div>
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
</div>
```

Il CSS riportato di seguito mostra le aggiunte apportate a default.css.

```css
#fView {
    background-color:#0094ff;
    height: 500px;
    margin: 25px;
}
```

Nell'esempio di codice seguente viene illustrato il codice JavaScript completo in default.js. I riferimenti agli spazi dei nomi WinJS necessari per questo codice si trovano nel file default.html del modello.

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
        myData[x] = { flipImg: "/images/logo.png" }
    };

    var pages = new WinJS.Binding.List(myData, { proxy: true });

    app.onactivated = function (args) {
        if (args.detail.kind === activation.ActivationKind.launch) {
            if (args.detail.previousExecutionState !==
            activation.ApplicationExecutionState.terminated) {
                // TODO: . . .
            } else {
                // TODO: . . .
            }
            args.setPromise(WinJS.UI.processAll());

            updateImages();
        }
    };

    function updateImages() {

        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    };

    app.oncheckpoint = function (args) {
    };

    app.start();

    var publicMembers = {
        items: pages
    };

    WinJS.Namespace.define("Data", publicMembers);

})();
```

## <a name="see-also"></a>Vedere anche
- [Avvio rapido: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
