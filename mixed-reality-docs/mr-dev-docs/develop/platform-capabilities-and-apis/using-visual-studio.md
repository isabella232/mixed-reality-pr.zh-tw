---
title: 使用 Visual Studio 來部署和偵錯
description: 了解如何使用 Visual Studio 來建置、偵錯及部署 HoloLens 和 Windows Mixed Reality 的應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合實境, 偵錯, 部署
ms.openlocfilehash: 5ac3d6bbc93adda68a23a8682b5e23ff5c0adbbd
ms.sourcegitcommit: 87274e80837ba0420ea5767b6ce3eacd1b5f1fec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100633"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="24fbb-104">使用 Visual Studio 來部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="24fbb-105">無論您是使用 DirectX 或 Unity 來開發混合實境應用程式，Visual Studio 都是進行偵錯和部署的必備工具。</span><span class="sxs-lookup"><span data-stu-id="24fbb-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="24fbb-106">在本節中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="24fbb-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="24fbb-107">透過 Visual Studio 將應用程式部署到 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置。</span><span class="sxs-lookup"><span data-stu-id="24fbb-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="24fbb-108">使用內建至 Visual Studio 的 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="24fbb-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="24fbb-109">針對混合實境應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="24fbb-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24fbb-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="24fbb-110">Prerequisites</span></span>

