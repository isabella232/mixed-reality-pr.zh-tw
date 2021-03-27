---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636280"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 提供內建的 [傳送系統](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) ，可自動跨明確的手和控制器運作。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

我們建議使用 MRTK 的遙傳執行。
如果您選擇不使用 MRTK，Unity 會在 [XR 互動工具](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)組中提供遙傳的實作為。
如果您選擇自行執行，請記住，您無法直接移動相機。 由於 Unity 的標頭控制，因此您必須為相機提供階層中的父代，並改為移動該 GameObject。 這相當於 MRTK 的 Playspace。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

我們建議使用 MRTK 的遙傳執行。
如果您選擇自行執行，請記住，您無法直接移動相機。 由於 Unity 的標頭控制，因此您必須為相機提供階層中的父代，並改為移動該 GameObject。 這相當於 MRTK 的 Playspace。