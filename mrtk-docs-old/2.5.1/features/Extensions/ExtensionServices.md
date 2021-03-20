---
title: ExtensionServices
description: MRTK 中擴充功能的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 9b1ed24d70c68805baa78143be35f7e94a59ac5f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682561"
---
# <a name="extension-services"></a>擴充服務

延伸模組服務是延伸混合現實工具組功能的元件。 這些服務可能由 MRTK 或其他各方提供。

## <a name="creating-an-extension-service"></a>建立延伸模組服務

建立擴充服務最有效率的方法是使用「 [擴充功能服務建立嚮導](../tools/ExtensionServiceCreationWizard.md)」。
若要啟動 [擴充功能服務建立嚮導]，請選取 [ **混合現實工具組] > 公用程式 > 建立延伸模組服務**。

![延伸模組服務建立嚮導](../images/extension-wizard/ExtensionServiceCreationWizard.png)

Wizard 會自動建立服務元件，並確保適當的介面繼承。

![延伸模組服務建立嚮導所建立的元件](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> 在 MRTK 版本2.0.0 中，需要產生服務偵測器和服務設定檔的延伸模組服務嚮導有問題。 如需詳細資訊，請參閱問題 [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) 。

當 wizard 完成時，就可以執行服務功能。

## <a name="registering-an-extension-service"></a>註冊擴充服務

若要供應用程式存取，新的擴充功能服務必須向混合現實工具組註冊。

您可以使用擴充服務建立嚮導來註冊服務。

![延伸模組服務建立嚮導註冊](../images/extension-wizard/ExtensionServiceWizardRegister.png)

您也可以使用「混合現實工具組設定偵測器」手動註冊服務。

![手動擴充服務註冊](../images/profiles/RegisterExtensionService.png)

如果延伸模組服務使用設定檔，請確定它是在偵測器中所指定。

![設定的擴充服務](../images/profiles/ConfiguredExtensionService.png)

元件名稱和優先權也可以進行調整。

## <a name="accessing-an-extension-service"></a>存取擴充服務

您可以使用程式碼中的擴充服務來存取， [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 如下列範例所示。

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>另請參閱

- [系統、延伸模組服務和資料提供者](../../architecture/SystemsExtensionsProviders.md)
- [延伸模組服務建立嚮導](../tools/ExtensionServiceCreationWizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
