---
title: 資產交換公用程式
description: 說明如何使用 MRTK for Unity 中的資產交換公用程式。
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
ms.openlocfilehash: bfdf0111d99f96c2b03f921da21368897d682d3d
ms.sourcegitcommit: ece91dbba40981720fe7e1a7c3b93e8b75ff71ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2021
ms.locfileid: "102583189"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="398ec-104">資產交換公用程式</span><span class="sxs-lookup"><span data-stu-id="398ec-104">Asset swap utility</span></span>

<span data-ttu-id="398ec-105">當您在文字和內容建立工具中工作時，尋找和取代是普遍的。</span><span class="sxs-lookup"><span data-stu-id="398ec-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="398ec-106">當您需要交換 Unity 場景內的許多資產時，您可以在這裡 [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 和 editor 的手上。</span><span class="sxs-lookup"><span data-stu-id="398ec-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="398ec-107">此公用程式包含在 `Microsoft.MixedReality.Toolkit.Unity.Tools` 套件中。</span><span class="sxs-lookup"><span data-stu-id="398ec-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="398ec-108">`AssetSwapUtility`會將所有尋找和取代動作儲存為 ScriptableObject，使其 trival 為來回交換或儲存交換「主題」以供日後使用。</span><span class="sxs-lookup"><span data-stu-id="398ec-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="398ec-109">交換資產</span><span class="sxs-lookup"><span data-stu-id="398ec-109">Swapping assets</span></span>

<span data-ttu-id="398ec-110">一旦建立之後，就可以輕鬆交換資產 `AssetSwapCollection` 。</span><span class="sxs-lookup"><span data-stu-id="398ec-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="398ec-111">讓我們示範如何使用場景中兩個藍色球體交換兩個紅色 cube。</span><span class="sxs-lookup"><span data-stu-id="398ec-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="398ec-112">首先，將兩個紅色 cube 新增至使用預設 Unity cube 和材質的場景 `MRTK_Standard_Red` 。</span><span class="sxs-lookup"><span data-stu-id="398ec-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="398ec-113">若要建立 `AssetSwapCollection` ，請流覽至 **混合現實工具組 > 公用程式 > 建立資產交換集合**。</span><span class="sxs-lookup"><span data-stu-id="398ec-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="398ec-114">使用 `AssetSwapCollection` 選取的填寫屬性，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="398ec-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Unity 編輯器中的資產交換集合](images/asset-swap-img-01.png)

<span data-ttu-id="398ec-116">接下來，從 [選取的主題] 下拉式清單中選取 [藍色球體]，然後按 [套用]。</span><span class="sxs-lookup"><span data-stu-id="398ec-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="398ec-117">您場景內的所有紅色 cube 都應取代為藍色球體。</span><span class="sxs-lookup"><span data-stu-id="398ec-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Unity 編輯器中已醒目提示所選主題的資產交換集合](images/asset-swap-img-02.png)

<span data-ttu-id="398ec-119">在此範例中，我們執行了完整的場景取代，但您可以藉由變更「選取模式」來取代場景的部分。</span><span class="sxs-lookup"><span data-stu-id="398ec-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="398ec-120">您也可以從 [選取的主題] 下拉式清單中選取 [紅色 Cube]，然後再按一次 [套用]，以切換回紅色 cube。</span><span class="sxs-lookup"><span data-stu-id="398ec-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="398ec-121">您可以交換任何資產類型，例如音訊檔案、字型、prefabs 等。 `AssetSwapUtility` 會執行一些例行性檢查，以確保您會交換至類似的類型。</span><span class="sxs-lookup"><span data-stu-id="398ec-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>