---
title: 針對 OpenXR 進行疑難排解
description: 針對 OpenXR 應用程式中的問題進行疑難排解。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、疑難排解
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903094"
---
# <a name="openxr-troubleshooting"></a>針對 OpenXR 進行疑難排解

以下是使用 Windows Mixed Reality OpenXR 執行時間開發 OpenXR 應用程式時的一些疑難排解秘訣。  如果您有任何其他有關 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的問題，請造訪 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a> 或 <a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。

>[!NOTE]
>目前 Windows Mixed Reality OpenXR 執行時間與 x86 應用程式有已知的問題。  您現在應該建立 x64 的桌面 OpenXR 應用程式。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 應用程式未啟動 Windows Mixed Reality

如果您的 OpenXR 應用程式未在執行時啟動 Windows Mixed Reality，Windows Mixed Reality OpenXR 執行時間可能不會設定為使用中執行時間。  請務必遵循 [Windows Mixed Reality 耳機開始使用 OpenXR](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 的指示，使執行時間成為使用中狀態。

您也可以執行 [適用于 Windows Mixed Reality 的 OpenXR 開發人員工具](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) ，以取得有關系統上 Windows Mixed Reality OpenXR 執行時間狀態的額外疑難排解協助。