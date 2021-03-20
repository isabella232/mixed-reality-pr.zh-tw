---
title: HoloLens (第1代) 空間 230-空間對應
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解空間對應概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、空間對應、表面重建、網格、HoloLens、混合現實學院、unity、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 933b5d331e814cdb2ced2689e06e0c8508f2d68a
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730135"
---
# <a name="hololens-1st-gen-spatial-230-spatial-mapping"></a>HoloLens (第1代) 空間230：空間對應

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](./mr-learning-base-01.md)。

[空間對應](../../../design/spatial-mapping.md) 結合了真實世界和虛擬世界，藉由教授有關環境的影像。 在 MR 空間 230 (Project 天文館) 我們將瞭解如何：

* 掃描環境，並將資料從 HoloLens 傳送至您的開發電腦。
* 探索著色器，並學習如何使用它們來視覺化您的空間。
* 使用網格處理將房間網格細分為簡單的平面。
* 超越我們在 [MR 基礎 101](../../../develop/unity/tutorials/holograms-101.md)中學習到的放置技術，並提供可在環境中放置全息圖的相關意見反應。
* 探索遮蔽效果，如此一來，當您的全像是真實世界的物件之後，您仍然可以透過 x 光線視覺來看到它！

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Spatial 230：空間對應</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>在您開始使用 Intune 之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。
* 一些基本的 c # 程式設計功能。
* 您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。
* [針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 檔案。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。
  * 如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。
  * 如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)取得。

### <a name="notes"></a>備註

* 在 Visual Studio 中必須停用 [啟用 Just My Code] (*取消* 核取 [工具] > [選項] > [選項] 下的) ，才能在程式碼中叫用中斷點。

## <a name="unity-setup"></a>Unity 設定

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* 啟動 **Unity**。
* 選取 [ **新增** ] 以建立新專案。
* 將專案命名為 **天文館**。
* 確認已選取 [ **3d** ] 設定。
* 按一下 [ **建立專案**]。
* Unity 啟動後，請移至 **> Player 的 [編輯 > 專案設定**]。
* 在 [偵測 **器** ] 面板中，尋找並選取綠色的 **Windows 商店** 圖示。
* 展開 [ **其他設定**]。
* **在 [轉譯] 區段中**，檢查 **虛擬實境支援** 的選項。
* 確認 **Windows** 全像是出現在 **虛擬實境 sdk** 清單中。 如果沒有，請選取 **+** 清單底部的按鈕，然後選擇 [ **Windows** 全像]。
* 展開 [ **發行設定**]。
* 在 [ **功能** ] 區段中，檢查下列設定：
    * InternetClientServer
    * PrivateNetworkClientServer
    * 麥克風
    * SpatialPerception
* 移至 [ **編輯] > 專案設定 > 品質**
* 在 [偵測 **器** ] 面板的 [Windows 市集中] 圖示底下，選取 [預設] 資料列底下的黑色下拉箭號，並將預設設定變更為 [ **非常低**]。
* 移至 [ **資產] > 匯入套件 > 自訂套件**。
* 流覽至 **..\holographicacademy-holograms-230-SpatialMapping\Starting** 資料夾。
* 按一下 [ **天文館 unitypackage**]。
* 按一下 [開啟]。
* 隨即出現 [匯 **入 Unity 套件** ] 視窗，請按一下 [匯 **入** ] 按鈕。
* 等候 Unity 匯入完成此專案所需的所有資產。
* **在 [階層] 面板中**，刪除 **主要攝影機**。
* 在 [ **專案** ] 面板的 [ **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** ] 資料夾中，尋找 [ **主要攝影機** ] 物件。
* 將 **主要攝影機** 預製專案拖放到 [階層 **] 面板中** 。
* **在 [階層] 面板中**，刪除 **方向光源** 物件。
* 在 [ **專案** ] 面板的 [全像 **] 資料夾中，找** 出 **游標** 物件。
* 拖曳 & 將資料 **指標** 預製專案拖放到階層 **中。**
* **在 [階層] 面板中**，選取 [資料 **指標**] 物件。
* 在 [偵測 **器** ] 面板中，按一下 [ **圖層** ] 下拉式清單，然後選取 [ **編輯圖層**]。
* 將 **使用者第 31** 名命名為 "**SpatialMapping**"。
* 儲存新場景： **File > 另存場景為**.。。
* 按一下 [ **新增資料夾** ]，然後將資料夾命名為 **幕後**。
* 將檔案命名為 "**天文館**"，並將它儲存在 **幕後** 資料夾中。

