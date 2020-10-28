---
title: Unity 中的 HP 回音 G2 控制器
description: 使用 SteamVR 和 Windows Mixed Reality 中的 HP 回音 G2 控制器的指示。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity、回音、回音、HP 回音、mixed reality、開發、移動控制器、使用者輸入、功能、新專案、模擬器、檔、指南、功能、全像遊戲開發
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638385"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="9abe9-104">Unity 中的 HP 回音 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="9abe9-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="9abe9-105">開始使用</span><span class="sxs-lookup"><span data-stu-id="9abe9-105">Getting started</span></span>

<span data-ttu-id="9abe9-106">如果您正在針對 SteamVR 進行開發，或使用 Windows Mixed Reality 輸入 API (XR，則不需要額外的設定，就能使用「HP 回音」 G2 控制器。Wsa。輸入) 。</span><span class="sxs-lookup"><span data-stu-id="9abe9-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="9abe9-107">不過，除非您使用 SteamVR，否則無法透過輸入管理員存取 A、B、X、Y 按鈕和擠壓觸發程式。</span><span class="sxs-lookup"><span data-stu-id="9abe9-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="9abe9-108">在不久的將來，將可支援額外的「回音」 G2 輸入，因此請務必回來查看！</span><span class="sxs-lookup"><span data-stu-id="9abe9-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="9abe9-109">移植現有的應用程式</span><span class="sxs-lookup"><span data-stu-id="9abe9-109">Porting existing applications</span></span>

<span data-ttu-id="9abe9-110">如果您已經有正在為 Windows Mixed Reality 沉浸式耳機開發的現有應用程式，請參閱我們的 [移植指南](../porting-apps/porting-guides.md) 和 [專案設定](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 章節，以取得一般建議。</span><span class="sxs-lookup"><span data-stu-id="9abe9-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="9abe9-111">對應輸入</span><span class="sxs-lookup"><span data-stu-id="9abe9-111">Mapping input</span></span>

<span data-ttu-id="9abe9-112">當您準備好要讓新控制器啟動並執行輸入對應時，請從「沉浸式移植指南」的 [ [輸入對應](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) ] 區段開始。</span><span class="sxs-lookup"><span data-stu-id="9abe9-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="9abe9-113">[筆勢和移動控制器](gestures-and-motion-controllers-in-unity.md)會詳細說明如何在 Unity 中設定輸入的指示，以及用於參考的完整[按鈕和軸對應表](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers)。</span><span class="sxs-lookup"><span data-stu-id="9abe9-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="9abe9-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9abe9-114">See also</span></span>
* [<span data-ttu-id="9abe9-115">更新 SteamVR</span><span class="sxs-lookup"><span data-stu-id="9abe9-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)