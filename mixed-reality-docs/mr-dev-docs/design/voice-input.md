---
title: 語音輸入
description: 語音輸入是 HoloLens 和 Windows Mixed Reality 沉浸式耳機的核心輸入。 語音可以用於命令、聽寫、Cortana 等等。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、語音、cortana、語音、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、注視
ms.openlocfilehash: f4f81383f942961857b088b05c4e8cac07ab7dfe
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703204"
---
# <a name="voice-input"></a><span data-ttu-id="a888b-105">語音輸入</span><span class="sxs-lookup"><span data-stu-id="a888b-105">Voice input</span></span>

![語音輸入](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="a888b-107">語音是 HoloLens 輸入的其中一種主要形式。</span><span class="sxs-lookup"><span data-stu-id="a888b-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="a888b-108">它可讓您直接命令全息圖，而不需要使用 [手手勢](gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="a888b-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="a888b-109">語音輸入是溝通意圖的一種自然方式。</span><span class="sxs-lookup"><span data-stu-id="a888b-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="a888b-110">語音在往返複雜介面時特別有用，因為它可讓使用者使用一個命令來剪下整個嵌套功能表。</span><span class="sxs-lookup"><span data-stu-id="a888b-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="a888b-111">語音輸入是由在所有其他 _通用 Windows 應用程式_ 中支援語音的 [相同引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)所驅動。</span><span class="sxs-lookup"><span data-stu-id="a888b-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="a888b-112">在 HoloLens 上，語音辨識一律會以設定中設定的 Windows 顯示語言運作。</span><span class="sxs-lookup"><span data-stu-id="a888b-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="a888b-113">語音和注視</span><span class="sxs-lookup"><span data-stu-id="a888b-113">Voice and gaze</span></span>

<span data-ttu-id="a888b-114">使用語音命令時， (head 或眼睛) 眼通常會用來做為目的機制，不論是使用資料指標 ( 「選取」 ) 或將命令隱含地通道處理至您所查看的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a888b-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="a888b-115">如此一來，甚至可能還不需要顯示任何 _看起來的游標 ( 「看起來」 )_。</span><span class="sxs-lookup"><span data-stu-id="a888b-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="a888b-116">當然，有些語音命令根本不需要目標，例如「移至開始」或「嗨 Cortana」。</span><span class="sxs-lookup"><span data-stu-id="a888b-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="a888b-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a888b-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a888b-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="a888b-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a888b-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a888b-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a888b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a888b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a888b-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="a888b-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a888b-122">語音輸入</span><span class="sxs-lookup"><span data-stu-id="a888b-122">Voice input</span></span></td>
        <td><span data-ttu-id="a888b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a888b-123">✔️</span></span></td>
        <td><span data-ttu-id="a888b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="a888b-124">✔️</span></span></td>
        <td><span data-ttu-id="a888b-125">使用麥克風的✔️ () </span><span class="sxs-lookup"><span data-stu-id="a888b-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="a888b-126">"Select" 命令</span><span class="sxs-lookup"><span data-stu-id="a888b-126">The "select" command</span></span>

<span data-ttu-id="a888b-127">**HoloLens (第 1 代)**</span><span class="sxs-lookup"><span data-stu-id="a888b-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="a888b-128">即使沒有特別為您的應用程式新增語音支援，您的使用者只要說出系統 voice 命令「select」就可以啟用全像。</span><span class="sxs-lookup"><span data-stu-id="a888b-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="a888b-129">這 [與在 hololens 上按](gaze-and-commit.md#composite-gestures) 下滑鼠的方式相同，在 [hololens clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按下 [選取] 按鈕，或按 [Windows Mixed Reality 運動控制器](motion-controllers.md)上的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="a888b-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="a888b-130">您將聽到音效，並看到具有 [選取] 的工具提示顯示為 [確認]。</span><span class="sxs-lookup"><span data-stu-id="a888b-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="a888b-131">「選取」是由低功率關鍵字偵測演算法所啟用，因此隨時都能以最少的電池生命週期來說，即使您手上也可以。</span><span class="sxs-lookup"><span data-stu-id="a888b-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="a888b-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="a888b-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="a888b-133">若要在 HoloLens 2 中使用 [選取] 語音命令，您必須先顯示要用來作為指標的注視游標。</span><span class="sxs-lookup"><span data-stu-id="a888b-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="a888b-134">要讓它啟動的命令很容易記住，只要說「select」就可以了。</span><span class="sxs-lookup"><span data-stu-id="a888b-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="a888b-135">若要結束此模式，只要使用您的手，就可以藉由按下滑鼠按鍵、使用手指接近按鈕，或使用系統手勢來退出。</span><span class="sxs-lookup"><span data-stu-id="a888b-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="a888b-136">*影像：說「選取」以使用語音命令進行選取*</span><span class="sxs-lookup"><span data-stu-id="a888b-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![使用者可以說「選取」以使用語音命令進行選取。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="a888b-138">嗨 Cortana</span><span class="sxs-lookup"><span data-stu-id="a888b-138">Hey Cortana</span></span>

<span data-ttu-id="a888b-139">您也可以說「嗨 Cortana」以隨時帶出 Cortana。</span><span class="sxs-lookup"><span data-stu-id="a888b-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="a888b-140">您不必等待她繼續詢問您的問題，或為她提供指示，例如，嘗試說「嗨 Cortana，天氣是什麼？」。</span><span class="sxs-lookup"><span data-stu-id="a888b-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="a888b-141">作為單一句子。</span><span class="sxs-lookup"><span data-stu-id="a888b-141">as a single sentence.</span></span> <span data-ttu-id="a888b-142">如需 Cortana 和您可以做什麼的詳細資訊，請直接詢問她！</span><span class="sxs-lookup"><span data-stu-id="a888b-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="a888b-143">說「嗨 Cortana，我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="a888b-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="a888b-144">她將會提取一份工作和建議的命令清單。</span><span class="sxs-lookup"><span data-stu-id="a888b-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="a888b-145">如果您已經在 Cortana 應用程式中，也可以按一下 [ **？]。**</span><span class="sxs-lookup"><span data-stu-id="a888b-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="a888b-146">圖示，以提取這個相同的功能表。</span><span class="sxs-lookup"><span data-stu-id="a888b-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="a888b-147">**HoloLens 專用的命令**</span><span class="sxs-lookup"><span data-stu-id="a888b-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="a888b-148">「我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="a888b-148">"What can I say?"</span></span>
* <span data-ttu-id="a888b-149">「移至開始」-而不是 [bloom](system-gesture.md#bloom) 來進入 [開始功能表](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="a888b-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="a888b-150">「啟動 <app> 」</span><span class="sxs-lookup"><span data-stu-id="a888b-150">"Launch <app>"</span></span>
* <span data-ttu-id="a888b-151">「移 <app> 至這裡」</span><span class="sxs-lookup"><span data-stu-id="a888b-151">"Move <app> here"</span></span>
* <span data-ttu-id="a888b-152">「拍攝相片」</span><span class="sxs-lookup"><span data-stu-id="a888b-152">"Take a picture"</span></span>
* <span data-ttu-id="a888b-153">「開始錄製」</span><span class="sxs-lookup"><span data-stu-id="a888b-153">"Start recording"</span></span>
* <span data-ttu-id="a888b-154">「停止錄製」</span><span class="sxs-lookup"><span data-stu-id="a888b-154">"Stop recording"</span></span>
* <span data-ttu-id="a888b-155">「顯示手邊的光線」</span><span class="sxs-lookup"><span data-stu-id="a888b-155">"Show hand ray"</span></span>
* <span data-ttu-id="a888b-156">「隱藏手光線」</span><span class="sxs-lookup"><span data-stu-id="a888b-156">"Hide hand ray"</span></span>
* <span data-ttu-id="a888b-157">「提高亮度」</span><span class="sxs-lookup"><span data-stu-id="a888b-157">"Increase the brightness"</span></span>
* <span data-ttu-id="a888b-158">「降低亮度」</span><span class="sxs-lookup"><span data-stu-id="a888b-158">"Decrease the brightness"</span></span>
* <span data-ttu-id="a888b-159">「增加磁片區」</span><span class="sxs-lookup"><span data-stu-id="a888b-159">"Increase the volume"</span></span>
* <span data-ttu-id="a888b-160">「減少音量」</span><span class="sxs-lookup"><span data-stu-id="a888b-160">"Decrease the volume"</span></span>
* <span data-ttu-id="a888b-161">「靜音」或「取消靜音」</span><span class="sxs-lookup"><span data-stu-id="a888b-161">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="a888b-162">「關閉裝置」</span><span class="sxs-lookup"><span data-stu-id="a888b-162">"Shut down the device"</span></span>
* <span data-ttu-id="a888b-163">「重新開機裝置」</span><span class="sxs-lookup"><span data-stu-id="a888b-163">"Restart the device"</span></span>
* <span data-ttu-id="a888b-164">「移至睡眠」</span><span class="sxs-lookup"><span data-stu-id="a888b-164">"Go to sleep"</span></span>
* <span data-ttu-id="a888b-165">「這是什麼時候？」</span><span class="sxs-lookup"><span data-stu-id="a888b-165">"What time is it?"</span></span>
* <span data-ttu-id="a888b-166">「我剩下多少電池？」</span><span class="sxs-lookup"><span data-stu-id="a888b-166">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="a888b-167">「看它，說它」</span><span class="sxs-lookup"><span data-stu-id="a888b-167">"See It, Say It"</span></span><br>
        <span data-ttu-id="a888b-168">HoloLens 具有語音輸入的「查看」模型，其中按鈕上的標籤會告訴使用者他們可以說的語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-168">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="a888b-169">例如，查看 HoloLens 中的應用程式視窗時 (第1代) ，使用者可以說出他們在應用程式行中看到的「調整」命令，來調整世界上應用程式的位置。</span><span class="sxs-lookup"><span data-stu-id="a888b-169">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="a888b-170">*影像：使用者可以說出他們在應用程式行中看到的「調整」命令，以調整應用程式的位置。*</span><span class="sxs-lookup"><span data-stu-id="a888b-170">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a888b-171">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a888b-171">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="a888b-172">![查看應用程式視窗或全像影像時，使用者可以說出他們在應用程式行中看到的「調整」命令，以調整應用程式在世界中的位置。](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="a888b-172">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="a888b-173">當應用程式遵循此規則時，使用者很容易就能瞭解如何控制系統。</span><span class="sxs-lookup"><span data-stu-id="a888b-173">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="a888b-174">若要強調這一點，在 HoloLens (第一代) 中的按鈕上撥雲見日時，如果按鈕為語音啟用，您將會看到「聲音停留」工具提示，並顯示「按下」所說的命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-174">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="a888b-175">若要顯示 HoloLens 2 中的語音工具提示，請說「選取」或「我可以說什麼」來顯示語音游標 (請參閱影像) 。</span><span class="sxs-lookup"><span data-stu-id="a888b-175">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="a888b-176">*影像：「看到它，假設」命令出現在按鈕下方*</span><span class="sxs-lookup"><span data-stu-id="a888b-176">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![查看它，假設命令出現在按鈕下方](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="a888b-178">快速全息圖操作的語音命令</span><span class="sxs-lookup"><span data-stu-id="a888b-178">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="a888b-179">在撥雲見日時，您可以說一些語音命令，以快速執行操作工作。</span><span class="sxs-lookup"><span data-stu-id="a888b-179">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="a888b-180">這些語音命令適用于應用程式視窗，以及您放在世界各地的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="a888b-180">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="a888b-181">**全息圖操作命令**</span><span class="sxs-lookup"><span data-stu-id="a888b-181">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="a888b-182">臉部</span><span class="sxs-lookup"><span data-stu-id="a888b-182">Face me</span></span>
* <span data-ttu-id="a888b-183">更大 |提高</span><span class="sxs-lookup"><span data-stu-id="a888b-183">Bigger | Enhance</span></span>
* <span data-ttu-id="a888b-184">小</span><span class="sxs-lookup"><span data-stu-id="a888b-184">Smaller</span></span>

<span data-ttu-id="a888b-185">在 HoloLens 2 上，您也可以結合眼睛來建立更自然的互動，以隱含的方式提供您所參考之內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a888b-185">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="a888b-186">例如，您可以只查看一個全息圖，然後說 _「放入_」，然後查看您要放置它的位置，然後說「在 _這裡_」。</span><span class="sxs-lookup"><span data-stu-id="a888b-186">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="a888b-187">或者，您可以在複雜的電腦上查看全像的部分，然後說：「給我更多關於 _這個_ 的資訊」。</span><span class="sxs-lookup"><span data-stu-id="a888b-187">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="a888b-188">探索語音命令</span><span class="sxs-lookup"><span data-stu-id="a888b-188">Discovering voice commands</span></span>

<span data-ttu-id="a888b-189">某些命令（例如上述快速操作的命令）可以隱藏。</span><span class="sxs-lookup"><span data-stu-id="a888b-189">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="a888b-190">若要瞭解您可以使用的命令，請在物件上看看，然後說「我可以怎麼說？」。</span><span class="sxs-lookup"><span data-stu-id="a888b-190">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="a888b-191">可能會快顯的命令清單。</span><span class="sxs-lookup"><span data-stu-id="a888b-191">A list of possible commands pops up.</span></span> <span data-ttu-id="a888b-192">您也可以使用前端指標來查看，並在您前面顯示每個按鈕的語音工具提示。</span><span class="sxs-lookup"><span data-stu-id="a888b-192">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="a888b-193">如果您想要完整的清單，只要說「顯示所有命令」即可。</span><span class="sxs-lookup"><span data-stu-id="a888b-193">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="a888b-194">聽寫</span><span class="sxs-lookup"><span data-stu-id="a888b-194">Dictation</span></span>

<span data-ttu-id="a888b-195">語音聽寫可以更有效率地在應用程式中輸入文字，而不是以 [空中](gaze-and-commit.md#composite-gestures)的方式輸入。</span><span class="sxs-lookup"><span data-stu-id="a888b-195">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="a888b-196">這可大幅加速輸入，讓使用者更不費力。</span><span class="sxs-lookup"><span data-stu-id="a888b-196">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="a888b-197">![語音聽寫會從選取麥克風按鈕開始](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="a888b-197">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="a888b-198">*語音聽寫的開頭是選取鍵盤上的麥克風按鈕*</span><span class="sxs-lookup"><span data-stu-id="a888b-198">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="a888b-199">任何時候全像全像鍵盤都處於使用中狀態時，您都可以切換到聽寫模式，而不是鍵入。</span><span class="sxs-lookup"><span data-stu-id="a888b-199">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="a888b-200">選取文字輸入方塊旁邊的麥克風，開始使用。</span><span class="sxs-lookup"><span data-stu-id="a888b-200">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="a888b-201">將語音命令新增至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a888b-201">Adding voice commands to your app</span></span>

<span data-ttu-id="a888b-202">請考慮對您所建置的任何體驗新增語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-202">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="a888b-203">語音是功能強大的方式，可方便您控制系統和應用程式。</span><span class="sxs-lookup"><span data-stu-id="a888b-203">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="a888b-204">因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-204">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="a888b-205">最佳作法</span><span class="sxs-lookup"><span data-stu-id="a888b-205">Best practices</span></span>

<span data-ttu-id="a888b-206">以下是有助於順利辨識語音的一些做法。</span><span class="sxs-lookup"><span data-stu-id="a888b-206">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="a888b-207">**使用精簡的命令** - 盡可能選擇有兩個以上音節的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a888b-207">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="a888b-208">口音不同的人在說單音節的單字時往往會使用不同的元音。</span><span class="sxs-lookup"><span data-stu-id="a888b-208">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="a888b-209">範例：「播放影片」優於「播放目前選取的影片」</span><span class="sxs-lookup"><span data-stu-id="a888b-209">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="a888b-210">**使用簡單詞彙** -範例：「顯示附注」優於「顯示牌子」</span><span class="sxs-lookup"><span data-stu-id="a888b-210">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="a888b-211">**確定命令不具破壞性** - 確定可透過語音命令來採取的動作不具破壞性，如果使用者附近有其他人不小心觸發命令，也可以輕鬆地加以復原。</span><span class="sxs-lookup"><span data-stu-id="a888b-211">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="a888b-212">**避免類似發音的命令** - 避免註冊多個聽起來非常類似的語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-212">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="a888b-213">範例：「顯示更多」和「顯示存放區」可能非常類似的發音。</span><span class="sxs-lookup"><span data-stu-id="a888b-213">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="a888b-214">**將未使用的應用程式取消註冊** - 當應用程式並非處在會讓特定語音命令生效的狀態時，請考慮將其取消註冊，以免該命令與其他命令混淆。</span><span class="sxs-lookup"><span data-stu-id="a888b-214">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="a888b-215">**使用不同口音進行測試** - 請使用不同口音的使用者測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="a888b-215">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="a888b-216">**讓語音命令保持一致** - 如果 "Go back" 會回到上一頁，請在應用程式中保持這個行為。</span><span class="sxs-lookup"><span data-stu-id="a888b-216">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="a888b-217">**避免使用系統命令** - 下列語音命令已保留給系統使用。</span><span class="sxs-lookup"><span data-stu-id="a888b-217">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="a888b-218">應用程式請勿使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-218">These should not be used by applications.</span></span>
   * <span data-ttu-id="a888b-219">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="a888b-219">"Hey Cortana"</span></span>
   * <span data-ttu-id="a888b-220">"Select"</span><span class="sxs-lookup"><span data-stu-id="a888b-220">"Select"</span></span>
   * <span data-ttu-id="a888b-221">「移至開始」</span><span class="sxs-lookup"><span data-stu-id="a888b-221">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="a888b-222">語音輸入的優點</span><span class="sxs-lookup"><span data-stu-id="a888b-222">Advantages of voice input</span></span>

<span data-ttu-id="a888b-223">語音輸入是很自然的意圖溝通方式。</span><span class="sxs-lookup"><span data-stu-id="a888b-223">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="a888b-224">語音在介面 **周遊** 中特別有用，因為它可協助使用者切換介面的多個步驟， (使用者可能會在查看網頁時說「返回」，而不需要在應用程式) 中啟動並按 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a888b-224">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="a888b-225">這小段節省時間對使用者對體驗的認知有強大的 **情緒影響** ，並讓他們增強。</span><span class="sxs-lookup"><span data-stu-id="a888b-225">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="a888b-226">當我們無法騰出雙手或是在執行 **多工** 處理時，使用語音也是很方便的輸入方法。</span><span class="sxs-lookup"><span data-stu-id="a888b-226">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="a888b-227">在鍵盤上輸入的裝置上， **語音聽寫** 可以是輸入文字的有效替代方式。</span><span class="sxs-lookup"><span data-stu-id="a888b-227">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="a888b-228">最後，在某些情況下，當注視和手勢的 **精確度範圍** 有限時，語音有助於區分使用者的意圖。</span><span class="sxs-lookup"><span data-stu-id="a888b-228">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="a888b-229">**使用語音如何讓使用者受益**</span><span class="sxs-lookup"><span data-stu-id="a888b-229">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="a888b-230">減少時間 - 語音應該會讓最終目標更有效率。</span><span class="sxs-lookup"><span data-stu-id="a888b-230">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="a888b-231">最不費力 - 語音應該會讓工作變得更為流暢且更不費力。</span><span class="sxs-lookup"><span data-stu-id="a888b-231">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="a888b-232">降低認知負荷 - 語音既直覺、易於了解且容易記住。</span><span class="sxs-lookup"><span data-stu-id="a888b-232">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="a888b-233">符合社交規範 - 語音應該會符合社會行為規範。</span><span class="sxs-lookup"><span data-stu-id="a888b-233">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="a888b-234">語音很平常 - 語音隨時可以變成慣常行為。</span><span class="sxs-lookup"><span data-stu-id="a888b-234">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="a888b-235">語音輸入的挑戰</span><span class="sxs-lookup"><span data-stu-id="a888b-235">Challenges for voice input</span></span>

<span data-ttu-id="a888b-236">雖然語音輸入很適合用於許多不同的應用程式，但它也面臨數個挑戰。</span><span class="sxs-lookup"><span data-stu-id="a888b-236">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="a888b-237">瞭解語音輸入的優點和挑戰，可讓應用程式開發人員針對使用語音輸入的方式和時機，以及為使用者建立絕佳的體驗，提供更明智的選擇。</span><span class="sxs-lookup"><span data-stu-id="a888b-237">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="a888b-238">**連續輸入控制的語音輸入** 精細控制是其中之一。</span><span class="sxs-lookup"><span data-stu-id="a888b-238">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="a888b-239">例如，使用者可能會想要在其「音樂」應用程式中變更其磁片區。</span><span class="sxs-lookup"><span data-stu-id="a888b-239">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="a888b-240">她可以單純說「更高」，但不清楚系統應該如何提高磁片區數量。</span><span class="sxs-lookup"><span data-stu-id="a888b-240">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="a888b-241">使用者可以說：「讓它變得更大」，但很難量化。</span><span class="sxs-lookup"><span data-stu-id="a888b-241">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="a888b-242">使用聲音移動或調整全像影像也很困難。</span><span class="sxs-lookup"><span data-stu-id="a888b-242">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="a888b-243">**語音輸入偵測的可靠性** 雖然語音輸入系統變得更好且更好，但有時它們可能會不正確地聆聽及解讀語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-243">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="a888b-244">重要的是，在系統正在接聽時提供意見反應給使用者，以及系統如何理解，以明確地瞭解使用者的潛在問題，以解決應用程式中的這項挑戰。</span><span class="sxs-lookup"><span data-stu-id="a888b-244">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="a888b-245">**共用空間中的語音輸入** 您與其他人共用的空格可能無法接受語音社交。</span><span class="sxs-lookup"><span data-stu-id="a888b-245">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="a888b-246">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="a888b-246">Here are a few examples:</span></span>
* <span data-ttu-id="a888b-247">使用者可能不會想要打擾他人 (例如，在安靜文件庫或共用的辦公室) </span><span class="sxs-lookup"><span data-stu-id="a888b-247">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="a888b-248">使用者可能覺得很難在公眾的對話中看到</span><span class="sxs-lookup"><span data-stu-id="a888b-248">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="a888b-249">使用者可能會覺得不舒服地聽寫個人或機密郵件 (包括密碼) 而其他人正在接聽</span><span class="sxs-lookup"><span data-stu-id="a888b-249">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="a888b-250">**唯一或未知單字的語音輸入** 當使用者聽寫可能對系統不明的字詞（例如昵稱、某些俚語單字或縮寫）時，也會發生語音輸入的問題。</span><span class="sxs-lookup"><span data-stu-id="a888b-250">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="a888b-251">**學習語音命令** 雖然最終目標是自然地與您的系統對話，但應用程式通常仍依賴特定的預先定義語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-251">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="a888b-252">與大量語音命令相關的挑戰是，如何在不多載使用者的情況下教授這些問題，以及如何協助使用者進行保留。</span><span class="sxs-lookup"><span data-stu-id="a888b-252">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="a888b-253">語音反饋狀態</span><span class="sxs-lookup"><span data-stu-id="a888b-253">Voice feedback states</span></span>

<span data-ttu-id="a888b-254">當語音正確套用時，使用者會了解 **他們能說什麼並獲得清楚的反饋** 而知道系統 **正確聽懂他們的語音**。</span><span class="sxs-lookup"><span data-stu-id="a888b-254">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="a888b-255">這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。</span><span class="sxs-lookup"><span data-stu-id="a888b-255">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="a888b-256">下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。</span><span class="sxs-lookup"><span data-stu-id="a888b-256">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="a888b-257">![1. 一般資料指標狀態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="a888b-257">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="a888b-258">**1. 一般資料指標狀態**</span><span class="sxs-lookup"><span data-stu-id="a888b-258">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a888b-259">![2. 傳達語音意見反應，然後消失](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="a888b-259">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="a888b-260">**2. 傳達語音意見反應，然後消失**</span><span class="sxs-lookup"><span data-stu-id="a888b-260">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a888b-261">![3.</span><span class="sxs-lookup"><span data-stu-id="a888b-261">![\*3.</span></span> <span data-ttu-id="a888b-262">一般資料指標狀態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="a888b-262">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="a888b-263">**3. 返回一般資料指標狀態**</span><span class="sxs-lookup"><span data-stu-id="a888b-263">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="a888b-264">針對混合實境中的「語音」，使用者最應該了解的事</span><span class="sxs-lookup"><span data-stu-id="a888b-264">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="a888b-265">在鎖定按鈕時說出 **"Select"** (您可以在任何地方使用這個命令來按一下按鈕)。</span><span class="sxs-lookup"><span data-stu-id="a888b-265">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="a888b-266">在某些應用程式中，您可以說出 **應用程式列按鈕的標籤名稱** 來採取動作。</span><span class="sxs-lookup"><span data-stu-id="a888b-266">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="a888b-267">例如，在查看應用程式的同時，使用者可以說出「Remove」命令來從該世界中移除應用程式 (這可省下必須用手按一下按鈕的時間)。</span><span class="sxs-lookup"><span data-stu-id="a888b-267">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="a888b-268">您可以說 **「嗨 Cortana」** 讓 Cortana 開始聽取命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-268">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="a888b-269">您可以向她問問題 (「嗨 Cortana，艾菲爾鐵塔有多高」)、請她開啟應用程式 (「嗨 Cortana，開啟 Netflix」)，或請她顯示 [開始] 功能表 (「嗨 Cortana，回到首頁」) 等等。</span><span class="sxs-lookup"><span data-stu-id="a888b-269">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="a888b-270">使用者會有的語音相關常見問題和疑慮</span><span class="sxs-lookup"><span data-stu-id="a888b-270">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="a888b-271">我可以說什麼？</span><span class="sxs-lookup"><span data-stu-id="a888b-271">What can I say?</span></span>
* <span data-ttu-id="a888b-272">如何知道系統沒有聽錯？</span><span class="sxs-lookup"><span data-stu-id="a888b-272">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="a888b-273">系統一直聽錯我的語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-273">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="a888b-274">我提供了語音命令，系統卻沒有反應。</span><span class="sxs-lookup"><span data-stu-id="a888b-274">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="a888b-275">我提供了語音命令，系統卻做出錯誤反應。</span><span class="sxs-lookup"><span data-stu-id="a888b-275">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="a888b-276">如何讓我的語音以特定應用程式或應用程式命令作為目標？</span><span class="sxs-lookup"><span data-stu-id="a888b-276">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="a888b-277">在 HoloLens 上的全像攝影畫面外，是否可以使用語音來命令物件？</span><span class="sxs-lookup"><span data-stu-id="a888b-277">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="a888b-278">通訊</span><span class="sxs-lookup"><span data-stu-id="a888b-278">Communication</span></span>

<span data-ttu-id="a888b-279">如果應用程式想要利用 HoloLens 提供的自訂音訊輸入處理選項，請務必瞭解您的應用程式可使用的各種 [音訊串流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="a888b-279">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="a888b-280">Windows 10 支援數種不同的串流類別和 HoloLens，可利用其中三種來啟用自訂處理，以優化專為語音提供的麥克風音訊品質、通訊，以及可用於環境音效音訊捕獲 (例如「攝影機」 ) 案例。</span><span class="sxs-lookup"><span data-stu-id="a888b-280">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="a888b-281">已針對通話品質和旁白案例自訂 AudioCategory_Communications 資料流程類別，並為用戶端提供使用者語音的 16kHz 24bit mono 音訊串流</span><span class="sxs-lookup"><span data-stu-id="a888b-281">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="a888b-282">AudioCategory_Speech 串流類別是針對 HoloLens (Windows) 語音引擎自訂，並為其提供使用者語音的 16kHz 24bit mono 串流。</span><span class="sxs-lookup"><span data-stu-id="a888b-282">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="a888b-283">如有需要，協力廠商語音引擎可以使用此類別。</span><span class="sxs-lookup"><span data-stu-id="a888b-283">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="a888b-284">AudioCategory_Other 串流類別目錄是針對環境環境音訊錄製自訂，並為用戶端提供48kHz 的24位身歷聲音訊串流。</span><span class="sxs-lookup"><span data-stu-id="a888b-284">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="a888b-285">所有的音訊處理都是硬體加速的，這表示在 HoloLens CPU 上執行相同的處理功能時，這些功能的耗電量會少很多。</span><span class="sxs-lookup"><span data-stu-id="a888b-285">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="a888b-286">避免在 CPU 上執行其他音訊輸入處理，以將系統電池壽命最大化，並充分利用內建的卸載音訊輸入處理。</span><span class="sxs-lookup"><span data-stu-id="a888b-286">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="a888b-287">語言</span><span class="sxs-lookup"><span data-stu-id="a888b-287">Languages</span></span>

<span data-ttu-id="a888b-288">HoloLens 2 [支援多種語言](https://docs.microsoft.com/hololens/hololens2-language-support)。</span><span class="sxs-lookup"><span data-stu-id="a888b-288">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="a888b-289">請記住，即使安裝了多個鍵盤或應用程式嘗試以不同的語言建立語音辨識器，語音命令一律會以系統的顯示語言執行。</span><span class="sxs-lookup"><span data-stu-id="a888b-289">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="a888b-290">疑難排解</span><span class="sxs-lookup"><span data-stu-id="a888b-290">Troubleshooting</span></span>

<span data-ttu-id="a888b-291">如果您在使用「選取」和「嗨 Cortana」時遇到任何問題，請嘗試移至更安靜的空間、關閉雜訊來源，或說出更遠。</span><span class="sxs-lookup"><span data-stu-id="a888b-291">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="a888b-292">目前，HoloLens 上的所有語音辨識都會專門針對美國英文的原生喇叭進行調整及優化。</span><span class="sxs-lookup"><span data-stu-id="a888b-292">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="a888b-293">針對 Windows Mixed Reality Developer Edition 2017 版，在初始 HMD 連線之後登出和重新登入電腦桌面之後，音訊端點管理邏輯將可正常運作 (永久) 。</span><span class="sxs-lookup"><span data-stu-id="a888b-293">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="a888b-294">在經過 WMR OOBE 之後第一次登出/進入事件之前，使用者可能會遇到各種音訊功能問題，範圍從沒有音訊到音訊切換，視系統在第一次連接 HMD 之前的設定方式而定。</span><span class="sxs-lookup"><span data-stu-id="a888b-294">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a888b-295">MRTK 中的語音輸入 (適用于 Unity 的混合現實工具組) </span><span class="sxs-lookup"><span data-stu-id="a888b-295">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a888b-296">透過 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，您可以輕鬆地對任何物件指派語音命令。</span><span class="sxs-lookup"><span data-stu-id="a888b-296">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="a888b-297">使用 MRTK 的 **語音輸入設定檔** 來定義關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a888b-297">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="a888b-298">藉由指派 **SpeechInputHandler** 腳本，您可以讓任何物件回應語音輸入設定檔中定義的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a888b-298">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="a888b-299">SpeechInputHandler 也會提供語音確認標籤，以提升使用者的信心。</span><span class="sxs-lookup"><span data-stu-id="a888b-299">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="a888b-300">MRTK-Voice 命令</span><span class="sxs-lookup"><span data-stu-id="a888b-300">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="a888b-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a888b-301">See also</span></span>
* [<span data-ttu-id="a888b-302">目光和行動</span><span class="sxs-lookup"><span data-stu-id="a888b-302">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a888b-303">本能互動</span><span class="sxs-lookup"><span data-stu-id="a888b-303">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a888b-304">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="a888b-304">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="a888b-305">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="a888b-305">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)
