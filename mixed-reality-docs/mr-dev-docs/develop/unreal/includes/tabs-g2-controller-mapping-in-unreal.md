---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204197"
---
# <a name="all-platforms"></a>[所有平台](#tab/all)

您可以從 c + + 使用遊戲輸入專案設定中的相同動作和軸對應。

1. 使用 File/New c + + 類別建立新的 c + + 類別 .。。

![建立新的 c + + 類別](../images/reverb-g2-img-11.png)

2. 建立卒

![建立卒](../images/reverb-g2-img-12.png)

3. 在專案的 Visual Studio 方案中，找出新的卒類別，並將它設定為輸入。
* 首先，在函式中，將 AutoPossessPlayer 設定為第一個播放機，以將輸入路由至卒。

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* 然後，在 SetupPlayerInputComponent 中，將動作和軸事件系結至專案輸入設定中的動作名稱。

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* 將回呼函數新增至類別：

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* 以回呼函數定義更新卒的標頭：

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. 從 Visual Studio 編譯，以新的卒啟動編輯器。 將 [內容瀏覽器] 中的 [卒] 拖放到遊戲中，而卒現在會在按下輸入時執行回呼。

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

使用操縱杆軸事件時，軸事件的名稱必須以「_X」或「_Y」結尾，對應于所使用的索引鍵。

![使用操縱杆事件](../images/reverb-g2-img-09.png)

最後，使用 SteamVR 在遊戲中註冊動作，方法是使用 [**重新產生動作資訊清單**]，然後在 Project 設定 > 串流 VR 輸入中 **重新產生控制器** 系結按鈕。

![在專案設定中註冊動作](../images/reverb-g2-img-10.png)

