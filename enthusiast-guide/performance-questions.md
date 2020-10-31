---
title: 效能常見問題集
description: 超越標準取用者支援檔的效能 Windows Mixed Reality 疑難排解。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、效能
appliesto:
- Windows 10
ms.openlocfilehash: d6b37f8f6c964222b90fff57f0ba994c14fcaeab
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131962"
---
# <a name="performance-faqs"></a><span data-ttu-id="d6a0b-104">效能常見問題集</span><span class="sxs-lookup"><span data-stu-id="d6a0b-104">Performance FAQs</span></span>

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a><span data-ttu-id="d6a0b-105">我的 Windows Mixed Reality 耳機轉譯（以60Hz 或90Hz 的速率呈現）</span><span class="sxs-lookup"><span data-stu-id="d6a0b-105">Is my Windows Mixed Reality headset rendering at 60Hz or 90Hz framerate</span></span>

<span data-ttu-id="d6a0b-106">如果您的獨立 GPU 具有 HDMI 2.0 埠，而 CPU 有四個以上的實體核心，則應該取得 90 Hz。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-106">If you have a discrete GPU with HDMI 2.0 ports and a CPU with four or more physical cores, you should be getting 90 Hz.</span></span> <span data-ttu-id="d6a0b-107">若要確認，請檢查 **裝置入口網站 > 效能** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-107">To confirm, check the **Device Portal > Performance** tab.</span></span>

