---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748486"
---
# <a name="mrtk"></a>[<span data-ttu-id="53212-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="53212-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="53212-102">使用 MRTK for Unity 中的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 類別，並將 **目標縮放** 設定為 [已 **安裝**]：</span><span class="sxs-lookup"><span data-stu-id="53212-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![MRTK 設定視窗](../../images/mrtk-target-scale.png)

<span data-ttu-id="53212-104">MRTK 應該會自動處理 playspace 和相機的位置，但最好再次檢查：</span><span class="sxs-lookup"><span data-stu-id="53212-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="53212-106">從 [階層 **] 面板中，展開 [** **MixedRealityPlayspace** ] GameObject，並尋找 [ **主要攝影機** ] 子物件</span><span class="sxs-lookup"><span data-stu-id="53212-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="53212-107">在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="53212-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="53212-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="53212-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="53212-109">在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上設定追蹤原始模式。</span><span class="sxs-lookup"><span data-stu-id="53212-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="53212-110">取得子系統之後，請呼叫 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="53212-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="53212-111">並使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。</span><span class="sxs-lookup"><span data-stu-id="53212-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![階層中的 XR rig](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="53212-113">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="53212-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="53212-114">移至 **Windows Store Player 設定** 的 [**其他設定**] 區段</span><span class="sxs-lookup"><span data-stu-id="53212-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="53212-115">選擇 [ **Windows Mixed Reality** ] 作為裝置，可能會列為舊版 Unity 的 **Windows** 全像攝影版</span><span class="sxs-lookup"><span data-stu-id="53212-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="53212-116">選取 **支援的虛擬實境**</span><span class="sxs-lookup"><span data-stu-id="53212-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="53212-117">由於主攝影機物件會自動標記為相機，因此 Unity 可支援所有移動和轉譯。</span><span class="sxs-lookup"><span data-stu-id="53212-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="53212-118">這些設定必須套用至應用程式每個場景中的相機。</span><span class="sxs-lookup"><span data-stu-id="53212-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="53212-119">依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但未正確套用下列設定。</span><span class="sxs-lookup"><span data-stu-id="53212-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="53212-120">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="53212-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="53212-121">**類型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="53212-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="53212-122">若要建立 **僅限方向** 或內部 **規模的體驗**，您必須將 Unity 設定為「固定追蹤空間」類型。</span><span class="sxs-lookup"><span data-stu-id="53212-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="53212-123">固定追蹤空間會設定 Unity 的全局座標系統，以追蹤 [固定的參考框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="53212-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="53212-124">在「固定追蹤」模式中，放在「相機」預設位置前方之編輯器中的內容 (轉寄是-Z) 將會在應用程式啟動時出現在使用者前面。</span><span class="sxs-lookup"><span data-stu-id="53212-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="53212-125">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="53212-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="53212-126">**類型：** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="53212-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="53212-127">若要取得純 **方向的體驗** （例如360度的影片檢視器） (其中的位置標頭更新會使假像) 損毀，您可以接著設定 [XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 至 true：</span><span class="sxs-lookup"><span data-stu-id="53212-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="53212-128">針對內部 **規模的體驗**，讓使用者稍後 recenter 已安裝的來源，您可以呼叫 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：</span><span class="sxs-lookup"><span data-stu-id="53212-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="53212-129">如果您要建立 [大規模的體驗](../../../../design/coordinate-systems.md)，您可以藉由呼叫 XR，在使用者目前的標頭位置 recenter Unity 的世界原點 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="53212-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>