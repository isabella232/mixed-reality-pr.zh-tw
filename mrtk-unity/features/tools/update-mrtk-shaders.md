---
title: 著色器更新工具
description: 如何更新 MRTK 標準著色器的相關檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647096"
---
# <a name="updating-shaders"></a><span data-ttu-id="e0574-104">更新著色器</span><span class="sxs-lookup"><span data-stu-id="e0574-104">Updating Shaders</span></span>

<span data-ttu-id="e0574-105">從版本2.6.0 開始，MRTK 著色器會透過 MRTK 進行版本設定。著色器 sentinel 檔。</span><span class="sxs-lookup"><span data-stu-id="e0574-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="e0574-106">升級至新版本的 MRTK 時，可能會出現下列訊息。</span><span class="sxs-lookup"><span data-stu-id="e0574-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![更新著色器提示](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="e0574-108">選取 **[是]** 會指示 MRTK 以最新版本覆寫 **資產**  >  **MRTK**  >  **著色** 器的內容。</span><span class="sxs-lookup"><span data-stu-id="e0574-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="e0574-109">選取 [ **否** ] 將會保留目前的檔案。</span><span class="sxs-lookup"><span data-stu-id="e0574-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="e0574-110">**Ignore** 會 `IgnoreUpdateCheck.sentinel` 在 **資產** MRTK 著色器中建立檔案 ()  >    >  \*\*\*\*，這會隱藏未來的著色器更新檢查。</span><span class="sxs-lookup"><span data-stu-id="e0574-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0574-111">覆寫著色器檔案時，將會遺失任何自訂修改。</span><span class="sxs-lookup"><span data-stu-id="e0574-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="e0574-112">在升級之前，請務必先備份任何已修改的著色器檔案。</span><span class="sxs-lookup"><span data-stu-id="e0574-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="e0574-113">如果專案已設定為使用通用轉譯管線 (URP) 先前的輕量轉譯管線 (LWRP) ，請針對輕量轉譯管線重新執行 **混合現實** > **工具** 組 > **公用程式** >
>  **升級 MRTK 標準著色器**。</span><span class="sxs-lookup"><span data-stu-id="e0574-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="e0574-114">您也可以在  >    >  Unity 編輯器的功能表列上，使用混合現實工具組 **公用程式**  >  **檢查著色器更新**，隨時檢查著色器更新。</span><span class="sxs-lookup"><span data-stu-id="e0574-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![檢查著色器更新](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="e0574-116">**檢查著色器更新是否** 會忽略檔案 `IgnoreUpdateCheck.sentinel` ，並允許隨選著色器更新。</span><span class="sxs-lookup"><span data-stu-id="e0574-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="e0574-117">匯入 MRTK unitypackage 檔案時，不需要檢查著色器更新。</span><span class="sxs-lookup"><span data-stu-id="e0574-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