1. <span data-ttu-id="24fbb-111">如需安裝指示，請參閱[安裝工具](../../develop/install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="24fbb-111">See [Install the Tools](../../develop/install-the-tools.md) for installation instructions.</span></span>
2. <span data-ttu-id="24fbb-112">在 Visual Studio 中建立新的通用 Windows app 專案。</span><span class="sxs-lookup"><span data-stu-id="24fbb-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="24fbb-113">對於 HoloLens (第 1 代)，使用 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="24fbb-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="24fbb-114">對於 HoloLens 2，使用 Visual Studio 2019 16.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="24fbb-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="24fbb-115">支援 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="24fbb-115">C# and C++ are supported.</span></span> <span data-ttu-id="24fbb-116">(或者遵循指示，[在 Unity 中建立應用程式](../../develop/unity/tutorials/holograms-100.md)。)</span><span class="sxs-lookup"><span data-stu-id="24fbb-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="24fbb-117">啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="24fbb-117">Enabling Developer Mode</span></span>

<span data-ttu-id="24fbb-118">從在您的裝置上啟用 **開發人員模式** 開始，讓 Visual Studio 可以與它連線。</span><span class="sxs-lookup"><span data-stu-id="24fbb-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="24fbb-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="24fbb-119">HoloLens</span></span>

1. <span data-ttu-id="24fbb-120">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="24fbb-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="24fbb-121">使用[開始手勢](../../design/system-gesture.md)來啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="24fbb-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="24fbb-122">選取 [設定]  磚，在您的環境中啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="24fbb-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="24fbb-123">選取 [更新]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="24fbb-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="24fbb-124">選取 [適用於開發人員]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="24fbb-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="24fbb-125">啟用 [開發人員模式] 以將應用程式從 Visual Studio 部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="24fbb-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="24fbb-126">選擇性：向下捲動而且啟用 [裝置入口網站]，可讓您從網頁瀏覽器連線到您 HoloLens 上的 [Windows 裝置入口網站](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="24fbb-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="24fbb-127">Windows PC</span><span class="sxs-lookup"><span data-stu-id="24fbb-127">Windows PC</span></span>

<span data-ttu-id="24fbb-128">如果您使用的是連線到電腦的 Windows Mixed Reality 頭戴式裝置，就必須在電腦上啟用 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="24fbb-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="24fbb-129">移至 [設定] </span><span class="sxs-lookup"><span data-stu-id="24fbb-129">Go to **Settings**</span></span>
2. <span data-ttu-id="24fbb-130">選取 [更新與安全性] </span><span class="sxs-lookup"><span data-stu-id="24fbb-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="24fbb-131">選取 [適用於開發人員] </span><span class="sxs-lookup"><span data-stu-id="24fbb-131">Select **For developers**</span></span>
4. <span data-ttu-id="24fbb-132">啟用 [開發人員模式]，閱讀您所選設定的免責聲明，然後選取 [是] 來接受變更。</span><span class="sxs-lookup"><span data-stu-id="24fbb-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a><span data-ttu-id="24fbb-133">透過 Wi-Fi 部署應用程式 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="24fbb-133">Deploying an app over Wi-Fi - HoloLens 2</span></span>

<span data-ttu-id="24fbb-134">使用下列屬性來設定您的 Visual Studio 專案：</span><span class="sxs-lookup"><span data-stu-id="24fbb-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="24fbb-135">選取 [應用程式編譯的 **發行** 或 **主要** ] 選項</span><span class="sxs-lookup"><span data-stu-id="24fbb-135">Select either **Release** or **Master** for the apps compilation option</span></span>
2. <span data-ttu-id="24fbb-136">選取 **ARM** 或 **ARM64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="24fbb-136">Select an **ARM** or **ARM64** build configuration</span></span></br>
<span data-ttu-id="24fbb-137">![Visual Studio 中的 ARM64 組建設定](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-137">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
3. <span data-ttu-id="24fbb-138">在 [部署目標] 下拉式功能表中，選取 [遠端電腦] </span><span class="sxs-lookup"><span data-stu-id="24fbb-138">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="24fbb-139">![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-139">![Remote machine deployment target in Visual Studio](images/remotemachinesetting_arm64.png)</span></span></br>

<span data-ttu-id="24fbb-140">接下來，您需要設定遠端連線。</span><span class="sxs-lookup"><span data-stu-id="24fbb-140">Next, you need to set your remote connection.</span></span> <span data-ttu-id="24fbb-141">針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。</span><span class="sxs-lookup"><span data-stu-id="24fbb-141">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="24fbb-142">如果您是在 c # 專案中工作，對話方塊應該會自動出現。</span><span class="sxs-lookup"><span data-stu-id="24fbb-142">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="24fbb-143">如果 [遠端連線] 對話方塊未出現在 c # 專案中，您可以從 [ **屬性] > Debug**] 手動開啟。</span><span class="sxs-lookup"><span data-stu-id="24fbb-143">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="24fbb-144">在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="24fbb-144">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="24fbb-145">您可以在 HoloLens 下的 [ **設定] > Network & Internet > Advanced 選項** 中找到 IP 位址，也可以詢問 Cortana 「我的 IP 位址是什麼？」</span><span class="sxs-lookup"><span data-stu-id="24fbb-145">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
2. <span data-ttu-id="24fbb-146">將 **驗證模式** 設定為 **通用 (未加密的通訊協定)**</span><span class="sxs-lookup"><span data-stu-id="24fbb-146">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="24fbb-147">![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-147">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
<span data-ttu-id="24fbb-148">3選取 **Debug > 開始調試** 程式，以部署您的應用程式並開始進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="24fbb-148">3 Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="24fbb-149">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-149">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="24fbb-150">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="24fbb-150">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="24fbb-151">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="24fbb-151">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a><span data-ttu-id="24fbb-152">透過 Wi-Fi 部署應用程式 - HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="24fbb-152">Deploying an app over Wi-Fi - HoloLens (1st gen)</span></span>

<span data-ttu-id="24fbb-153">使用下列屬性來設定您的 Visual Studio 專案：</span><span class="sxs-lookup"><span data-stu-id="24fbb-153">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="24fbb-154">選取 [應用程式編譯的 **發行** 或 **主要** ] 選項</span><span class="sxs-lookup"><span data-stu-id="24fbb-154">Select either **Release** or **Master** for the apps compilation option</span></span>
2. <span data-ttu-id="24fbb-155">為您的應用程式選取 **x86** 組建設定</span><span class="sxs-lookup"><span data-stu-id="24fbb-155">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="24fbb-156">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-156">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="24fbb-157">在 [部署目標] 下拉式功能表中，選取 [遠端電腦] </span><span class="sxs-lookup"><span data-stu-id="24fbb-157">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="24fbb-158">![Visual Studio 應用程式中的遠端電腦部署目標](images/remotemachinesetting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-158">![Remote machine deployment target in Visual Studio application](images/remotemachinesetting.png)</span></span></br>

<span data-ttu-id="24fbb-159">接下來，您需要設定遠端連線。</span><span class="sxs-lookup"><span data-stu-id="24fbb-159">Next, you need to set your remote connection.</span></span> <span data-ttu-id="24fbb-160">針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。</span><span class="sxs-lookup"><span data-stu-id="24fbb-160">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="24fbb-161">如果您是在 c # 專案中工作，對話方塊應該會自動出現。</span><span class="sxs-lookup"><span data-stu-id="24fbb-161">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="24fbb-162">如果 [遠端連線] 對話方塊未出現在 c # 專案中，您可以從 [ **屬性] > Debug**] 手動開啟。</span><span class="sxs-lookup"><span data-stu-id="24fbb-162">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="24fbb-163">在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="24fbb-163">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="24fbb-164">您可以在 HoloLens 下的 [ **設定] > Network & Internet > Advanced 選項** 中找到 IP 位址，也可以詢問 Cortana 「我的 IP 位址是什麼？」</span><span class="sxs-lookup"><span data-stu-id="24fbb-164">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
2. <span data-ttu-id="24fbb-165">將驗證模式設定為 [通用 (未加密的通訊協定)] </span><span class="sxs-lookup"><span data-stu-id="24fbb-165">Set Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="24fbb-166">![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-166">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
3. <span data-ttu-id="24fbb-167">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-167">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="24fbb-168">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-168">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="24fbb-169">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="24fbb-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="24fbb-170">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="24fbb-170">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-usb---hololens-2"></a><span data-ttu-id="24fbb-171">透過 USB 部署應用程式 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="24fbb-171">Deploying an app over USB - HoloLens 2</span></span>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="24fbb-172">選取 [應用程式編譯的 **發行** 或 **主要** ] 選項</span><span class="sxs-lookup"><span data-stu-id="24fbb-172">Select either **Release** or **Master** for the apps compilation option</span></span>
2. <span data-ttu-id="24fbb-173">為您的應用程式選取 **ARM** 或 **ARM64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="24fbb-173">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="24fbb-174">![Visual Studio 中的 ARM64 組建設定](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-174">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
3. <span data-ttu-id="24fbb-175">在 [部署目標] 下拉式功能表中，選取 [裝置] </span><span class="sxs-lookup"><span data-stu-id="24fbb-175">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="24fbb-176">![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-176">![Device deployment in Visual Studio](images/buildsettingsusbdeploy_arm64.png)</span></span></br>
4. <span data-ttu-id="24fbb-177">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-177">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="24fbb-178">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-178">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="24fbb-179">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="24fbb-179">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="24fbb-180">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="24fbb-180">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="24fbb-181">如果您在透過 USB 部署應用程式時看到相當長的延遲時間，建議您在上一節中使用 [遠端電腦的指示](#deploying-an-app-over-wi-fi---hololens-2) 。</span><span class="sxs-lookup"><span data-stu-id="24fbb-181">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-an-app-over-wi-fi---hololens-2) in the previous section.</span></span>

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a><span data-ttu-id="24fbb-182">將應用程式部署到您的本機電腦 - 沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="24fbb-182">Deploying an app to your Local PC - immersive headset</span></span>

<span data-ttu-id="24fbb-183">若要使用可連線到您的電腦或[混合實境模擬器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式頭戴裝置：</span><span class="sxs-lookup"><span data-stu-id="24fbb-183">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="24fbb-184">為您的應用程式選取 **x86** 或 **x64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="24fbb-184">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="24fbb-185">在 [部署目標] 下拉式功能表中，選取 [本機電腦] </span><span class="sxs-lookup"><span data-stu-id="24fbb-185">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="24fbb-186">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-186">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a><span data-ttu-id="24fbb-187">透過 USB 部署應用程式 - HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="24fbb-187">Deploying an app over USB - HoloLens (1st gen)</span></span>

1. <span data-ttu-id="24fbb-188">選取 [應用程式編譯的 **發行** 或 **主要** ] 選項</span><span class="sxs-lookup"><span data-stu-id="24fbb-188">Select either **Release** or **Master** for the apps compilation option</span></span>
2. <span data-ttu-id="24fbb-189">為您的應用程式選取 **x86** 組建設定</span><span class="sxs-lookup"><span data-stu-id="24fbb-189">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="24fbb-190">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-190">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="24fbb-191">在 [部署目標] 下拉式功能表中，選取 [裝置] </span><span class="sxs-lookup"><span data-stu-id="24fbb-191">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="24fbb-192">![Visual Studio 應用程式中的裝置部署](images/buildsettingsusbdeploy.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-192">![Device deployment in Visual Studio application](images/buildsettingsusbdeploy.png)</span></span></br>
4. <span data-ttu-id="24fbb-193">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-193">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="24fbb-194">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-194">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="24fbb-195">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="24fbb-195">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="24fbb-196">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="24fbb-196">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="24fbb-197">如果您在透過 USB 部署應用程式時看到相當長的延遲時間，建議您在上一節中使用 [遠端電腦的指示](#deploying-an-app-over-wi-fi---hololens-1st-gen) 。</span><span class="sxs-lookup"><span data-stu-id="24fbb-197">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-an-app-over-wi-fi---hololens-1st-gen) in the previous section.</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="24fbb-198">配對您的裝置</span><span class="sxs-lookup"><span data-stu-id="24fbb-198">Pairing your device</span></span>

<span data-ttu-id="24fbb-199">當您第一次從 Visual Studio 將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="24fbb-199">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="24fbb-200">在 HoloLens 上，移至 [更新 > 適用於開發人員]，並點選 [配對]，藉由啟動 [設定] 應用程式來產生 PIN。</span><span class="sxs-lookup"><span data-stu-id="24fbb-200">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="24fbb-201">當您的 HoloLens 上顯示 PIN 時，請將其輸入 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="24fbb-201">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="24fbb-202">配對完成之後，點選 HoloLens 上的 [完成]  以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="24fbb-202">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="24fbb-203">這部電腦現在已與 HoloLens 配對，您可以自動部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="24fbb-203">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="24fbb-204">針對用來將應用程式部署至 HoloLens 的每部電腦重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="24fbb-204">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="24fbb-205">若要解除配對您的 HoloLens 與所有配對的電腦：</span><span class="sxs-lookup"><span data-stu-id="24fbb-205">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="24fbb-206">啟動 [設定] 應用程式，移至 [更新] > [適用於開發人員]，然後點選 [清除]。</span><span class="sxs-lookup"><span data-stu-id="24fbb-206">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a><span data-ttu-id="24fbb-207">將應用程式部署至 HoloLens (第 1 代) 模擬器</span><span class="sxs-lookup"><span data-stu-id="24fbb-207">Deploying an app to the HoloLens (1st gen) Emulator</span></span>

1. <span data-ttu-id="24fbb-208">請確定您已 **[安裝 HoloLens 模擬器](../install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="24fbb-208">Make sure you've **[installed the HoloLens Emulator](../install-the-tools.md)**.</span></span>
2. <span data-ttu-id="24fbb-209">為您的應用程式選取 **x86** 組建設定。</span><span class="sxs-lookup"><span data-stu-id="24fbb-209">Select an **x86** build configuration for your app.</span></span></br>
<span data-ttu-id="24fbb-210">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-210">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="24fbb-211">在 [部署目標] 下拉式功能表中，選取 [HoloLens 模擬器] </span><span class="sxs-lookup"><span data-stu-id="24fbb-211">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="24fbb-212">![Visual Studio 中的模擬器目標](images/deployemulator.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-212">![Emulator target in Visual Studio](images/deployemulator.png)</span></span></br>
4. <span data-ttu-id="24fbb-213">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-213">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="24fbb-214">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-214">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a><span data-ttu-id="24fbb-215">將應用程式部署至 HoloLens 2 模擬器</span><span class="sxs-lookup"><span data-stu-id="24fbb-215">Deploying an app to the HoloLens 2 Emulator</span></span>

1. <span data-ttu-id="24fbb-216">請確定您已 **[安裝 HoloLens 模擬器](../install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="24fbb-216">Make sure you've **[installed the HoloLens Emulator](../install-the-tools.md)**.</span></span>
2. <span data-ttu-id="24fbb-217">為您的應用程式選取 **x86** 或 **x64** 組建設定。</span><span class="sxs-lookup"><span data-stu-id="24fbb-217">Select an **x86** or **x64** build configuration for your app.</span></span></br>
<span data-ttu-id="24fbb-218">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-218">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="24fbb-219">在 [部署目標] 下拉式功能表中，選取 [HoloLens 2 模擬器] </span><span class="sxs-lookup"><span data-stu-id="24fbb-219">Select **HoloLens 2 Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="24fbb-220">![Visual Studio 應用程式中的模擬器目標](images/deployemulator2.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-220">![Emulator target in Visual Studio application](images/deployemulator2.png)</span></span></br>
4. <span data-ttu-id="24fbb-221">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-221">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="24fbb-222">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="24fbb-222">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="24fbb-223">HoloLens (第 1 代) 的圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="24fbb-223">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="24fbb-224">撰寫和最佳化全像攝影應用程式時，Visual Studio 圖形診斷工具很有幫助。</span><span class="sxs-lookup"><span data-stu-id="24fbb-224">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="24fbb-225">如需完整詳細資料，請參閱 [MSDN 上的 Visual Studio 圖形診斷](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)。</span><span class="sxs-lookup"><span data-stu-id="24fbb-225">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="24fbb-226">**啟動圖形偵錯工具**</span><span class="sxs-lookup"><span data-stu-id="24fbb-226">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="24fbb-227">遵循上述指示，以裝置或模擬器為目標</span><span class="sxs-lookup"><span data-stu-id="24fbb-227">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="24fbb-228">移至 [偵錯 > 圖形 > 開始診斷] </span><span class="sxs-lookup"><span data-stu-id="24fbb-228">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="24fbb-229">第一次使用 HoloLens 開始診斷時，您可能會遇到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="24fbb-229">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="24fbb-230">將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="24fbb-230">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="24fbb-231">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="24fbb-231">Profiling</span></span>

<span data-ttu-id="24fbb-232">Visual Studio 程式碼剖析工具可讓您分析應用程式的效能和資源使用。</span><span class="sxs-lookup"><span data-stu-id="24fbb-232">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="24fbb-233">包括將 CPU、記憶體、圖形和網路使用最佳化的工具。</span><span class="sxs-lookup"><span data-stu-id="24fbb-233">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="24fbb-234">如需完整詳細資料，請參閱 [MSDN 上的執行診斷工具而不進行偵錯](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)。</span><span class="sxs-lookup"><span data-stu-id="24fbb-234">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="24fbb-235">**使用 HoloLens 啟動程式碼剖析工具**</span><span class="sxs-lookup"><span data-stu-id="24fbb-235">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="24fbb-236">遵循上述指示，以裝置或模擬器為目標</span><span class="sxs-lookup"><span data-stu-id="24fbb-236">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="24fbb-237">移至 [偵錯 > 啟動診斷工具但不偵錯...]  。</span><span class="sxs-lookup"><span data-stu-id="24fbb-237">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="24fbb-238">選取您想要使用的工具</span><span class="sxs-lookup"><span data-stu-id="24fbb-238">Select the tools you want to use</span></span>
4. <span data-ttu-id="24fbb-239">選取 [啟動]</span><span class="sxs-lookup"><span data-stu-id="24fbb-239">Select **Start**</span></span>
5. <span data-ttu-id="24fbb-240">第一次使用 HoloLens 開始診斷但不進行偵錯時，您可能會遇到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="24fbb-240">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="24fbb-241">將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="24fbb-241">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="24fbb-242">針對已安裝或執行中的應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="24fbb-242">Debugging an installed or running app</span></span>

<span data-ttu-id="24fbb-243">您可以使用 Visual Studio 針對已安裝但未從 Visual Studio 專案部署的通用 Windows 應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="24fbb-243">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="24fbb-244">如果您想要對已安裝的應用程式套件進行偵錯，或對已經在執行中的應用程式進行偵錯，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="24fbb-244">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="24fbb-245">移至 [偵錯 -> 其他偵錯目標 -> 針對已安裝的應用程式套件進行偵錯] </span><span class="sxs-lookup"><span data-stu-id="24fbb-245">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="24fbb-246">針對 HoloLens 選取 [遠端電腦]  目標，或針對沉浸式頭戴裝置選取 [本機電腦]  。</span><span class="sxs-lookup"><span data-stu-id="24fbb-246">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="24fbb-247">輸入您裝置的 **IP 位址**</span><span class="sxs-lookup"><span data-stu-id="24fbb-247">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="24fbb-248">選擇 [通用]  驗證模式</span><span class="sxs-lookup"><span data-stu-id="24fbb-248">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="24fbb-249">此視窗會顯示執行中和非使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="24fbb-249">The window shows both running and inactive apps.</span></span> <span data-ttu-id="24fbb-250">挑選您想要進行偵錯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="24fbb-250">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="24fbb-251">選擇要進行偵錯的程式碼類型 (受控、原生、混合)</span><span class="sxs-lookup"><span data-stu-id="24fbb-251">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="24fbb-252">選取 [連結] 或 [啟動]</span><span class="sxs-lookup"><span data-stu-id="24fbb-252">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="24fbb-253">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="24fbb-253">Next Development Checkpoint</span></span>

<span data-ttu-id="24fbb-254">依循我們配置的 Unity 開發檢查點旅程，此時您會進入部署階段。</span><span class="sxs-lookup"><span data-stu-id="24fbb-254">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="24fbb-255">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="24fbb-255">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24fbb-256">部署至 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="24fbb-256">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="24fbb-257">或者，直接跳到新增進階服務的主題：</span><span class="sxs-lookup"><span data-stu-id="24fbb-257">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24fbb-258">進階服務</span><span class="sxs-lookup"><span data-stu-id="24fbb-258">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="24fbb-259">您可以隨時回到 [Unity 開發檢查點](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。</span><span class="sxs-lookup"><span data-stu-id="24fbb-259">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="24fbb-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24fbb-260">See also</span></span>
* [<span data-ttu-id="24fbb-261">安裝工具</span><span class="sxs-lookup"><span data-stu-id="24fbb-261">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="24fbb-262">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="24fbb-262">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="24fbb-263">部署和偵錯通用 Windows 平台 (UWP) app</span><span class="sxs-lookup"><span data-stu-id="24fbb-263">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="24fbb-264">啟用您的裝置以進行開發</span><span class="sxs-lookup"><span data-stu-id="24fbb-264">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)