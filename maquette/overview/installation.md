---
title: 安裝 Maquette
description: 瞭解如何在 VSCode 中安裝和設定 Maquette。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、原型設計、混合現實、虛擬實境、VR、MR、意見反應、意見反應中樞、bug
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935361"
---
# <a name="installing-maquette"></a>安裝 Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![標誌 ](../images/MaquetteIcon.png) MaquetteScript 安裝

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
MaquetteScript 開發主要是在 VSCode 中完成。 MaquetteScript 可以從檔案包含的腳本中執行 `.mqjs` ，也可以透過特殊的 VSCode 延伸模組介面來執行。 VSCode 與 Maquette 之間的整合可讓擴充介面透過 MaquetteScript VSCode 延伸模組來完成。

## <a name="installing-the-vscode-extension"></a>安裝 VSCode 延伸模組

* 下載並安裝 [VSCode](https://code.visualstudio.com)。 

Maquette javascript 延伸模組位於 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)中。

* 執行擴充功能的 [安裝程式](vscode:extension/ms-maquette.vscode-maquette-javascript)。

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>啟用腳本

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

若要在發行前進行可存取的腳本：

* 將名為 Maquette 的檔案放在 `scripting.enabled` 使用者的 [檔] 目錄中： `~/Documents/Maquette/Settings` 。

安裝之後，基於安全性考慮，預設會停用腳本。

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* 若要啟用腳本的執行，請在附屬視窗的主要索引標籤或 json 設定檔案中開啟腳本。

![在 VS Code 中啟用腳本](images/IntroductionEnableScripting.png)


