---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443685"
---
# <a name="425"></a>[<span data-ttu-id="f7155-101">4.25</span><span class="sxs-lookup"><span data-stu-id="f7155-101">4.25</span></span>](#tab/425)

<span data-ttu-id="f7155-102">針對 UE 4.25 無須進行額外的啟用步驟。</span><span class="sxs-lookup"><span data-stu-id="f7155-102">There are no additional enabling steps specific to UE 4.25.</span></span>

# <a name="426"></a>[<span data-ttu-id="f7155-103">4.26</span><span class="sxs-lookup"><span data-stu-id="f7155-103">4.26</span></span>](#tab/426)

<span data-ttu-id="f7155-104">如果您使用的是 UE 4.26，建議您使用下列藍圖設定新增較小的延遲，因為在啟動 AR 工作階段之後，必須初始化 QR 代碼追蹤：</span><span class="sxs-lookup"><span data-stu-id="f7155-104">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![具有延遲的「切換 ARCapture」函式藍圖](../images/qr-codes-img-01.png)
