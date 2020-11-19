---
title: 核心語言
description: 深入瞭解 Maquette 的核心語言詳細資料。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、原型設計、混合現實、虛擬實境、VR、MR、意見反應、意見反應中樞、bug
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935417"
---
# <a name="maquettescript-core-language-details"></a>MaquetteScript 核心語言詳細資料

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette 標誌 ](../images/MaquetteIcon.png) MaquetteScript 核心語言詳細資料

## <a name="accessing-maquette-object-and-namespace"></a>存取 `Maquette` 物件和命名空間

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette 會透過物件和其子系，在 JavaScript 中公開內建物件和介面 `Maquette` 。 這項功能會在 [Maquette 物件和命名空間](https://www.maquette.ms/doc_staging/objects/Maquette.html) 檔中說明。 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
`Maquette`物件具有最上層的函式，可讓您更輕鬆地與 Maquette 本身互動，並讓解決重複的問題變得更容易。 這在 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)的檔中有相關說明。

## <a name="maquette-startup-and-loading"></a>Maquette 啟動和載入

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette 會載入並評估特定的 JavaScript 檔案，以便在下列時間啟用設定、設定和初始化：

在 Maquette 啟動期間：
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

每次載入任何專案時：
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

專案會載入其各自的專案腳本：
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript 執行

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Maquette 中使用的 JavaScript 解譯器是以 [Jint](https://github.com/sebastienros/jint)為基礎。 Jint 與 ECMAScript 5.1 相容，並支援 [ecmascript 6 的其他擴充](https://github.com/sebastienros/jint/issues/343)功能。 

此延伸模組 `.mqjs` 是用來區別 Maquette javascript 檔案與一般 javascript。

## <a name="see-also"></a>另請參閱 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->