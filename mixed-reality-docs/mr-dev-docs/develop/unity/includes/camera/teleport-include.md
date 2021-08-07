---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212239"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 提供內建的 [傳送系統](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) ，可自動跨明確的手和控制器運作。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

我們建議使用 MRTK 的遙傳執行。
如果您選擇不使用 MRTK，Unity 會在 [XR 互動工具](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)組中提供遙傳的實作為。
如果您選擇自行執行，請記住，您無法直接移動相機。 由於 Unity 的標頭控制，因此您必須為相機提供階層中的父代，並改為移動該 GameObject。 這相當於 MRTK 的 Playspace。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

我們建議使用 MRTK 的遙傳執行。
如果您選擇自行執行，請記住，您無法直接移動相機。 由於 Unity 的標頭控制，因此您必須為相機提供階層中的父代，並改為移動該 GameObject。 這相當於 MRTK 的 Playspace。