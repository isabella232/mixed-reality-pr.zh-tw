---
title: 著色器更新工具
description: 如何更新 MRTK 標準著色器的相關檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 9ed8a1e439b2bf911d8144a90259d99bf38b12e0404d9ad3365152bed633042c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197062"
---
# <a name="updating-shaders"></a>更新著色器

從版本2.6.0 開始，MRTK 著色器會透過 MRTK 進行版本設定。著色器 sentinel 檔。 升級至新版本的 MRTK 時，可能會出現下列訊息。

![更新著色器提示](../images/tools/UpdateShaderPrompt.png)

選取 **[是]** 會指示 MRTK 以最新版本覆寫 **資產**  >  **MRTK**  >  **著色** 器的內容。 選取 [ **否** ] 將會保留目前的檔案。 **Ignore** 會 `IgnoreUpdateCheck.sentinel` 在 **資產** MRTK 著色器中建立檔案 ()  >    >  ****，這會隱藏未來的著色器更新檢查。

> [!IMPORTANT]
> 覆寫著色器檔案時，將會遺失任何自訂修改。 在升級之前，請務必先備份任何已修改的著色器檔案。
>
> 如果專案已設定為使用通用轉譯管線 (URP) 先前的輕量轉譯管線 (LWRP) ，請針對輕量轉譯管線重新執行 **混合現實** > **工具** 組 > **公用程式** >
>  **升級 MRTK 標準著色器**。

您也可以在  >    >  Unity 編輯器的功能表列上，使用混合現實工具組 **公用程式**  >  **檢查著色器更新**，隨時檢查著色器更新。

![檢查著色器更新](../images/tools/ShaderUpdateMenu.png)

**檢查著色器更新是否** 會忽略檔案 `IgnoreUpdateCheck.sentinel` ，並允許隨選著色器更新。

> [!NOTE]
> 匯入 MRTK unitypackage 檔案時，不需要檢查著色器更新。