## <a name="chapter-1---scanning"></a>第1章-掃描

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**目標**

* 瞭解 SurfaceObserver 及其設定如何影響體驗和效能。
* 建立房間掃描體驗來收集房間的網格。

**指示**

* 在 **專案** 面板的 [ **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** ] 資料夾中，尋找 **SpatialMapping** 預製專案。
* 將 [ **SpatialMapping** ] 預製專案拖曳 & 放入 [階層 **] 面板中** 。

**組建和部署 (第1部)**

* 在 Unity 中，選取 [ **File > Build Settings**]。
* 按一下 [ **新增開啟的場景** ]，將 **天文館** 場景新增至組建。
* 在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。
* 將 **SDK** 設定為 **通用 10** ，並將 **UWP 組建類型** 設定為 **D3D**。
* 檢查 **Unity c # 專案**。
* 按一下 [建置]。
* 建立名為 "App" 的 **新資料夾** 。
* 按一下 **應用程式** 資料夾。
* 按下 [ **選取資料夾** ] 按鈕。
* 當 Unity 完成建立時，將會出現檔案總管視窗。
* 按兩下 **應用程式** 資料夾以開啟它。
* 按兩下 [ **天文館** ]，在 Visual Studio 中載入專案。
* 在 Visual Studio 中，使用頂端工具列將設定變更為 [ **發行**]。
* 將平臺變更為 **x86**。
* 按一下 [本機電腦] 右邊的下拉箭號，然後選取 [ **遠端電腦**]。
* 在 [位址] 欄位中輸入 [您裝置的 IP 位址](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) ，並將驗證模式變更為 **通用 (未加密的通訊協定)**。
* 按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。
* 觀賞 Visual Studio 中的 [ **輸出** ] 面板，以取得組建和部署狀態。
* 當您的應用程式部署完成後，請四處移動空間。 您將會看到黑色和白色線框網格所涵蓋的周圍表面。
* 掃描您的環境。 請務必查看牆、上限和樓層。

**組建和部署 (第2部分)**

現在讓我們來探索空間對應會如何影響效能。

* 在 Unity 中，選取 [ **Window > Profiler]**。
* 按一下 [ **新增 Profiler > GPU**]。
* 按一下 [ **Active Profiler <Enter IP> >**]。
* 輸入 HoloLens 的 **IP 位址** 。
* 按一下 [連線]。
* 觀察 GPU 呈現框架所需的毫秒數。
* 停止應用程式在裝置上執行。
* 返回 Visual Studio 並開啟 **SpatialMappingObserver。** 您會在 Assembly-CSharp (通用 Windows) 專案的 HoloToolkit\SpatialMapping 資料夾中找到它。
* 尋找 **喚醒的 ()** 函式，並加入下列程式程式碼： **TrianglesPerCubicMeter = 1200;**
* 將專案重新部署至您的裝置，然後 **重新連接** 分析工具。 觀察轉譯畫面格的毫秒數變更。
* 停止應用程式在裝置上執行。

**在 Unity 中儲存和載入**

最後，讓我們來儲存房間網格並將它載入 Unity 中。

