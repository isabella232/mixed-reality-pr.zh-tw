---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748520"
---
# <a name="mrtk"></a>[<span data-ttu-id="5fe0e-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="5fe0e-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5fe0e-102">遵循這個 [逐步教學](../../tutorials/mr-learning-base-01.md) 課程，在您的 Unity 專案中新增和自動設定混合現實工具組。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="5fe0e-103">您也可以直接從 MRTK for Unity 使用 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 類別，並將 **目標規模** 設定為 **World**：</span><span class="sxs-lookup"><span data-stu-id="5fe0e-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![MRTK 設定視窗](../../images/mrtk-target-scale.png)

<span data-ttu-id="5fe0e-105">MRTK 應該會自動處理 playspace 和相機的位置，但最好再次檢查：</span><span class="sxs-lookup"><span data-stu-id="5fe0e-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="5fe0e-107">從 [階層 **] 面板中，展開 [** **MixedRealityPlayspace** ] GameObject，並尋找 [ **主要攝影機** ] 子物件</span><span class="sxs-lookup"><span data-stu-id="5fe0e-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="5fe0e-108">在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="5fe0e-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="5fe0e-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="5fe0e-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5fe0e-110">在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上設定追蹤原始模式。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="5fe0e-111">取得子系統之後，請呼叫 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="5fe0e-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="5fe0e-112">您可以針對 HoloLens 應用程式使用 [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) ，其搭配錨點和 ARKit/ARCore 更好用。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![階層中的 AR 會話](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="5fe0e-114">AR 會話和相關功能需要已安裝 AR Foundation。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="5fe0e-115">您也可以手動套用相機變更，而不需要使用 ARSession：</span><span class="sxs-lookup"><span data-stu-id="5fe0e-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="5fe0e-116">選取 **[階層**] 面板中的 [**主要攝影機**]</span><span class="sxs-lookup"><span data-stu-id="5fe0e-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="5fe0e-117">在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="5fe0e-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="5fe0e-118">![Unity 中的 [偵測器] 窗格中的相機](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="5fe0e-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="5fe0e-119">*Unity 中的 [偵測器] 窗格中的相機*</span><span class="sxs-lookup"><span data-stu-id="5fe0e-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="5fe0e-120">將 **TrackedPoseDriver** 新增至 **主要攝影機**</span><span class="sxs-lookup"><span data-stu-id="5fe0e-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="5fe0e-121">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="5fe0e-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="5fe0e-122">選取 **[階層**] 面板中的 [**主要攝影機**]</span><span class="sxs-lookup"><span data-stu-id="5fe0e-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="5fe0e-123">在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="5fe0e-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="5fe0e-124">![Unity 中的 [偵測器] 窗格中的相機](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="5fe0e-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="5fe0e-125">*Unity 中的 [偵測器] 窗格中的相機*</span><span class="sxs-lookup"><span data-stu-id="5fe0e-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="5fe0e-126">移至 **Windows Store Player 設定** 的 [**其他設定**] 區段</span><span class="sxs-lookup"><span data-stu-id="5fe0e-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="5fe0e-127">選擇 [ **Windows Mixed Reality** ] 作為裝置，可能會列為舊版 Unity 的 **Windows** 全像攝影版</span><span class="sxs-lookup"><span data-stu-id="5fe0e-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="5fe0e-128">選取 **支援的虛擬實境**</span><span class="sxs-lookup"><span data-stu-id="5fe0e-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="5fe0e-129">由於主攝影機物件會自動標記為相機，因此 Unity 可支援所有移動和轉譯。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="5fe0e-130">這些設定必須套用至應用程式每個場景中的相機。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="5fe0e-131">依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但可能未正確套用設定。</span><span class="sxs-lookup"><span data-stu-id="5fe0e-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>