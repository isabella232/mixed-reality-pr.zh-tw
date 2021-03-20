---
title: ExtensionServiceCreationWizard
description: 將 singleton 轉換為服務 MRTK 的 Wizard 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 8b28824b7226f02826d8962d763ef2ba7150aea2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684051"
---
# <a name="extension-service-creation-wizard"></a>延伸模組服務建立嚮導

將 singleton 轉換為服務可能很困難。 此嚮導可以補充我們的其他檔和範例程式碼，方法是讓開發人員建立新的服務， (大致上) 與建立新的 MonoBehaviour 腳本一樣簡單。 若要瞭解如何從頭開始建立服務，請參閱 (即將推出) [建立已註冊服務的指南](../../configuration/MixedRealityConfigurationGuide.md) 。

## <a name="launching-the-wizard"></a>啟動嚮導

從主功能表啟動嚮導： [ **MixedRealityToolkit]/[公用程式]/[建立延伸模組服務** ]-接著，嚮導會帶您完成產生服務腳本、介面和設定檔類別的程式。

## <a name="editing-your-service-script"></a>編輯服務腳本

根據預設，將會在資料夾中產生新的腳本資產 `MixedRealityToolkit.Generated/Extensions` 。 完成嚮導之後，請在這裡流覽並開啟您的新服務腳本。

產生的服務腳本包含一些類似于新 MonoBehaviour 腳本的提示。 它們可讓您知道要在哪裡初始化和更新您的服務。

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

如果您選擇在嚮導中註冊您的服務，您只需要編輯此腳本，就會自動更新您的服務。 否則，您可以在 [這裡閱讀註冊新服務](../../configuration/MixedRealityConfigurationGuide.md)的相關資訊。