<span data-ttu-id="d6a0b-108">注意：如果您的 GPU 只有 HDMI 1.4 輸出，您可以使用 DisplayPort 至 [HDMI 2.0 介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 作為因應措施。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-108">Note: If your GPU only has a HDMI 1.4 output, you can use a DisplayPort to [HDMI 2.0 adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) as a workaround.</span></span>

<span data-ttu-id="d6a0b-109">注意：「耳機顯示器」中的視覺品質設定只會影響 Windows Mixed Reality 首頁體驗的呈現。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-109">Note: The visual quality settings in "Headset display" only affect the rendering of the Windows Mixed Reality home experience.</span></span>

## <a name="my-pc-is-running-slowly"></a><span data-ttu-id="d6a0b-110">我的電腦執行速度很慢</span><span class="sxs-lookup"><span data-stu-id="d6a0b-110">My PC is running slowly</span></span>

<span data-ttu-id="d6a0b-111">基於許多原因，系統可能會變慢，在大部分情況下，這只是幾秒鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-111">The system may be slow for many reasons and in most cases this only last a few seconds.</span></span> <span data-ttu-id="d6a0b-112">如果您在一段長時間內遇到此問題：</span><span class="sxs-lookup"><span data-stu-id="d6a0b-112">If you experience this problem over long periods of time:</span></span>

1. <span data-ttu-id="d6a0b-113">關閉桌面上所有未使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-113">Close all unused application on the desktop.</span></span>
2. <span data-ttu-id="d6a0b-114">確定您的膝上型電腦已插入電源來源。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-114">Ensure that your laptop is plugged into a power source.</span></span>
3. <span data-ttu-id="d6a0b-115">請確定電腦未準備好。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-115">Make sure that the PC is not warming up.</span></span>
4. <span data-ttu-id="d6a0b-116">降低 Windows Mixed Reality 首頁的視覺品質。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-116">Lower the visual quality in your Windows Mixed Reality home.</span></span>
5. <span data-ttu-id="d6a0b-117">確定您的電腦具有最新的 [圖形驅動程式](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) 。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-117">Ensure that you have the latest [graphics drivers](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) for your PC.</span></span>

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a><span data-ttu-id="d6a0b-118">我的電腦在執行混合現實體驗時正在準備。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-118">My PC is warming up as I run the Mixed Reality experiences.</span></span> <span data-ttu-id="d6a0b-119">如何? 保持很酷</span><span class="sxs-lookup"><span data-stu-id="d6a0b-119">How do I keep it cool</span></span>

1. <span data-ttu-id="d6a0b-120">檢查電池是否已收費，以及電源是否插電。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-120">Check that the battery is charged and the power source is plugged in.</span></span>
2. <span data-ttu-id="d6a0b-121">請確定電腦風扇未封鎖。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-121">Make sure that the PC fans are not blocked.</span></span>
3. <span data-ttu-id="d6a0b-122">在相當酷炫的環境中使用電腦。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-122">Use the PC in a relatively cool environment.</span></span>
4. <span data-ttu-id="d6a0b-123">請確定沒有任何熱度來源 (例如，在電腦上) 的太陽或熱度通風。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-123">Make sure there are no heat sources (for example, the sun or heat vents) pointed at the PC.</span></span>

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a><span data-ttu-id="d6a0b-124">我的視覺效果很慢、載入速度很慢，或看起來沒問題</span><span class="sxs-lookup"><span data-stu-id="d6a0b-124">My visuals are choppy, load slowly, or don't look good</span></span>

* <span data-ttu-id="d6a0b-125">請確定您的耳機已插入您電腦上正確的圖形配接器。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-125">Make sure your headset is plugged into the correct graphics card on your PC.</span></span> <span data-ttu-id="d6a0b-126">有些電腦具有整合式和離散的圖形配接器。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-126">Some PCs have both integrated and discrete graphics cards.</span></span> <span data-ttu-id="d6a0b-127">離散卡片通常會提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-127">The discrete card will generally provide the best performance.</span></span> <span data-ttu-id="d6a0b-128">[深入瞭解電腦硬體](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-128">[Learn more about PC hardware](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).</span></span>
* <span data-ttu-id="d6a0b-129">關閉桌面上未使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-129">Close unused applications on your desktop.</span></span>
* <span data-ttu-id="d6a0b-130">確定您的耳機適合 snugly (將它移到較低或更高的位置，或靠左和向右調整) 。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-130">Make sure your headset fits snugly (move it lower and higher, or left and right, to adjust).</span></span>
* <span data-ttu-id="d6a0b-131">在 [ **設定] > 混合現實 > 耳機顯示** 中調整您的耳機視覺效果設定。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-131">Adjust your headset's visual settings in **Settings > Mixed reality > Headset display** .</span></span> <span data-ttu-id="d6a0b-132">當「視覺品質」設定為「自動」時，將會自動選擇您電腦的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-132">When "Visual quality" is set to "Automatic", the mixed reality experience for your PC will be chosen automatically.</span></span> <span data-ttu-id="d6a0b-133">如需更多視覺效果的詳細資訊，請將「視覺品質」設定為「高」。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-133">For more visual detail, set "Visual quality" to "High".</span></span> <span data-ttu-id="d6a0b-134">如果您的視覺效果斷斷續續，請選取較低的設定。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-134">If your visuals are choppy, select a lower setting.</span></span>
* <span data-ttu-id="d6a0b-135">調整耳機校正旋鈕，以確定鏡頭設定為瞳孔 (（稱為 IPD) ）之間的正確距離。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-135">Adjust the headset calibration knob to make sure that the lenses are set to the correct distance between your pupils (called IPD).</span></span> <span data-ttu-id="d6a0b-136">如果您不知道 IPD，optometrist 應該能夠為您測量，或使用設計來測量 IPD 的網站。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-136">If you don't know your IPD, an optometrist should be able to measure it for you, or use a website designed to measure IPD.</span></span> <span data-ttu-id="d6a0b-137">如果耳機沒有校正旋鈕，請選取 [ **設定] > 混合現實 > 耳機顯示** 並調整「校正控制項」。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-137">If the headset doesn't have a calibration knob, select **Settings > Mixed reality > Headset display** and adjust the "Calibration control".</span></span>
* <span data-ttu-id="d6a0b-138">如果您使用的是 USB 或 DisplayPort 至 HDMI 介面卡，請試著另一個。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-138">If you’re using a USB-C or DisplayPort to HDMI adapter, try a different one.</span></span> <span data-ttu-id="d6a0b-139">請參閱 [建議的介面卡。](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</span><span class="sxs-lookup"><span data-stu-id="d6a0b-139">See [recommended adapters.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</span></span>
* <span data-ttu-id="d6a0b-140">中斷任何可能連接到電腦圖形配接器的額外監視器。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-140">Disconnect any extra monitors that may be connected to your PC’s graphics card.</span></span>
* <span data-ttu-id="d6a0b-141">從 Windows 市集中試用一些不同的混合現實應用程式，有些應用程式可能更適合您的電腦設定。</span><span class="sxs-lookup"><span data-stu-id="d6a0b-141">Try some different mixed reality apps from the Windows Store — some may work better with your computer setup.</span></span>
