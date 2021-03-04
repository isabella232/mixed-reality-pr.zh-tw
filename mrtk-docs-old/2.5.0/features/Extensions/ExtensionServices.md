---
title: ExtensionServices
description: MRTK 中擴充功能的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 981c7cd164e99760ee93ff4db7af906dbe5ab9a9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780630"
---
# <a name="extension-services"></a><span data-ttu-id="1c12e-104">擴充服務</span><span class="sxs-lookup"><span data-stu-id="1c12e-104">Extension services</span></span>

<span data-ttu-id="1c12e-105">延伸模組服務是延伸混合現實工具組功能的元件。</span><span class="sxs-lookup"><span data-stu-id="1c12e-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1c12e-106">這些服務可能由 MRTK 或其他各方提供。</span><span class="sxs-lookup"><span data-stu-id="1c12e-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="1c12e-107">建立延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="1c12e-107">Creating an extension service</span></span>

<span data-ttu-id="1c12e-108">建立擴充服務最有效率的方法是使用「 [擴充功能服務建立嚮導](../Tools/ExtensionServiceCreationWizard.md)」。</span><span class="sxs-lookup"><span data-stu-id="1c12e-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../Tools/ExtensionServiceCreationWizard.md).</span></span>
<span data-ttu-id="1c12e-109">若要啟動 [擴充功能服務建立嚮導]，請選取 [ **混合現實工具組] > 公用程式 > 建立延伸模組服務**。</span><span class="sxs-lookup"><span data-stu-id="1c12e-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![延伸模組服務建立嚮導](../Images/ExtensionWizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="1c12e-111">Wizard 會自動建立服務元件，並確保適當的介面繼承。</span><span class="sxs-lookup"><span data-stu-id="1c12e-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![延伸模組服務建立嚮導所建立的元件](../Images/ExtensionWizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="1c12e-113">在 MRTK 版本2.0.0 中，需要產生服務偵測器和服務設定檔的延伸模組服務嚮導有問題。</span><span class="sxs-lookup"><span data-stu-id="1c12e-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="1c12e-114">如需詳細資訊，請參閱問題 [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) 。</span><span class="sxs-lookup"><span data-stu-id="1c12e-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="1c12e-115">當 wizard 完成時，就可以執行服務功能。</span><span class="sxs-lookup"><span data-stu-id="1c12e-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="1c12e-116">註冊擴充服務</span><span class="sxs-lookup"><span data-stu-id="1c12e-116">Registering an extension service</span></span>

<span data-ttu-id="1c12e-117">若要供應用程式存取，新的擴充功能服務必須向混合現實工具組註冊。</span><span class="sxs-lookup"><span data-stu-id="1c12e-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="1c12e-118">您可以使用擴充服務建立嚮導來註冊服務。</span><span class="sxs-lookup"><span data-stu-id="1c12e-118">The extension service creation wizard can be used to register the service.</span></span>

![延伸模組服務建立嚮導註冊](../Images/ExtensionWizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="1c12e-120">您也可以使用「混合現實工具組設定偵測器」手動註冊服務。</span><span class="sxs-lookup"><span data-stu-id="1c12e-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![手動擴充服務註冊](../Images/Profiles/RegisterExtensionService.png)

<span data-ttu-id="1c12e-122">如果延伸模組服務使用設定檔，請確定它是在偵測器中所指定。</span><span class="sxs-lookup"><span data-stu-id="1c12e-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![設定的擴充服務](../Images/Profiles/ConfiguredExtensionService.png)

<span data-ttu-id="1c12e-124">元件名稱和優先權也可以進行調整。</span><span class="sxs-lookup"><span data-stu-id="1c12e-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="1c12e-125">存取擴充服務</span><span class="sxs-lookup"><span data-stu-id="1c12e-125">Accessing an extension service</span></span>

<span data-ttu-id="1c12e-126">您可以使用程式碼中的擴充服務來存取， [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1c12e-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="1c12e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c12e-127">See also</span></span>

- [<span data-ttu-id="1c12e-128">系統、延伸模組服務和資料提供者</span><span class="sxs-lookup"><span data-stu-id="1c12e-128">Systems, extension services and data providers</span></span>](../../architecture/SystemsExtensionsProviders.md)
- [<span data-ttu-id="1c12e-129">延伸模組服務建立嚮導</span><span class="sxs-lookup"><span data-stu-id="1c12e-129">Extension service creation wizard</span></span>](../Tools/ExtensionServiceCreationWizard.md)
- [<span data-ttu-id="1c12e-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="1c12e-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="1c12e-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="1c12e-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
