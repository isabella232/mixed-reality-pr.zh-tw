---
title: 使用 Visual Studio 來部署和偵錯
description: 了解如何使用 Visual Studio 來建置、偵錯及部署 HoloLens 和 Windows Mixed Reality 的應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合實境, 偵錯, 部署
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543224"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="22977-104">使用 Visual Studio 來部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="22977-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="22977-105">無論您是使用 DirectX 或 Unity 來開發混合實境應用程式，Visual Studio 都是進行偵錯和部署的必備工具。</span><span class="sxs-lookup"><span data-stu-id="22977-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="22977-106">在本節中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="22977-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="22977-107">透過 Visual Studio 將應用程式部署到 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置。</span><span class="sxs-lookup"><span data-stu-id="22977-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="22977-108">使用內建至 Visual Studio 的 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="22977-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="22977-109">針對混合實境應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="22977-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22977-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="22977-110">Prerequisites</span></span>

1. <span data-ttu-id="22977-111">如需安裝指示，請參閱[安裝工具](../../develop/install-the-tools.md#installation-checklist)。</span><span class="sxs-lookup"><span data-stu-id="22977-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="22977-112">在 Visual Studio 中建立新的通用 Windows app 專案。</span><span class="sxs-lookup"><span data-stu-id="22977-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="22977-113">對於 HoloLens (第 1 代)，使用 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="22977-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="22977-114">對於 HoloLens 2，使用 Visual Studio 2019 16.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="22977-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="22977-115">支援 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="22977-115">C# and C++ are supported.</span></span> <span data-ttu-id="22977-116">(或者遵循指示，[在 Unity 中建立應用程式](../../develop/unity/tutorials/holograms-100.md)。)</span><span class="sxs-lookup"><span data-stu-id="22977-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="22977-117">啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="22977-117">Enabling Developer Mode</span></span>

<span data-ttu-id="22977-118">從在您的裝置上啟用 **開發人員模式** 開始，讓 Visual Studio 可以與它連線。</span><span class="sxs-lookup"><span data-stu-id="22977-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="22977-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="22977-119">HoloLens</span></span>

1. <span data-ttu-id="22977-120">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="22977-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="22977-121">使用[開始手勢](../../design/system-gesture.md)來啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="22977-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="22977-122">選取 [設定]  磚，在您的環境中啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="22977-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="22977-123">選取 [更新]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="22977-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="22977-124">選取 [適用於開發人員]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="22977-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="22977-125">啟用 [ **使用開發人員功能** ]，將應用程式從 Visual Studio 部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="22977-125">Enable **Use developer features** to deploy apps from Visual Studio to your HoloLens.</span></span> <span data-ttu-id="22977-126">如果您的裝置正在執行 Windows 全像21H1 版或更新版本，也可以啟用 **裝置探索**。</span><span class="sxs-lookup"><span data-stu-id="22977-126">If your device is running Windows Holographic version 21H1 or newer, also enable **Device discovery**.</span></span>
7. <span data-ttu-id="22977-127">選擇性：向下捲動而且啟用 [裝置入口網站]，可讓您從網頁瀏覽器連線到您 HoloLens 上的 [Windows 裝置入口網站](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="22977-127">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="22977-128">Windows PC</span><span class="sxs-lookup"><span data-stu-id="22977-128">Windows PC</span></span>

<span data-ttu-id="22977-129">如果您使用的是連線到電腦的 Windows Mixed Reality 頭戴式裝置，就必須在電腦上啟用 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="22977-129">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="22977-130">移至 [設定] </span><span class="sxs-lookup"><span data-stu-id="22977-130">Go to **Settings**</span></span>
2. <span data-ttu-id="22977-131">選取 [更新與安全性] </span><span class="sxs-lookup"><span data-stu-id="22977-131">Select **Update and Security**</span></span>
3. <span data-ttu-id="22977-132">選取 [適用於開發人員] </span><span class="sxs-lookup"><span data-stu-id="22977-132">Select **For developers**</span></span>
4. <span data-ttu-id="22977-133">啟用 [開發人員模式]，閱讀您所選設定的免責聲明，然後選取 [是] 來接受變更。</span><span class="sxs-lookup"><span data-stu-id="22977-133">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="22977-134">透過 Wi-Fi 部署 HoloLens 應用程式</span><span class="sxs-lookup"><span data-stu-id="22977-134">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="22977-135">使用下列屬性來設定您的 Visual Studio 專案：</span><span class="sxs-lookup"><span data-stu-id="22977-135">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="22977-136">選取您的應用程式編譯選項</span><span class="sxs-lookup"><span data-stu-id="22977-136">Select your apps compilation options</span></span>
    * <span data-ttu-id="22977-137">針對 Unity 專案，選擇 [**發行**] 或 [**主要**]</span><span class="sxs-lookup"><span data-stu-id="22977-137">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="22977-138">針對所有其他專案，選擇 [**發行**]</span><span class="sxs-lookup"><span data-stu-id="22977-138">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="22977-139">您可以在 [匯出和建立 Visual Studio 方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中，找到每個編譯選項的完整定義。</span><span class="sxs-lookup"><span data-stu-id="22977-139">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="22977-140">根據您的裝置選取組建設定</span><span class="sxs-lookup"><span data-stu-id="22977-140">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="22977-141">在 [部署目標] 下拉式功能表中，選取 [遠端電腦] </span><span class="sxs-lookup"><span data-stu-id="22977-141">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting_arm64.png)

<span data-ttu-id="22977-143">接下來，您需要設定遠端連線。</span><span class="sxs-lookup"><span data-stu-id="22977-143">Next, you need to set your remote connection.</span></span> <span data-ttu-id="22977-144">針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。</span><span class="sxs-lookup"><span data-stu-id="22977-144">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="22977-145">如果您是在 c # 專案中工作，對話方塊應該會自動出現。</span><span class="sxs-lookup"><span data-stu-id="22977-145">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="22977-146">如果 [遠端連線] 對話方塊未出現在 c # 專案中，您可以從 [ **屬性] > Debug**] 手動開啟。</span><span class="sxs-lookup"><span data-stu-id="22977-146">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="22977-147">在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="22977-147">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="22977-148">您可以在 HoloLens 下的 [**設定] > Network & Internet > Advanced Options** 中找到 IP 位址</span><span class="sxs-lookup"><span data-stu-id="22977-148">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="22977-149">我們一律建議以手動方式輸入您的 IP 位址，而不是根據自動偵測到的功能。</span><span class="sxs-lookup"><span data-stu-id="22977-149">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="22977-150">將 **驗證模式** 設定為 **通用 (未加密的通訊協定)**</span><span class="sxs-lookup"><span data-stu-id="22977-150">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)

3. <span data-ttu-id="22977-152">根據您的需求來建立、部署及偵測您的應用程式</span><span class="sxs-lookup"><span data-stu-id="22977-152">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22977-153">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="22977-153">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22977-154">選取 **組建 > 部署** 以在不進行調試的情況下進行組建和部署</span><span class="sxs-lookup"><span data-stu-id="22977-154">Select **Build > Deploy** to build and deploy without debugging</span></span>

![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)

4. <span data-ttu-id="22977-156">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="22977-156">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="22977-157">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="22977-157">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="22977-158">透過 USB 部署 HoloLens 應用程式</span><span class="sxs-lookup"><span data-stu-id="22977-158">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="22977-159">選取您的應用程式編譯選項</span><span class="sxs-lookup"><span data-stu-id="22977-159">Select your apps compilation options</span></span>
    * <span data-ttu-id="22977-160">針對 Unity 專案，選擇 [**發行**] 或 [**主要**]</span><span class="sxs-lookup"><span data-stu-id="22977-160">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="22977-161">針對所有其他專案，選擇 [**發行**]</span><span class="sxs-lookup"><span data-stu-id="22977-161">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="22977-162">您可以在 [匯出和建立 Visual Studio 方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中，找到每個編譯選項的完整定義。</span><span class="sxs-lookup"><span data-stu-id="22977-162">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="22977-163">根據您的裝置選取組建設定</span><span class="sxs-lookup"><span data-stu-id="22977-163">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="22977-164">在 [部署目標] 下拉式功能表中，選取 [裝置] </span><span class="sxs-lookup"><span data-stu-id="22977-164">Select **Device** in the deployment target drop-down menu</span></span>

![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="22977-166">根據您的需求來建立、部署及偵測您的應用程式</span><span class="sxs-lookup"><span data-stu-id="22977-166">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22977-167">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="22977-167">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22977-168">選取 **組建 > 部署** 以在不進行調試的情況下進行組建和部署</span><span class="sxs-lookup"><span data-stu-id="22977-168">Select **Build > Deploy** to build and deploy without debugging</span></span>

![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="22977-170">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="22977-170">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="22977-171">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="22977-171">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="22977-172">如果您在透過 USB 部署應用程式時看到相當長的延遲時間，建議您在上一節中使用 [遠端電腦的指示](#deploying-a-hololens-app-over-wi-fi) 。</span><span class="sxs-lookup"><span data-stu-id="22977-172">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="22977-173">將應用程式部署到 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="22977-173">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="22977-174">請確定您已 **[安裝 HoloLens 2 或 HoloLens (第1代) 模擬器](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="22977-174">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="22977-175">根據您的裝置選取組建設定和模擬器</span><span class="sxs-lookup"><span data-stu-id="22977-175">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="22977-176">根據您的需求來建立、部署及偵測您的應用程式</span><span class="sxs-lookup"><span data-stu-id="22977-176">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22977-177">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="22977-177">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22977-178">選取 **組建 > 部署** 至不 debuggingg 的組建和部署</span><span class="sxs-lookup"><span data-stu-id="22977-178">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="22977-180">將 VR 應用程式部署到您的本機電腦</span><span class="sxs-lookup"><span data-stu-id="22977-180">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="22977-181">若要使用可連線到您的電腦或[混合實境模擬器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式頭戴裝置：</span><span class="sxs-lookup"><span data-stu-id="22977-181">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="22977-182">為您的應用程式選取 **x86** 或 **x64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="22977-182">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="22977-183">在 [部署目標] 下拉式功能表中，選取 [本機電腦] </span><span class="sxs-lookup"><span data-stu-id="22977-183">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="22977-184">根據您的需求來建立、部署及偵測您的應用程式</span><span class="sxs-lookup"><span data-stu-id="22977-184">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22977-185">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="22977-185">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22977-186">選取 **組建 > 部署** 以在不進行調試的情況下進行組建和部署</span><span class="sxs-lookup"><span data-stu-id="22977-186">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="22977-187">配對您的裝置</span><span class="sxs-lookup"><span data-stu-id="22977-187">Pairing your device</span></span>

<span data-ttu-id="22977-188">當您第一次從 Visual Studio 將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="22977-188">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="22977-189">在 HoloLens 上，移至 [更新 > 適用於開發人員]，並點選 [配對]，藉由啟動 [設定] 應用程式來產生 PIN。</span><span class="sxs-lookup"><span data-stu-id="22977-189">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="22977-190">當您的 HoloLens 上顯示 PIN 時，請將其輸入 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="22977-190">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="22977-191">配對完成之後，點選 HoloLens 上的 [完成]  以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="22977-191">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="22977-192">這部電腦現在已與 HoloLens 配對，您可以自動部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="22977-192">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="22977-193">針對用來將應用程式部署至 HoloLens 的每部電腦重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="22977-193">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="22977-194">若要解除配對您的 HoloLens 與所有配對的電腦：</span><span class="sxs-lookup"><span data-stu-id="22977-194">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="22977-195">啟動 [設定] 應用程式，移至 [更新] > [適用於開發人員]，然後點選 [清除]。</span><span class="sxs-lookup"><span data-stu-id="22977-195">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="22977-196">HoloLens (第 1 代) 的圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="22977-196">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="22977-197">撰寫和最佳化全像攝影應用程式時，Visual Studio 圖形診斷工具很有幫助。</span><span class="sxs-lookup"><span data-stu-id="22977-197">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="22977-198">如需完整詳細資料，請參閱 [MSDN 上的 Visual Studio 圖形診斷](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)。</span><span class="sxs-lookup"><span data-stu-id="22977-198">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="22977-199">**啟動圖形偵錯工具**</span><span class="sxs-lookup"><span data-stu-id="22977-199">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="22977-200">遵循上述指示，以裝置或模擬器為目標</span><span class="sxs-lookup"><span data-stu-id="22977-200">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="22977-201">移至 [偵錯 > 圖形 > 開始診斷] </span><span class="sxs-lookup"><span data-stu-id="22977-201">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="22977-202">第一次使用 HoloLens 開始診斷時，您可能會遇到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="22977-202">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="22977-203">將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="22977-203">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="22977-204">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="22977-204">Profiling</span></span>

<span data-ttu-id="22977-205">Visual Studio 程式碼剖析工具可讓您分析應用程式的效能和資源使用。</span><span class="sxs-lookup"><span data-stu-id="22977-205">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="22977-206">包括將 CPU、記憶體、圖形和網路使用最佳化的工具。</span><span class="sxs-lookup"><span data-stu-id="22977-206">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="22977-207">如需完整詳細資料，請參閱 [MSDN 上的執行診斷工具而不進行偵錯](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)。</span><span class="sxs-lookup"><span data-stu-id="22977-207">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="22977-208">**使用 HoloLens 啟動程式碼剖析工具**</span><span class="sxs-lookup"><span data-stu-id="22977-208">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="22977-209">遵循上述指示，以裝置或模擬器為目標</span><span class="sxs-lookup"><span data-stu-id="22977-209">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="22977-210">移至 [偵錯 > 啟動診斷工具但不偵錯...]  。</span><span class="sxs-lookup"><span data-stu-id="22977-210">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="22977-211">選取您想要使用的工具</span><span class="sxs-lookup"><span data-stu-id="22977-211">Select the tools you want to use</span></span>
4. <span data-ttu-id="22977-212">選取 [啟動]</span><span class="sxs-lookup"><span data-stu-id="22977-212">Select **Start**</span></span>
5. <span data-ttu-id="22977-213">第一次使用 HoloLens 開始診斷但不進行偵錯時，您可能會遇到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="22977-213">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="22977-214">將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="22977-214">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="22977-215">針對已安裝或執行中的應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="22977-215">Debugging an installed or running app</span></span>

<span data-ttu-id="22977-216">您可以使用 Visual Studio 針對已安裝但未從 Visual Studio 專案部署的通用 Windows 應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="22977-216">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="22977-217">如果您想要對已安裝的應用程式套件進行偵錯，或對已經在執行中的應用程式進行偵錯，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="22977-217">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="22977-218">移至 [偵錯 -> 其他偵錯目標 -> 針對已安裝的應用程式套件進行偵錯] </span><span class="sxs-lookup"><span data-stu-id="22977-218">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="22977-219">針對 HoloLens 選取 [遠端電腦]  目標，或針對沉浸式頭戴裝置選取 [本機電腦]  。</span><span class="sxs-lookup"><span data-stu-id="22977-219">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="22977-220">輸入您裝置的 **IP 位址**</span><span class="sxs-lookup"><span data-stu-id="22977-220">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="22977-221">選擇 [通用]  驗證模式</span><span class="sxs-lookup"><span data-stu-id="22977-221">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="22977-222">此視窗會顯示執行中和非使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="22977-222">The window shows both running and inactive apps.</span></span> <span data-ttu-id="22977-223">挑選您想要進行偵錯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="22977-223">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="22977-224">選擇要進行偵錯的程式碼類型 (受控、原生、混合)</span><span class="sxs-lookup"><span data-stu-id="22977-224">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="22977-225">選取 [連結] 或 [啟動]</span><span class="sxs-lookup"><span data-stu-id="22977-225">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="22977-226">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="22977-226">Next Development Checkpoint</span></span>

<span data-ttu-id="22977-227">依循我們配置的 Unity 開發檢查點旅程，此時您會進入部署階段。</span><span class="sxs-lookup"><span data-stu-id="22977-227">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="22977-228">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="22977-228">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22977-229">部署至 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="22977-229">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="22977-230">或者，直接跳到新增進階服務的主題：</span><span class="sxs-lookup"><span data-stu-id="22977-230">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22977-231">進階服務</span><span class="sxs-lookup"><span data-stu-id="22977-231">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="22977-232">您可以隨時回到 [Unity 開發檢查點](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。</span><span class="sxs-lookup"><span data-stu-id="22977-232">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="22977-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22977-233">See also</span></span>
* [<span data-ttu-id="22977-234">安裝工具</span><span class="sxs-lookup"><span data-stu-id="22977-234">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="22977-235">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="22977-235">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="22977-236">部署和偵錯通用 Windows 平台 (UWP) app</span><span class="sxs-lookup"><span data-stu-id="22977-236">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="22977-237">啟用您的裝置以進行開發</span><span class="sxs-lookup"><span data-stu-id="22977-237">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)
