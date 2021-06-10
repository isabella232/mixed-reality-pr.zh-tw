---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748505"
---
# <a name="mrtk"></a>[<span data-ttu-id="b21a8-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="b21a8-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b21a8-102">使用 MRTK for Unity 的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 類別，並將 **目標規模** 設定為 **房間** 或 **站**：</span><span class="sxs-lookup"><span data-stu-id="b21a8-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![MRTK 設定視窗](../../images/mrtk-target-scale.png)

<span data-ttu-id="b21a8-104">MRTK 應該會自動處理 playspace 和相機的位置，但最好再次檢查：</span><span class="sxs-lookup"><span data-stu-id="b21a8-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="b21a8-106">從 [階層 **] 面板中，展開 [** **MixedRealityPlayspace** ] GameObject，並尋找 [ **主要攝影機** ] 子物件</span><span class="sxs-lookup"><span data-stu-id="b21a8-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="b21a8-107">在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="b21a8-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="b21a8-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="b21a8-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b21a8-109">在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上設定追蹤原始模式。</span><span class="sxs-lookup"><span data-stu-id="b21a8-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="b21a8-110">取得子系統之後，請呼叫 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="b21a8-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="b21a8-111">並使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。</span><span class="sxs-lookup"><span data-stu-id="b21a8-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![階層中的 XR rig](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="b21a8-113">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="b21a8-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="b21a8-114">移至 **Windows Store Player 設定** 的 [**其他設定**] 區段</span><span class="sxs-lookup"><span data-stu-id="b21a8-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="b21a8-115">選擇 [ **Windows Mixed Reality** ] 作為裝置，可能會列為舊版 Unity 的 **Windows** 全像攝影版</span><span class="sxs-lookup"><span data-stu-id="b21a8-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="b21a8-116">選取 **支援的虛擬實境**</span><span class="sxs-lookup"><span data-stu-id="b21a8-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="b21a8-117">由於主攝影機物件會自動標記為相機，因此 Unity 可支援所有移動和轉譯。</span><span class="sxs-lookup"><span data-stu-id="b21a8-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="b21a8-118">這些設定必須套用至應用程式每個場景中的相機。</span><span class="sxs-lookup"><span data-stu-id="b21a8-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="b21a8-119">依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但未正確套用下列設定。</span><span class="sxs-lookup"><span data-stu-id="b21a8-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="b21a8-120">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b21a8-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b21a8-121">**類型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b21a8-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b21a8-122">若要獲得 **大規模** 或 **房間規模的體驗**，您必須將內容放在地面的相對位置。</span><span class="sxs-lookup"><span data-stu-id="b21a8-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="b21a8-123">您可以使用 **[空間階段](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**（代表使用者定義的樓層層級來源和選擇性的空間界限），在第一次執行期間設定使用者的樓層。</span><span class="sxs-lookup"><span data-stu-id="b21a8-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="b21a8-124">為了確保 Unity 在地面層級的全局座標系統運作，您可以設定並測試 Unity 是否使用 RoomScale 追蹤空間類型：</span><span class="sxs-lookup"><span data-stu-id="b21a8-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="b21a8-125">如果 SetTrackingSpaceType 傳回 true，表示 Unity 已成功切換其全局座標系統，以追蹤 [參考的階段框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="b21a8-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="b21a8-126">如果 SetTrackingSpaceType 傳回 false，則 Unity 無法切換至參考的階段框架，可能是因為使用者未在其環境中設定 floor。</span><span class="sxs-lookup"><span data-stu-id="b21a8-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="b21a8-127">雖然錯誤傳回值並不常見，但如果階段是在不同的房間內設定的，而且裝置會移至目前的房間，而沒有使用者設定新的階段，就可能發生此情況。</span><span class="sxs-lookup"><span data-stu-id="b21a8-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="b21a8-128">一旦您的應用程式成功設定 RoomScale 追蹤空間類型，放在 y = 0 平面上的內容就會出現在樓層上。</span><span class="sxs-lookup"><span data-stu-id="b21a8-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="b21a8-129">0、0、0的原點將是使用者在房間設定期間勇敢面對考驗的特定位置，而-Z 代表在安裝期間所面對的順向方向。</span><span class="sxs-lookup"><span data-stu-id="b21a8-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>