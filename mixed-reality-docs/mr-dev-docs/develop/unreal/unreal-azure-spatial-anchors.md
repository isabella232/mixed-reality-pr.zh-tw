---
title: Unreal 中的 Azure Spatial Anchors
description: 了解如何在 Unreal 混合實境應用程式中建立、管理及尋找現有的 Azure Spatial Anchors。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure 開發, 空間錨點, 混合實境, 開發, 功能, 新專案, 模擬器, 文件, 指南, 全像投影, 遊戲開發, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 95e8ad708dd44a05fb306b2ea49f167fd400c5d8
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009768"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Unreal 中的 Azure Spatial Anchors

Azure Spatial Anchors 是 Microsoft Mixed Reality 服務，可讓擴增實境裝置探索、共用及保存實體世界中的錨點。 以下文件提供將 Azure Spatial Anchors 服務整合到 Unreal 專案中的指示。 如果您要尋找更多資訊，請參閱 [Azure Spatial Anchors 服務](https://azure.microsoft.com/services/spatial-anchors/)。

> [!NOTE]
> 如果您以 iOS 或 Android 作為目標，則 Unreal Engine 4.26 現在有適用於 ARKit 和 ARCore 支援的外掛程式。

> [!IMPORTANT]
> 本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。 如果您要將錨點儲存在裝置本機上，我們有[本機空間錨點](unreal-spatial-anchors.md)文件，可協助您逐步完成此程序。 請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。

## <a name="prerequisites"></a>必要條件

若要完成本指南，請確定您：

- 已安裝 [Unreal 4.25 版](https://www.unrealengine.com/get-now)或更新版本
- 在 Unreal 中設定了 [HoloLens 2 專案](tutorials/unreal-uxt-ch1.md) 
- 請參閱 [Azure Spatial Anchors 概觀](https://docs.microsoft.com/azure/spatial-anchors/overview)
- C++ 和 Unreal 的基本知識

## <a name="getting-azure-spatial-anchors-account-info"></a>取得 Azure Spatial Anchors 帳戶資訊

在您的專案中使用 Azure Spatial Anchors 之前，您必須：
* [建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)並複製下列帳戶欄位。 這些值用來向您的應用程式帳戶驗證使用者：
    * **帳戶識別碼**
    * **帳戶金鑰**

如需詳細資訊，請參閱 [Azure Spatial Anchors 驗證](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp)文件。

> [!NOTE]
> Unreal 4.25 中的 Azure Spatial Anchors 不支援 Azure AD 驗證權杖，但這項功能的支援將會在後續版本中推出。

## <a name="adding-azure-spatial-anchors-plugins"></a>新增 Azure Spatial Anchors 外掛程式

在 Unreal 編輯器中啟用 Azure Spatial Anchors 外掛程式，方法如下：
1. 按一下 [編輯] > [外掛程式] 並搜尋 **AzureSpatialAnchors** 和 **AzureSpatialAnchorsForWMR**。
2. 在兩個外掛程式中選取 [已啟用] 核取方塊，以允許存取您應用程式中的 Azure Spatial Anchors 藍圖程式庫。

![Unreal 編輯器中的空間錨點外掛程式的螢幕擷取畫面](images/asa-unreal/unreal-spatial-anchors-img-01.png)

完成後，請重新啟動 Unreal 編輯器，讓外掛程式變更生效。 專案現在已準備好使用 Azure Spatial Anchors。

## <a name="starting-a-spatial-anchors-session"></a>啟動空間錨點工作階段

Azure Spatial Anchors 工作階段可讓用戶端應用程式與 Azure Spatial Anchors 服務進行通訊。 您必須建立並啟動 Azure Spatial Anchors 工作階段，才能建立、保存和共用 Azure Spatial Anchors：

1. 針對您在應用程式中使用的 Pawn 開啟藍圖。
2. 為 [帳戶識別碼] 和 [帳戶金鑰] 新增兩個字串變數，然後從您的 Azure Spatial Anchors 帳戶指派對應的值，以驗證工作階段。

![詳細資料面板的螢幕擷取畫面，其中已醒目提示 Azure Spatial Anchors 帳戶識別碼、金鑰和變數類型](images/asa-unreal/unreal-spatial-anchors-img-02.png)

啟動 Azure Spatial Anchors 工作階段，方法如下：
1. 檢查 [AR 工作階段] 是否正在 HoloLens 應用程式中執行，因為直到 AR 工作階段執行，才能啟動 Azure Spatial Anchors 工作階段。 如果您尚未設定工作階段，請[建立 AR 工作階段資產](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)。
2. 新增 [啟動 Azure Spatial Anchors 工作階段] 自訂事件並加以設定，如下列螢幕擷取畫面所示。
    * 建立工作階段時，依預設不會啟動工作階段，這可讓您使用 Azure Spatial Anchors 服務設定工作階段以進行驗證。

![開始 Azure Spatial Anchors 工作階段自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. 設定 Azure Spatial Anchors 工作階段，以提供 [帳戶識別碼] 和 [帳戶金鑰]。

![已新增帳戶識別碼和金鑰的設定工作階段函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. 啟動 Azure Spatial Anchors 工作階段，讓應用程式能夠建立及尋找 Azure Spatial Anchors。

![Azure Spatial Anchors 工作階段啟動函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-05.png)

當您不再使用該服務時，在事件圖形藍圖中清除 Azure Spatial Anchors 資源是很好的作法：

1. 停止 Azure Spatial Anchors 工作階段。 工作階段將不再執行，但其相關聯的資源仍會存在於 Azure Spatial Anchors 外掛程式中。

![停止 Azure Spatial Anchors 工作階段自訂事件和停止工作階段函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. 終結 Azure Spatial Anchors 工作階段，以清除 Azure Spatial Anchors 外掛程式仍知道的任何 Azure Spatial Anchors 工作階段資源。

![終結工作階段函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-07.png)

您的事件圖形藍圖看起來應該類似下列螢幕擷取畫面：

![Azure Spatial Anchors 工作階段設定的完整事件圖形的藍圖](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a>建立錨點

Azure Spatial Anchors 代表擴增實境應用程式空間中的實體世界姿態，會將擴增實境內容連結至實體位置。 Azure Spatial Anchors 也可以在不同的使用者間共用。 此共用可讓在不同裝置上繪製的擴增實境內容放置於實體世界中的相同位置。 

若要建立新的 Azure Spatial Anchors：
1. 檢查 Azure Spatial Anchors 工作階段是否正在執行。 若沒有任何正在執行的 Azure Spatial Anchors 工作階段，應用程式就無法建立或保存 Azure Spatial Anchors。

![建立 Azure Spatial Anchors 自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. 建立或取得應保存其位置的 Unreal **[場景元件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** 。 
    * 在下圖中，[需要錨點的場景元件] 元件會當作變數使用。 需要 Unreal 場景元件才能建立 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 和 Azure Spatial Anchors 的應用程式世界轉換。

![建立 Azure Spatial Anchors 自訂事件與場景元件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-10.png)

若要為 Unreal 場景元件建構並儲存 Azure Spatial Anchors：
1. 針對 Unreal 場景元件呼叫 [Pin 元件](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)，並指定場景元件的 [世界轉換] 作為用於 AR Pin 的世界轉換。
    * Unreal 會使用 AR Pin 來追蹤應用程式空間中的 AR 點，其用來建立 Azure Spatial Anchors。 在 Unreal 中，AR Pin 類似於 HoloLens 上的空間錨點。

![連線至釘選元件函式之場景元件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. 使用新建立的 AR Pin 呼叫 [建立雲端錨點]。
    * 「建立雲端錨點」會在本機建立 Azure Spatial Anchors，但不在 Azure Spatial Anchors 服務中。 在透過服務建立 Azure Spatial Anchors 之前，可以設定 Azure Spatial Anchors 的參數 (例如到期日)。

![釘選元件函式連線至會傳回 ARPin 的建立雲端錨點函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. 設定 Azure Spatial Anchors 到期。 此函式的 Lifetime 參數可讓開發人員以秒為單位指定服務應維護錨點的時間長度。
    * 例如，為期一週的到期日會採用 60秒 x 60 分鐘 x 24 小時 x 7 天 = 604,800 秒的值。

![雲端錨點連線至設定到期函式 (存留期值設定為 604,800 秒) 的藍圖](images/asa-unreal/unreal-spatial-anchors-img-13.png)

設定錨點參數之後，請將錨點宣告為準備好儲存。 在下列範例中，新建立的 Azure Spatial Anchors 會新增至需要儲存的一組 Azure Spatial Anchors。 此集合會宣告為 Pawn 藍圖的變數。

![錨點已準備好要儲存在設定變數中的藍圖](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>儲存錨點

使用您的參數設定 Azure Spatial Anchors 之後，請呼叫 [儲存雲端錨點]。 「儲存雲端錨點」會對 Azure Spatial Anchors 服務宣告錨點。 當「儲存雲端錨點」的呼叫成功時，Azure Spatial Anchors 可供 Azure Spatial Anchors 服務的其他使用者使用。  

![呼叫的儲存雲端錨點函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> 「儲存雲端錨點」是非同步函式，只能在遊戲執行緒事件 (例如 **EventTick**) 上呼叫。 「儲存雲端錨點」可能不會顯示為自訂藍圖函式中可用的藍圖函式。 不過，其應可在 Pawn 事件圖形藍圖編輯器中使用。

在下列範例中，Azure Spatial Anchors 會在輸入事件回呼期間儲存在集合中。 然後錨點會儲存在 EventTick 上。 視您的 Azure Spatial Anchors 工作階段所建立的空間資料量而定，儲存 Azure Spatial Anchors 可能會進行多次嘗試。 這就是為何檢查儲存呼叫是否成功是個好主意。

若未儲存錨點，請將其重新新增至仍需要儲存的錨點集合。 未來的 EventTicks 會繼續嘗試儲存錨點，直到成功儲存為止。

![未儲存的錨點再次儲存到設定變數中的藍圖](images/asa-unreal/unreal-spatial-anchors-img-16.png)

儲存錨點後，AR Pin 的轉換可作為參考轉換，以便將內容放在您的應用程式中。 其他使用者可以偵測此錨點，並針對實體世界中的不同裝置對齊 AR 內容。

## <a name="deleting-an-anchor"></a>刪除錨點

您可藉由呼叫 [刪除雲端錨點]，從 Azure Spatial Anchors 服務刪除錨點。

![呼叫的刪除雲端錨點函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> 「刪除雲端錨點」是潛伏的函式，只能在遊戲執行緒事件 (例如 EventTick) 上呼叫。 「刪除雲端錨點」可能不會顯示為自訂藍圖函式中可用的藍圖函式。 不過，其應可在 Pawn 事件圖形藍圖編輯器中使用。

在下列範例中，錨點會在自訂輸入事件上標示要刪除。 然後會在 EventTick 上嘗試刪除。 如果錨點刪除失敗，請將 Azure Spatial Anchors 新增至標示要刪除的錨點集合，然後在稍後的 EventTick 上再次嘗試。

您的事件圖形藍圖現在看起來應該類似下列螢幕擷取畫面：

![用來處理雲端錨點的完整事件圖形的藍圖](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>尋找既有的錨點

具有 Azure Spatial Anchors 服務的對等節點可以建立現有的錨點：

1. 針對您想要偵測的錨點，取得 Azure Spatial Anchors 識別碼。
    * 在先前的 Azure Spatial Anchors 工作階段中，可以為相同裝置所建立的錨點取得錨點識別碼。 其也可透過與 Azure Spatial Anchors 服務互動的對等裝置來建立及共用。

![使用取得 Azure 雲端識別碼函式的儲存 Azure Spatial Anchors 識別碼自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. 將 **AzureSpatialAnchorsEvent** 元件新增至您的 Pawn 藍圖。
    * 此元件可讓您訂閱各種 Azure Spatial Anchors 事件，例如找到 Azure Spatial Anchors 時所呼叫的事件。

![在藍圖編輯器中開啟 BP_Pawn，且已開啟元件和詳細資料面板的螢幕擷取畫面](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. 針對 [AzureSpatialAnchorsEvent] 元件訂閱 [ASAAnchor 找出的委派]。
    * 委派可讓應用程式知道何時找到與 Azure Spatial Anchors 帳戶相關聯的新錨點。
    * 透過事件回呼，使用 Azure Spatial Anchors 工作階段所建立對等節點的 Azure Spatial Anchors，預設不會建立 AR Pin。 若要為偵測到的 Azure Spatial Anchors 建立 AR Pin，開發人員可以呼叫 [建立以 Azure Cloud Spatial Anchors 為主的 ARPin]。

![開始播放事件連線至 ASAAnchor 找出的委派的藍圖](images/asa-unreal/unreal-spatial-anchors-img-20.png)

若要使用 Azure Spatial Anchors 服務找出對等節點所建立的 Azure Spatial Anchors，應用程式必須建立 [Azure Spatial Anchors 監看員]：
1. 檢查 Azure Spatial Anchors 工作階段是否正在執行。
2. 建立 **AzureSpatialAnchorsLocateCriteria**。
    * 您可以指定各種位置參數，例如與使用者的距離或與另一個錨點的距離。
3. 在 **AzureSpatialAnchorsLocateCritieria** 中宣告您所尋找的 Azure Spatial Anchor 識別碼。
4. 呼叫 [建立監看員]。

![啟動 Azure Spatial Anchors 監看員自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-21.png)

應用程式現在會開始尋找 Azure Spatial Anchors 服務已知的 Azure Spatial Anchors，這表示使用者可以找出其對等節點所建立的 Azure Spatial Anchors。

找出 Azure Spatial Anchor 之後，請呼叫 [停止監看員] 以停止 Azure Spatial Anchors 監看員並清除監看員資源。

![呼叫停止監看員函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-22.png)

您的最終事件圖形藍圖現在看起來應該類似下列螢幕擷取畫面：

![用來處理錨點委派事件的完整事件圖形的藍圖](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊： 

> [!div class="nextstepaction"]
> [空間對應](unreal-spatial-mapping.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。


## <a name="next-steps"></a>接下來的步驟
* [本機空間錨點](unreal-spatial-anchors.md)
* [空間錨點文件](https://docs.microsoft.com/azure/spatial-anchors/)
* [空間錨點功能](https://azure.microsoft.com/services/spatial-anchors/#features)
* [有效的錨點體驗指導方針](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)