---
ms.openlocfilehash: 5444bd0e8667c7ef63bca7f15803e6ac8e4113b1
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111429632"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="145d2-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="145d2-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="145d2-102">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="145d2-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity [建置設定] 功能表路徑](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="145d2-104">在 [組建設定] 視窗中，選取 **通用 Windows 平臺** 和：</span><span class="sxs-lookup"><span data-stu-id="145d2-104">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="145d2-105">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="145d2-105">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="145d2-106">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="145d2-106">Set **Architecture** to **ARM 64**</span></span>
3. <span data-ttu-id="145d2-107">將 [組建類型] 設定為 [D3D 專案]</span><span class="sxs-lookup"><span data-stu-id="145d2-107">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="145d2-108">將 **目標 SDK 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="145d2-108">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="145d2-109">將 **最低平臺版本** 設定為 **10.0.1024.0**</span><span class="sxs-lookup"><span data-stu-id="145d2-109">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="145d2-110">將 **Visual Studio 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="145d2-110">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="145d2-111">設定 **組建並在** **USB 裝置** 上執行</span><span class="sxs-lookup"><span data-stu-id="145d2-111">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="145d2-112">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="145d2-112">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="145d2-113">按一下 [切換平臺] 按鈕</span><span class="sxs-lookup"><span data-stu-id="145d2-113">Click the Switch Platform button</span></span>

![設定通用 Windows 平臺設定的 Unity 組建設定](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="145d2-115">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="145d2-115">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切換平台](../images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="145d2-117">當 Unity 完成切換平臺時，請按一下  **x** 圖示以關閉 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="145d2-117">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window:</span></span>

![已醒目提示 [關閉] 圖示的 Unity 建置視窗](../images/mr-learning-base/base-02-section2-step1-4-openxr.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="145d2-119">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="145d2-119">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="145d2-120">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="145d2-120">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity [建置設定] 功能表路徑](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="145d2-122">在 [組建設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="145d2-122">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![已選取 UWP 以從 [獨立式] 平台進行切換的 Unity [建置設定] 視窗](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="145d2-124">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="145d2-124">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切換平台](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="145d2-126">當 Unity 完成切換平臺時，請按一下 **x** 圖示以關閉 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="145d2-126">When Unity has finished switching the platform, click the **x** icon to close the Build Settings window:</span></span>

![已醒目提示 [關閉] 圖示的 Unity 建置視窗](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="145d2-128">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="145d2-128">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="145d2-129">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="145d2-129">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity [建置設定] 功能表路徑](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="145d2-131">在 [組建設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="145d2-131">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![已選取 UWP 以從 [獨立式] 平台進行切換的 Unity [建置設定] 視窗](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="145d2-133">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="145d2-133">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切換平台](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="145d2-135">當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="145d2-135">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![已醒目提示 [關閉] 圖示的 Unity 建置視窗](../images/mr-learning-base/base-02-section2-step1-4.png)
