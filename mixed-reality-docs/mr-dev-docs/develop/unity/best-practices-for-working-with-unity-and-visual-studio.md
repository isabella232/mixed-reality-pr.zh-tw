---
title: Unity 和 Visual Studio 的最佳作法
description: 使用 Unity 和 Visual Studio 來簡化建立混合現實應用程式之工作流程的秘訣和訣竅。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署、unity、visual studio、HoloLens、HoloLens 2、沉浸式耳機、最佳作法、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、UWP、Visual Studio Tools Windows SDK
ms.openlocfilehash: 9464c86826b9a8ea2c64384dfa699fc6d98743dd
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009368"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="a6aba-104">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="a6aba-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="a6aba-105">當您使用 Unity 建立混合現實應用程式時，您需要在 Unity 與 Visual Studio 之間切換，以建立應用程式套件，並將其部署到 HoloLens 或沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="a6aba-105">When you're creating a mixed reality application with Unity, you need to switch between Unity and Visual Studio to build and deploy the app package to HoloLens or an immersive headset.</span></span> <span data-ttu-id="a6aba-106">根據預設，需要 Visual Studio 的兩個實例-一個可修改 Unity 腳本的實例，另一個則是要部署至裝置和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a6aba-106">By default, two instances of Visual Studio are required - one instance to modify Unity scripts and another to deploy to the device and debug.</span></span> <span data-ttu-id="a6aba-107">下列指示可讓您使用單一 Visual Studio 實例進行開發，減少匯出 Unity 專案的頻率，並改善偵錯工具的體驗。</span><span class="sxs-lookup"><span data-stu-id="a6aba-107">The following instructions let you develop using a single Visual Studio instance, reducing the frequency of exporting Unity projects and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="a6aba-108">改善反復專案時間</span><span class="sxs-lookup"><span data-stu-id="a6aba-108">Improving iteration time</span></span>

<span data-ttu-id="a6aba-109">Unity 2018 中的 .NET 腳本後端支援已被取代，並已在 Unity 2019 + 中移除。</span><span class="sxs-lookup"><span data-stu-id="a6aba-109">Support for .NET scripting back-end in Unity is being deprecated in Unity 2018 and removed in Unity 2019+.</span></span> <span data-ttu-id="a6aba-110">因此建議您改用 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。</span><span class="sxs-lookup"><span data-stu-id="a6aba-110">so we recommend you switch to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> <span data-ttu-id="a6aba-111">不過，您可能會遇到從 Unity 到 Visual Studio 的較長組建時間。</span><span class="sxs-lookup"><span data-stu-id="a6aba-111">However, you may experience longer build times from Unity to Visual Studio.</span></span> <span data-ttu-id="a6aba-112">為了改進以加快反覆運算速度，請設定您的環境以獲得最佳編譯結果：</span><span class="sxs-lookup"><span data-stu-id="a6aba-112">To improve for faster iteration, set up your environment for best compilation results:</span></span>

1) <span data-ttu-id="a6aba-113">每次在相同的目錄中建立您的專案，並在該處重複使用預先建立的檔案，藉以使用增量建立</span><span class="sxs-lookup"><span data-stu-id="a6aba-113">Use incremental building by building your project to the same directory every time, reusing the pre-built files there</span></span>
2) <span data-ttu-id="a6aba-114">針對您的專案停用反惡意程式碼軟體掃描 & 組建資料夾</span><span class="sxs-lookup"><span data-stu-id="a6aba-114">Disable anti-malware software scans for your project & build folders</span></span>
   - <span data-ttu-id="a6aba-115">在您的 Windows 10 設定應用程式下開啟 **病毒 & 威脅防護**</span><span class="sxs-lookup"><span data-stu-id="a6aba-115">Open **Virus & threat protection** under your Windows 10 settings app</span></span>
   - <span data-ttu-id="a6aba-116">選取 [**病毒 & 威脅防護設定**] 下的 [**管理設定**]</span><span class="sxs-lookup"><span data-stu-id="a6aba-116">Select **Manage Settings** under **Virus & threat protection settings**</span></span>
   - <span data-ttu-id="a6aba-117">選取 [**排除**] 區段底下的 [**新增或移除排除** 專案]</span><span class="sxs-lookup"><span data-stu-id="a6aba-117">Select **Add or remove exclusions** under the **Exclusions** section</span></span>
   - <span data-ttu-id="a6aba-118">選取 [ **新增排除** ]，然後選取包含 Unity 專案程式碼和組建輸出的資料夾</span><span class="sxs-lookup"><span data-stu-id="a6aba-118">Select **Add an exclusion** and select the folder containing your Unity project code and build outputs</span></span>
3) <span data-ttu-id="a6aba-119">使用 SSD 來建立</span><span class="sxs-lookup"><span data-stu-id="a6aba-119">Use an SSD for building</span></span>

