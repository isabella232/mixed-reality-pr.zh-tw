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
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="05af3-104">MaquetteScript 核心語言詳細資料</span><span class="sxs-lookup"><span data-stu-id="05af3-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="05af3-105">![Maquette 標誌 ](../images/MaquetteIcon.png) MaquetteScript 核心語言詳細資料</span><span class="sxs-lookup"><span data-stu-id="05af3-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="05af3-106">存取 `Maquette` 物件和命名空間</span><span class="sxs-lookup"><span data-stu-id="05af3-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="05af3-107">Maquette 會透過物件和其子系，在 JavaScript 中公開內建物件和介面 `Maquette` 。</span><span class="sxs-lookup"><span data-stu-id="05af3-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="05af3-108">這項功能會在 [Maquette 物件和命名空間](https://www.maquette.ms/doc_staging/objects/Maquette.html) 檔中說明。</span><span class="sxs-lookup"><span data-stu-id="05af3-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="05af3-109">`Maquette`物件具有最上層的函式，可讓您更輕鬆地與 Maquette 本身互動，並讓解決重複的問題變得更容易。</span><span class="sxs-lookup"><span data-stu-id="05af3-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="05af3-110">這在 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)的檔中有相關說明。</span><span class="sxs-lookup"><span data-stu-id="05af3-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="05af3-111">Maquette 啟動和載入</span><span class="sxs-lookup"><span data-stu-id="05af3-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="05af3-112">Maquette 會載入並評估特定的 JavaScript 檔案，以便在下列時間啟用設定、設定和初始化：</span><span class="sxs-lookup"><span data-stu-id="05af3-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="05af3-113">在 Maquette 啟動期間：</span><span class="sxs-lookup"><span data-stu-id="05af3-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="05af3-114">每次載入任何專案時：</span><span class="sxs-lookup"><span data-stu-id="05af3-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="05af3-115">專案會載入其各自的專案腳本：</span><span class="sxs-lookup"><span data-stu-id="05af3-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="05af3-116">JavaScript 執行</span><span class="sxs-lookup"><span data-stu-id="05af3-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="05af3-117">Maquette 中使用的 JavaScript 解譯器是以 [Jint](https://github.com/sebastienros/jint)為基礎。</span><span class="sxs-lookup"><span data-stu-id="05af3-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="05af3-118">Jint 與 ECMAScript 5.1 相容，並支援 [ecmascript 6 的其他擴充](https://github.com/sebastienros/jint/issues/343)功能。</span><span class="sxs-lookup"><span data-stu-id="05af3-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="05af3-119">此延伸模組 `.mqjs` 是用來區別 Maquette javascript 檔案與一般 javascript。</span><span class="sxs-lookup"><span data-stu-id="05af3-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="05af3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05af3-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->