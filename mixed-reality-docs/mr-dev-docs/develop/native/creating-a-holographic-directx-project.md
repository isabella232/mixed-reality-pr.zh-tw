---
title: 建立全像攝影 DirectX 專案
description: 說明如何根據 Windows Mixed Reality 應用程式範本建立新的全像全像攝影應用程式。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality，全像攝影應用程式、新的應用程式、UWP 應用程式、範本應用程式、全像投影、新專案、逐步解說、下載、範例程式碼、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: f377ca5b8af08beb53c878e1ebf665b8074853f6
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613082"
---
# <a name="creating-a-holographic-directx-project"></a>建立全像攝影 DirectX 專案

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。

您為 HoloLens 建立的全像攝影應用程式將會是 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平臺 (UWP) 應用程式</a>。  如果以桌面為目標 Windows Mixed Reality 耳機，您可以建立 UWP 應用程式或 Win32 應用程式。

DirectX 11 全像 UWP 應用程式範本非常類似于 DirectX 11 UWP 應用程式範本。 範本包含程式迴圈、用來管理 Direct3D 裝置和內容的 **DeviceResources** 類別，以及簡化的內容轉譯器類別。 它也有 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像任何其他 UWP 應用程式一樣。

不過，混合現實應用程式中有一些其他功能不存在於一般的 Direct3D UWP 應用程式中。 Windows Mixed Reality 應用程式範本可以：
* 處理與全像攝影攝影機相關聯的 Direct3D 裝置資源。
* 從系統取出相機背面緩衝區。 在 Direct3D12 的案例中，請建立全像背景緩衝區資源，並管理資源存留期。
* 處理 [注視](../../design/gaze-and-commit.md) 輸入，並辨識 [手勢](../../design/gaze-and-commit.md#composite-gestures)。
* 進入全螢幕身歷聲轉譯模式。

## <a name="how-do-i-get-started"></a>如何開始？

請先依照下載 Visual Studio 2019 和 Windows Mixed Reality 應用程式範本的指示， [安裝這些工具](../install-the-tools.md)。 混合現實應用程式範本可在 Visual Studio marketplace 上以 [網路下載](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)的形式提供，或透過 Visual Studio UI 安裝為擴充功能。

現在您已經準備好建立 DirectX 11 Windows Mixed Reality 應用程式！ 請注意，若要移除範例內容，請將 *pch* 中的 **DRAW_SAMPLE_CONTENT** 預處理器指示詞標記為批註。

## <a name="creating-a-uwp-project"></a>建立 UWP 專案

安裝工具之後，請 (]。install-the-tools.md) 您接著可以建立全像的 DirectX UWP 專案。

