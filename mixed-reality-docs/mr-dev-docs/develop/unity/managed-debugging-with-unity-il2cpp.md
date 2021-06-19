---
title: 使用 Unity 的 Managed 調試
description: 本文涵蓋如何在 Unity IL2CPP UWP 專案上執行 managed 偵錯工具。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity、visual studio、調試、il2cpp、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、UWP
ms.openlocfilehash: 48f5fbd4b2ac217a3f840117595aa36fb3d7c10e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394502"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="af0cb-104">使用 Unity 的 Managed 調試</span><span class="sxs-lookup"><span data-stu-id="af0cb-104">Managed debugging with Unity</span></span>

<span data-ttu-id="af0cb-105">遵循下列步驟將 managed 偵錯工具附加至適用于 HoloLens 和 HoloLens 2 的 Unity IL2CPP UWP 組建。</span><span class="sxs-lookup"><span data-stu-id="af0cb-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="af0cb-106">您需要在支援 [多播](https://en.wikipedia.org/wiki/Multicast)的網路上。</span><span class="sxs-lookup"><span data-stu-id="af0cb-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="af0cb-107">移至 **UWP 發行設定功能** ，並查看 **InternetClientServer** 和 **PrivateNetworkClientServer**：</span><span class="sxs-lookup"><span data-stu-id="af0cb-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![UWP 發行設定功能](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="af0cb-109">設定 Unity UWP 組建設定：</span><span class="sxs-lookup"><span data-stu-id="af0cb-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="af0cb-110">開發組建</span><span class="sxs-lookup"><span data-stu-id="af0cb-110">Development Build</span></span>
    - <span data-ttu-id="af0cb-111">指令碼偵錯</span><span class="sxs-lookup"><span data-stu-id="af0cb-111">Script Debugging</span></span>
    - <span data-ttu-id="af0cb-112">等候 Managed 偵錯工具 (選擇性) </span><span class="sxs-lookup"><span data-stu-id="af0cb-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP 組建設定](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="af0cb-114">Unity 中的組建。</span><span class="sxs-lookup"><span data-stu-id="af0cb-114">Build in Unity.</span></span>
5. <span data-ttu-id="af0cb-115">從 Visual Studio 解決方案建立並部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="af0cb-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="af0cb-116">您應該使用 **Debug** 或 **Release** 設定來建立。</span><span class="sxs-lookup"><span data-stu-id="af0cb-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="af0cb-117">**主要** 設定會停用 Unity profiler，並可防止最佳的調試。</span><span class="sxs-lookup"><span data-stu-id="af0cb-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="af0cb-118">（選擇性）在解決方案的 package.appxmanifest 的 [功能] 清單中，確認 **(用戶端 & 伺服器)** 和 **私人網路 (用戶端 & 伺服器)** 。</span><span class="sxs-lookup"><span data-stu-id="af0cb-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="af0cb-119">確定您的裝置已連線到與您電腦相同的網路，然後在您的裝置上啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="af0cb-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="af0cb-120">請確定裝置 **未** 透過 USB 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="af0cb-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="af0cb-121">按兩下 Unity 中的其中一個腳本，然後移至開啟以查看和編輯的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="af0cb-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="af0cb-122">Debug-> 附加 Unity 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="af0cb-122">Debug -> Attach Unity Debugger.</span></span>

    ![附加 Unity 偵錯工具](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="af0cb-124">在清單中選取您的裝置，然後按一下 [確定] 以連接。</span><span class="sxs-lookup"><span data-stu-id="af0cb-124">Select your device in the list and click "OK" to attach.</span></span>

    ![裝置清單](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a><span data-ttu-id="af0cb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af0cb-126">See also</span></span> 

* [<span data-ttu-id="af0cb-127">C # 調試</span><span class="sxs-lookup"><span data-stu-id="af0cb-127">C# debugging</span></span>](/visualstudio/get-started/csharp/tutorial-debugger)
