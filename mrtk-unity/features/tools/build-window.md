---
title: 組建視窗
description: 使用 MRTK for Unity 中的 [組建] 視窗的相關檔。
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、組建、組建視窗、工具
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176156"
---
# <a name="build-window"></a><span data-ttu-id="13c74-104">組建視窗</span><span class="sxs-lookup"><span data-stu-id="13c74-104">Build window</span></span>
![組建 & 部署流程](images/MRTK_BuildWindow0.png)

<span data-ttu-id="13c74-106">MRTK 的 [組建] 視窗可讓您輕鬆地建立 & 部署 MRTK-Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="13c74-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="13c74-107">只要按一下滑鼠按鍵，您就可以建立 Unity 專案並產生 Visual Studio 的解決方案 (。.SLN) 、UWP 應用程式套件 (。APPX) ，並在裝置上安裝應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="13c74-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="13c74-108">Unity 組建選項</span><span class="sxs-lookup"><span data-stu-id="13c74-108">Unity Build Options</span></span>
![組建視窗-Unity 組建選項1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="13c74-110">這些場景來自 Unity Build 設定。</span><span class="sxs-lookup"><span data-stu-id="13c74-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="13c74-111">您可以使用下拉式功能表來變更目標裝置類型。</span><span class="sxs-lookup"><span data-stu-id="13c74-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="13c74-112">Appx 組建選項</span><span class="sxs-lookup"><span data-stu-id="13c74-112">Appx Build Options</span></span>
![組建視窗-Appx 組建選項2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="13c74-114">此索引標籤會顯示 Visual Studio 解決方案的設定。</span><span class="sxs-lookup"><span data-stu-id="13c74-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="13c74-115">若要啟用 HoloLens 2 的眼睛追蹤輸入功能，請核取 [**注視輸入功能**] 選項。</span><span class="sxs-lookup"><span data-stu-id="13c74-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="13c74-116">您可以在 **3d 應用程式 Launcher 模型**] 欄位中，為自訂3d 應用程式啟動器圖示指派 glb 檔案。</span><span class="sxs-lookup"><span data-stu-id="13c74-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="13c74-117">如需詳細資訊，請參閱 [3d 應用程式啟動器設計指導](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 方針。</span><span class="sxs-lookup"><span data-stu-id="13c74-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="13c74-118">依預設，會在版本控制選項中檢查 **自動遞增** 。</span><span class="sxs-lookup"><span data-stu-id="13c74-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="13c74-119">AppX 版本將會自動遞增。</span><span class="sxs-lookup"><span data-stu-id="13c74-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="13c74-120">部署選項</span><span class="sxs-lookup"><span data-stu-id="13c74-120">Deploy Options</span></span>
![組建視窗-部署選項3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="13c74-122">在此索引標籤中，您可以輸入裝置入口網站的使用者名稱和密碼來連接到裝置。</span><span class="sxs-lookup"><span data-stu-id="13c74-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="13c74-123">在頁面底部，您可以找到已建立的應用程式套件清單。</span><span class="sxs-lookup"><span data-stu-id="13c74-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

