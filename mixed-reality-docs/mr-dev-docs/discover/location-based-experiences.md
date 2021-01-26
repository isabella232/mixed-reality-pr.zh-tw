---
title: Windows Mixed Reality 的位置型娛樂
description: 瞭解以位置為基礎的娛樂 Windows Mixed Reality —硬體、背包」的電腦、追蹤、設定和支援。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: 混合的現實、vr、lbe、位置、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、硬體、HoloLens、多玩家、雲端服務、azure
ms.openlocfilehash: 1cc54ad0ef4b9892c49e13c7437a4d5356093c79
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810106"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="6412f-104">Windows Mixed Reality 的位置型娛樂</span><span class="sxs-lookup"><span data-stu-id="6412f-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="6412f-105">在過去幾年來，我們在以位置為基礎的娛樂類別中看到大量的成長和創新。</span><span class="sxs-lookup"><span data-stu-id="6412f-105">In the last couple of years, we've seen an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="6412f-106">傳統的場地（例如主題公園和劇院）已開始提供沉浸式、多玩家體驗，作為現有乘車點和安裝的免費體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-106">Traditional venues like theme parks and theaters have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="6412f-107">新的操作員和場地為 masses 帶來了獨特的多 sensorial、多玩家體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="6412f-108">所有這些經驗都會將信封推播到混合現實的可能原因。</span><span class="sxs-lookup"><span data-stu-id="6412f-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="6412f-109">本檔是在以位置為基礎的娛樂類別中開始使用 Windows Mixed Reality 的指南。</span><span class="sxs-lookup"><span data-stu-id="6412f-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="6412f-110">下列指導方針可能還適用于除了訓練、產品設計和其他使用案例以外的位置型體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design, and other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="6412f-111">工程常見問題</span><span class="sxs-lookup"><span data-stu-id="6412f-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="6412f-112">硬體</span><span class="sxs-lookup"><span data-stu-id="6412f-112">Hardware</span></span>

<span data-ttu-id="6412f-113">**問： Microsoft 及其合作夥伴可在我的設定中使用的硬體有哪些？**</span><span class="sxs-lookup"><span data-stu-id="6412f-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="6412f-114">答： Microsoft 及其 OEM 合作夥伴提供了一套具吸引力的裝置組合，可根據您的需求進行選擇。</span><span class="sxs-lookup"><span data-stu-id="6412f-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="6412f-115">如果您為客戶提供的體驗需要虛擬實境耳機，HP、Samsung 和 Acer 的市場耳機很適合。</span><span class="sxs-lookup"><span data-stu-id="6412f-115">If the experiences you’re providing to your customers requires a virtual reality headset, in-market headsets from HP, Samsung, and Acer are a great fit.</span></span> <span data-ttu-id="6412f-116">每個耳機都有自己的差異化屬性。</span><span class="sxs-lookup"><span data-stu-id="6412f-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="6412f-117">下列各項的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6412f-117">More details on each below.</span></span>

