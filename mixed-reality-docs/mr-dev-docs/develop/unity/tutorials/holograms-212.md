---
title: HoloLens (第1代) 輸入 212-語音
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解語音概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、語音、HoloLens、混合現實學術、unity、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 8e36233ff4abd3ac91670dd7d04b6675bec045ff
ms.sourcegitcommit: 3236abcba27335fe3d52e38423d2b265ca883355
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106269924"
---
# <a name="hololens-1st-gen-input-212-voice"></a><span data-ttu-id="c9ab7-104">HoloLens (第1代) 輸入212：語音</span><span class="sxs-lookup"><span data-stu-id="c9ab7-104">HoloLens (1st gen) Input 212: Voice</span></span>

>[!IMPORTANT]
><span data-ttu-id="c9ab7-105">混合的現實學術教學課程是以 HoloLens (第一代) 、Unity 2017 和混合現實的沉浸式耳機來設計的。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen), Unity 2017, and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c9ab7-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span> <span data-ttu-id="c9ab7-107">這些教學課程 **_不_** 會使用最新的工具組或互動進行 HoloLens 2，而且可能與較新版本的 Unity 不相容。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2 and may not be compatible with newer versions of Unity.</span></span>  <span data-ttu-id="c9ab7-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c9ab7-109">已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="c9ab7-110">[語音輸入](../../../design/voice-input.md) 可讓我們以另一種方式與我們的全像影像互動。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-110">[Voice input](../../../design/voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="c9ab7-111">語音命令的運作方式非常自然且簡單。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="c9ab7-112">設計您的語音命令，使其為：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="c9ab7-113">Natural</span><span class="sxs-lookup"><span data-stu-id="c9ab7-113">Natural</span></span>
* <span data-ttu-id="c9ab7-114">容易記住</span><span class="sxs-lookup"><span data-stu-id="c9ab7-114">Easy to remember</span></span>
* <span data-ttu-id="c9ab7-115">適當的內容</span><span class="sxs-lookup"><span data-stu-id="c9ab7-115">Context appropriate</span></span>
* <span data-ttu-id="c9ab7-116">與相同內容中的其他選項有充分的差異</span><span class="sxs-lookup"><span data-stu-id="c9ab7-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="c9ab7-117">在 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)中，我們使用了 KeywordRecognizer 來建立兩個簡單的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-117">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="c9ab7-118">在 MR 輸入212中，我們將深入探討並學習如何：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="c9ab7-119">設計針對 HoloLens 語音引擎優化的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="c9ab7-120">讓使用者知道有哪些語音命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="c9ab7-121">確認我們已聽過使用者的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="c9ab7-122">使用聽寫辨識器瞭解使用者的意思。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="c9ab7-123">使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）來接聽命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="c9ab7-124">在此課程中，我們將重新流覽 [模型瀏覽器]，這是我們在 [Mr 輸入 210](holograms-210.md) 和 [MR 輸入 211](holograms-211.md)中建立的。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="c9ab7-125">下列各章節中內嵌的影片是使用較舊版本的 Unity 和混合現實工具組所記錄。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="c9ab7-126">雖然逐步指示是正確且最新的，但您可能會在相對應的影片中看到已過期的腳本和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="c9ab7-127">影片仍隨附于 posterity，因為所涵蓋的概念仍然適用。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="c9ab7-128">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c9ab7-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c9ab7-129">課程</span><span class="sxs-lookup"><span data-stu-id="c9ab7-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c9ab7-130"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c9ab7-130"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c9ab7-131"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="c9ab7-131"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c9ab7-132">MR Input 212：語音</span><span class="sxs-lookup"><span data-stu-id="c9ab7-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="c9ab7-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c9ab7-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c9ab7-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c9ab7-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c9ab7-135">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="c9ab7-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c9ab7-136">必要條件</span><span class="sxs-lookup"><span data-stu-id="c9ab7-136">Prerequisites</span></span>

