---
title: 開始手勢
description: 瞭解如何使用開始手勢來呼叫 HoloLens 上的 [開始] 功能表，以及 Windows Mixed Reality 沉浸式耳機。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合的現實、手勢、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、bloom
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583229"
---
# <a name="start-gesture"></a><span data-ttu-id="0a7a9-104">開始手勢</span><span class="sxs-lookup"><span data-stu-id="0a7a9-104">Start gesture</span></span>

<span data-ttu-id="0a7a9-105">開始手勢是用來叫用 [開始] 功能表的手手勢。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="0a7a9-106">這相當於按下鍵盤上的 Windows 鍵、Xbox 控制器上的 Xbox 按鈕，或沉浸式耳機移動控制器上的 Windows 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="0a7a9-107">請特別注意每個混合現實裝置上的保留系統手勢，以避免在設計互動時產生衝突。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="0a7a9-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0a7a9-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0a7a9-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="0a7a9-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="0a7a9-110"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0a7a9-110"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0a7a9-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0a7a9-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0a7a9-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="0a7a9-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0a7a9-113">盛開</span><span class="sxs-lookup"><span data-stu-id="0a7a9-113">Bloom</span></span></td>
        <td><span data-ttu-id="0a7a9-114">✔️</span><span class="sxs-lookup"><span data-stu-id="0a7a9-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="0a7a9-115">手腕按鈕</span><span class="sxs-lookup"><span data-stu-id="0a7a9-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="0a7a9-116">✔️</span><span class="sxs-lookup"><span data-stu-id="0a7a9-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="0a7a9-117">眼睛和棕櫚</span><span class="sxs-lookup"><span data-stu-id="0a7a9-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="0a7a9-118">✔️</span><span class="sxs-lookup"><span data-stu-id="0a7a9-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="0a7a9-119">盛開</span><span class="sxs-lookup"><span data-stu-id="0a7a9-119">Bloom</span></span>

<span data-ttu-id="0a7a9-120">我們設計了 "Bloom"，將 HoloLens 中的 [開始] 功能表 (第一代) ，也就是模擬花卉櫻花的符號手勢。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="0a7a9-121">它是確定-footed 互動、簡單易用以及快速重新叫用的獨特方式。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="0a7a9-122">若要使用手勢，請將您的手中的手朝您手上一處，然後散佈手指來開啟您的手。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0a7a9-123">![Bloom 關閉](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="0a7a9-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="0a7a9-124">**步驟1：輕鬆搭配使用**</span><span class="sxs-lookup"><span data-stu-id="0a7a9-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="0a7a9-125">![Bloom 開啟](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="0a7a9-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="0a7a9-126">**步驟2：使用輕鬆散佈的掌上**</span><span class="sxs-lookup"><span data-stu-id="0a7a9-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="0a7a9-127">開始手勢</span><span class="sxs-lookup"><span data-stu-id="0a7a9-127">Start gesture</span></span>

<span data-ttu-id="0a7a9-128">在 HoloLens 2 中，我們將 Bloom 手勢取代為虛擬手腕按鈕，這對使用者來說更 instinctual。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="0a7a9-129">藉由顯示使用者手腕上的按鈕，可以直覺地聯繫，並將其與他人一起按。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0a7a9-130">![手腕按鈕就緒](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="0a7a9-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="0a7a9-131">**步驟1：掌上一步，顯示手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="0a7a9-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="0a7a9-132">![手腕按鈕按下](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="0a7a9-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="0a7a9-133">**步驟2：按手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="0a7a9-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="0a7a9-134">單向開始手勢</span><span class="sxs-lookup"><span data-stu-id="0a7a9-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a7a9-135">若要讓右手開始手勢正常運作：</span><span class="sxs-lookup"><span data-stu-id="0a7a9-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="0a7a9-136">您必須更新為2019年11月更新 (組建 18363.1039) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="0a7a9-137">您的眼睛必須在裝置上校正，讓眼睛追蹤能夠正常運作。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="0a7a9-138">如果您看不到 [開始] 圖示周圍的軌道點，則裝置上不會校正您的眼睛。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="0a7a9-139">您也可以只使用一手勢來使用開始手勢。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="0a7a9-140">將您手上的手向您手上，看看您的內部手腕上的 [ **開始] 圖示** 。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="0a7a9-141">**當您隨時留意圖示時**，請將您的 thumb 和索引手指放在一起。</span><span class="sxs-lookup"><span data-stu-id="0a7a9-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="0a7a9-142">![手腕按鈕就緒](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="0a7a9-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="0a7a9-143">**步驟1：掌上一步，顯示手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="0a7a9-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="0a7a9-144">![手腕按鈕縮小](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="0a7a9-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="0a7a9-145">**步驟2：按鈕上的眼睛，然後縮小**</span><span class="sxs-lookup"><span data-stu-id="0a7a9-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="0a7a9-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a7a9-146">See also</span></span>

* [<span data-ttu-id="0a7a9-147">本能互動</span><span class="sxs-lookup"><span data-stu-id="0a7a9-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0a7a9-148">眼睛</span><span class="sxs-lookup"><span data-stu-id="0a7a9-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="0a7a9-149">語音輸入</span><span class="sxs-lookup"><span data-stu-id="0a7a9-149">Voice input</span></span>](voice-input.md)