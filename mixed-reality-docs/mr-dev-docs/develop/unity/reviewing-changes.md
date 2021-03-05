---
title: 授權專案變更
description: 瞭解如何授權專案變更適用于 HoloLens 和 VR 開發的 MR 功能工具。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230758"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="70055-104">授權專案變更</span><span class="sxs-lookup"><span data-stu-id="70055-104">Authorizing project changes</span></span>

<span data-ttu-id="70055-105">在修改 Unity 專案之前，必須先審核並核准資訊清單和專案檔的變更：</span><span class="sxs-lookup"><span data-stu-id="70055-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![要求授權](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="70055-107">file:///</span><span class="sxs-lookup"><span data-stu-id="70055-107">Manifest</span></span>

<span data-ttu-id="70055-108">建議的資訊清單變更可以在左邊的 **資訊清單** 欄中查看。</span><span class="sxs-lookup"><span data-stu-id="70055-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="70055-109">內容就是要寫入專案資訊清單 (**套件/manifest.js在) 上** 的內容：</span><span class="sxs-lookup"><span data-stu-id="70055-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![資訊清單預覽](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="70055-111">要複製到專案中的檔案</span><span class="sxs-lookup"><span data-stu-id="70055-111">Files to be copied into the project</span></span>

<span data-ttu-id="70055-112">**要複製到右邊專案** 區段的檔案，會列出將複製到 Unity 專案的特定功能套件檔案：</span><span class="sxs-lookup"><span data-stu-id="70055-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![具有要複製之檔案的資訊清單預覽](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="70055-114">比較資訊清單</span><span class="sxs-lookup"><span data-stu-id="70055-114">Compare manifests</span></span>

<span data-ttu-id="70055-115">您可以藉由選取 [ **比較**]，查看所有建議變更的並列比較：</span><span class="sxs-lookup"><span data-stu-id="70055-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![比較資訊清單](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="70055-117">核准變更</span><span class="sxs-lookup"><span data-stu-id="70055-117">Approving changes</span></span>

<span data-ttu-id="70055-118">當建議的變更通過核准時，所列出的檔案將會複製到 Unity 專案中，而資訊清單會以這些檔案的參考進行更新。</span><span class="sxs-lookup"><span data-stu-id="70055-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="70055-119">應將功能套件 ( \*. tgz) 檔案新增至原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="70055-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="70055-120">它們是使用相對路徑來參考，讓開發小組能夠輕鬆地共用功能和資訊清單變更。</span><span class="sxs-lookup"><span data-stu-id="70055-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="70055-121">在修改過程中，會備份目前的檔案 **manifest.js** 。</span><span class="sxs-lookup"><span data-stu-id="70055-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70055-122">在觀看資訊清單備份時，最舊的 **manifest.js會在備份上呼叫。**</span><span class="sxs-lookup"><span data-stu-id="70055-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="70055-123">較新的備份會以數值標注，從零開始 (0) 。</span><span class="sxs-lookup"><span data-stu-id="70055-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="70055-124">回到上一個步驟</span><span class="sxs-lookup"><span data-stu-id="70055-124">Going back to the previous step</span></span>

<span data-ttu-id="70055-125">如果您需要變更您的功能選項， **請使用 [返回]** 返回匯 [入](importing-features.md) 步驟。</span><span class="sxs-lookup"><span data-stu-id="70055-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="70055-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70055-126">See also</span></span>

- [<span data-ttu-id="70055-127">歡迎使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="70055-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="70055-128">匯入選取的封裝</span><span class="sxs-lookup"><span data-stu-id="70055-128">Importing selected packages</span></span>](importing-features.md)