<span data-ttu-id="a6aba-120">如需詳細資訊，請參閱 [優化 IL2CPP 的組建時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 。</span><span class="sxs-lookup"><span data-stu-id="a6aba-120">Review [Optimizing Build Times for IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) for more info.</span></span> <span data-ttu-id="a6aba-121">此外，請參閱 [IL2CPP 腳本後端的調試](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。</span><span class="sxs-lookup"><span data-stu-id="a6aba-121">Also, review [Debugging on IL2CPP Scripting Back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).</span></span>

<span data-ttu-id="a6aba-122">請考慮安裝 [ *UnityScriptAnalyzer* Visual Studio 擴充](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)功能。</span><span class="sxs-lookup"><span data-stu-id="a6aba-122">Consider installing the [*UnityScriptAnalyzer* Visual Studio extension](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer).</span></span> <span data-ttu-id="a6aba-123">這項工具會分析您的 Unity c # 腳本，找出可以更優化的方式撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6aba-123">This tool analyzes your Unity C# scripts for code that can be written in a more optimized manner.</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="a6aba-124">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="a6aba-124">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="a6aba-125">下載 [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span><span class="sxs-lookup"><span data-stu-id="a6aba-125">Download [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span></span>

<span data-ttu-id="a6aba-126">**Visual Studio Tools for Unity 的優點**</span><span class="sxs-lookup"><span data-stu-id="a6aba-126">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="a6aba-127">藉由放置中斷點、評估變數和複雜運算式，從 Visual Studio 中調試 Unity in 編輯器播放模式。</span><span class="sxs-lookup"><span data-stu-id="a6aba-127">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="a6aba-128">使用 Unity Project Explorer 找出您的腳本，其與 Unity 所顯示的完全相同階層。</span><span class="sxs-lookup"><span data-stu-id="a6aba-128">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="a6aba-129">直接在 Visual Studio 內取得 Unity 主控台。</span><span class="sxs-lookup"><span data-stu-id="a6aba-129">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="a6aba-130">使用 [嚮導] 快速建立或流覽至腳本。</span><span class="sxs-lookup"><span data-stu-id="a6aba-130">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="a6aba-131">公開 c # 類別變數以方便微調</span><span class="sxs-lookup"><span data-stu-id="a6aba-131">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="a6aba-132">有兩種方式可以公開類別變數。</span><span class="sxs-lookup"><span data-stu-id="a6aba-132">There are two ways to expose class variables.</span></span> <span data-ttu-id="a6aba-133">建議的方式是將 [SerializeField] 屬性新增至您的私用變數。</span><span class="sxs-lookup"><span data-stu-id="a6aba-133">The recommended way is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="a6aba-134">您可以從編輯器存取序列化欄位，但無法以程式設計方式公開。</span><span class="sxs-lookup"><span data-stu-id="a6aba-134">Serialized fields can be accessed from the editor but not programmatically exposed.</span></span>  <span data-ttu-id="a6aba-135">另一個選項是將 c # 類別變數設為公用，以在編輯器 UI 中公開這些變數。</span><span class="sxs-lookup"><span data-stu-id="a6aba-135">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="a6aba-136">這兩種方法都可讓您在編輯器中播放時輕鬆地調整變數，這對於微調互動技師修理屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="a6aba-136">Both approaches make it possible to easily tweak variables while playing in-editor, which is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="a6aba-137">在 Windows SDK 或 Unity 升級之後重新產生 UWP Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="a6aba-137">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="a6aba-138">已簽入至原始檔控制的 UWP Visual Studio 解決方案，在升級至新的 Windows SDK 或 Unity 引擎之後可能會過期。</span><span class="sxs-lookup"><span data-stu-id="a6aba-138">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="a6aba-139">您可以從 Unity 建立新的 UWP 解決方案，然後將差異合併到簽入解決方案，以解決過期的解決方案。</span><span class="sxs-lookup"><span data-stu-id="a6aba-139">You can resolve out-of-date solutions after by building a new UWP solution from Unity and merging differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="a6aba-140">使用文字格式資產來輕鬆比較內容變更</span><span class="sxs-lookup"><span data-stu-id="a6aba-140">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="a6aba-141">以文字格式儲存資產可讓您更輕鬆地查看 Visual Studio 中的內容變更差異。</span><span class="sxs-lookup"><span data-stu-id="a6aba-141">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="a6aba-142">您可以選取 [ **編輯 > 專案設定] > 編輯器** ，並變更 **資產序列化** 模式來 **強制文字**，以將資產儲存成文字格式。</span><span class="sxs-lookup"><span data-stu-id="a6aba-142">You can store assets in text format by selecting **Edit > Project Settings > Editor** and change **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="a6aba-143">不過，合併文字資產檔案變更很容易出錯且不建議使用，因此請考慮在原始檔控制中啟用獨佔二進位簽出。</span><span class="sxs-lookup"><span data-stu-id="a6aba-143">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6aba-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6aba-144">See also</span></span>
- [<span data-ttu-id="a6aba-145">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="a6aba-145">Visual Studio Tools for Unity</span></span>](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [<span data-ttu-id="a6aba-146">優化 IL2CPP 的組建時間</span><span class="sxs-lookup"><span data-stu-id="a6aba-146">Optimizing Build Times for IL2CPP</span></span>](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [<span data-ttu-id="a6aba-147">*UnityScriptAnalyzer* Visual Studio 擴充功能</span><span class="sxs-lookup"><span data-stu-id="a6aba-147">*UnityScriptAnalyzer* Visual Studio extension</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
