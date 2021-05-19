---
title: 延伸模組服務建立嚮導
description: 將 singleton 轉換為服務 MRTK 的 Wizard 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143548"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="555fc-104">延伸模組服務建立嚮導</span><span class="sxs-lookup"><span data-stu-id="555fc-104">Extension service creation wizard</span></span>

<span data-ttu-id="555fc-105">將 singleton 轉換為服務可能很困難。</span><span class="sxs-lookup"><span data-stu-id="555fc-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="555fc-106">此嚮導可以補充我們的其他檔和範例程式碼，方法是讓開發人員建立新的服務， (大致上) 與建立新的 MonoBehaviour 腳本一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="555fc-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="555fc-107">若要瞭解如何從頭開始建立服務，請參閱 (即將推出) [建立已註冊服務的指南](../../configuration/mixed-reality-configuration-guide.md) 。</span><span class="sxs-lookup"><span data-stu-id="555fc-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="555fc-108">啟動嚮導</span><span class="sxs-lookup"><span data-stu-id="555fc-108">Launching the wizard</span></span>

<span data-ttu-id="555fc-109">從主功能表啟動嚮導： [ **MixedRealityToolkit]/[公用程式]/[建立延伸模組服務** ]-接著，嚮導會帶您完成產生服務腳本、介面和設定檔類別的程式。</span><span class="sxs-lookup"><span data-stu-id="555fc-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="555fc-110">編輯服務腳本</span><span class="sxs-lookup"><span data-stu-id="555fc-110">Editing your service script</span></span>

<span data-ttu-id="555fc-111">根據預設，將會在資料夾中產生新的腳本資產 `MixedRealityToolkit.Generated/Extensions` 。</span><span class="sxs-lookup"><span data-stu-id="555fc-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="555fc-112">完成嚮導之後，請在這裡流覽並開啟您的新服務腳本。</span><span class="sxs-lookup"><span data-stu-id="555fc-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="555fc-113">產生的服務腳本包含一些類似于新 MonoBehaviour 腳本的提示。</span><span class="sxs-lookup"><span data-stu-id="555fc-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="555fc-114">它們可讓您知道要在哪裡初始化和更新您的服務。</span><span class="sxs-lookup"><span data-stu-id="555fc-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="555fc-115">如果您選擇在嚮導中註冊您的服務，您只需要編輯此腳本，就會自動更新您的服務。</span><span class="sxs-lookup"><span data-stu-id="555fc-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="555fc-116">否則，您可以在 [這裡閱讀註冊新服務](../../configuration/mixed-reality-configuration-guide.md)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="555fc-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
