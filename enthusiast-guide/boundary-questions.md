---
title: 界限常見問題
description: 先進的 Windows Mixed Reality 針對超出標準取用者支援檔的界限問題進行疑難排解。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，疑難排解，錯誤，說明，支援，界限
appliesto:
- Windows 10
ms.openlocfilehash: 9ddf9c7f7c5f36567e6968f619dabead9107731d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174395"
---
# <a name="boundary-faqs"></a>界限常見問題

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>什麼是界限，以及為什麼應該建立一個界限？

界限會定義您可以四處移動的區域，而戴 Windows Mixed Reality 耳機。 請務必建立界限，以協助您避免在耳機中看到的障礙。 界限在混合現實內部看起來像白色外框，當您接近它時，它就會出現。 當您看到它時，會使您的移動變慢，並避免跨越界限或將樹幹延伸至外。

界限內的區域應該是「傢俱」、「低燈燈燈」、「天花板風扇」等等，因此您不會在任何地方進行任何動作。 [瞭解 Windows Mixed Reality 中的健康狀態和安全性](wmr-health-safety-comfort.md)。

## <a name="how-do-i-create-a-boundary"></a>如何? 建立界限？

當您第一次設定耳機時，安裝應用程式 (混合實境入口) 將會引導您完成建立界限的步驟。 但是您可以在任何時間建立一個：

1. 選取您桌面上的 [ **開始] > 混合實境入口** 。
2. 開啟 [功能表]。
3. 選取 [安裝空間界限] 以建立新的界限。

如果有其他人使用您的耳機，請務必瞭解界限，以及其使用方式。 如果您將耳機移至新位置，則必須設定適用于該空間的新界限。

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>當我嘗試建立界限時，出現錯誤訊息

* 建立界限時，請勿太接近牆或其他障礙物。
* 請務必將您的耳機保持在 waist 高度，並在追蹤界限時面對您的電腦。
* 請確定感應器未遭到封鎖，且有足夠的光線。
* 您要追蹤的空間應大於三個正方形計量。
* 空間不應太大或太複雜。 不需要太多訣竅，就能繼續使用簡單的幾何形狀。
* 當您進行追蹤時，請勿交叉回復自己的路徑。
* 如果您卡在角落，請從頭開始。

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>系統找不到界限，而且我會看到安裝程式 UI

這表示追蹤系統無法辨識您的環境。 如果您是在新的環境中，您必須設定 [界限](set-up-windows-mixed-reality.md#set-up-your-room-boundary)。
如果您先前曾在此環境中使用裝置，並設定界限：

* 請確定房間有足夠的光線。
* 請確定您已將裝置磨損，並已查看房間。 裝置必須觀察您的環境，以瞭解其所在位置。 如果它位於桌上或桌上，它就不會找到您的界限。
* 拔掉裝置，關閉 Windows Mixed Reality，然後重新插入。
* 如果環境中的內容已變更，則裝置可能無法再辨識。 設定新的界限。

如果這些步驟無法解決問題，請刪除您的環境資料，然後再次設定界限。

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>系統會向我呈現 UI，要求我針對所有體驗或站上/站選設定，並看到我的範圍

裝置花太多時間找出界限。 您可以藉由選擇使用界限的選項來略過此訊息，系統會將您的界限帶到您的 Windows Mixed Reality home。

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>我經常會看到一則訊息，指出「我已遺失界限」

追蹤系統正在追蹤及識別您的環境。 在此狀態下，裝置不會再顯示您的界限，而耳機會切換至3DOF，讓您能夠上下加減一點到真實世界中的專案，直到它再次找到您的界限為止。 修正方法：

1. 請確定房間有足夠的光線。
2. 如果您最近 redecorated 或改建年份空間，請重新執行安裝程式。
3. 拔掉裝置，關閉 Windows Mixed Reality，然後重新插入。
4. 清除您的環境資料，然後再次設定裝置。
5. 如果訊息持續存在，請洽詢客戶支援。

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>如果找不到我的界限，則會顯示訊息。 我該怎麼辦？

Windows Mixed Reality 可能無法識別您的現有界限。 您可以建立新的界限，也可以在「站上和站上」模式中使用您的裝置。

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>訊息指出「遺失追蹤」或「我們沒有這個空間的界限」

您必須建立新的界限。 若要這樣做：

1. 選取 [ **開始] > 混合實境入口**。
2. 開啟 [功能表]。
3. 選取 [安裝空間界限]。

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>界限一律可見。 如何讓它消失？

當您接近界限時，即會顯示界限。 如果您的界限包含任何具有窄或不規則圖形的區段，您最後可能會接近它，並使其出現，比您想要的還多。 若要修正此問題，請嘗試使用較大且更一般的圖形再次建立您的界限。 若要這樣做：

1. 選取 [ **開始] > 混合實境入口**。
2. 開啟 [功能表]。
3. 選取 [安裝空間界限]。

## <a name="can-i-turn-off-the-boundary-temporarily"></a>可以暫時關閉界限嗎？

* 選取 [ **開始] > 混合實境入口**。
* 開啟 [功能表]。
* 將「界限」變成「關閉」。 當界限關閉時，請務必保持在一個位置。

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何? 在「站上和站內」和「所有體驗」之間做選擇？

如果您在耳機設定或更新版本中選擇 [已待命]，則會在沒有界限的情況下使用耳機。 這表示當您使用耳機時，必須保持在一個位置，如此您就可以避免發生實體障礙並產生風險。 您可以坐在外，但無法四處移動。 請記住，阻礙可能會有額外負荷，也可能會造成您的負擔。

某些應用程式可能是設計來搭配界限使用，因此您可能無法使用它們，如果您不使用界限，則可能不會有相同的體驗。

如果您選擇 [所有體驗]，您將會設定界限，而且能夠使用應用程式和體驗來使用界限以及不需要的體驗。

## <a name="see-also"></a>另請參閱

* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)