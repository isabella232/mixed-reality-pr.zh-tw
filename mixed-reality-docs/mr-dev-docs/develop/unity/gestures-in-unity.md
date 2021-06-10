---
title: Unity 中的手勢
description: 瞭解如何使用 XR 和一般按鈕和軸 Api，在您的電腦上對您的注視進行手勢動作。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手勢、unity、注視、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 87666c120686547b1a07f6da41519219d4a47720
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600637"
---
# <a name="gestures-in-unity"></a>Unity 中的手勢

您可以透過兩種主要方式，在您 [的 [Unity](gaze-in-unity.md)]、[ [手手勢](../../design/gaze-and-commit.md#composite-gestures) ] 和 [ [運動] 控制器](../../design/motion-controllers.md) 中針對 HoloLens 和沉浸式 HMD 採取行動。 您可以透過 Unity 中的相同 Api，存取兩個空間輸入來源的資料。

Unity 提供兩種主要方式來存取 Windows Mixed Reality 的空間輸入資料。 常見的 *GetButton/GetAxis* api 可跨多個 Unity XR sdk 運作，而 Windows Mixed Reality 特定的 *InteractionManager/GestureRecognizer* api 會公開一組完整的空間輸入資料。

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高層級複合手勢 Api (GestureRecognizer) 

**命名空間：** *UnityEngine. XR。輸入*<br>
**類型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*

您的應用程式也可以辨識空間輸入來源、點擊、按住、操作和導覽手勢的較高層級複合手勢。 您可以使用 GestureRecognizer，跨 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [移動控制器](../../design/motion-controllers.md) 辨識這些複合手勢。

GestureRecognizer 上的每個手勢事件都會提供輸入的 SourceKind，以及事件時的目標 head 光線。 某些事件提供其他內容特定的資訊。

使用手勢辨識器來捕捉手勢時，只需要執行幾個步驟：
1. 建立新的手勢辨識器
2. 指定要監看的手勢
3. 訂閱這些手勢的事件
4. 開始捕獲手勢

### <a name="create-a-new-gesture-recognizer"></a>建立新的手勢辨識器

若要使用 *GestureRecognizer*，您必須建立 *GestureRecognizer*：

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要監看的手勢

透過 *SetRecognizableGestures ()* 指定您感興趣的手勢：

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>訂閱這些手勢的事件

針對您感興趣的手勢訂閱事件。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>導覽和操作手勢在 *GestureRecognizer* 的實例上是互斥的。

### <a name="start-capturing-gestures"></a>開始捕獲手勢

根據預設， *GestureRecognizer* 在呼叫 *StartCapturingGestures ()* 之前不會監視輸入。 如果在處理 *StopCapturingGestures ()* 的框架之前執行輸入，可能會在呼叫 *StopCapturingGestures ()* 後產生手勢事件。 *GestureRecognizer* 會記得在先前的畫面格進行實際發生的情況下，它是開啟或關閉，因此可以根據此框架的監看式目標來開始和停止手勢監視。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕捉手勢

若要停止手勢辨識：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>移除手勢辨識器

請記得在終結 *GestureRecognizer* 物件之前取消訂閱的事件。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>在 Unity 中轉譯移動控制器模型

![移動控制器模型和遙傳](images/motioncontrollertest-teleport-1000px.png)<br>
*移動控制器模型和遙傳*

若要在您的應用程式中轉譯與您的使用者所持有的實體控制器相符的移動控制站，並在按下各種按鈕時表達清楚，您可以在 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/)組中使用 **MotionController 預製專案**。  這個預製專案會從系統已安裝的移動控制器驅動程式，在執行時間動態載入正確的 glTF 模型。  請務必以動態方式載入這些模型，而不是在編輯器中手動匯入這些模型，如此您的應用程式就會針對使用者可能擁有的任何目前和未來控制器顯示實際精確的3D 模型。

1. 遵循 [開始使用](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 指示下載 Mixed Reality 工具組，並將它新增至 Unity 專案。
2. 如果您在開始使用步驟中將相機替換成 *MixedRealityCameraParent* 預製專案，您就可以開始使用！  該預製專案包括移動控制器轉譯。  否則，請從 [專案] 窗格將 *資產/HoloToolkit/Input/Prefabs/MotionControllers* 加入場景中。  當使用者在場景中 teleports 時，您會想要將該預製專案新增為您用來移動攝影機之任何父物件的子系，以便讓控制器與使用者一起使用。  如果您的應用程式不需要 teleporting，只要在場景的根目錄新增預製專案即可。

## <a name="throwing-objects"></a>擲回物件

在虛擬實境中擲回物件，是比一開始可能更困難的問題。 如同大部分的實際互動，在遊戲中擲回時，它會以非預期的方式運作，並中斷深度。 我們花了一些時間來思考如何表示實體正確的擲回行為，並提供一些指導方針，讓我們想要與您分享，並透過我們的平臺更新來啟用。

您可以在 [這裡](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到建議如何執行擲回的範例。 此範例會遵循下列四個指導方針：
* **使用控制器的 *速度* ，而不是位置**。 在 Windows 的11月更新中，我們引進了「 [近似」位置追蹤狀態](../../design/motion-controllers.md#controller-tracking-state)時的行為變更。 處於此狀態時，系統會繼續回報控制器的相關速度資訊，只要我們相信其高精確度，通常會比位置維持高準確度更長。
* **納入控制器的 *角度速度***。 此邏輯全部包含在靜態方法的檔案中，該檔案 `throwing.cs` 位於 `GetThrownObjectVelAngVel` 上述連結的封裝內：
   1. 由於 conserved 的角度速度，擲回的物件必須維持與擲回時相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 因為擲回物件的中央可能不是在底框姿勢的原點，所以它的速度可能與使用者參考框架中控制器的速度不同。 以這種方式產生的物件速度的部分，就是在控制器原點周圍擲回物件的最大中心的瞬間相切速度。 這種相切速度是控制器角度速度的交叉乘積，向量表示控制器原點與擲回物件的中央之間的距離。

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. 擲回之物件的總速度是控制器速度和這個相切速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* 請密切 **注意我們應用速度的 *時間***。 按下按鈕時，該事件最多可能需要20毫秒的時間，才能透過藍牙向上到作業系統。 這表示，如果您輪詢控制器狀態變更，而不是按下的狀態或其他方式，則控制器會引發您所取得的資訊。 此外，我們的輪詢 API 所呈現的控制器會向前預測，以反映畫面上顯示的可能原因，未來可能會超過20毫秒。 這適合用來 *呈現* 保留的物件，但是會在計算使用者釋出擲回的軌跡時，將我們的時間問題轉譯為 *目標* 物件。 幸運的是，在11月更新中，當傳送 *InteractionSourcePressed* 或 *InteractionSourceReleased* 這類 Unity 事件時，狀態包括在按下或放開按鈕時，會從背面提出資料。  若要在擲回期間取得最精確的控制器轉譯和控制器目標，您必須適當地正確地使用輪詢和事件：
   * 針對每個畫面格的 **控制器呈現** ，您的應用程式應該將控制器的 *GameObject* 放在向前預測的控制器上，以表示目前畫面格的 photon 時間。  您可以從 Unity 輪詢 Api （例如 XR）取得此資料 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。Wsa。輸入. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。
   * 針對以按下或放開的 **控制器為目標的控制器** ，您的應用程式應該根據該按下或釋放事件的歷程控制器姿勢來 raycast 和計算軌跡。  您可以從 Unity 事件 Api 取得這類資料，例如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。
* **使用** 底框姿勢。 相對於底框姿勢（而不是指標姿勢）回報角度速度和速度。

未來的 Windows 更新將持續改善擲回，而您可以預期在此找到更多資訊。

## <a name="gesture-and-motion-controllers-in-mrtk"></a>MRTK 中的手勢和移動控制器

您可以從輸入管理員存取手勢和移動控制器。

* [MRTK 中的手勢](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [MRTK 中的動作控制器](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>遵循教學課程

混合現實學術中提供逐步教學課程，包含更詳細的自訂範例：

- [MR Input 211：筆勢](tutorials/holograms-211.md)
- [MR Input 213：運動控制器](../../deprecated/mixed-reality-213.md)

[![MR 輸入 213-移動控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR 輸入 213-移動控制器*

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [手部和眼睛追蹤](./hand-eye-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [頭部目光和行動](../../design/gaze-and-commit.md)
* [運動控制器](../../design/motion-controllers.md)