* 返回 Visual Studio，並移除您在上一節中于 **喚醒 ()** 函數中新增的 **TrianglesPerCubicMeter** 行。
* 將專案重新部署至您的裝置。 我們現在應該以每個三立方計量的 **500** 三角形來執行。
* 開啟瀏覽器並輸入您的 HoloLens IPAddress，以流覽至 **Windows 裝置入口網站**。
* 選取左面板中的 [ **3D 視圖** ] 選項。
* 在 [ **表面重建** ] 下，選取 [ **更新** ] 按鈕。
* 請注意，您在 HoloLens 上掃描的區域會出現在 [顯示] 視窗中。
* 若要儲存您的房間掃描，請按 [ **儲存** ] 按鈕。
* 開啟您的 [**下載**] 資料夾，以尋找已儲存的房間模型 **SRMesh。**
* 將 **SRMesh** 複製到 Unity 專案的 [ **資產** ] 資料夾中。
* 在 Unity 中，選取 **階層面板中的 [** **SpatialMapping** ] 物件。
* 找出 **物件介面觀察器 (腳本)** 元件。
* 按一下 [ **房間模型** ] 屬性右邊的圓形。
* 尋找並選取 [ **SRMesh** ] 物件，然後關閉視窗。
* 確認 [**檢查**] 面板中的 [**房間模型**] 屬性現在已設定為 [ **SRMesh**]。
* 按下 [ **播放** ] 按鈕以進入 Unity 的預覽模式。
* SpatialMapping 元件會從已儲存的房間模型載入網格，讓您可以在 Unity 中使用它們。
* 切換至 **場景** 視圖，以查看以線框著色器顯示的所有房間模型。
* 再按一次 [ **播放** ] 按鈕以結束預覽模式。

**注意：** 下次您在 Unity 中進入預覽模式時，預設會載入儲存的房間網格。

## <a name="chapter-2---visualization"></a>第2章-視覺效果

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**目標**

* 瞭解著色器的基本概念。
* 視覺化您的環境。

**指示**

* 在 Unity 的 **階層面板中** ，選取 [ **SpatialMapping** ] 物件。
* 在 [偵測 **器** ] 面板中，尋找 **(腳本) 元件的空間對應管理員** 。
* 按一下 [ **Surface 材質** ] 屬性右邊的圓形。
* 尋找並選取 **BlueLinesOnWalls** 材質，然後關閉視窗。
* 在 [ **專案** 面板 **著色** 器] 資料夾中，按兩下 [ **BlueLinesOnWalls** ] 以開啟 Visual Studio 中的著色器。
* 這是一個簡單的圖元 (頂點到片段) 著色器，它會完成下列工作：
    1. 將頂點的位置轉換成世界空間。
    2. 檢查頂點的一般，以判斷圖元是否為垂直。
    3. 設定用來呈現的圖元色彩。

**組建和部署**

* 返回 Unity，然後按下 [ **播放** ] 進入預覽模式。
* 系統會在房間網格的所有垂直表面上轉譯藍線 (這會從已儲存的掃描資料) 自動載入。
* 切換至 [ **場景** ] 索引標籤，以調整您的房間視圖，並查看整個房間網格在 Unity 中的顯示方式。
* 在 [ **專案** ] 面板中，尋找 [ **材質** ] 資料夾，並選取 **BlueLinesOnWalls** 材質。
* 修改某些屬性，並查看如何在 Unity 編輯器中顯示變更。
    * 在 [偵測 **器** ] 面板中，調整 **LineScale** 值，讓線條顯示為較粗或更細。
    * 在 [偵測 **器** ] 面板中，調整 **LinesPerMeter** 值以變更每個牆上出現的行數。
* 按一下 [ **播放** ] 以結束預覽模式。
* 建立並部署至 HoloLens，並觀察著色器轉譯如何顯示在實際表面上。

Unity 有很大的預覽材質，但最好是在裝置中簽出轉譯的好主意。

## <a name="chapter-3---processing"></a>第3章-處理

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**目標**

* 瞭解處理空間對應資料以在應用程式中使用的技術。
* 分析空間對應資料以尋找平面和移除三角形。
* 使用平面來放置全息圖。

**指示**

* 在 Unity 的 [ **專案** ] **面板中，** [全像] 資料夾中，尋找 **SpatialProcessing** 物件。
* 將 **SpatialProcessing** 物件拖曳 & 放入 [階層 **] 面板中** 。