* <span data-ttu-id="c9ab7-137">[已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-137">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="c9ab7-138">一些基本的 c # 程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c9ab7-139">您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-139">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="c9ab7-140">您應已完成 [MR 輸入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="c9ab7-141">您應已完成 [MR 輸入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="c9ab7-142">[針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-142">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c9ab7-143">專案檔</span><span class="sxs-lookup"><span data-stu-id="c9ab7-143">Project files</span></span>

* <span data-ttu-id="c9ab7-144">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="c9ab7-145">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="c9ab7-146">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c9ab7-147">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)取得。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c9ab7-148">勘誤表和記事</span><span class="sxs-lookup"><span data-stu-id="c9ab7-148">Errata and Notes</span></span>

* <span data-ttu-id="c9ab7-149">您必須在 [工具]-[>選項] 下的 Visual Studio 中停用 [啟用 Just My Code] (*未* 核取) ，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="c9ab7-150">Unity 設定</span><span class="sxs-lookup"><span data-stu-id="c9ab7-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="c9ab7-151">指示</span><span class="sxs-lookup"><span data-stu-id="c9ab7-151">Instructions</span></span>

1. <span data-ttu-id="c9ab7-152">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-152">Start Unity.</span></span>
2. <span data-ttu-id="c9ab7-153">選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-153">Select **Open**.</span></span>
3. <span data-ttu-id="c9ab7-154">流覽至您先前取消封存的 HolographicAcademy-全像 **-212-Voice** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="c9ab7-155">尋找並選取 [**啟動** / **模型瀏覽器**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="c9ab7-156">按一下 [ **選取資料夾** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="c9ab7-157">在 [ **專案** ] 面板中，展開 [ **場景** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="c9ab7-158">按兩下 [ **ModelExplorer** 場景]，以在 Unity 中載入。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="c9ab7-159">建置</span><span class="sxs-lookup"><span data-stu-id="c9ab7-159">Building</span></span>

1. <span data-ttu-id="c9ab7-160">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c9ab7-161">如果 **場景/ModelExplorer** 未列在 **組建的場景** 中，請按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c9ab7-162">如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c9ab7-163">否則，請將它保留在 **任何裝置** 上。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="c9ab7-164">請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="c9ab7-165">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-165">Click **Build**.</span></span>
6. <span data-ttu-id="c9ab7-166">建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="c9ab7-167">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="c9ab7-168">按下 [ **選取資料夾** ]，Unity 就會開始建立 Visual Studio 的專案。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="c9ab7-169">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c9ab7-170">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="c9ab7-171">開啟 **ModelExplorer Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c9ab7-172">如果要部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c9ab7-173">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c9ab7-174">按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c9ab7-175">輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c9ab7-176">按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-176">Click **Select**.</span></span> <span data-ttu-id="c9ab7-177">如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c9ab7-178">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c9ab7-179">如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="c9ab7-180">部署應用程式之後，請使用 **選取手勢** 來關閉 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="c9ab7-181">如果部署到沉浸式耳機：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c9ab7-182">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c9ab7-183">請確定部署目標設定為 [ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c9ab7-184">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="c9ab7-185">部署應用程式之後，請在動作控制器上提取觸發程式來關閉 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="c9ab7-186">您可能會注意到 Visual Studio 錯誤面板中有一些紅色錯誤。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="c9ab7-187">您可以放心地忽略它們。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-187">It is safe to ignore them.</span></span> <span data-ttu-id="c9ab7-188">切換至 [輸出] 面板以查看實際的組建進度。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="c9ab7-189">輸出面板中的錯誤會要求您進行修正 (最常見的原因是腳本) 中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="c9ab7-190">第1章-認知</span><span class="sxs-lookup"><span data-stu-id="c9ab7-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="c9ab7-191">目標</span><span class="sxs-lookup"><span data-stu-id="c9ab7-191">Objectives</span></span>

* <span data-ttu-id="c9ab7-192">瞭解語音命令設計的 **Dos 和不注意事項** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="c9ab7-193">使用 **KeywordRecognizer** 來新增以注視為基礎的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="c9ab7-194">使用游標 **回饋** 讓使用者知道語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="c9ab7-195">語音命令設計</span><span class="sxs-lookup"><span data-stu-id="c9ab7-195">Voice Command Design</span></span>

<span data-ttu-id="c9ab7-196">在本章中，您將瞭解如何設計語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="c9ab7-197">建立語音命令時：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="c9ab7-198">DO</span><span class="sxs-lookup"><span data-stu-id="c9ab7-198">DO</span></span>

* <span data-ttu-id="c9ab7-199">建立簡潔的命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-199">Create concise commands.</span></span> <span data-ttu-id="c9ab7-200">您不想要使用「 *播放目前選取的影片*」，因為該命令並非簡潔，而且使用者很容易就會忘記。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="c9ab7-201">相反地，您應該使用：「 *播放影片*」，因為它很簡潔，而且有多個音節。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c9ab7-202">使用簡單的詞彙。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-202">Use a simple vocabulary.</span></span> <span data-ttu-id="c9ab7-203">請一律嘗試使用簡單的單字和片語，方便使用者探索和記住。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="c9ab7-204">例如，如果您的應用程式具有可顯示或隱藏的附注物件，您就不會使用 " *Show 牌子"* 命令，因為 "牌子" 是很少使用的詞彙。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="c9ab7-205">相反地，您會 *使用下列命令來顯示應用* 程式中的附注。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="c9ab7-206">保持一致。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-206">Be consistent.</span></span> <span data-ttu-id="c9ab7-207">語音命令在您的應用程式中應該保持一致。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="c9ab7-208">假設您的應用程式中有兩個場景，而且這兩個場景都包含用來關閉應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="c9ab7-209">如果第一個場景使用 " *Exit"* 命令來觸發按鈕，但第二個場景使用「 *關閉應用程式*」命令，則使用者會感到混淆。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="c9ab7-210">如果相同的功能跨多個場景保存，則應該使用相同的語音命令來觸發它。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="c9ab7-211">不要</span><span class="sxs-lookup"><span data-stu-id="c9ab7-211">DON'T</span></span>

* <span data-ttu-id="c9ab7-212">使用單一的音節命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-212">Use single syllable commands.</span></span> <span data-ttu-id="c9ab7-213">例如，如果您要建立語音命令來播放影片，您應該避免使用簡單的命令「 *播放*」，因為這只是一個音節，而且可能很容易被系統錯過。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="c9ab7-214">相反地，您應該使用：「 *播放影片*」，因為它很簡潔，而且有多個音節。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c9ab7-215">使用系統命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-215">Use system commands.</span></span> <span data-ttu-id="c9ab7-216">系統會保留 *"Select"* 命令，以觸發目前焦點物件的點擊事件。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="c9ab7-217">請勿重複使用關鍵字或片語中的 *"Select"* 命令，因為它可能無法如您預期般運作。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="c9ab7-218">例如，如果在您的應用程式中選取 cube 的聲音命令為「 *選取 cube*」，但使用者在從未提到命令時正在查看球體，則會改為選取球體。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="c9ab7-219">同樣地，已啟用語音的應用程式行命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="c9ab7-220">請勿在 CoreWindow View 中使用下列語音命令：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="c9ab7-221">向後</span><span class="sxs-lookup"><span data-stu-id="c9ab7-221">Go Back</span></span>
    2. <span data-ttu-id="c9ab7-222">捲軸工具</span><span class="sxs-lookup"><span data-stu-id="c9ab7-222">Scroll Tool</span></span>
    3. <span data-ttu-id="c9ab7-223">Zoom 工具</span><span class="sxs-lookup"><span data-stu-id="c9ab7-223">Zoom Tool</span></span>
    4. <span data-ttu-id="c9ab7-224">拖曳工具</span><span class="sxs-lookup"><span data-stu-id="c9ab7-224">Drag Tool</span></span>
    5. <span data-ttu-id="c9ab7-225">Adjust</span><span class="sxs-lookup"><span data-stu-id="c9ab7-225">Adjust</span></span>
    6. <span data-ttu-id="c9ab7-226">移除</span><span class="sxs-lookup"><span data-stu-id="c9ab7-226">Remove</span></span>
* <span data-ttu-id="c9ab7-227">使用類似的聲音。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-227">Use similar sounds.</span></span> <span data-ttu-id="c9ab7-228">請嘗試避免使用 rhyme 的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="c9ab7-229">如果您的購物應用程式支援 [ *顯示存放區]* 和 [ *顯示更多]* 作為語音命令，則您會想要在另一個使用中的命令停用其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="c9ab7-230">例如，您可以使用 [ *顯示存放區]* 按鈕來開啟存放區，然後在商店顯示時停用該命令，如此就可以使用 [ *顯示更多]* 命令來進行流覽。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9ab7-231">指示</span><span class="sxs-lookup"><span data-stu-id="c9ab7-231">Instructions</span></span>

* <span data-ttu-id="c9ab7-232">在 **Unity 的階層** 面板中，使用搜尋工具來尋找 **holoComm_screen_mesh** 物件。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="c9ab7-233">按兩下 **holoComm_screen_mesh** 物件以在 **場景** 中加以查看。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="c9ab7-234">這是太空人的監看，它會回應我們的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="c9ab7-235">在 [偵測 **器** ] 面板中，找出 **語音輸入來源 (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="c9ab7-236">展開 [ **關鍵字** ] 區段以查看支援的語音命令： **開啟 Communicator**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="c9ab7-237">按一下右邊的齒輪，然後選取 [ **編輯腳本**]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="c9ab7-238">探索 **SpeechInputSource** ，瞭解它如何使用 **KeywordRecognizer** 來新增語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c9ab7-239">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c9ab7-239">Build and Deploy</span></span>

* <span data-ttu-id="c9ab7-240">在 Unity 中，使用檔案 **> 組建設定** 來重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="c9ab7-241">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-241">Open the **App** folder.</span></span>
* <span data-ttu-id="c9ab7-242">開啟 **ModelExplorer Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c9ab7-243"> (如果您已在安裝期間于 Visual Studio 中建立或部署此專案，則您可以開啟 VS 的實例，然後在出現) 提示時按一下 [全部重載]。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="c9ab7-244">在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="c9ab7-245">將應用程式部署到 HoloLens 之後，請使用 [點 [一下手勢] 關閉 [符合](../../../design/gaze-and-commit.md#composite-gestures) ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](../../../design/gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="c9ab7-246">觀賞太空人的觀賞。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="c9ab7-247">當 watch 具有焦點時，請確認游標變更為麥克風。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="c9ab7-248">這會提供應用程式接聽語音命令的意見反應。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="c9ab7-249">確認 watch 上出現工具提示。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="c9ab7-250">這可協助使用者探索 *"Open Communicator"* 命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="c9ab7-251">撥雲見日監看時，請說「 *開啟 communicator* 」來開啟 communicator 面板。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="c9ab7-252">第2章-確認</span><span class="sxs-lookup"><span data-stu-id="c9ab7-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="c9ab7-253">目標</span><span class="sxs-lookup"><span data-stu-id="c9ab7-253">Objectives</span></span>

* <span data-ttu-id="c9ab7-254">使用麥克風輸入記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="c9ab7-255">將意見反應提供給使用者，指出應用程式正在接聽其語音。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="c9ab7-256">必須針對要從麥克風錄製的應用程式宣告 **麥克風** 功能。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c9ab7-257">您已在 MR 輸入212中為您完成這項操作，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c9ab7-258">在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定</span><span class="sxs-lookup"><span data-stu-id="c9ab7-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c9ab7-259">按一下 [通用 Windows 平臺] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="c9ab7-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c9ab7-260">在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能</span><span class="sxs-lookup"><span data-stu-id="c9ab7-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c9ab7-261">指示</span><span class="sxs-lookup"><span data-stu-id="c9ab7-261">Instructions</span></span>

* <span data-ttu-id="c9ab7-262">在 Unity 的 **階層面板中** ，確認已選取 **holoComm_screen_mesh** 物件。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="c9ab7-263">在 [偵測 **器** ] 面板中，尋找 **太空人 Watch (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="c9ab7-264">按一下設定為 [ **Communicator 預製專案** ] 屬性值的小、藍色 cube。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="c9ab7-265">在 [ **專案** ] 面板中， **Communicator** 預製專案現在應該會有焦點。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="c9ab7-266">按一下 [**專案**] 面板中的 **Communicator** 預製專案，以在偵測 **器** 中查看其元件。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="c9ab7-267">查看 **麥克風管理員 (腳本)** 元件，這可讓我們記錄使用者的聲音。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="c9ab7-268">請注意， **Communicator** 物件具有 **語音輸入處理常式 (腳本)** 元件，可回應 **傳送訊息** 命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="c9ab7-269">查看 **Communicator (腳本)** 元件，然後按兩下腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="c9ab7-270">Communicator 負責在 communicator 裝置上設定適當的按鈕狀態。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="c9ab7-271">這可讓我們的使用者記錄訊息、播放訊息，然後將訊息傳送至太空人。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="c9ab7-272">它也會啟動和停止動畫 wave 表單，以向使用者確認他們的聲音聽到。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="c9ab7-273">在 **Communicator** 中，刪除從 **Start** 方法 (81 和 82) 的下列幾行。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="c9ab7-274">這會啟用 communicator 上的 [記錄] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="c9ab7-275">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c9ab7-275">Build and Deploy</span></span>

* <span data-ttu-id="c9ab7-276">在 Visual Studio 中，重建您的應用程式並部署至裝置。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="c9ab7-277">觀賞太空人的監看，然後說「 *開啟 communicator* 」來顯示 Communicator。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="c9ab7-278">按下 [ **錄製** ] 按鈕 (麥克風) ，開始記錄太空人的口頭訊息。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="c9ab7-279">開始說話，並確認 wave 動畫是在 communicator 上播放的，它會將意見反應提供給使用者，指出他們的聲音聽起來。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="c9ab7-280">按下 [ **停止** ] 按鈕 (左方塊) ，並確認 wave 動畫停止執行。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="c9ab7-281">按下 [ **播放** ] 按鈕 (右三角形) 播放錄製的訊息，並在裝置上聆聽。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="c9ab7-282">按下 [ **停止** ] 按鈕 (右方塊) 停止播放錄製的訊息。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="c9ab7-283">說「 *傳送訊息* 」以關閉 communicator，並接收來自太空人的「訊息已接收」回應。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="c9ab7-284">第3章-瞭解與聽寫辨識器</span><span class="sxs-lookup"><span data-stu-id="c9ab7-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="c9ab7-285">目標</span><span class="sxs-lookup"><span data-stu-id="c9ab7-285">Objectives</span></span>

* <span data-ttu-id="c9ab7-286">使用聽寫辨識器將使用者的語音轉換成文字。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="c9ab7-287">在 communicator 中顯示聽寫辨識器的假設和最終結果。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="c9ab7-288">在本章中，我們將使用聽寫辨識器來建立太空人的訊息。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="c9ab7-289">使用聽寫辨識器時，請記住：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="c9ab7-290">您必須連線到 WiFi，聽寫辨識器才能運作。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="c9ab7-291">在設定的一段時間後發生超時。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="c9ab7-292">有兩個需要注意的超時：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="c9ab7-293">如果辨識器啟動，但在前五秒內未收到任何音訊，則會超時。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="c9ab7-294">如果辨識器已指定結果，但接著會聽到20秒的無回應，則會超時。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="c9ab7-295">一次只能執行一種辨識器 (關鍵字或聽寫) 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="c9ab7-296">必須針對要從麥克風錄製的應用程式宣告 **麥克風** 功能。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c9ab7-297">您已在 MR 輸入212中為您完成這項操作，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c9ab7-298">在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定</span><span class="sxs-lookup"><span data-stu-id="c9ab7-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c9ab7-299">按一下 [通用 Windows 平臺] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="c9ab7-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c9ab7-300">在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能</span><span class="sxs-lookup"><span data-stu-id="c9ab7-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c9ab7-301">指示</span><span class="sxs-lookup"><span data-stu-id="c9ab7-301">Instructions</span></span>

<span data-ttu-id="c9ab7-302">我們將編輯 **MicrophoneManager** ，以使用聽寫辨識器。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="c9ab7-303">這就是我們要新增的內容：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-303">This is what we'll add:</span></span>

1. <span data-ttu-id="c9ab7-304">當您按下 [ **錄製] 按鈕** 時，我們會 **啟動 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="c9ab7-305">顯示 DictationRecognizer 瞭解的 **假設** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="c9ab7-306">鎖定 DictationRecognizer 瞭解的 **結果** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="c9ab7-307">檢查 DictationRecognizer 是否有超時。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="c9ab7-308">當按下 [ **停止] 按鈕** 或 mic 會話超時時，請 **停止 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="c9ab7-309">重新開機 **KeywordRecognizer**，它會接聽 **傳送訊息** 命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="c9ab7-310">讓我們開始這次的教學。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-310">Let's get started.</span></span> <span data-ttu-id="c9ab7-311">在 **MicrophoneManager** 中完成3的所有程式碼撰寫練習，或複製並貼上完成的程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="c9ab7-312">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c9ab7-312">Build and Deploy</span></span>

* <span data-ttu-id="c9ab7-313">在 Visual Studio 中重建並部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="c9ab7-314">使用輕量手勢關閉 [符合] 方塊。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c9ab7-315">觀賞太空人的監看，然後說「 *開啟 Communicator*」。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="c9ab7-316">選取 [ **錄製** ] 按鈕 (麥克風) 以記錄您的訊息。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="c9ab7-317">開始說話。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-317">Start speaking.</span></span> <span data-ttu-id="c9ab7-318">**聽寫辨識器** 會解讀您的語音，並顯示 communicator 中的假設文字。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="c9ab7-319">當您記錄訊息時，請嘗試說出「 *傳送訊息* 」。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="c9ab7-320">請注意， **關鍵字辨識器** 沒有回應，因為 **聽寫辨識器** 仍在作用中。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="c9ab7-321">停止說話幾秒鐘。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="c9ab7-322">觀賞聽寫辨識器完成其假設並顯示最終結果。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="c9ab7-323">開始說話，然後暫停20秒。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="c9ab7-324">這會導致 **聽寫辨識器** 超時。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="c9ab7-325">請注意，在上述 timeout 之後， **關鍵字辨識器** 會重新啟用。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="c9ab7-326">Communicator 現在會回應語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="c9ab7-327">說「 *傳送訊息* 」，將訊息傳送至太空人。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="c9ab7-328">第4章-文法辨識器</span><span class="sxs-lookup"><span data-stu-id="c9ab7-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="c9ab7-329">目標</span><span class="sxs-lookup"><span data-stu-id="c9ab7-329">Objectives</span></span>

* <span data-ttu-id="c9ab7-330">使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）辨識使用者的語音。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="c9ab7-331">必須針對要從麥克風錄製的應用程式宣告 **麥克風** 功能。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c9ab7-332">您已在 MR 輸入212中為您完成這項操作，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c9ab7-333">在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定</span><span class="sxs-lookup"><span data-stu-id="c9ab7-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c9ab7-334">按一下 [通用 Windows 平臺] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="c9ab7-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c9ab7-335">在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能</span><span class="sxs-lookup"><span data-stu-id="c9ab7-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c9ab7-336">指示</span><span class="sxs-lookup"><span data-stu-id="c9ab7-336">Instructions</span></span>

1. <span data-ttu-id="c9ab7-337">**在 [階層**] 面板中搜尋 **Jetpack_Center** ，然後選取它。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="c9ab7-338">在 [偵測 **器**] 面板中尋找 **Tagalong 動作** 腳本。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="c9ab7-339">按一下 [物件] 右邊的小圓圈， **沿著欄位標記** 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="c9ab7-340">在彈出的視窗中，搜尋 **SRGSToolbox** ，然後從清單中選取它。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="c9ab7-341">請查看 **StreamingAssets** 資料夾中的 **SRGSColor.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="c9ab7-342">您可以在 [W3C 網站上](https://www.w3.org/TR/speech-grammar/)找到 SRGS 設計規格。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="c9ab7-343">在我們的 SRGS 檔案中，有三種類型的規則：</span><span class="sxs-lookup"><span data-stu-id="c9ab7-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="c9ab7-344">此規則可讓您從十二個色彩的清單中說出一種色彩。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="c9ab7-345">有三個規則會接聽色彩規則和三個圖形之一的組合。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="c9ab7-346">ColorChooser 的根規則，它會接聽三個「色彩 + 圖形」規則的任何組合。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="c9ab7-347">您可以依任何順序或從1到全部三個的任意數量，來說出圖形。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="c9ab7-348">這是唯一接聽的規則，因為它在初始文法標記中是指定為檔案頂端的根規則 &lt; &gt; 。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c9ab7-349">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c9ab7-349">Build and Deploy</span></span>

* <span data-ttu-id="c9ab7-350">在 Unity 中重建應用程式，然後從 Visual Studio 建立和部署，以在 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="c9ab7-351">使用輕量手勢關閉 [符合] 方塊。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c9ab7-352">看看太空人的 jetpack，然後執行一下點一下手勢。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="c9ab7-353">開始說話。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-353">Start speaking.</span></span> <span data-ttu-id="c9ab7-354">**文法辨識器** 會解讀您的語音，並根據辨識來變更圖形的色彩。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="c9ab7-355">範例命令為「藍色圓圈、黃色方形」。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="c9ab7-356">執行另一個輕量手勢來關閉工具箱。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="c9ab7-357">結束</span><span class="sxs-lookup"><span data-stu-id="c9ab7-357">The End</span></span>

<span data-ttu-id="c9ab7-358">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c9ab7-358">Congratulations!</span></span> <span data-ttu-id="c9ab7-359">您現在已完成 **MR 輸入212： Voice**。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="c9ab7-360">您知道語音命令的 Dos 和注意事項。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="c9ab7-361">您已瞭解如何運用工具提示，讓使用者知道語音命令。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="c9ab7-362">您看到了數種類型的意見反應，用來確認使用者的聲音聽起來。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="c9ab7-363">您知道如何在關鍵字辨識器與聽寫辨識器之間切換，以及這兩項功能如何理解及解讀您的聲音。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="c9ab7-364">您已瞭解如何在您的應用程式中使用 SRGS 檔案和文法辨識器進行語音辨識。</span><span class="sxs-lookup"><span data-stu-id="c9ab7-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>