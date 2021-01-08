---
title: 使用 Visual Studio 來部署和偵錯
description: 了解如何使用 Visual Studio 來建置、偵錯及部署 HoloLens 和 Windows Mixed Reality 的應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合實境, 偵錯, 部署
ms.openlocfilehash: 20bda2cd247f18680d3f9fe95284e238a32e1140
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97529971"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="84813-104">使用 Visual Studio 來部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="84813-105">無論您是使用 DirectX 或 Unity 來開發混合實境應用程式，Visual Studio 都是進行偵錯和部署的必備工具。</span><span class="sxs-lookup"><span data-stu-id="84813-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="84813-106">在本節中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="84813-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="84813-107">透過 Visual Studio 將應用程式部署到 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置。</span><span class="sxs-lookup"><span data-stu-id="84813-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="84813-108">使用內建至 Visual Studio 的 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="84813-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="84813-109">針對混合實境應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="84813-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84813-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="84813-110">Prerequisites</span></span>
1. <span data-ttu-id="84813-111">如需安裝指示，請參閱[安裝工具](../../develop/install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="84813-111">See [Install the Tools](../../develop/install-the-tools.md) for installation instructions.</span></span>
2. <span data-ttu-id="84813-112">在 Visual Studio 中建立新的通用 Windows app 專案。</span><span class="sxs-lookup"><span data-stu-id="84813-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="84813-113">對於 HoloLens (第 1 代)，使用 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="84813-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="84813-114">對於 HoloLens 2，使用 Visual Studio 2019 16.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="84813-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="84813-115">支援 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="84813-115">C# and C++ are supported.</span></span> <span data-ttu-id="84813-116">(或者遵循指示，[在 Unity 中建立應用程式](../../develop/unity/tutorials/holograms-100.md)。)</span><span class="sxs-lookup"><span data-stu-id="84813-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="84813-117">啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="84813-117">Enabling Developer Mode</span></span>

<span data-ttu-id="84813-118">從在您的裝置上啟用 **開發人員模式** 開始，讓 Visual Studio 可以與它連線。</span><span class="sxs-lookup"><span data-stu-id="84813-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="84813-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="84813-119">HoloLens</span></span>
1. <span data-ttu-id="84813-120">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="84813-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="84813-121">使用[開始手勢](../../design/system-gesture.md)來啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="84813-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="84813-122">選取 [設定]  磚，在您的環境中啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="84813-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="84813-123">選取 [更新]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="84813-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="84813-124">選取 [適用於開發人員]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="84813-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="84813-125">啟用 [開發人員模式] 以[將應用程式從 Visual Studio](using-visual-studio.md) 部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="84813-125">Enable **Developer Mode** to [deploy apps from Visual Studio](using-visual-studio.md) to your HoloLens.</span></span>
7. <span data-ttu-id="84813-126">選擇性：向下捲動而且啟用 [裝置入口網站]，可讓您從網頁瀏覽器連線到您 HoloLens 上的 [Windows 裝置入口網站](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="84813-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="84813-127">Windows PC</span><span class="sxs-lookup"><span data-stu-id="84813-127">Windows PC</span></span>

<span data-ttu-id="84813-128">如果您使用的是連線到電腦的 Windows Mixed Reality 頭戴式裝置，就必須在電腦上啟用 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="84813-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="84813-129">移至 [設定] </span><span class="sxs-lookup"><span data-stu-id="84813-129">Go to **Settings**</span></span>
2. <span data-ttu-id="84813-130">選取 [更新與安全性] </span><span class="sxs-lookup"><span data-stu-id="84813-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="84813-131">選取 [適用於開發人員] </span><span class="sxs-lookup"><span data-stu-id="84813-131">Select **For developers**</span></span>
4. <span data-ttu-id="84813-132">啟用 [開發人員模式]，閱讀您所選設定的免責聲明，然後選取 [是] 來接受變更。</span><span class="sxs-lookup"><span data-stu-id="84813-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a><span data-ttu-id="84813-133">透過 Wi-Fi 部署應用程式 - HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="84813-133">Deploying an app over Wi-Fi - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="84813-134">為您的應用程式選取 **x86** 組建設定</span><span class="sxs-lookup"><span data-stu-id="84813-134">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="84813-135">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-135">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="84813-136">在 [部署目標] 下拉式功能表中，選取 [遠端電腦] </span><span class="sxs-lookup"><span data-stu-id="84813-136">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="84813-137">![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-137">![Remote machine deployment target in Visual Studio](images/remotemachinesetting.png)</span></span></br>
3. <span data-ttu-id="84813-138">針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。</span><span class="sxs-lookup"><span data-stu-id="84813-138">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="84813-139">針對 C# 專案，會自動顯示用來設定連線的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84813-139">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="84813-140">a.</span><span class="sxs-lookup"><span data-stu-id="84813-140">a.</span></span> <span data-ttu-id="84813-141">在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="84813-141">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="84813-142">在 [設定 > 網路和網際網路 > 進階選項]  底下，尋找 HoloLens 的 IP 位址，或者您可以詢問 Cortana：「我的 IP 位址是什麼？」</span><span class="sxs-lookup"><span data-stu-id="84813-142">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="84813-143">b.</span><span class="sxs-lookup"><span data-stu-id="84813-143">b.</span></span> <span data-ttu-id="84813-144">將驗證模式設定為 [通用 (未加密的通訊協定)] </span><span class="sxs-lookup"><span data-stu-id="84813-144">Set Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="84813-145">![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="84813-145">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="84813-146">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-146">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="84813-147">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="84813-147">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="84813-148">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="84813-148">The first time you deploy an app to your HoloLens from your PC, you'lll be prompted for a PIN.</span></span> <span data-ttu-id="84813-149">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="84813-149">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a><span data-ttu-id="84813-150">透過 Wi-Fi 部署應用程式 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="84813-150">Deploying an app over Wi-Fi - HoloLens 2</span></span>
1. <span data-ttu-id="84813-151">為您的應用程式選取 **ARM** 或 **ARM64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="84813-151">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="84813-152">![Visual Studio 中的 ARM64 組建設定](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-152">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="84813-153">在 [部署目標] 下拉式功能表中，選取 [遠端電腦] </span><span class="sxs-lookup"><span data-stu-id="84813-153">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="84813-154">![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="84813-154">![Remote machine deployment target in Visual Studio](images/remotemachinesetting_arm64.png)</span></span></br>
3. <span data-ttu-id="84813-155">針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。</span><span class="sxs-lookup"><span data-stu-id="84813-155">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="84813-156">針對 C# 專案，會自動顯示用來設定連線的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84813-156">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="84813-157">a.</span><span class="sxs-lookup"><span data-stu-id="84813-157">a.</span></span> <span data-ttu-id="84813-158">在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="84813-158">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="84813-159">在 [設定 > 網路和網際網路 > 進階選項]  底下，尋找 HoloLens 的 IP 位址，或者您可以詢問 Cortana：「我的 IP 位址是什麼？」</span><span class="sxs-lookup"><span data-stu-id="84813-159">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="84813-160">b.</span><span class="sxs-lookup"><span data-stu-id="84813-160">b.</span></span> <span data-ttu-id="84813-161">將驗證模式設定為 [通用 (未加密的通訊協定)] </span><span class="sxs-lookup"><span data-stu-id="84813-161">Set the Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="84813-162">![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="84813-162">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="84813-163">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-163">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="84813-164">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="84813-164">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="84813-165">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="84813-165">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="84813-166">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="84813-166">Follow the **Pairing your device** instructions below.</span></span>

<span data-ttu-id="84813-167">如果您的 HoloLens IP 位址變更，您可以移至 [專案 > 屬性 > 設定屬性 > 偵錯]  ，以變更目標電腦的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="84813-167">If your HoloLens IP address changes, you can change the IP address of the target machine by going to **Project > Properties > Configuration Properties > Debugging**</span></span>

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a><span data-ttu-id="84813-168">透過 USB 部署應用程式 - HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="84813-168">Deploying an app over USB - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="84813-169">為您的應用程式選取 **x86** 組建設定</span><span class="sxs-lookup"><span data-stu-id="84813-169">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="84813-170">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-170">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="84813-171">在 [部署目標] 下拉式功能表中，選取 [裝置] </span><span class="sxs-lookup"><span data-stu-id="84813-171">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="84813-172">![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy.png)</span><span class="sxs-lookup"><span data-stu-id="84813-172">![Device deployment in Visual Studio](images/buildsettingsusbdeploy.png)</span></span></br>
3. <span data-ttu-id="84813-173">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-173">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="84813-174">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="84813-174">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="84813-175">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="84813-175">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="84813-176">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="84813-176">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-usb---hololens-2"></a><span data-ttu-id="84813-177">透過 USB 部署應用程式 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="84813-177">Deploying an app over USB - HoloLens 2</span></span>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="84813-178">為您的應用程式選取 **ARM** 或 **ARM64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="84813-178">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="84813-179">![Visual Studio 中的 ARM64 組建設定](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-179">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="84813-180">在 [部署目標] 下拉式功能表中，選取 [裝置] </span><span class="sxs-lookup"><span data-stu-id="84813-180">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="84813-181">![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="84813-181">![Device deployment in Visual Studio](images/buildsettingsusbdeploy_arm64.png)</span></span></br>
3. <span data-ttu-id="84813-182">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-182">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="84813-183">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="84813-183">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="84813-184">當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="84813-184">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="84813-185">遵循以下的 **配對您的裝置** 指示。</span><span class="sxs-lookup"><span data-stu-id="84813-185">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a><span data-ttu-id="84813-186">將應用程式部署到您的本機電腦 - 沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="84813-186">Deploying an app to your Local PC - immersive headset</span></span>

<span data-ttu-id="84813-187">若要使用可連線到您的電腦或[混合實境模擬器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式頭戴裝置：</span><span class="sxs-lookup"><span data-stu-id="84813-187">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="84813-188">為您的應用程式選取 **x86** 或 **x64** 組建設定</span><span class="sxs-lookup"><span data-stu-id="84813-188">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="84813-189">在 [部署目標] 下拉式功能表中，選取 [本機電腦] </span><span class="sxs-lookup"><span data-stu-id="84813-189">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="84813-190">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-190">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="84813-191">配對您的裝置</span><span class="sxs-lookup"><span data-stu-id="84813-191">Pairing your device</span></span>

<span data-ttu-id="84813-192">當您第一次從 Visual Studio 將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。</span><span class="sxs-lookup"><span data-stu-id="84813-192">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="84813-193">在 HoloLens 上，移至 [更新 > 適用於開發人員]，並點選 [配對]，藉由啟動 [設定] 應用程式來產生 PIN。</span><span class="sxs-lookup"><span data-stu-id="84813-193">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="84813-194">當您的 HoloLens 上顯示 PIN 時，請將其輸入 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="84813-194">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="84813-195">配對完成之後，點選 HoloLens 上的 [完成]  以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84813-195">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="84813-196">這部電腦現在已與 HoloLens 配對，您可以自動部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="84813-196">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="84813-197">針對用來將應用程式部署至 HoloLens 的每部電腦重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="84813-197">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="84813-198">若要解除配對您的 HoloLens 與所有配對的電腦：</span><span class="sxs-lookup"><span data-stu-id="84813-198">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="84813-199">啟動 [設定] 應用程式，移至 [更新] > [適用於開發人員]，然後點選 [清除]。</span><span class="sxs-lookup"><span data-stu-id="84813-199">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a><span data-ttu-id="84813-200">將應用程式部署至 HoloLens (第 1 代) 模擬器</span><span class="sxs-lookup"><span data-stu-id="84813-200">Deploying an app to the HoloLens (1st gen) Emulator</span></span>
1. <span data-ttu-id="84813-201">請確定您已 **[安裝 HoloLens 模擬器](../install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="84813-201">Make sure you've **[installed the HoloLens Emulator](../install-the-tools.md)**.</span></span>
2. <span data-ttu-id="84813-202">為您的應用程式選取 **x86** 組建設定。</span><span class="sxs-lookup"><span data-stu-id="84813-202">Select an **x86** build configuration for your app.</span></span></br>
<span data-ttu-id="84813-203">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-203">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="84813-204">在 [部署目標] 下拉式功能表中，選取 [HoloLens 模擬器] </span><span class="sxs-lookup"><span data-stu-id="84813-204">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="84813-205">![Visual Studio 中的模擬器目標](images/deployemulator.png)</span><span class="sxs-lookup"><span data-stu-id="84813-205">![Emulator target in Visual Studio](images/deployemulator.png)</span></span></br>
4. <span data-ttu-id="84813-206">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-206">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="84813-207">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="84813-207">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a><span data-ttu-id="84813-208">將應用程式部署至 HoloLens 2 模擬器</span><span class="sxs-lookup"><span data-stu-id="84813-208">Deploying an app to the HoloLens 2 Emulator</span></span>
1. <span data-ttu-id="84813-209">請確定您已 **[安裝 HoloLens 模擬器](../install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="84813-209">Make sure you've **[installed the HoloLens Emulator](../install-the-tools.md)**.</span></span>
2. <span data-ttu-id="84813-210">為您的應用程式選取 **x86** 或 **x64** 組建設定。</span><span class="sxs-lookup"><span data-stu-id="84813-210">Select an **x86** or **x64** build configuration for your app.</span></span></br>
<span data-ttu-id="84813-211">![Visual Studio 中的 x86 組建設定](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="84813-211">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="84813-212">在 [部署目標] 下拉式功能表中，選取 [HoloLens 2 模擬器] </span><span class="sxs-lookup"><span data-stu-id="84813-212">Select **HoloLens 2 Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="84813-213">![Visual Studio 中的模擬器目標](images/deployemulator2.png)</span><span class="sxs-lookup"><span data-stu-id="84813-213">![Emulator target in Visual Studio](images/deployemulator2.png)</span></span></br>
4. <span data-ttu-id="84813-214">選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-214">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="84813-215">![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="84813-215">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="84813-216">HoloLens (第 1 代) 的圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="84813-216">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="84813-217">撰寫和最佳化全像攝影應用程式時，Visual Studio 圖形診斷工具很有幫助。</span><span class="sxs-lookup"><span data-stu-id="84813-217">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="84813-218">如需完整詳細資料，請參閱 [MSDN 上的 Visual Studio 圖形診斷](https://msdn.microsoft.com/library/hh315751.aspx)。</span><span class="sxs-lookup"><span data-stu-id="84813-218">See [Visual Studio Graphics Diagnostics on MSDN](https://msdn.microsoft.com/library/hh315751.aspx) for full details.</span></span>

<span data-ttu-id="84813-219">**啟動圖形偵錯工具**</span><span class="sxs-lookup"><span data-stu-id="84813-219">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="84813-220">遵循上述指示，以裝置或模擬器為目標</span><span class="sxs-lookup"><span data-stu-id="84813-220">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="84813-221">移至 [偵錯 > 圖形 > 開始診斷] </span><span class="sxs-lookup"><span data-stu-id="84813-221">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="84813-222">第一次使用 HoloLens 開始診斷時，您可能會遇到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="84813-222">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="84813-223">將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="84813-223">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="84813-224">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="84813-224">Profiling</span></span>

<span data-ttu-id="84813-225">Visual Studio 程式碼剖析工具可讓您分析應用程式的效能和資源使用。</span><span class="sxs-lookup"><span data-stu-id="84813-225">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="84813-226">包括將 CPU、記憶體、圖形和網路使用最佳化的工具。</span><span class="sxs-lookup"><span data-stu-id="84813-226">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="84813-227">如需完整詳細資料，請參閱 [MSDN 上的執行診斷工具而不進行偵錯](https://msdn.microsoft.com/library/dn957936.aspx)。</span><span class="sxs-lookup"><span data-stu-id="84813-227">See [Run diagnostic tools without debugging on MSDN](https://msdn.microsoft.com/library/dn957936.aspx) for full details.</span></span>

<span data-ttu-id="84813-228">**使用 HoloLens 啟動程式碼剖析工具**</span><span class="sxs-lookup"><span data-stu-id="84813-228">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="84813-229">遵循上述指示，以裝置或模擬器為目標</span><span class="sxs-lookup"><span data-stu-id="84813-229">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="84813-230">移至 [偵錯 > 啟動診斷工具但不偵錯...]  。</span><span class="sxs-lookup"><span data-stu-id="84813-230">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="84813-231">選取您想要使用的工具</span><span class="sxs-lookup"><span data-stu-id="84813-231">Select the tools you want to use</span></span>
4. <span data-ttu-id="84813-232">選取 [啟動]</span><span class="sxs-lookup"><span data-stu-id="84813-232">Select **Start**</span></span>
5. <span data-ttu-id="84813-233">第一次使用 HoloLens 開始診斷但不進行偵錯時，您可能會遇到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="84813-233">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="84813-234">將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="84813-234">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="84813-235">針對已安裝或執行中的應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="84813-235">Debugging an installed or running app</span></span>

<span data-ttu-id="84813-236">您可以使用 Visual Studio 針對已安裝但未從 Visual Studio 專案部署的通用 Windows 應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="84813-236">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="84813-237">如果您想要對已安裝的應用程式套件進行偵錯，或對已經在執行中的應用程式進行偵錯，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="84813-237">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="84813-238">移至 [偵錯 -> 其他偵錯目標 -> 針對已安裝的應用程式套件進行偵錯] </span><span class="sxs-lookup"><span data-stu-id="84813-238">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="84813-239">針對 HoloLens 選取 [遠端電腦]  目標，或針對沉浸式頭戴裝置選取 [本機電腦]  。</span><span class="sxs-lookup"><span data-stu-id="84813-239">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="84813-240">輸入您裝置的 **IP 位址**</span><span class="sxs-lookup"><span data-stu-id="84813-240">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="84813-241">選擇 [通用]  驗證模式</span><span class="sxs-lookup"><span data-stu-id="84813-241">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="84813-242">此視窗會顯示執行中和非使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="84813-242">The window shows both running and inactive apps.</span></span> <span data-ttu-id="84813-243">挑選您想要進行偵錯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="84813-243">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="84813-244">選擇要進行偵錯的程式碼類型 (受控、原生、混合)</span><span class="sxs-lookup"><span data-stu-id="84813-244">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="84813-245">選取 [連結] 或 [啟動]</span><span class="sxs-lookup"><span data-stu-id="84813-245">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="84813-246">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="84813-246">Next Development Checkpoint</span></span>

<span data-ttu-id="84813-247">依循我們配置的 Unity 開發檢查點旅程，此時您會進入部署階段。</span><span class="sxs-lookup"><span data-stu-id="84813-247">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="84813-248">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="84813-248">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84813-249">部署至 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="84813-249">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="84813-250">或者，直接跳到新增進階服務的主題：</span><span class="sxs-lookup"><span data-stu-id="84813-250">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84813-251">進階服務</span><span class="sxs-lookup"><span data-stu-id="84813-251">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="84813-252">您可以隨時回到 [Unity 開發檢查點](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。</span><span class="sxs-lookup"><span data-stu-id="84813-252">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="84813-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84813-253">See also</span></span>
* [<span data-ttu-id="84813-254">安裝工具</span><span class="sxs-lookup"><span data-stu-id="84813-254">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="84813-255">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="84813-255">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="84813-256">部署和偵錯通用 Windows 平台 (UWP) app</span><span class="sxs-lookup"><span data-stu-id="84813-256">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [<span data-ttu-id="84813-257">啟用您的裝置以進行開發</span><span class="sxs-lookup"><span data-stu-id="84813-257">Enable your device for development</span></span>](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