SpatialProcessing 預製專案包含處理空間對應資料的元件。 **SurfaceMeshesToPlanes** 會根據空間對應資料尋找並產生平面。 我們將在應用程式中使用平面來代表牆壁、樓層和上限。 此預製專案也包含可從空間對應網格移除頂點的 **RemoveSurfaceVertices。** 這可以用來在網格中建立洞，或移除不再需要的多餘三角形 (因為可以改用平面來取代) 。

* 在 Unity 的 [ **專案** ] **面板中，** [全像] 資料夾中，尋找 **SpaceCollection** 物件。
* 將 **SpaceCollection** 物件拖放 **到 [階層** ] 面板中。
* **在 [階層] 面板中**，選取 [ **SpatialProcessing** ] 物件。
* 在 [偵測 **器** ] 面板中，尋找 [ **播放空間管理員] (腳本)** 元件。
* 按兩下 **PlaySpaceManager** ，在 Visual Studio 中開啟。

PlaySpaceManager 包含應用程式特定的程式碼。 我們將在此腳本中新增功能，以啟用下列行為：

1. 超過掃描時間限制 (10 秒) 之後，停止收集空間對應資料。
2. 處理空間對應資料：
    1. 使用 SurfaceMeshesToPlanes 來建立更簡單的世界表示，作為平面 (牆壁、樓層、上限等) 。
    2. 使用 RemoveSurfaceVertices 來移除落在平面邊界內的表面三角形。
3. 產生世界各地的全像投影集合，並將它們放在靠近使用者的牆和地面平面上。

完成標示在 PlaySpaceManager 中的程式碼撰寫練習，或將腳本取代為以下的完成解決方案：

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**組建和部署**

* 部署到 HoloLens 之前，請按 Unity 中的 [ **播放** ] 按鈕進入播放模式。
* 從檔案載入空間網格之後，請等候10秒鐘，然後在空間對應網格上開始處理。
* 當處理完成時，平面會顯示為代表樓層、牆壁、上限等等。
* 找到所有的平面之後，您應該會看到日光系統出現在相機附近的桌子上。
* 兩個海報也應該出現在相機附近的牆上。 如果您無法在 **遊戲** 模式中看到，請切換至 [**場景**] 索引標籤。
* 再按一次 [ **播放** ] 按鈕以結束播放模式。
* 照常建立並部署到 HoloLens。
* 等候空間對應資料的掃描和處理完成。
* 一旦您看到了飛機，請試著找出您世界中的日光系統和海報。

## <a name="chapter-4---placement"></a>第4章-放置

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**目標**

* 判斷是否要在表面上容納全像影像。
* 當您的影像可在表面上無法容納時，為使用者提供意見反應。

**指示**

* 在 Unity 的 **階層面板中** ，選取 [ **SpatialProcessing** ] 物件。
* 在 [偵測 **器** ] 面板中，尋找 **平面網格以 (腳本)** 元件。
* 將 [ **繪製平面** ] 屬性變更為 [ **Nothing** ] 以清除選取專案。
* 將 **Draw 平面** 屬性變更為 **牆**，如此就只會轉譯牆壁平面。
* 在 [ **專案** ] 面板的 [ **腳本** ] 資料夾中，按兩下可 **放置的 .cs** ，在 Visual Studio 中開啟。

可 **放置** 的腳本已附加至在完成平面尋找之後所建立的海報和投影方塊。 我們只需要取消批註一些程式碼，這個腳本就能達成下列目標：

1. 從周框 cube 的中央和四個角落 raycasting，判斷是否要在表面上容納全像影像。
2. 檢查 surface normal，判斷是否有足夠的空間可讓全像影像排清。
3. 轉譯影像周圍的周框 cube，以在放置時顯示其實際大小。
4. 將陰影轉換下/後方的陰影，以顯示將放置在地面/牆上的位置。
5. 如果無法在表面上放置全像影像，則將陰影轉譯為紅色，如果可能的話，則呈現綠色。
6. 重新排列影像的方向，使其與具有親和性的表面類型 (垂直或水準) 對齊。
7. 順暢地將全像放置在選取的介面上，以避免跳躍或貼齊行為。

