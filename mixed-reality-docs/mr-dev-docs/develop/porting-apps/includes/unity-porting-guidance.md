---
ms.openlocfilehash: 0ef22142ac2efc3ef47ece2619d31dbeddcff8fe
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192658"
---
# <a name="project-settings"></a>[專案設定](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. 檢查上面所列的常見移植步驟

請檢查上面所列的常見步驟，以確定您的開發環境已正確設定。 在步驟 #3 中，如果您使用 Visual Studio 您應該選取使用 Unity 工作負載的 **遊戲開發** 。 您可以取消選取「Unity 編輯器選擇性」元件，因為您將在下一個步驟中安裝較新版本的 Unity。

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. 使用 Windows MR 支援升級至 Unity 的最新公開組建
1. 下載 Unity 的最新 [建議公用組建](../../install-the-tools.md) ，並提供混合現實支援。
2. 開始之前，請先儲存專案的複本
3. 如果您的專案是以較舊版本的 Unity 建立的，請參閱升級中 Unity 所提供的 [檔](https://docs.unity3d.com/Manual/UpgradeGuides.html) 。
4. 遵循 Unity 網站上的 [指示](https://docs.unity3d.com/Manual/APIUpdater.html) ，以使用其自動 API 更新程式
5. 檢查並查看是否有其他需要進行的變更，讓您的專案執行，並處理任何剩餘的錯誤和警告。 

> [!Note] 
> 如果您有相依的中介軟體，請確認您使用的是最新版本 () 的步驟3中的詳細資料。

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. 將中介軟體升級至最新版本

使用任何 Unity 更新時，您很可能需要更新您的遊戲或應用程式所依賴的一或多個中介軟體套件。 此外，與最新的中介軟體保持在最新狀態，可提高移植程式其餘部分的成功機率。

### <a name="4-target-your-application-to-run-on-win32"></a>4. 以您的應用程式為目標在 Win32 上執行

從 Unity 應用程式內：

* 流覽至檔案 > 組建設定
* 選取 [電腦、Mac、Linux 獨立]
* 將目標平臺設定為 "Windows"
* 將 [架構] 設定為 [x86] 選取 [切換平臺]

> [!NOTE] 
> 如果您的應用程式對裝置特定服務具有任何相依性，例如從串流進行比對，您必須在此步驟停用它們。 您可以連結到 Windows 稍後提供的對等服務。

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. 設定您的 Windows Mixed Reality 硬體
1. 在[沉浸式耳機設定](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)中檢查步驟
2. 瞭解如何 [使用 Windows Mixed Reality](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 模擬器和 [導覽 Windows Mixed Reality 首頁](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. 將應用程式設為目標，以在 Windows Mixed Reality 上執行
1. 首先，您必須移除或有條件地編譯特定的 VR SDK 專屬的任何其他程式庫支援。 這些資產經常會變更專案的設定和屬性，其方式與其他的 VR Sdk （例如 Windows Mixed Reality）不相容。
    * 例如，如果您的專案參考 SteamVR SDK，您將需要更新您的專案，改為使用 Unity 的通用 VR Api 來支援 Windows Mixed Reality 和 SteamVR。
    * 有條件地排除其他 VR Sdk 的特定步驟即將推出。
2. 在您的 Unity 專案中，以 [WINDOWS 10 SDK 為目標](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. 針對每個場景 [設定相機](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. 使用階段將內容放在樓層上

您可以跨多種 [體驗規模](../../../design/coordinate-systems.md)來建立混合的現實體驗。

如果您要移植的是 **大規模的體驗**，您必須確定 Unity 已設定為 **固定** 的追蹤空間類型：

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

上述程式碼會設定 Unity 的全局座標系統，以追蹤 [固定的參考框架](../../../design/coordinate-systems.md#spatial-coordinate-systems)。 在「固定追蹤」模式中，放在「相機」預設位置前方之編輯器中的內容 (轉寄是-Z) 會在應用程式啟動時出現在使用者前面。 若要 recenter 使用者的原始來源，您可以呼叫 Unity 的 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法。

如果您要移植 **大規模體驗** 或 **房間規模的體驗**，您將會放置相對於樓層的內容。 您可以使用 **[空間階段](../../../design/coordinate-systems.md#spatial-coordinate-systems)**（代表使用者定義的樓層層級來源和選擇性的空間界限），在第一次執行期間設定使用者的樓層。 針對這些經驗，您必須確定 Unity 已設定為 **RoomScale** 追蹤空間類型。 雖然 RoomScale 是預設值，但您會想要明確進行設定，並確保您會得到 true，以找出使用者將電腦移離他們所校正之房間的情況：

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

一旦您的應用程式成功設定 RoomScale 追蹤空間類型，放在 y = 0 平面上的內容就會出現在樓層上。  (0、0、0) 的原點將會是使用者在房間設定期間勇敢面對考驗的特定位置，而-Z 代表在安裝期間所面對的正向方向。

在腳本程式碼中，您可以呼叫 UnityEngine 的 TryGetGeometry 方法，以取得界限多邊形，並指定 TrackedArea 的界限類型。 如果使用者定義了界限， (您取得頂點) 的清單，就可以安全地將 **房間規模的體驗** 提供給使用者，讓他們可以在您建立的場景周圍四處進行。

當使用者進行方法時，系統會自動呈現界限。 您的應用程式不需要使用此多邊形來呈現界限本身。

如需詳細資訊，請參閱 [Unity 頁面中的座標系統](../../unity/coordinate-systems-in-unity.md) 。

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

結果範例：

![結果範例](../../porting-apps/images/largestrectangle-400px.jpg)

演算法是根據 Daniel Smilkov：[多邊形中最大矩形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)的 blog

### <a name="8-work-through-your-input-model"></a>8. 完成輸入模型的工作

以現有 HMD 為目標的每個遊戲或應用程式將會有一組其處理的輸入、體驗所需的輸入類型，以及它所呼叫以取得這些輸入的特定 Api。 我們致力於嘗試使其盡可能簡單明瞭，以充分利用 Windows Mixed Reality 中提供的輸入。

請閱讀相鄰索引標籤中 Unity 的《 [輸入移植指南》](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input) ，以取得 Windows Mixed Reality 如何公開輸入的詳細資料，以及該如何對應至您的應用程式目前所能執行的作業。

### <a name="9-performance-testing-and-tuning"></a>9. 效能測試和微調

Windows Mixed Reality 將可在各式各樣的裝置上使用，範圍從高終端遊戲電腦到廣大市場主流電腦都有。 根據您的目標市場，您應用程式的可用計算和圖形預算有很大的差異。 在此移植練習期間，您可能會運用高階電腦，而且您的應用程式可以使用大量的計算和圖形預算。 如果您想要讓您的應用程式可供更廣大的物件使用，您應該在想 [要作為目標的代表性硬體](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)上測試及分析您的應用程式。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)和[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)都包含效能分析工具，以及[Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)與[Intel](https://software.intel.com/articles/vr-content-developer-guide)發行有關效能分析和優化的指導方針。 在 [瞭解混合現實的效能](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)時，有廣泛的效能討論可供您使用。 此外，unity 的 [效能建議](../../unity/performance-recommendations-for-unity.md)下會有 unity 的特定詳細資料。

# <a name="input-mapping"></a>[輸入對應](#tab/input)

您可以使用下列兩種方法之一來將輸入邏輯移植到 Windows Mixed Reality： Unity 的一般輸入。跨多個平臺的 GetButton/GetAxis Api，或 Windows 特定的 XR。Wsa。輸入 Api，專為運動控制器和 HoloLens 手提供更豐富的資料。

> [!IMPORTANT]
> 如果您使用 HP-UX 的 G2 控制器，請參閱 [這篇文章](../../unity/unity-reverb-g2-controllers.md) 以取得其他輸入對應指示。

## <a name="unity-xr-input-apis"></a>Unity XR 輸入 Api

針對新的專案，我們建議您從頭開始使用新的 XR 輸入 Api。 

您可以在這裡找到有關 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的詳細資訊。

## <a name="inputgetbuttongetaxis-apis"></a>GetButton/GetAxis Api

Unity 目前使用其一般輸入. GetButton/GetAxis Api 來公開 [OCULUS SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 和 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的輸入。 如果您的應用程式已經使用這些 Api 進行輸入，這是在 Windows Mixed Reality 中支援移動控制器最簡單的路徑：您應該只需要重新對應輸入管理員中的按鈕和軸。

如需詳細資訊，請參閱 [unity 按鈕/軸對應表](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 和 [通用 Unity api 的總覽](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 特定 XR。Wsa。輸入 Api

> [!CAUTION]
> 如果您的專案使用任何 XR。WSA Api 在未來的 Unity 版本中，將會以 XR SDK 的方式來淘汰這些 Api。 針對新的專案，我們建議您從一開始就使用 XR SDK。 您可以在 [這裡找到 XR 輸入系統和 api](https://docs.unity3d.com/Manual/xr_input.html)的詳細資訊。

如果您的應用程式已經為每個平臺建立自訂輸入邏輯，您可以選擇使用 **UnityEngine. XR** 命名空間底下的 Windows 特定空間輸入 api。 這可讓您存取額外的資訊，例如位置精確度或來源種類，讓您可以在 HoloLens 上分辨手和控制器。

> [!NOTE]
> 如果您使用 HP-UX 的 G2 控制器，除了 **InteractionSource** 以外，所有輸入 api 仍可繼續運作，但會傳回 false，而不會傳回任何觸控板資料。

如需詳細資訊，請參閱 [UnityEngine. XR. 輸入 api 的總覽](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>底姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的運動控制器，每個控制器的設計各有不同之處，就是使用者的位置與應用程式在轉譯控制器時應使用的自然「向前」方向之間的關聯性。

為了更妥善地表示這些控制器，您可以針對每個互動來源進行兩種調查：

* 底框 **姿勢**，代表 HoloLens 所偵測到之掌上的位置，或是持有運動控制器的掌上。
    * 在沉浸式耳機上，這個姿勢最適合用 **來呈現使用者手** 或 **使用者手中所持有的物件**，例如寶劍或機槍。
    * 把手 **位置**：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。
    * 底 **圖方向的右軸**：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) 
    * 底圖 **方向的向前軸**：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。
    * 底圖 **方向的向上軸**：右邊和向前定義所隱含的向上軸。
    * 您可以透過 Unity 的跨廠商輸入 API (XR 來存取抓住姿勢 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替**) 或透過 Windows 特定 API (**SourceState. SourcePose. TryGetPosition/旋轉**，要求底框姿勢) 。
* **指標姿勢**，代表指向轉寄之控制器的秘訣。
    * 當您在呈現控制器模型本身時 **指向 UI** 時，最好使用這個姿勢來 raycast。
    * 目前，指標姿勢只能透過 Windows 特定 API 來使用 (**sourceState. sourcePose. TryGetPosition/旋轉**，要求指標姿勢) 。

這些姿勢座標全都以 Unity 全局座標表示。
