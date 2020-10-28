---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638636"
---
# <a name="all-platforms"></a>[<span data-ttu-id="48419-101">所有平台</span><span class="sxs-lookup"><span data-stu-id="48419-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="48419-102">您可以從 c + + 使用遊戲輸入專案設定中的相同動作和軸對應。</span><span class="sxs-lookup"><span data-stu-id="48419-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="48419-103">使用 File/New c + + 類別建立新的 c + + 類別 .。。</span><span class="sxs-lookup"><span data-stu-id="48419-103">Create a new C++ Class with File/New C++ Class...</span></span>

![建立新的 c + + 類別](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="48419-105">建立卒</span><span class="sxs-lookup"><span data-stu-id="48419-105">Create a pawn</span></span>

![建立卒](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="48419-107">在專案的 Visual Studio 方案中，找出新的卒類別，並將它設定為輸入。</span><span class="sxs-lookup"><span data-stu-id="48419-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="48419-108">首先，在函式中，將 AutoPossessPlayer 設定為第一個播放機，以將輸入路由至卒。</span><span class="sxs-lookup"><span data-stu-id="48419-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="48419-109">然後，在 SetupPlayerInputComponent 中，將動作和軸事件系結至專案輸入設定中的動作名稱。</span><span class="sxs-lookup"><span data-stu-id="48419-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="48419-110">將回呼函數新增至類別：</span><span class="sxs-lookup"><span data-stu-id="48419-110">Add the callback functions to the class:</span></span>

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

* <span data-ttu-id="48419-111">以回呼函數定義更新卒的標頭：</span><span class="sxs-lookup"><span data-stu-id="48419-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="48419-112">從 Visual Studio 編譯，以新的卒啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="48419-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="48419-113">將 [內容瀏覽器] 中的 [卒] 拖放到遊戲中，而卒現在會在按下輸入時執行回呼。</span><span class="sxs-lookup"><span data-stu-id="48419-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="48419-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="48419-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="48419-115">使用操縱杆軸事件時，軸事件的名稱必須以「_X」或「_Y」結尾，對應于所使用的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="48419-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![使用操縱杆事件](../images/reverb-g2-img-09.png)

<span data-ttu-id="48419-117">最後，使用 SteamVR 在遊戲中註冊動作，方法是使用 [ **重新產生動作資訊清單** ]，然後在專案設定中 **重新產生控制器** 系結按鈕 > 的串流 VR 輸入。</span><span class="sxs-lookup"><span data-stu-id="48419-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![在專案設定中註冊動作](../images/reverb-g2-img-10.png)

