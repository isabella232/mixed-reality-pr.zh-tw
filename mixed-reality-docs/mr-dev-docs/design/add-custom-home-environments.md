---
title: 設計自己的沉浸式環境
description: 瞭解如何建立您自己的 Windows Mixed Reality home 環境。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、Home、自訂環境、地點、cliff 房子、skyloft、使用者、建立、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: ca6a41f8388a767b1191ddc3b377822567a603a6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583303"
---
# <a name="design-your-own-immersive-environments"></a><span data-ttu-id="a0774-104">設計自己的沉浸式環境</span><span class="sxs-lookup"><span data-stu-id="a0774-104">Design your own immersive environments</span></span>

>[!NOTE]
><span data-ttu-id="a0774-105">這是實驗性的功能。</span><span class="sxs-lookup"><span data-stu-id="a0774-105">This is an experimental feature.</span></span> <span data-ttu-id="a0774-106">請試試看，它很有趣，但如果一切沒有如預期般運作，則不會感到驚訝。</span><span class="sxs-lookup"><span data-stu-id="a0774-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="a0774-107">我們正在評估這項功能的可行性並對其使用感興趣，因此請告訴我們您的體驗 (以及您在 [開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)) 找到的任何 bug。</span><span class="sxs-lookup"><span data-stu-id="a0774-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="a0774-108">從 [2018 年4月更新 Windows 10](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)開始，我們已啟用實驗性功能，可讓您將自訂環境新增至 [開始] 功能表) 上的 [位置選擇器] (，以做為 [Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md)使用。</span><span class="sxs-lookup"><span data-stu-id="a0774-108">Starting with the [Windows 10 April 2018 update](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="a0774-109">Windows Mixed Reality 有兩個預設環境：懸崖之屋和 Skyloft，您可以選擇做為您的首頁。</span><span class="sxs-lookup"><span data-stu-id="a0774-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, you can choose as your home.</span></span> <span data-ttu-id="a0774-110">建立自訂環境可讓您使用自己的建立來展開清單。</span><span class="sxs-lookup"><span data-stu-id="a0774-110">Creating custom environments allows you to expand the list with your own creations.</span></span> <span data-ttu-id="a0774-111">這項功能是以早期的狀態提供，以評估建立者和開發人員的興趣。</span><span class="sxs-lookup"><span data-stu-id="a0774-111">We're making this feature available in an early state to evaluate interest from creators and developers.</span></span> <span data-ttu-id="a0774-112">查看您所建立的各種領域，並瞭解如何使用不同的 authoring tools。</span><span class="sxs-lookup"><span data-stu-id="a0774-112">See what kinds of worlds you create and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="a0774-113">使用自訂環境時，您會注意到 teleporting、與應用程式互動，以及放置全像投影一樣的運作方式，與在懸崖之屋和 Skyloft 中一樣。</span><span class="sxs-lookup"><span data-stu-id="a0774-113">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="a0774-114">您可以在幻想環境中流覽 web，或使用全像幻想式道具城市來填滿，這可能是無限的。</span><span class="sxs-lookup"><span data-stu-id="a0774-114">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="a0774-115">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a0774-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a0774-116"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="a0774-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a0774-117"><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a0774-117"><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a0774-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="a0774-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a0774-119">自訂家用環境</span><span class="sxs-lookup"><span data-stu-id="a0774-119">Custom home environments</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a0774-120">✔️</span><span class="sxs-lookup"><span data-stu-id="a0774-120">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="a0774-121">嘗試範例環境</span><span class="sxs-lookup"><span data-stu-id="a0774-121">Trying a sample environment</span></span>

<span data-ttu-id="a0774-122">我們建立了一個範例環境，顯示自訂家用環境的一些創意潛力。</span><span class="sxs-lookup"><span data-stu-id="a0774-122">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="a0774-123">請遵循下列步驟來試用：</span><span class="sxs-lookup"><span data-stu-id="a0774-123">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="a0774-124">[下載我們的範例幻想島環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (連結點，以) 自動解壓縮的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a0774-124">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="a0774-125">![幻想島範例環境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="a0774-125">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="a0774-126">*幻想島範例環境*</span><span class="sxs-lookup"><span data-stu-id="a0774-126">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="a0774-127">執行您所下載的 **Fantasy_Island.exe** 檔案。</span><span class="sxs-lookup"><span data-stu-id="a0774-127">Run the **Fantasy_Island.exe** file you downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a0774-128">當您嘗試執行從 web (下載的 .exe 檔案，就像這樣的) ，您可能會遇到「Windows 已保護您的電腦」快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="a0774-128">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="a0774-129">若要從此快顯視窗執行 Fantasy_Island.exe，請選取 [ **更多資訊** ]，然後 **繼續執行**。</span><span class="sxs-lookup"><span data-stu-id="a0774-129">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="a0774-130">此安全性設定的目的是要防止您下載不想要信任的檔案，因此當您信任檔案的來源時，請選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="a0774-130">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="a0774-131">開啟 **檔案總管** 並在網址列中貼上下列檔案位置，以流覽至 [環境] 資料夾： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 。</span><span class="sxs-lookup"><span data-stu-id="a0774-131">Open **File Explorer** and navigate to the environments folder by pasting the following file location in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="a0774-132">將您下載的範例環境複製到此資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0774-132">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="a0774-133">重新開機 **混合實境入口** ，以重新整理位置選擇器中的環境清單。</span><span class="sxs-lookup"><span data-stu-id="a0774-133">Restart **Mixed Reality Portal** to refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="a0774-134">放在您的耳機上。</span><span class="sxs-lookup"><span data-stu-id="a0774-134">Put on your headset.</span></span> <span data-ttu-id="a0774-135">一旦您在家中，請使用 [Windows] 按鈕來開啟 **[開始] 功能表** 。</span><span class="sxs-lookup"><span data-stu-id="a0774-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="a0774-136">選取釘選應用程式清單上方的 [ **地點** ] 圖示，以選擇主環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="a0774-137">您會在您的地點清單中找到您下載的幻想島環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-137">You'll find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="a0774-138">選取 [ **幻想島** ] 以進入新的自訂家用環境！</span><span class="sxs-lookup"><span data-stu-id="a0774-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="a0774-139">建立您自己的自訂環境</span><span class="sxs-lookup"><span data-stu-id="a0774-139">Creating your own custom environment</span></span>

<span data-ttu-id="a0774-140">除了使用我們的範例環境，您還可以使用您最愛的3D 編輯軟體來匯出自己的自訂環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="a0774-141">模型指導方針</span><span class="sxs-lookup"><span data-stu-id="a0774-141">Modeling guidelines</span></span>

<span data-ttu-id="a0774-142">為您的環境建立模型時，請記住下列建議，讓使用者在 believably 規模的世界中產生正確的方向：</span><span class="sxs-lookup"><span data-stu-id="a0774-142">When modeling your environment, keep the following recommendations in mind so that users spawns in the correct orientation in a believably sized world:</span></span>

1. <span data-ttu-id="a0774-143">使用者將會產生0、0、0，以將您的產生位置置中到原點的中心。</span><span class="sxs-lookup"><span data-stu-id="a0774-143">Users will spawn at 0,0,0 so center your spawn location around the origin.</span></span>
2. <span data-ttu-id="a0774-144">工作單位應該設定為計量，以便能夠以全球規模撰寫資產。</span><span class="sxs-lookup"><span data-stu-id="a0774-144">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="a0774-145">向上軸應設定為 "Y"。</span><span class="sxs-lookup"><span data-stu-id="a0774-145">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="a0774-146">資產應「轉寄」朝正 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="a0774-146">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="a0774-147">您不需要將所有的網格合併，但如果您是以資源限制的裝置為目標，則建議使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a0774-147">You don't have to combine all your meshes, but it's recommended if you're targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="a0774-148">匯出您的環境</span><span class="sxs-lookup"><span data-stu-id="a0774-148">Exporting your environment</span></span>

<span data-ttu-id="a0774-149">Windows Mixed Reality 依賴二進位 glTF (. glb) 做為環境的資產傳遞格式。</span><span class="sxs-lookup"><span data-stu-id="a0774-149">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="a0774-150">glTF 是 Khronos 群組所維護之3D 資產傳遞的專利免費開放標準。</span><span class="sxs-lookup"><span data-stu-id="a0774-150">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="a0774-151">Microsoft 對 Windows 應用程式和體驗的格式支援將隨著 glTF 發展成為互通3D 內容的產業標準。</span><span class="sxs-lookup"><span data-stu-id="a0774-151">Microsoft’s support for the format across Windows apps and experiences will grow as glTF evolves as an industry standard for interoperable 3D content.</span></span>

<span data-ttu-id="a0774-152">匯出用來作為自訂家用環境之資產的第一個步驟是產生 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="a0774-152">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="a0774-153">GlTF 工作群組會維護一份 [支援的匯出工具和轉換器清單，](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 以建立 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="a0774-153">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="a0774-154">若要開始使用，請使用此頁面上所列的其中一個程式來建立和匯出 glTF 2.0 模型，或使用其中一個支援的轉換器來轉換現有的模型。</span><span class="sxs-lookup"><span data-stu-id="a0774-154">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="a0774-155">此外，請參閱 [這篇實用的文章，其中提供了直接從 Blender 和 3DS Max 匯出 glTF 模型的藝術工作流程總覽。</span><span class="sxs-lookup"><span data-stu-id="a0774-155">Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="a0774-156">環境限制</span><span class="sxs-lookup"><span data-stu-id="a0774-156">Environment limits</span></span>

<span data-ttu-id="a0774-157">所有環境都必須是 < 256 mb。</span><span class="sxs-lookup"><span data-stu-id="a0774-157">All environments must be < 256 mbs.</span></span> <span data-ttu-id="a0774-158">大於 256 mb 的環境將無法載入，而且只會使用使用者周圍的預設 skybox 來切換回空白世界。</span><span class="sxs-lookup"><span data-stu-id="a0774-158">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="a0774-159">建立模型時，請記住此檔案大小限制。</span><span class="sxs-lookup"><span data-stu-id="a0774-159">Keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="a0774-160">此外，如果您打算使用 WindowsMRAssetConverter （如下所述）將您的環境優化，請 cognizant 材質大小會隨著優化工具建立檔案大小較大但載入速度更快的材質而增加。</span><span class="sxs-lookup"><span data-stu-id="a0774-160">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="a0774-161">優化您的環境</span><span class="sxs-lookup"><span data-stu-id="a0774-161">Optimizing your environment</span></span>

<span data-ttu-id="a0774-162">Windows Mixed Reality 支援許多可大幅降低環境載入時間的選擇性優化。</span><span class="sxs-lookup"><span data-stu-id="a0774-162">Windows Mixed Reality supports many optional optimizations that can significantly reduce your environment load times.</span></span> <span data-ttu-id="a0774-163">請特別注意具有許多材質的環境，因為它們有時候會在載入時出現。</span><span class="sxs-lookup"><span data-stu-id="a0774-163">Pay special attention with environments that have lots of textures, as they'll sometimes time out while loading.</span></span> <span data-ttu-id="a0774-164">一般來說，我們建議所有資產都使用此步驟，不過，只有少數或低解析度紋理的較小環境並不一定需要它。</span><span class="sxs-lookup"><span data-stu-id="a0774-164">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="a0774-165">為了簡化此程式，我們建立了 Windows Mixed Reality 的 [資產轉換器 (可在 GitHub) 上 ](https://github.com/Microsoft/glTF-Toolkit/releases) 取得，以進行優化。</span><span class="sxs-lookup"><span data-stu-id="a0774-165">To make this process easier, we've created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to do your optimizations.</span></span> <span data-ttu-id="a0774-166">這項工具會使用 Microsoft glTF 工具組中提供的一組公用程式，藉由執行額外的材質封裝、壓縮和解析度向下調整，來優化任何標準 2.0 glTF 或 glb。</span><span class="sxs-lookup"><span data-stu-id="a0774-166">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or.glb by performing an extra texture packing, compression, and resolution down-scaling.</span></span> 

<span data-ttu-id="a0774-167">轉換器目前支援數個旗標，以調整優化的確切行為。</span><span class="sxs-lookup"><span data-stu-id="a0774-167">The converter currently supports several flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="a0774-168">建議您以下列旗標執行，以獲得最佳結果：</span><span class="sxs-lookup"><span data-stu-id="a0774-168">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="a0774-169">旗標</span><span class="sxs-lookup"><span data-stu-id="a0774-169">Flag</span></span>|<span data-ttu-id="a0774-170">建議值 (s) </span><span class="sxs-lookup"><span data-stu-id="a0774-170">Recommended Value(s)</span></span>|<span data-ttu-id="a0774-171">描述</span><span class="sxs-lookup"><span data-stu-id="a0774-171">Description</span></span>
---|---|---
<span data-ttu-id="a0774-172">-最大材質-大小</span><span class="sxs-lookup"><span data-stu-id="a0774-172">-max-texture-size</span></span>|<span data-ttu-id="a0774-173">1024或2048</span><span class="sxs-lookup"><span data-stu-id="a0774-173">1024 or 2048</span></span>| <span data-ttu-id="a0774-174">調整值以改善紋理的品質，預設值為512x512。</span><span class="sxs-lookup"><span data-stu-id="a0774-174">Tweak the value to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="a0774-175">較大的值會大幅影響環境的檔案大小，因此請記住 256-mb 的限制</span><span class="sxs-lookup"><span data-stu-id="a0774-175">A larger value will significantly impact the file size of the environment so keep the 256-mb limit in mind</span></span>
<span data-ttu-id="a0774-176">-最小-版本</span><span class="sxs-lookup"><span data-stu-id="a0774-176">-min-version</span></span>|<span data-ttu-id="a0774-177">1803</span><span class="sxs-lookup"><span data-stu-id="a0774-177">1803</span></span>|<span data-ttu-id="a0774-178">只有在 windows >= 1803 的版本上才支援自訂環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-178">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="a0774-179">此旗標會移除較舊版本的材質，並減少最終資產的檔案大小</span><span class="sxs-lookup"><span data-stu-id="a0774-179">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="a0774-180">例如：</span><span class="sxs-lookup"><span data-stu-id="a0774-180">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="a0774-181">測試您的環境</span><span class="sxs-lookup"><span data-stu-id="a0774-181">Testing your environment</span></span>

<span data-ttu-id="a0774-182">當您擁有最終的 glb 環境之後，即可在耳機中進行測試。</span><span class="sxs-lookup"><span data-stu-id="a0774-182">Once you have your final.glb environment, you're ready to test it out in the headset.</span></span> <span data-ttu-id="a0774-183">從「 [試用範例環境](#trying-a-sample-environment) 」一節的步驟2開始，使用您的自訂環境做為混合實境首頁。</span><span class="sxs-lookup"><span data-stu-id="a0774-183">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="sending-feedback"></a><span data-ttu-id="a0774-184">傳送意見反應</span><span class="sxs-lookup"><span data-stu-id="a0774-184">Sending feedback</span></span>

<span data-ttu-id="a0774-185">在評估這項實驗性功能時，我們想要瞭解您使用自訂環境的方式、您可能發現的任何錯誤，以及您喜歡此功能的方式。</span><span class="sxs-lookup"><span data-stu-id="a0774-185">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may find, and how you like the feature.</span></span> <span data-ttu-id="a0774-186">分享在 [開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)中建立及使用自訂家用環境的任何意見反應。</span><span class="sxs-lookup"><span data-stu-id="a0774-186">Share any feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="a0774-187">疑難排解與秘訣</span><span class="sxs-lookup"><span data-stu-id="a0774-187">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="a0774-188">如何? 變更環境的名稱？</span><span class="sxs-lookup"><span data-stu-id="a0774-188">How do I change the name of the environment?</span></span>

<span data-ttu-id="a0774-189">[環境] 資料夾中的檔案名將用於位置選擇器中。</span><span class="sxs-lookup"><span data-stu-id="a0774-189">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="a0774-190">若要變更您的環境名稱，請重新命名環境檔案名，然後重新開機混合實境入口。</span><span class="sxs-lookup"><span data-stu-id="a0774-190">To change the name of your environment, rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="a0774-191">如何? 從我的地點選擇器移除自訂環境？</span><span class="sxs-lookup"><span data-stu-id="a0774-191">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="a0774-192">若要移除自訂環境，請在您的電腦上開啟環境資料夾 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 並刪除環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-192">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="a0774-193">一旦您重新開機混合實境入口，此環境將不會再出現在位置選擇器中。</span><span class="sxs-lookup"><span data-stu-id="a0774-193">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="a0774-194">如何? 預設為我最愛的自訂環境？</span><span class="sxs-lookup"><span data-stu-id="a0774-194">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="a0774-195">您目前無法變更預設環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-195">You can't currently change the default environment.</span></span> <span data-ttu-id="a0774-196">每次您重新開機混合實境入口時，您都會回到懸崖之屋環境。</span><span class="sxs-lookup"><span data-stu-id="a0774-196">Each time you restart Mixed Reality Portal, you'll be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="a0774-197">我產生了一個空格</span><span class="sxs-lookup"><span data-stu-id="a0774-197">I spawn into a blank space</span></span>

<span data-ttu-id="a0774-198">Windows Mixed Reality [不支援超過 256 mb 的環境](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="a0774-198">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="a0774-199">當環境超過此限制時，您會進入空白的天空方塊，而不需要模型。</span><span class="sxs-lookup"><span data-stu-id="a0774-199">When an environment exceeds this limit, you'll land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="a0774-200">載入我的環境需要很長的時間</span><span class="sxs-lookup"><span data-stu-id="a0774-200">It takes a long time to load my environment</span></span>

<span data-ttu-id="a0774-201">您可以為您的環境新增選擇性的優化，以加快載入的速度。</span><span class="sxs-lookup"><span data-stu-id="a0774-201">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="a0774-202">如需詳細資訊，請參閱「 [將您的環境優化](#optimizing-your-environment) 」。</span><span class="sxs-lookup"><span data-stu-id="a0774-202">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="a0774-203">我的環境規模不正確</span><span class="sxs-lookup"><span data-stu-id="a0774-203">The scale of my environment is incorrect</span></span>

<span data-ttu-id="a0774-204">Windows Mixed Reality 會在載入環境時將 glTF 單位轉譯為1計量。</span><span class="sxs-lookup"><span data-stu-id="a0774-204">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="a0774-205">如果您的環境載入未預期的規模，請再次檢查您的匯出工具，以確定您是以1計量規模的模型化。</span><span class="sxs-lookup"><span data-stu-id="a0774-205">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1-meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="a0774-206">我的環境中產生的位置不正確</span><span class="sxs-lookup"><span data-stu-id="a0774-206">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="a0774-207">預設產生位置位於環境中0、0、0。</span><span class="sxs-lookup"><span data-stu-id="a0774-207">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="a0774-208">目前無法自訂此位置，因此您必須將您的環境與您想要的產生點上的來源一起匯出，以修改產生點。</span><span class="sxs-lookup"><span data-stu-id="a0774-208">It's not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the spawn point you want.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="a0774-209">音訊在環境中無法正確播放</span><span class="sxs-lookup"><span data-stu-id="a0774-209">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="a0774-210">當您建立自訂環境時，它會使用聲場呈現模擬，而不符合您所建立的實體空間。</span><span class="sxs-lookup"><span data-stu-id="a0774-210">When you create your custom environment, it will be using an acoustics rendering simulation that doesn't match the physical space you've created.</span></span> <span data-ttu-id="a0774-211">音效可能來自錯誤的方向，而且可能音效 muffled。</span><span class="sxs-lookup"><span data-stu-id="a0774-211">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="a0774-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0774-212">See also</span></span>
* [<span data-ttu-id="a0774-213">GitHub 上的 Windows Mixed Reality 資產轉換器 () </span><span class="sxs-lookup"><span data-stu-id="a0774-213">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)