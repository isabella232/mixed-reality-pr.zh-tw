---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638637"
---
# <a name="all-platforms"></a>[<span data-ttu-id="1a4c8-101">所有平台</span><span class="sxs-lookup"><span data-stu-id="1a4c8-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="1a4c8-102">啟用 HP 移動控制器外掛程式</span><span class="sxs-lookup"><span data-stu-id="1a4c8-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="1a4c8-103">互動設定檔和控制器對應位於 HP 移動控制器外掛程式中，必須啟用此外掛程式才能將控制器對應公開給 Unreal 的輸入系統。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![啟用 OpenXRHPController 外掛程式](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="1a4c8-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="1a4c8-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="1a4c8-106">設定啟動和 HMDPluginPriority</span><span class="sxs-lookup"><span data-stu-id="1a4c8-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="1a4c8-107">使用 SteamVR 的 Unreal 輸入有一些差異。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="1a4c8-108">設定專案時，請先確認它是藉由新增 vr 來使用 SteamVR 的新輸入系統 **。SteamVR. EnableVRInput = 1** 至 **Engine/Config/ConsoleVariables.ini** 中的 **啟動** 區段。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="1a4c8-109">此 ini 可在引擎安裝目錄中找到，而不是在專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-109">This ini is found in the engine install directory, not the project directory.</span></span>

![更新啟動設定](../images/reverb-g2-img-07.png)

<span data-ttu-id="1a4c8-111">HP 移動控制器外掛程式將會啟用 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="1a4c8-112">如果您不是使用 OpenXR，您將需要在 ConsoleVariables.ini 的相同目錄中編輯 BaseEngine.ini SteamVR 的 HMDPluginPriority。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="1a4c8-113">將 SteamVR 值變更為大於 OpenXRHMD 值。</span><span class="sxs-lookup"><span data-stu-id="1a4c8-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![更新 HMDPluginPriority 設定](../images/reverb-g2-img-08.png)