若要在 Visual Studio 2019 中建立新專案：
1. 開始 **Visual Studio**。
2. 在右邊的 **開始** 區段中，選取 [ **建立新專案**]。
3. 在 [ **建立新專案** ] 對話方塊的下拉式功能表中，選取 [ **c + +**]、[ **Windows Mixed Reality**] 和 [ **UWP**]。
4. 選取 **(通用 Windows)  (c + +/WinRT) 的全像 DirectX 11 應用程式**。
   ![Visual Studio 2019 中全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Visual Studio 2019 的全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本*
   >[!IMPORTANT]
   >請確定專案範本的名稱包含 " (c + +/WinRT) "。  如果沒有，則會安裝較舊版本的全像攝影專案範本。  若要取得最新的專案範本，請將 [其安裝](../install-the-tools.md) 為 Visual Studio 2019 的擴充功能。
5. 選取 [下一步]。
5. 填寫 [ **專案名稱** ] 和 [ **位置** ] 文字方塊，然後選取或按一下 [ **建立**]。 建立全像應用程式專案。
6. 針對僅限 HoloLens 2 的開發目標，請確定 **目標版本** 和 **最低版本** 都設為 **Windows 10 1903 版**。  如果您也將目標設為 HoloLens (第1代) 或桌面 Windows Mixed Reality 耳機，您可以將 **最低版本** 設定為 **Windows 10 版本 1809**。 當您使用 HoloLens 2 的新功能時，您的程式碼中將需要一些 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本的自我調整性檢查</a> 。
   ![將 Windows 10 1903 版設定為目標和最小版本的螢幕擷取畫面](images/new-uwp-project.png)<br>
   *將 **Windows 10 1903 版** 設定為目標和最小版本*
   >[!IMPORTANT]
   >如果您沒有看到 **Windows 10，版本 1903** 是一個選項，則未安裝最新的 Windows 10 SDK。  若要讓此選項出現，請 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安裝 WINDOWS 10 SDK 的版本10.0.18362.0 或更新版本</a>。

若要在 Visual Studio 2017 中建立新專案：
1. 開始 **Visual Studio**。
2. **在 [檔案] 功能表中**，指向 [**新增**]，然後從內容功能表中選取 [**專案**]。 [新增專案]  對話方塊隨即開啟。
3. 展開左側的 [ **已安裝** ]，然後展開 **Visual C++** 語言節點。
4. 流覽至 [ **Windows 通用 >** 全像] 節點，然後選取 [全像] **DirectX 11 應用程式 (通用 Windows)  (c + +/WinRT])**。
   ![Visual Studio 2017 中全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio 2017 的全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本*
   >[!IMPORTANT]
   >請確定專案範本的名稱包含 " (c + +/WinRT) "。  如果沒有，則會安裝較舊版本的全像攝影專案範本。  若要取得最新的專案範本，請將 [其安裝](../install-the-tools.md) 為 Visual Studio 2017 的擴充功能。
5. 填寫 [ **名稱** ] 和 [ **位置** ] 文字方塊，然後選取或按一下 **[確定]**。 建立全像應用程式專案。
6. 針對僅限 HoloLens 2 的開發目標，請確定 **目標版本** 和 **最低版本** 都設為 **Windows 10 1903 版**。  如果您也將目標設為 HoloLens (第1代) 或桌面 Windows Mixed Reality 耳機，您可以將 **最低版本** 設定為 **Windows 10 版本 1809**。 當您使用 HoloLens 2 的新功能時，您的程式碼中將需要一些 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本的自我調整性檢查</a> 。
   ![將 Windows 10 1903 版設定為目標和最小版本的螢幕擷取畫面](images/new-uwp-project.png)<br>
   *將 **Windows 10 1903 版** 設定為目標和最小版本*
   >[!IMPORTANT]
   >如果您沒有看到 **Windows 10，版本 1903** 是一個選項，則未安裝最新的 Windows 10 SDK。  若要讓此選項出現，請 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安裝 WINDOWS 10 SDK 的版本10.0.18362.0 或更新版本</a>。

此範本會使用 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>來產生專案，這是支援任何符合標準的 c + + 17 編譯器之 Windows 執行階段 Api 的 c + + 17 語言投射。  專案會顯示如何建立由使用者放置2個計量的全球鎖定 cube。 使用者可以 [按一下](../../design/gaze-and-commit.md#composite-gestures) 或按下控制器上的按鈕，將 cube 放在使用者的 [注視](../../design/gaze-and-commit.md)所指定的不同位置。 您可以修改此專案來建立任何混合現實應用程式。

您也可以使用以 SharpDX 為基礎的 **Visual c #** 全像投影專案範本來建立新專案。  如果您的全像 c # 專案不是從 Windows 全像應用程式範本開始，則必須從 Windows Mixed Reality c # 範本專案中複製 fxcompile 檔，並將它匯入 .csproj 檔案，以編譯您新增至專案的 HLSL 檔案。 您也可以在 Windows Mixed Reality 應用程式範本延伸模組中提供 Direct3D 12 範本，以 Visual Studio。

請參閱 [使用 Visual Studio 部署和調試](../platform-capabilities-and-apis/using-visual-studio.md) 程式，以取得如何建立範例，並將其部署至您的 HoloLens、具有沉浸式裝置連接的電腦或模擬器的資訊。

下列其餘指示將假設您使用 c + + 來建立應用程式。

### <a name="uwp-app-entry-point"></a>UWP 應用程式進入點

您的全像 UWP 應用程式會在 AppView 中的 **wWinMain** 函式開始。 **WWinMain** 函式會建立應用程式的 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，並使用它來啟動 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。

從 **AppView .cpp**：

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

從該時間點開始，AppView 類別會處理與 Windows 基本輸入事件、CoreWindow 事件和訊息等的互動。 它也會建立您的應用程式所使用的 HolographicSpace。

## <a name="creating-a-win32-project"></a>建立 Win32 專案

開始建立 Win32 全像專案的最簡單方式，就是調整 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* win32 範例</a>。

這個 Win32 範例使用 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>，這是支援任何符合標準的 c + + 17 編譯器之 Windows 執行階段 Api 的 c + + 17 語言投射。  專案會顯示如何建立由使用者放置2個計量的全球鎖定 cube。 使用者可以按下控制器上的按鈕，將 cube 放在使用者的 [注視](../../design/gaze-and-commit.md)所指定的不同位置。 您可以修改此專案來建立任何混合現實應用程式。

### <a name="win32-app-entry-point"></a>Win32 應用程式進入點

您的全像 Win32 應用程式會在 AppMain 中的 **wWinMain** 函式開始。 **WWinMain** 函式會建立應用程式的 HWND，並啟動其訊息迴圈。

從 **AppMain .cpp**：

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

從該時間點開始，AppMain 類別會處理與基本視窗訊息的互動等等。 它也會建立您的應用程式所使用的 HolographicSpace。

## <a name="render-holographic-content"></a>轉譯全息內容

專案的 **Content** 資料夾包含用來轉譯全像攝影 [空間](getting-a-holographicspace.md)中之全息的類別。 範本中的預設全息圖是放置2個計量離開使用者的旋轉 cube。 繪圖這個 cube 是在 **SpinningCubeRenderer** 中執行，其中包含下列主要方法：

|  方法  |  說明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  載入著色器並建立立方體網格。 | 
|  `PositionHologram` |  將全像放置於所提供 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>所指定的位置。 | 
|  `Update` |  旋轉 cube，並設定模型矩陣。 | 
|  `Render` |  使用頂點和圖元著色器呈現框架。 | 

**著色** 子資料夾包含四個預設著色器執行：

|  著色器  |  說明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  將幾何保留未修改狀態的傳遞。 | 
|  `PixelShader.hlsl` |  通過色彩資料。 色彩資料會在點陣化步驟中插補並指派給圖元。 | 
|  `VertexShader.hlsl` |  在 GPU 上進行頂點處理的簡單著色器。 | 
|  `VPRTVertexShader.hlsl` |  在 GPU 上進行頂點處理的簡單著色器，已針對 Windows Mixed Reality 身歷聲轉譯進行優化。 | 

`VertexShaderShared.hlsl` 包含與之間共用的通用程式碼 `VertexShader.hlsl` `VPRTVertexShader.hlsl` 。

注意： Direct3D 12 應用程式範本也包含 `ViewInstancingVertexShader.hlsl` 。 此變異使用 D3D12 選用功能來更有效率地轉譯身歷聲影像。

著色器會在建立專案時編譯，並且載入至 **SpinningCubeRenderer：： CreateDeviceDependentResources** 方法。

## <a name="interact-with-your-holograms"></a>與您的全像影像互動

使用者輸入是在 **SpatialInputHandler** 類別中處理，它會取得 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 實例並訂閱 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> 事件。 這可讓您偵測輕量手勢和其他空間輸入事件。

## <a name="update-holographic-content"></a>更新全像內容

遊戲迴圈中的混合現實應用程式更新，預設會在的 **Update** 方法中執行 `AppMain.cpp` 。 **Update** 方法會更新場景物件（例如旋轉 cube），並傳回用來取得最新的視圖和投射矩陣，以及呈現交換鏈的 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>物件。

中的轉譯方法 `AppMain.cpp` 會接受<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，並根據目前的應用程式和空間定位狀態，將目前的畫面格轉譯為每個全像攝影相機。

## <a name="notes"></a>備忘錄

Windows Mixed Reality 應用程式範本現在支援使用已啟用 Spectre 防護旗標的編譯 (/Qspectre) 。 在編譯設定 Spectre 緩和功能的設定之前，請務必先安裝 Spectre 緩和版的 Microsoft Visual C++ (MSVC) 執行時間程式庫。 若要安裝 Spectre 降低的 c + + 程式庫，請啟動 Visual Studio 安裝程式，然後選取 [ **修改**]。 流覽至 **個別元件** ，並搜尋 "spectre"。 選取對應至您需要編譯 Spectre 緩和程式碼之目標平臺和 MSVC 版本的方塊，然後按一下 [ **修改** ] 開始安裝。

## <a name="see-also"></a>另請參閱
* [取得 HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX 中的呈現](rendering-in-directx.md)
* [使用 Visual Studio 來部署和偵錯](../platform-capabilities-and-apis/using-visual-studio.md)
* [使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [使用全像攝影 DirectX 應用程式中的 XAML](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)