取消批註下列程式碼撰寫練習中的所有程式碼，或在可放置的中使用這個已完成的解決方案 **。 .cs**：

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**組建和部署**

* 同樣地，建立專案並部署到 HoloLens。
* 等候空間對應資料的掃描和處理完成。
* 當您看到日光系統時，請在下方的投射方塊中看看，並執行選取手勢來四處移動。 選取 [投射] 方塊時，會在投影方塊周圍顯示周框 cube。
* 將您移至房間的不同地點。 投影方塊應在您的注視之後。 當投影方塊下方的陰影變成紅色時，您就無法將全像放在表面上。 當投影方塊下方的陰影變成綠色時，您可以藉由執行另一個選取手勢來放置全像投影。
* 尋找並選取牆上的其中一個全息海報，將其移至新位置。 請注意，您不能將海報放在地面或最上方，而且當您四處移動時，它仍會正確地導向每個牆。

## <a name="chapter-5---occlusion"></a>第5章-遮蔽

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**目標**

* 判斷空間對應網格是否 pixels occluded 全像影像。
* 套用不同的遮蔽技術，以達成有趣的效果。

**指示**

首先，我們要讓空間對應網格遮蔽其他的全像不遮蔽真實世界的影像：

* **在 [階層] 面板中**，選取 [ **SpatialProcessing** ] 物件。
* 在 [偵測 **器** ] 面板中，尋找 [ **播放空間管理員] (腳本)** 元件。
* 按一下 **次要材質** 屬性右邊的圓形。
* 尋找並選取 **遮蔽** 材質，然後關閉視窗。

接下來，我們要將特殊行為新增至地球，使其在另一個全息圖 (（例如 sun) 或空間對應網格） pixels occluded 時有藍色反白顯示：

* 在 [ **專案** ] 面板的 [全像 **] 資料夾中** ，展開 [ **SolarSystem** ] 物件。
* 按一下 [ **地球**]。
* 在 [偵測 **器** ] 面板中，找出地球的材質 (底部的元件) 。
* 在 [ **著色器] 下拉式** 清單中，將著色器變更為 **自訂 > OcclusionRim**。 如果有另一個物件 pixels occluded，這會在地球周圍呈現藍色醒目提示。

最後，我們要為日光系統中的行星啟用 x 光線視覺效果。 我們必須在 Scripts\SolarSystem 資料夾) 中編輯 **PlanetOcclusion** (，才能達到下列目標：

1. 判斷 SpatialMapping 層是否 pixels occluded 行星 (房間網格和平面) 。
2. 當 SpatialMapping 圖層 pixels occluded 時，顯示行星的線框表示。
3. 隱藏 SpatialMapping 圖層未封鎖之行星的線框表示。

遵循 PlanetOcclusion 中的程式碼練習，或使用下列解決方案：

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**組建和部署**

* 照常建立應用程式，並將其部署到 HoloLens。
* 等候空間對應資料的掃描和處理完成， (您應該會看到藍線出現在) 的牆上。
* 尋找並選取日光系統的投射方塊，然後在某個牆旁邊或在計數器後方設定方塊。
* 您可以藉由在海報或投影方塊上隱藏對等的背後表面來查看基本遮蔽。
* 找出地球，每次出現在另一個全息圖或表面上時，應該會有藍色的強調效果。
* 當行星在房間後方或其他表面上移動時，請觀賞。 您現在有 x 光願景，可以看到它們的線框骨架！

## <a name="the-end"></a>結束

恭喜！ 您現在已完成 **MR 空間230：空間對應**。

* 您知道如何掃描您的環境，並將空間對應資料載入至 Unity。
* 您瞭解著色器的基本概念，以及如何使用材質重新將世界視覺化。
* 您已瞭解用來尋找平面和從網格中移除三角形的新處理技巧。
* 您可以移動影像並將其放在合理的表面上。
* 您遇到了不同的遮蔽技術，並和轉型了 x 光線願景的威力！