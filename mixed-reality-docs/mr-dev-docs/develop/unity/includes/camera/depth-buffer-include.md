---
ms.openlocfilehash: 3306a9925c55c24c4d72ecb58d7c744dd64b283e
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636270"
---
# <a name="mrtk"></a>[<span data-ttu-id="0d70f-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="0d70f-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="0d70f-102">[MRTK 的 [設定] 對話方塊](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 會嘗試設定 XR SDK 和舊版 WSA 的深度緩衝區設定，但最好是檢查這些索引標籤，並確認 Unity 中的設定。</span><span class="sxs-lookup"><span data-stu-id="0d70f-102">[MRTK's configuration dialog](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) will attempt to set depth buffer settings for both XR SDK and legacy WSA, but it's good to check those tabs and verify the settings in Unity.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="0d70f-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="0d70f-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="0d70f-104">設定您的 Unity 應用程式是否會提供 Windows 的深度緩衝區：</span><span class="sxs-lookup"><span data-stu-id="0d70f-104">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="0d70f-105">移至 [**編輯**  >  **專案設定**  >  **XR 外掛程式管理]** ，並確定功能表項目已展開。</span><span class="sxs-lookup"><span data-stu-id="0d70f-105">Go to **Edit** > **Project Settings** > **XR Plug-in Management** and ensure the menu item is expanded.</span></span>
2. <span data-ttu-id="0d70f-106">按一下對應到您所選 XR 執行時間的功能表項目（Windows Mixed Reality 或 OpenXR）。</span><span class="sxs-lookup"><span data-stu-id="0d70f-106">Click on the menu item corresponding to the XR runtime you've chosen, either Windows Mixed Reality or OpenXR.</span></span> <span data-ttu-id="0d70f-107">此外，請確定已選取正確的組建平臺，因為可以使用 Windows 獨立和通用 Windows 平臺的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d70f-107">Additionally, ensure the correct build platform is selected, as tabs for both Windows Standalone and Universal Windows Platform are available.</span></span>
3. <span data-ttu-id="0d70f-108">若要啟用和設定：</span><span class="sxs-lookup"><span data-stu-id="0d70f-108">To enable and configure:</span></span>
    1. <span data-ttu-id="0d70f-109">針對 [OpenXR]，在 [ **深度提交模式** ] 下拉式清單中選取深度格式或 [無]。</span><span class="sxs-lookup"><span data-stu-id="0d70f-109">For OpenXR, select either a depth format or "None" in the **Depth Submission Mode** dropdown.</span></span>
    2. <span data-ttu-id="0d70f-110">針對 Windows Mixed Reality，請核取或取消核取 [ **共用深度緩衝區** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0d70f-110">For Windows Mixed Reality, check or uncheck the **Shared Depth Buffer** check box.</span></span> <span data-ttu-id="0d70f-111">然後，從 [ **深度緩衝區格式** ] 下拉式清單中選取格式。</span><span class="sxs-lookup"><span data-stu-id="0d70f-111">Then, select a format from the **Depth Buffer Format** dropdown.</span></span>

<span data-ttu-id="0d70f-112">![Windows XR 外掛程式深度設定 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 深度設定](../../images/xrsdk-openxr-depth.png)</span><span class="sxs-lookup"><span data-stu-id="0d70f-112">![Windows XR Plugin depth settings](../../images/xrsdk-winxr-depth.png)
![OpenXR depth settings](../../images/xrsdk-openxr-depth.png)</span></span>

> [!NOTE]
> <span data-ttu-id="0d70f-113">通常建議使用16位深度緩衝區來改善效能。</span><span class="sxs-lookup"><span data-stu-id="0d70f-113">It is generally recommended to use 16 bit depth buffers for improved performance.</span></span> <span data-ttu-id="0d70f-114">但是，如果使用16位深度格式，樣板緩衝區所需的效果 (像是某些 Unity UI 捲軸) 將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="0d70f-114">However, if using 16-bit depth format, stencil buffer required effects (like some Unity UI scroll panels) will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="0d70f-115">相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區（](https://docs.unity3d.com/Manual/SL-Stencil.html) 如果適用于端點圖形平台）。</span><span class="sxs-lookup"><span data-stu-id="0d70f-115">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) if applicable on the endpoint graphics platform.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="0d70f-116">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="0d70f-116">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="0d70f-117">設定您的 Unity 應用程式是否會提供 Windows 的深度緩衝區：</span><span class="sxs-lookup"><span data-stu-id="0d70f-117">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="0d70f-118">移至 [**編輯**  >  **專案設定**  >  **播放機**  >  **] 通用 Windows 平臺** 索引標籤  >  **XR 設定**]。</span><span class="sxs-lookup"><span data-stu-id="0d70f-118">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="0d70f-119">展開 **WINDOWS MIXED REALITY SDK** 專案。</span><span class="sxs-lookup"><span data-stu-id="0d70f-119">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="0d70f-120">核取或取消核取 [ **啟用深度緩衝區共用** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0d70f-120">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span> <span data-ttu-id="0d70f-121">預設會在新的專案中核取 [啟用深度緩衝區共用]，但在較舊的專案中可能預設為未核取。</span><span class="sxs-lookup"><span data-stu-id="0d70f-121">Enable Depth Buffer Sharing is checked by default in new projects, but may have been unchecked by default in older projects.</span></span>

![舊版 XR 深度設定](../../images/wmr-depth.png)

<span data-ttu-id="0d70f-123">深度緩衝區可以改善視覺品質，只要 Windows 可以精確地將深度緩衝區中的正規化的每個圖元深度值對應到量值，就可以使用您在主要攝影機上的 Unity 中所設定的近距離和最遠的平面。</span><span class="sxs-lookup"><span data-stu-id="0d70f-123">A depth buffer can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span> <span data-ttu-id="0d70f-124">如果您的轉譯階段以一般方式處理深度值，您通常應該會在這裡進行，不過在顯示到現有的色彩圖元時，透明轉譯會寫入深度緩衝區的行程可能會使 reprojection 混淆。</span><span class="sxs-lookup"><span data-stu-id="0d70f-124">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="0d70f-125">如果您知道您的轉譯行程將會離開許多具有不正確深度值的最終深度圖元，您可能會藉由取消核取 [啟用深度緩衝區共用]，以取得更佳的視覺品質。</span><span class="sxs-lookup"><span data-stu-id="0d70f-125">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

> [!NOTE]
> <span data-ttu-id="0d70f-126">通常建議使用16位深度緩衝區來改善效能。</span><span class="sxs-lookup"><span data-stu-id="0d70f-126">It is generally recommended to use 16 bit depth buffers for improved performance.</span></span> <span data-ttu-id="0d70f-127">但是，如果使用16位深度格式，樣板緩衝區所需的效果 (像是某些 Unity UI 捲軸) 將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="0d70f-127">However, if using 16-bit depth format, stencil buffer required effects (like some Unity UI scroll panels) will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="0d70f-128">相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區（](https://docs.unity3d.com/Manual/SL-Stencil.html) 如果適用于端點圖形平台）。</span><span class="sxs-lookup"><span data-stu-id="0d70f-128">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) if applicable on the endpoint graphics platform.</span></span>