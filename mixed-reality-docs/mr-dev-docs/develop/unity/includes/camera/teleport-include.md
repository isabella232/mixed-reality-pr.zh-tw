---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636280"
---
# <a name="mrtk"></a>[<span data-ttu-id="d3081-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="d3081-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d3081-102">MRTK 提供內建的 [傳送系統](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) ，可自動跨明確的手和控制器運作。</span><span class="sxs-lookup"><span data-stu-id="d3081-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="d3081-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="d3081-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d3081-104">我們建議使用 MRTK 的遙傳執行。</span><span class="sxs-lookup"><span data-stu-id="d3081-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="d3081-105">如果您選擇不使用 MRTK，Unity 會在 [XR 互動工具](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)組中提供遙傳的實作為。</span><span class="sxs-lookup"><span data-stu-id="d3081-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="d3081-106">如果您選擇自行執行，請記住，您無法直接移動相機。</span><span class="sxs-lookup"><span data-stu-id="d3081-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="d3081-107">由於 Unity 的標頭控制，因此您必須為相機提供階層中的父代，並改為移動該 GameObject。</span><span class="sxs-lookup"><span data-stu-id="d3081-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="d3081-108">這相當於 MRTK 的 Playspace。</span><span class="sxs-lookup"><span data-stu-id="d3081-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d3081-109">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="d3081-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d3081-110">我們建議使用 MRTK 的遙傳執行。</span><span class="sxs-lookup"><span data-stu-id="d3081-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="d3081-111">如果您選擇自行執行，請記住，您無法直接移動相機。</span><span class="sxs-lookup"><span data-stu-id="d3081-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="d3081-112">由於 Unity 的標頭控制，因此您必須為相機提供階層中的父代，並改為移動該 GameObject。</span><span class="sxs-lookup"><span data-stu-id="d3081-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="d3081-113">這相當於 MRTK 的 Playspace。</span><span class="sxs-lookup"><span data-stu-id="d3081-113">This is the equivalent of MRTK's Playspace.</span></span>