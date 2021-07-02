---
title: 在 MRTK 中偵測控制器
description: 搭配使用各種控制器與 MRTK 的相關檔
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、控制器、HP 回音、Oculus、HTC Vive、手
ms.openlocfilehash: 2bb749f4e2f6294c4feb74f97af55ecb857d5f76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175592"
---
# <a name="detecting-controllers-in-mrtk"></a>在 MRTK 中偵測控制器

MRTK 具有許多不同控制器的支援。 許多控制器，例如 HTC Vive Knuckles 和 HTC Vive Wands，在相容裝置上啟動使用 MRTK 建立的應用程式時，將會以原生方式運作。 其他控制器（例如，在 Oculus 的要求和 HP 的回音控制器上進行明確的操作），在 MRTK 辨識這些控制器之前，需要額外的套件。

本檔將說明需要安裝額外套件的一般案例。 如需如何部署至裝置的指示，請參閱 [**Hololens/WMR**](./wmr-mrtk.md) 或 [**Oculus**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) 的部署頁面。 如需控制器的詳細資訊，請造訪 [**功能頁面**](../features/input/controllers.md)。 若要偵測控制器的問題，請參閱 [**控制器對應工具**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>HP 回音（G2）控制器

若要在使用 MRTK 時偵測並顯示 HP 回送 G2 控制器，請遵循下列步驟來安裝 [**MixedReality. 輸入**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 套件。 安裝此套件之後，就不需要對預設設定檔進行任何其他變更，就能讓控制器顯示在 HP 的「回音」上。 

若要在編輯器中顯示控制器，您必須確定您使用的是 [**OpenXR 外掛程式**](/windows/mixed-reality/develop/unity/openxr-getting-started)。

## <a name="oculus-controllers"></a>Oculus 控制器 

若要將 Oculus 控制器模型視覺化，請遵循 Oculus 的部署指示。 如果您想要在使用控制器時顯示虛擬手，請確定已在 [XR SDK Oculus 裝置管理員] 下核取 [轉譯大量圖片]， **而非 [控制器** ]。 否則，請取消核取此選項。

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
