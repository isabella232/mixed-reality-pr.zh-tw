---
title: Unity 中的焦點
description: 藉由設定焦點點，在 Unity 中手動調整全息圖穩定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、聚焦點、焦點平面、穩定平面、穩定點、reprojection、LSR、深度緩衝區、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: d2708dcf39f1d2c67ab1abf69f8330f9dd536ab0
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010269"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="0e2d9-104">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="0e2d9-104">Focus point in Unity</span></span>

<span data-ttu-id="0e2d9-105">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="0e2d9-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="0e2d9-106">**類型**： *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="0e2d9-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="0e2d9-107">使用 [焦點](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 來提供 HoloLens，並提供有關如何最好穩定目前顯示的全像投影的提示。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-107">Use the [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) to provide HoloLens with a hint about how to best stabilize the holograms currently being displayed.</span></span>

<span data-ttu-id="0e2d9-108">如果您想要在 Unity 中設定焦點點，則必須使用 *HolographicSettings. SetFocusPointForFrame ( # B1* 來設定每個框架。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="0e2d9-109">如果未設定框架的焦點點，則會使用預設穩定平面。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-109">When the Focus Point isn't set for a frame, the default stabilization plane is used.</span></span>

> [!NOTE]
> <span data-ttu-id="0e2d9-110">依預設，新的 Unity 專案會設定「啟用深度緩衝區共用」選項。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="0e2d9-111">使用此選項時，在沉浸式桌上型耳機或執行 Windows 10 2018 年4月更新 (RS4) 或更新版本的 HoloLens 上執行的 Unity 應用程式，會將您的深度緩衝區提交至 Windows，以自動優化全像影像穩定性，而不需要您的應用程式指定焦點點：</span><span class="sxs-lookup"><span data-stu-id="0e2d9-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="0e2d9-112">在沉浸式桌面耳機上，這會啟用依圖元深度為基礎的 reprojection。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="0e2d9-113">在執行 Windows 10 2018 年4月更新或更新版本的 HoloLens 上，這會分析深度緩衝區以自動挑選最佳的穩定平面。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="0e2d9-114">這兩種方法都應提供更佳的影像品質，而不會讓您的應用程式明確地為每個畫面格選取焦點點。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="0e2d9-115">請注意，如果您要以手動方式提供焦點，這將會覆寫上述的自動行為，而且通常會減少全像全像全像是。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="0e2d9-116">一般而言，當您的應用程式是在尚未更新為 Windows 10 2018 年4月更新的 HoloLens 上執行時，您應該只指定手動焦點點。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="0e2d9-117">範例</span><span class="sxs-lookup"><span data-stu-id="0e2d9-117">Example</span></span>

<span data-ttu-id="0e2d9-118">有許多方式可以設定焦點點，如 *SetFocusPointForFrame* 靜態函式上提供的多載所建議。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="0e2d9-119">以下是一個簡單的範例，可將焦點平面設定為每個框架所提供的物件：</span><span class="sxs-lookup"><span data-stu-id="0e2d9-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> <span data-ttu-id="0e2d9-120">上述的簡單程式碼可能會降低全像物件在使用者背後的焦點物件的穩定性。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-120">The simple code above may reduce hologram stability if the focused object ends up behind the user.</span></span> <span data-ttu-id="0e2d9-121">我們通常會建議您設定 **[啟用深度緩衝區共用](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** ，而不是手動指定焦點點。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-121">We generally recommend setting **[Enable Depth Buffer Sharing](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0e2d9-122">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="0e2d9-122">Next Development Checkpoint</span></span>

<span data-ttu-id="0e2d9-123">如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-123">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="0e2d9-124">您可以從這裡繼續前往下一個主題：</span><span class="sxs-lookup"><span data-stu-id="0e2d9-124">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e2d9-125">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="0e2d9-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="0e2d9-126">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="0e2d9-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e2d9-127">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="0e2d9-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="0e2d9-128">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="0e2d9-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="0e2d9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e2d9-129">See also</span></span>
* [<span data-ttu-id="0e2d9-130">穩定平面</span><span class="sxs-lookup"><span data-stu-id="0e2d9-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