<span data-ttu-id="6412f-118">HP 回音： [詳細資料](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="6412f-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="6412f-119">Samsung 電影對白 +： [詳細資料](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="6412f-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="6412f-120">Acer： [詳細資料](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="6412f-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="6412f-121">如果您的地點是以混合或增強的現實體驗來學習，請查看 Microsoft HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="6412f-121">If your location specializes in mixed or augmented reality experiences with see-through headsets, check out the Microsoft HoloLens 2.</span></span>  

<span data-ttu-id="6412f-122">HoloLens 2： [預先訂購的興趣](https://www.microsoft.com//hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="6412f-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com//hololens/buy)</span></span>

<span data-ttu-id="6412f-123">如果您想要試驗使用先進的電腦視覺、語音和內文追蹤的體驗，Azure Kinect DK 相當適合。</span><span class="sxs-lookup"><span data-stu-id="6412f-123">If you’re experimenting with experiences that use advanced computer vision, speech, and body tracking, the Azure Kinect DK is a good fit.</span></span>  

<span data-ttu-id="6412f-124">Azure Kinect： [詳細資料](https://azure.microsoft.com//services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="6412f-124">Azure Kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)</span></span>

<span data-ttu-id="6412f-125">**問：我可以使用哪些背包」電腦的組合來執行電腦行動網卡的 VR 體驗？**</span><span class="sxs-lookup"><span data-stu-id="6412f-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="6412f-126">針對電腦行動網卡的 VR 體驗，我們 Oem 提供了一系列完全為該需求打造的背包」電腦。</span><span class="sxs-lookup"><span data-stu-id="6412f-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="6412f-127">HP 剛剛推出了其 HP VR 背包」 G2，這是世界上最強大的穿戴式 PC –針對自由漫遊體驗進行優化，現在提供了30% 以上的 RTX 2080 GPU 功能。</span><span class="sxs-lookup"><span data-stu-id="6412f-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="6412f-128">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6412f-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="6412f-129">安裝程式</span><span class="sxs-lookup"><span data-stu-id="6412f-129">Setup</span></span>

<span data-ttu-id="6412f-130">**問：如何可以更輕鬆地設定安裝程式，並自訂 LBE 的混合實境入口？**</span><span class="sxs-lookup"><span data-stu-id="6412f-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="6412f-131">這項功能需要版本2000.19061.1011.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="6412f-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="6412f-132">您可能會發現您需要更多的混合實境入口自訂，而不是透過應用程式，將應用程式部署到 kiosk 或自訂體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="6412f-133">混合實境入口最新的7月更新支援數個可透過設定檔設定的 advanced settings：</span><span class="sxs-lookup"><span data-stu-id="6412f-133">The latest July update of Mixed Reality Portal supports several advanced settings, which you can set via a configuration file:</span></span>  

<span data-ttu-id="6412f-134">允許失敗的系統檢查–安裝程式通常會先檢查電腦是否與 Windows Mixed Reality 相容，再完成安裝程式。</span><span class="sxs-lookup"><span data-stu-id="6412f-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="6412f-135">如果發生相容性問題，略過相容性檢查可能會在嘗試執行 Windows Mixed Reality 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="6412f-135">Bypassing compatibility checks may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="6412f-136">略過裝置附屬應用程式– DCA 提供製造商提供的耳機專屬設定步驟，並允許更新耳機的固件。</span><span class="sxs-lookup"><span data-stu-id="6412f-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="6412f-137">略過房間設定–而不是收到建立空間界限的提示，您可以直接進入站上/固定模式的耳機。</span><span class="sxs-lookup"><span data-stu-id="6412f-137">Skip room setup – instead of being prompted to create a room boundary, you can continue directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="6412f-138">略過從存放區安裝應用程式-一般安裝程式會安裝數個存放區應用程式，包括3D 檢視器和 Edge 360 檢視器附加元件。</span><span class="sxs-lookup"><span data-stu-id="6412f-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="6412f-139">這會略過這些應用程式的安裝，但您可能遺失裝置功能。</span><span class="sxs-lookup"><span data-stu-id="6412f-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="6412f-140">以全螢幕顯示預覽–混合實境入口預設為在使用耳機時，于桌上型電腦的全螢幕中顯示耳機預覽。</span><span class="sxs-lookup"><span data-stu-id="6412f-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="6412f-141">隱藏側邊面板的新狀態-防止新的面板在啟動混合實境入口時展開。</span><span class="sxs-lookup"><span data-stu-id="6412f-141">Hide New for your side panel – prevents the New for your panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="6412f-142">如何設定：</span><span class="sxs-lookup"><span data-stu-id="6412f-142">How to configure:</span></span>  

<span data-ttu-id="6412f-143">若要設定這些設定中的任何一項，您必須在此目錄下建立名為 _UserConfig.js_ 的檔案： _$env \\ ： localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \localstate_</span><span class="sxs-lookup"><span data-stu-id="6412f-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="6412f-144">對大部分的使用者而言，這看起來會像這樣： _C:\Users \<username> \Appdata\local\packages\ microsoft.mixedreality.portal_8wekyb3d8bbwe \localstate \\_</span><span class="sxs-lookup"><span data-stu-id="6412f-144">For most users, this will look like: _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="6412f-145">針對您想要啟用的任何上述設定，JSON 檔案的下列內容應設定為 "true"：</span><span class="sxs-lookup"><span data-stu-id="6412f-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="6412f-146">**問：是否有設定 playspace 的任何指引？**</span><span class="sxs-lookup"><span data-stu-id="6412f-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="6412f-147">答：設定 playspace 的方式應該與取用者設定體驗一樣。</span><span class="sxs-lookup"><span data-stu-id="6412f-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="6412f-148">房間設定程式也可讓您定義您的房間界線。</span><span class="sxs-lookup"><span data-stu-id="6412f-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="6412f-149">您可以在 [這裡](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)閱讀更多有關設定空間界限的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6412f-149">More details on configuring room boundaries can be read [here](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="6412f-150">如同上述檔中所述，最大合理的單一座標 playspace 大約是5mx5m。</span><span class="sxs-lookup"><span data-stu-id="6412f-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="6412f-151">如果您想要有更大的區域，您可以在 Windows 全像 API 堆疊中使用空間錨點功能。</span><span class="sxs-lookup"><span data-stu-id="6412f-151">If you want to have a larger area, you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="6412f-152">使用此 API 時，您將需要在所產生的體驗中進行自訂工程。</span><span class="sxs-lookup"><span data-stu-id="6412f-152">Using this API will require custom engineering in the experiences you're producing.</span></span>  

<span data-ttu-id="6412f-153">您可以在 [這裡](/windows/mixed-reality/coordinate-systems)閱讀更多有關如何將內容優化以取得不同空間大小的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6412f-153">More details on how to optimize your content for different space sizes can be read [here](/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="6412f-154">**問：我的空間太大，當我嘗試設定具有界限的長期體驗時遇到錯誤。我該怎麼做才能設定我的大型自由漫遊體驗？**</span><span class="sxs-lookup"><span data-stu-id="6412f-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to set up my large free-roam experience work?**</span></span>

<span data-ttu-id="6412f-155">答：若要設定比 ~ 18x18ft 更大的空間，您無法使用系統提供的界限體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-155">A: To set up a larger space than ~18x18ft, you can't use the boundary experience provided by the system.</span></span>  <span data-ttu-id="6412f-156">界限系統依賴單一固定座標「錨點」，當使用者距離中央階段錨點太遠時，這可能會變得不穩定。</span><span class="sxs-lookup"><span data-stu-id="6412f-156">The boundary systems rely on a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="6412f-157">您可以設定「固定」模式，而不會顯示界限或設定階段界限或 playspace。</span><span class="sxs-lookup"><span data-stu-id="6412f-157">You can set up “seated” mode, which won't display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="6412f-158">您必須在應用程式內設定多個空間錨點，以參考實體界限區域。</span><span class="sxs-lookup"><span data-stu-id="6412f-158">You’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="6412f-159">應用程式開發人員負責顯示必要的保護措施，讓使用者不會與實體周圍發生衝突。</span><span class="sxs-lookup"><span data-stu-id="6412f-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="6412f-160">這些可能是在體驗或自訂遊戲界限視覺效果中的數位牆。</span><span class="sxs-lookup"><span data-stu-id="6412f-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="6412f-161">您可以在 [這裡](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到使用 WMR 設定房間界限的指引。</span><span class="sxs-lookup"><span data-stu-id="6412f-161">Guidance on setting up the room boundary with WMR can be found [here](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="6412f-162">**問： playspace 的原點在哪裡？**</span><span class="sxs-lookup"><span data-stu-id="6412f-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="6412f-163">答： playspace 的來源取決於房間設定體驗，更明確地說，在安裝期間按下中間按鈕的 HMD 位置。</span><span class="sxs-lookup"><span data-stu-id="6412f-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="6412f-164">多玩家設定</span><span class="sxs-lookup"><span data-stu-id="6412f-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="6412f-165">**問：我在的地點部署了多玩家體驗。Windows Mixed Reality 是否支援？**</span><span class="sxs-lookup"><span data-stu-id="6412f-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="6412f-166">答：如果您透過我們的測試人員計畫加入宣告 Windows 20H1 或更新版本的組建，您可以存取地圖共用的新介面。</span><span class="sxs-lookup"><span data-stu-id="6412f-166">A: If you opt into the Windows 20H1 or later build via our Insider program, you can access a new interface for map sharing.</span></span> <span data-ttu-id="6412f-167">這項新功能可透過 Windows 裝置入口網站的 [ [對應管理員](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) ] 介面使用。</span><span class="sxs-lookup"><span data-stu-id="6412f-167">This new functionality is available via the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) interface of the Windows Device portal.</span></span> <span data-ttu-id="6412f-168">若要使用此工具，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="6412f-168">To use this tool, follow the steps below:</span></span>
* <span data-ttu-id="6412f-169">請確定您加入宣告20H1 或更新版本-2019 年9月之後，這表示使用我們的測試人員計畫</span><span class="sxs-lookup"><span data-stu-id="6412f-169">Make sure you're opted into 20H1 or later - after September 2019, this means using our Insider program</span></span>
* <span data-ttu-id="6412f-170">使用這些[指示](/windows/uwp/debug-test-perf/device-portal-desktop)啟用 WINDOWS 裝置入口網站 (WDP) </span><span class="sxs-lookup"><span data-stu-id="6412f-170">Enable the Windows Device Portal (WDP) using these [instructions](/windows/uwp/debug-test-perf/device-portal-desktop)</span></span>
* <span data-ttu-id="6412f-171">插入您想要從 HMD 下載現有對應或匯入新對應的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6412f-171">Plug in a Windows Mixed Reality HMD that you wish to either download an existing map from or import a new map</span></span>
* <span data-ttu-id="6412f-172">使用 [設定] 畫面中提供的 URL，在您選擇的瀏覽器中流覽至 WDP。</span><span class="sxs-lookup"><span data-stu-id="6412f-172">Navigate to the WDP in your browser of choice using the URL provided in the settings screen.</span></span>
    * <span data-ttu-id="6412f-173">流覽至 [混合式事實] 區段，然後選取 [對應管理員]。</span><span class="sxs-lookup"><span data-stu-id="6412f-173">Once there Navigate to the "Mixed Reality" section and select "Map Manager".</span></span>
    * <span data-ttu-id="6412f-174">您現在可以使用 [下載] 按鈕，從電腦匯出現有的對應。</span><span class="sxs-lookup"><span data-stu-id="6412f-174">You can now use the "Download" button to export an existing map from the machine.</span></span>
    * <span data-ttu-id="6412f-175">您可以使用 [上傳對應檔] 按鈕，從先前的匯出匯入對應 (可能在不同的電腦上) 。</span><span class="sxs-lookup"><span data-stu-id="6412f-175">You can use the "Upload a map file" button to import a map from a previous export (perhaps on a different machine).</span></span>
    * <span data-ttu-id="6412f-176">您可以使用 [匯入]，讓系統在這部電腦上針對此 HMD 使用該對應。</span><span class="sxs-lookup"><span data-stu-id="6412f-176">You can use "Import" to enable the system to use that map for this HMD on this machine.</span></span>

> [!NOTE] 
> <span data-ttu-id="6412f-177">先前，您可以使用空間資料封裝工具，不過，該工具最初是以不受支援的形式發行，而且現在已正式淘汰，且不再于20H1 運作。</span><span class="sxs-lookup"><span data-stu-id="6412f-177">Previously, it was possible to use the Spatial Data Packager Tool, however, that tool was originally released as unsupported and is now officially deprecated and no longer functional on 20H1.</span></span> <span data-ttu-id="6412f-178">相反地，請使用如上所述的收件匣 [對應管理員](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) 工具。</span><span class="sxs-lookup"><span data-stu-id="6412f-178">Instead, please use the inbox [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool as described above.</span></span> 

### <a name="tracking"></a><span data-ttu-id="6412f-179">跟蹤</span><span class="sxs-lookup"><span data-stu-id="6412f-179">TRACKING</span></span>

<span data-ttu-id="6412f-180">問： Windows Mixed Reality 耳機中的追蹤技術如何運作？</span><span class="sxs-lookup"><span data-stu-id="6412f-180">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="6412f-181">混合現實與 HoloLens 共用相同的追蹤技術。</span><span class="sxs-lookup"><span data-stu-id="6412f-181">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="6412f-182">若要深入瞭解內部追蹤系統，請參閱 [此處](/windows/mixed-reality/enthusiast-guide/tracking-system)的檔。</span><span class="sxs-lookup"><span data-stu-id="6412f-182">To learn more about the inside-out tracking system, check out the documentation [here](/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="6412f-183">如需更高層級空間對應系統運作方式的說明，請參閱 [這裡](../design/spatial-mapping.md)的說明。</span><span class="sxs-lookup"><span data-stu-id="6412f-183">For a description of how the higher-level spatial mapping system works you can read our description [here](../design/spatial-mapping.md).</span></span>

<span data-ttu-id="6412f-184">**問：是否有任何取得可靠追蹤磁片區的最佳作法？**</span><span class="sxs-lookup"><span data-stu-id="6412f-184">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="6412f-185">若要以最佳方式設定追蹤成功的環境，您可以閱讀這 [篇文章](/hololens/hololens-environment-considerations)中的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="6412f-185">To best configure the environment for tracking success, you can read best practices in this [post](/hololens/hololens-environment-considerations).</span></span>

<span data-ttu-id="6412f-186">**問：是否有任何特定的細微差異，可考慮在倉儲規模空間或優化中進行追蹤？**</span><span class="sxs-lookup"><span data-stu-id="6412f-186">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="6412f-187">答：下列做法有助於取得更可靠的追蹤磁片區：</span><span class="sxs-lookup"><span data-stu-id="6412f-187">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="6412f-188">在多個位置重迭的房間內提供不同的功能，可協助追蹤系統取得穩固的鎖定。</span><span class="sxs-lookup"><span data-stu-id="6412f-188">Providing different features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="6412f-189">請考慮隨機油漆 splatters 和影線，而不是使用實線輪廓樣式線條。</span><span class="sxs-lookup"><span data-stu-id="6412f-189">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="6412f-190">盡可能將您區域中的燈光動態範圍降至最低。</span><span class="sxs-lookup"><span data-stu-id="6412f-190">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="6412f-191">混合現實 Hmd 上的追蹤攝影機不是 HDR，而且 AGC (自動取得) 和 AEC (自動曝光，) 處理不同的光源。</span><span class="sxs-lookup"><span data-stu-id="6412f-191">The tracking cameras on our Mixed Reality HMDs aren't HDR and have AGC (auto gain) and AEC (auto exposure) going to deal with different lighting.</span></span> <span data-ttu-id="6412f-192">視 surface light、模式和對比的分佈而定，AGC 或 AEC 可能會讓您成為最大的白色或黑色房間，這可能會讓您的功能更有可能與「色彩」相反。</span><span class="sxs-lookup"><span data-stu-id="6412f-192">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a much all white or black room, which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="6412f-193">如果您想要將內部圖片放在具有亮日光背後的外部視窗前方，然後調整曝光，讓您可以在外部看到詳細資料，則內部的所有專案都是 underexposed 和黑色。</span><span class="sxs-lookup"><span data-stu-id="6412f-193">If you're trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="6412f-194">或者，如果是在內部進行設定，則外部的所有專案現在都是 overexposed，而且全部都是白色。</span><span class="sxs-lookup"><span data-stu-id="6412f-194">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="6412f-195">在房間內的聚光燈 (甚至是) 的額外負荷，如果追蹤攝影機有時可能會原因，這會使追蹤攝影機的 AEC/AGC 混淆。</span><span class="sxs-lookup"><span data-stu-id="6412f-195">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits, which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="6412f-196">平面/漫射光源有助於。</span><span class="sxs-lookup"><span data-stu-id="6412f-196">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="6412f-197">混合現實雲端服務與 AZURE</span><span class="sxs-lookup"><span data-stu-id="6412f-197">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="6412f-198">**問：如何 Microsoft Azure 協助我的企業規模？**</span><span class="sxs-lookup"><span data-stu-id="6412f-198">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="6412f-199">答：以 Azure 為基礎的現場和遠端系統管理，可協助您的業務成為資料驅動、降低營運成本，並在現有和新的地點調整部署規模。</span><span class="sxs-lookup"><span data-stu-id="6412f-199">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="6412f-200">Azure 雲端服務（例如 Azure 儲存體、Azure Functions、App Service、Azure 網路和 IOT 中樞）可協助您進行下列使用案例：</span><span class="sxs-lookup"><span data-stu-id="6412f-200">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking, and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="6412f-201">遠端裝置部署 & 管理</span><span class="sxs-lookup"><span data-stu-id="6412f-201">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="6412f-202">Real-Time 現場分析</span><span class="sxs-lookup"><span data-stu-id="6412f-202">Real-Time Onsite Analytics</span></span> 

<span data-ttu-id="6412f-203">智慧型適應性的 LBE 遊戲</span><span class="sxs-lookup"><span data-stu-id="6412f-203">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="6412f-204">LBE 內容串流和部署</span><span class="sxs-lookup"><span data-stu-id="6412f-204">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="6412f-205">LBE Player 喜好設定熱度圖</span><span class="sxs-lookup"><span data-stu-id="6412f-205">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="6412f-206">LBE 保留與預約系統</span><span class="sxs-lookup"><span data-stu-id="6412f-206">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="6412f-207">**問：我正在開發空間 MMOG，以部署大量的使用量。任何有助於管理內容和物件持續性的服務？**</span><span class="sxs-lookup"><span data-stu-id="6412f-207">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="6412f-208">答： Azure 空間錨點是全新的混合現實服務，可在 HoloLens、iOS 和 Android 裝置上啟用多使用者、空間感知的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-208">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS, and Android devices.</span></span> <span data-ttu-id="6412f-209">您可以在 [這裡](https://azure.microsoft.com//services/spatial-anchors/)深入瞭解 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="6412f-209">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com//services/spatial-anchors/).</span></span>

<span data-ttu-id="6412f-210">**問。我們的場地專門採用多玩家體驗，而我想要將開發時間專注于內容和前端開發。是否有可協助我啟動或卸載後端開發的供應專案？**</span><span class="sxs-lookup"><span data-stu-id="6412f-210">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="6412f-211">答： Azure PlayFab 是適用于即時遊戲的完整後端平臺。</span><span class="sxs-lookup"><span data-stu-id="6412f-211">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="6412f-212">您可以在 [這裡](https://playfab.com/)深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="6412f-212">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="6412f-213">其他</span><span class="sxs-lookup"><span data-stu-id="6412f-213">Misc</span></span>

<span data-ttu-id="6412f-214">**問：我使用 SteamVR 來部署我的體驗。Windows Mixed Reality 可以搭配 SteamVR 使用嗎？**</span><span class="sxs-lookup"><span data-stu-id="6412f-214">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="6412f-215">答：適用于 SteamVR 的 Windows Mixed Reality 可讓使用者在 Windows Mixed Reality 的沉浸式耳機上執行 SteamVR 體驗。</span><span class="sxs-lookup"><span data-stu-id="6412f-215">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="6412f-216">[在這裡](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)深入瞭解使用 WMR SteamVR。</span><span class="sxs-lookup"><span data-stu-id="6412f-216">Learn more about SteamVR with WMR [here](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="6412f-217">支援和團體</span><span class="sxs-lookup"><span data-stu-id="6412f-217">Support and community</span></span>  

<span data-ttu-id="6412f-218">我們有幾個實用的資源，可協助您與小組的主題專家交流、取得疑難排解支援，以及對更廣大的混合現實開發人員群體貢獻。</span><span class="sxs-lookup"><span data-stu-id="6412f-218">We have a few helpful resources to help you engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="6412f-219">如果您遇到任何公開發行功能的問題，請使用意見反應中樞提出錯誤。如需指引，請參閱此 [頁面](/windows/mixed-reality/enthusiast-guide/filing-feedback)。</span><span class="sxs-lookup"><span data-stu-id="6412f-219">If you run into issues with any publicly released features, file a bug using Feedback Hub.For guidance, refer to this [page](/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="6412f-220">如需 WMR 的其他疑難排解協助，請向我們的客戶支援小組 [提出支援要求](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) 。</span><span class="sxs-lookup"><span data-stu-id="6412f-220">For other troubleshooting help with WMR, file a [support request](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) with our customer support team.</span></span>

<span data-ttu-id="6412f-221">加入我們的 HoloDevelopers 時差頻道，與混合現實開發人員和主題專家互動： [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="6412f-221">Join our HoloDevelopers Slack channel to engage with the mixed reality developers and subject matter experts: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="6412f-222">Twitter：遵循我們的混合現實開發人員關係小組來取得新聞、活動和更新 @MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="6412f-222">Twitter: Follow our Mixed Reality Developer Relations team for news, events, and updates @MxdRealityDev</span></span> 

<span data-ttu-id="6412f-223">如果您一直在三藩市或周圍，在 Microsoft Reactor 一律會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="6412f-223">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="6412f-224">您可以在 [這裡](https://developer.microsoft.com//reactor/Location/San%20Francisco)看到我們的活動行事曆。</span><span class="sxs-lookup"><span data-stu-id="6412f-224">You can see our calendar of events [here](https://developer.microsoft.com//reactor/Location/San%20Francisco).</span></span>