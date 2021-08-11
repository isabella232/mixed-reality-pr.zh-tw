---
title: 感知模擬
description: 使用認知模擬程式庫將沉浸式應用程式的模擬輸入自動化的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens、模擬、測試
ms.openlocfilehash: 8d2999868bfdcf67c1174209566e67fe937005946ef82dd50337d9098c1e1971
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193768"
---
# <a name="perception-simulation"></a>感知模擬

您是否要為您的應用程式建立自動化測試？ 您是否想要讓您的測試超越元件層級的單元測試，並讓您的應用程式端對端實際執行？ 認知模擬就是您要尋找的內容。 認知模擬程式庫會將人類和世界的輸入資料傳送到您的應用程式，以便讓您的測試自動化。 例如，您可以模擬人們的輸入，查看特定、可重複的位置，然後使用手勢或移動控制器。

認知模擬可將如下所示的模擬輸入傳送給實體 HoloLens、HoloLens 模擬器 (第一代) 、HoloLens 2 Emulator 或已安裝混合實境入口的電腦。 認知模擬會略過混合現實裝置上的即時感應器，並將模擬的輸入傳送給裝置上執行的應用程式。 應用程式會透過其一律使用的相同 Api 來接收這些輸入事件，而且無法分辨與實際感應器的執行與認知模擬之間的差異。 認知模擬是 HoloLens 模擬器用來將模擬的輸入傳送至 HoloLens 虛擬機器的相同技術。

若要開始在程式碼中使用模擬，請先建立 IPerceptionSimulationManager 物件。 您可以從該物件發出命令，以控制模擬「人」的屬性，包括頭部位置、手形位置和手勢。 您也可以啟用和操作移動控制器。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>設定感知模擬的 Visual Studio Project
1. 在您的開發電腦上[安裝 HoloLens 模擬器](../install-the-tools.md)。 模擬器包含您用來感知模擬的程式庫。
2. 建立新的 Visual Studio c # 桌面專案 (主控台 Project 非常適合開始) 。
3. 將下列二進位檔新增至您的專案，做為參考 (Project >的 [新增 >參考 ...] ) 。您可以在% ProgramFiles (x86) % \ microsoft XDE \\ (版本) 中找到它們，例如 () 的 **% ProgramFiles HoloLens 2 x86 Emulator% \ microsoft XDE \\ 10.0.18362.0** 。   (注意：雖然二進位檔是 HoloLens 2 Emulator 的一部分，但它們也適用于桌面上的 Windows Mixed Reality。 ) a。 用於感知模擬的 PerceptionSimulationManager.Interop.dll 受控 c # 包裝函式。
    b. PerceptionSimulationRest.dll 程式庫，用來設定 HoloLens 或模擬器的 web 通訊端通道。
    c. SimulationStream.Interop.dll-用於模擬的共用類型。
4. 將「執行二進位 PerceptionSimulationManager.dll」新增至您的專案 a。 首先，將它新增為專案的二進位檔 (Project >加入 >現有專案 ... ) 。將它儲存為連結，讓它不會將它複製到您的專案源資料夾。 ![將 PerceptionSimulationManager.dll 新增至專案做為連結 ](images/saveaslink.png) b。 然後，請確定它會複製到組建上的輸出檔案夾中。 這是在二進位檔的屬性工作表中。 ![標示 PerceptionSimulationManager.dll 複製到輸出目錄](images/copyalways.png)
5. 將使用中的方案平臺設定為 x64。   (使用設定管理員來建立 x64 的平臺專案（如果尚不存在的話）。 ) 

## <a name="creating-an-iperceptionsimulation-manager-object"></a>建立 IPerceptionSimulation 管理員物件

若要控制模擬，您要對從 IPerceptionSimulationManager 物件取出的物件發出更新。 第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。 您可以按一下[工具列](using-the-hololens-emulator.md)中的裝置入口網站按鈕，取得模擬器的 IP 位址

![開啟裝置入口網站圖示 ](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。  針對 Windows Mixed Reality，可在設定應用程式中，于 [更新 & 安全性] 下抓取，然後在 [啟用裝置入口網站] 下的 [連線使用：] 區段中，取得「適用于開發人員」。  請務必記下 IP 位址和埠。

首先，您會呼叫 RestSimulationStreamSink 來取得 RestSimulationStreamSink 物件。 這是您將透過 HTTP 連接控制的目標裝置或模擬器。 您的命令將會傳遞至裝置或模擬器上執行的[Windows 裝置入口網站](using-the-windows-device-portal.md)，並由其處理。 建立物件所需的四個參數如下：
* Uri uri-目標裝置的 IP 位址 (例如 " https://123.123.123.123 &quot; 或 &quot; https://123.123.123.123:50080 " ) 
* NetworkCredential 認證-用來連接到目標裝置或模擬器上[Windows 裝置入口網站](using-the-windows-device-portal.md)的使用者名稱/密碼。 如果您是透過本機位址連接到模擬器 (例如，168。*.*.* ) 在同一部電腦上，將會接受任何認證。
* bool 標準-True 表示正常優先順序，false 表示低優先順序。 您通常會想要在測試案例中將此設為 *true* ，以允許您的測試取得控制權。  模擬器與 Windows Mixed Reality 模擬會使用低優先順序的連接。  如果您的測試也會使用低優先順序的連接，則最近建立的連接將會受到控制。
* CancellationToken token-Token，以取消非同步作業。

其次，您將建立 IPerceptionSimulationManager。 這是您用來控制模擬的物件。 這也必須在非同步方法中完成。

## <a name="control-the-simulated-human"></a>控制模擬的人

IPerceptionSimulationManager 具有會傳回 ISimulatedHuman 物件的人類屬性。 若要控制模擬的人，請在此物件上執行作業。 例如：

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>基本的 c # 主控台應用程式範例

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>擴充的範例 c # 主控台應用程式

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>6 DOF 控制器上的附注

在模擬的 6 DOF 控制器上呼叫方法上的任何屬性之前，您必須先啟用控制器。  若未這麼做，將會導致例外狀況。  從 Windows 10 2019 年5月更新開始，只要將 ISimulatedSixDofController 物件的 Status 屬性設為 SimulatedSixDofControllerStatus，就可以安裝和啟用模擬的 DOF 控制器。
在 Windows 10 2018 年10月更新及更早的版本中，您必須先呼叫 PerceptionSimulationDevice 工具（位於 \ Windows \System32 資料夾）來個別安裝模擬的 6 DOF 控制器。  這項工具的使用方式如下：


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

例如：

```
    PerceptionSimulationDevice.exe i 6dof 1
```

支援的動作包括：
* i = 安裝
* q = 查詢
* r = 移除

支援的實例如下：
* 1 = 左方 6 DOF 控制器
* 2 = 右邊的 6 DOF 控制器

進程的結束代碼會指出成功 (零傳回值) 或失敗 (非零傳回值) 。  使用 ' q ' 動作來查詢是否已安裝控制器時，如果尚未安裝控制器，則傳回值會是零 (0) ，如果控制器已安裝則為 1 (1) 。

移除 Windows 10 2018 年10月更新或更早版本上的控制器時，請先透過 API 將其狀態設定為 Off，然後再呼叫 PerceptionSimulationDevice 工具。

此工具必須以系統管理員身分執行。




## <a name="api-reference"></a>API 參照

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>PerceptionSimulation. SimulatedDeviceType

描述模擬裝置類型

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**PerceptionSimulation. SimulatedDeviceType 參考**

虛構的參考裝置，預設值為 PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>PerceptionSimulation. HeadTrackerMode

描述 head 追蹤器模式

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**PerceptionSimulation. HeadTrackerMode. 預設值**

預設標頭追蹤。 這表示系統可能會根據執行時間條件來選取最佳的標頭追蹤模式。

**PerceptionSimulation. HeadTrackerMode 的方向**

僅限方向的標頭追蹤。 這表示追蹤的位置可能不可靠，而且某些相依于 head 位置的功能可能無法使用。

**PerceptionSimulation. HeadTrackerMode. Position**

位置標頭追蹤。 這表示追蹤的標頭位置和方向都是可靠的

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>PerceptionSimulation. SimulatedGesture

描述模擬的手勢

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**PerceptionSimulation. SimulatedGesture. None**

用來表示沒有手勢的 sentinel 值。

**PerceptionSimulation. SimulatedGesture. FingerPressed**

以手指按的手勢。

**PerceptionSimulation. SimulatedGesture. FingerReleased**

手指放開手勢。

**PerceptionSimulation. SimulatedGesture 首頁**

Home/system 手勢。

**PerceptionSimulation. SimulatedGesture. Max**

有效手勢的最大值。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>PerceptionSimulation. SimulatedSixDofControllerStatus

模擬 6 DOF 控制器的可能狀態。

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**PerceptionSimulation. SimulatedSixDofControllerStatus. Off**

6 DOF 控制器已關閉。

**PerceptionSimulation. SimulatedSixDofControllerStatus. Active**

已開啟並追蹤6個 DOF 控制器。

**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

6 DOF 控制器已開啟，但無法追蹤。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>PerceptionSimulation. SimulatedSixDofControllerButton

模擬的 6 DOF 控制器上支援的按鈕。

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**PerceptionSimulation. SimulatedSixDofControllerButton. None**

用來指出沒有按鈕的 sentinel 值。

**PerceptionSimulation. SimulatedSixDofControllerButton 首頁**

[首頁] 按鈕已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton 功能表**

已按下功能表按鈕。

**PerceptionSimulation. SimulatedSixDofControllerButton**

按下 [握住] 按鈕。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

已按下觸控板。

**PerceptionSimulation. SimulatedSixDofControllerButton. Select**

已按下 [選取] 按鈕。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

觸碰觸控板。

**PerceptionSimulation. SimulatedSixDofControllerButton**

已按下操縱杆。

**PerceptionSimulation. SimulatedSixDofControllerButton. Max**

有效的最大按鈕。


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>PerceptionSimulation. SimulatedEyesCalibrationState

模擬眼睛的校正狀態

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**PerceptionSimulation. SimulatedEyesCalibrationState. 無法使用**

無法使用眼睛校正。

**PerceptionSimulation. SimulatedEyesCalibrationState. Ready**

眼睛已經過校正。  這是預設值。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Config是**

正在校正眼睛。

**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

需要校正眼睛。

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>PerceptionSimulation. SimulatedHandJointTrackingAccuracy

手邊的追蹤準確度。

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 無法使用**

未追蹤聯合。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy 近似值**

會推斷聯合位置。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy 可見**

聯合已完全追蹤。

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>PerceptionSimulation. SimulatedHandPose

手邊的追蹤準確度。

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**PerceptionSimulation. SimulatedHandPose. 關閉**

手形的手指設定為反映封閉的姿勢。

**PerceptionSimulation. SimulatedHandPose. Open**

手形的手指設定為反映開放式姿勢。

**PerceptionSimulation. SimulatedHandPose. Point**

手形的手指會設定為反映指標姿勢。

**PerceptionSimulation. SimulatedHandPose**

手形的手指設定為反映捏合姿勢。

**PerceptionSimulation. SimulatedHandPose. Max**

SimulatedHandPose 的最大有效值。


### <a name="microsoftperceptionsimulationplaybackstate"></a>PerceptionSimulation. PlaybackState

描述播放的狀態。

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**PerceptionSimulation. PlaybackState. 已停止**

錄製目前已停止並可供播放。

**PerceptionSimulation. PlaybackState. 播放**

錄製現正播放中。

**PerceptionSimulation. PlaybackState. 暫停**

錄製目前已暫停。

**PerceptionSimulation. PlaybackState. End**

錄製已到達結尾。

### <a name="microsoftperceptionsimulationvector3"></a>PerceptionSimulation. Vector3

描述三個元件向量，可能會描述3D 空間中的點或向量。

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**PerceptionSimulation. Vector3. X**

此向量的 X 元件。

**PerceptionSimulation. Vector3. Y**

此向量的 Y 元件。

**PerceptionSimulation. Vector3. Z**

此向量的 Z 元件。

**PerceptionSimulation. Vector3. #ctor (system.string、system. single)**

建立新的 Vector3。

參數
* x-向量的 x 元件。
* y-向量的 y 元件。
* z-向量的 z 元件。

### <a name="microsoftperceptionsimulationrotation3"></a>PerceptionSimulation. Rotation3

描述三個元件旋轉。

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**PerceptionSimulation. Rotation3**

旋轉的音調元件，圍繞 X 軸。

**PerceptionSimulation. Rotation3. 偏擺**

旋轉的偏擺元件，位於 Y 軸的右方。

**PerceptionSimulation. Rotation3。**

旋轉的變換元件，位於 Z 軸的右方。

**PerceptionSimulation. Rotation3. #ctor (system.string、system. single)**

建立新的 Rotation3。

參數
* 音調-旋轉的音調部分。
* 偏擺-旋轉的偏擺元件。
* 向前復原：旋轉的變換元件。

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>PerceptionSimulation. SimulatedHandJointConfiguration

描述模擬手上的聯合設定。

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**PerceptionSimulation. SimulatedHandJointConfiguration. Position**

聯合的位置。

**PerceptionSimulation. SimulatedHandJointConfiguration. 旋轉**

聯合的旋轉。

**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**

聯合的追蹤精確度。


### <a name="microsoftperceptionsimulationfrustum"></a>PerceptionSimulation

描述圖的視圖（像是相機一般使用的）。

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**PerceptionSimulation，Near**

包含在截量中的最小距離。

**PerceptionSimulation 到目前為止**

包含在錐中的最大距離。

**PerceptionSimulation. FieldOfView**

以弧度為單位之視圖的水準欄位， (小於 PI) 。

**PerceptionSimulation. AspectRatio**

水準欄位對視圖的水準對齊比例。

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>PerceptionSimulation. SimulatedDisplayConfiguration

描述模擬耳機顯示器的設定。

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**

從頭部中央到左方的轉換，以利身歷聲轉譯的用途。

**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**

針對身歷聲轉譯用途的左方旋轉。

**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**

從頭部中心到右邊的轉換，以提供身歷聲轉譯的目的。

**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**

適用于身歷聲轉譯用途的正確眼睛旋轉。

**PerceptionSimulation. SimulatedDisplayConfiguration Ipd**

系統回報的 Ipd 值，用於身歷聲轉譯。

**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**

是否應將提供給左和右眼睛轉換的值視為有效，並套用至執行中的系統。

**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**

是否應將為 Ipd 提供的值視為有效，並套用到執行中的系統。


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>PerceptionSimulation. IPerceptionSimulationManager

用來產生用來控制裝置的封包的根目錄。

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**PerceptionSimulation. IPerceptionSimulationManager 裝置**

取出模擬的裝置物件，以解讀模擬的人類和模擬的世界。

**PerceptionSimulation. IPerceptionSimulationManager 人類**

取出控制模擬人類的物件。

**PerceptionSimulation. IPerceptionSimulationManager 重設**

將模擬重設為其預設狀態。

### <a name="microsoftperceptionsimulationisimulateddevice"></a>PerceptionSimulation. ISimulatedDevice

描述裝置的介面，該裝置會解釋模擬的世界和模擬的人類

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**PerceptionSimulation. ISimulatedDevice. HeadTracker**

從模擬裝置取出 Head 追蹤器。

**PerceptionSimulation. ISimulatedDevice. HandTracker**

從模擬裝置取出手形追蹤程式。

**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**

設定模擬裝置的屬性，使其符合提供的裝置類型。

參數
* 類型-模擬裝置的新類型

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>PerceptionSimulation. ISimulatedDevice2

將 ISimulatedDevice 轉換成 ISimulatedDevice2，即可使用其他屬性

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**

取得或設定模擬的人是否主動佩戴耳機。

**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**

取得或設定模擬顯示的屬性。

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>PerceptionSimulation. ISimulatedHeadTracker

描述模擬的裝置部分的介面，該部分會追蹤模擬人類的標頭。

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**

抓取並設定目前的 head 追蹤器模式。

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>PerceptionSimulation. ISimulatedHandTracker

描述模擬的裝置部分的介面，以追蹤模擬人類的手

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

以計量表的關聯性抓取節點的位置。

**PerceptionSimulation. ISimulatedHandTracker. Position**

取得和設定模擬的手追蹤器相對於 head 中央的位置。

**PerceptionSimulation. ISimulatedHandTracker**

取出模擬的手追蹤器，並將其設定為向下。

**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**

取得並設定是否忽略模擬的手追蹤器的截量。 略過時，一律會顯示這兩個手。 未略過時 (預設) 手只會在其位於 [手形追蹤器] 的 [截量] 中時才會顯示。

**PerceptionSimulation. ISimulatedHandTracker**

取出並設定用來判斷模擬的手追蹤器是否可以看到手的錐屬性。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>PerceptionSimulation. ISimulatedHuman

控制模擬人類的最上層介面。

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**PerceptionSimulation. ISimulatedHuman. WorldPosition**

取得和設定與世界相關之節點的位置（以計量為單位）。 位置會對應到人類的點中央。

**PerceptionSimulation. ISimulatedHuman. Direction**

取得並設定模擬的人臉在世界中的方向。 0弧度會朝下負 Z 軸。 正弧度旋轉 Y 軸的順時針旋轉。

**PerceptionSimulation. ISimulatedHuman. Height**

取得和設定模擬人類的高度（以計量為單位）。

**PerceptionSimulation. ISimulatedHuman. LeftHand**

取出模擬人類的左邊。

**PerceptionSimulation. ISimulatedHuman. RightHand**

取出模擬人類的右手邊。

**PerceptionSimulation. ISimulatedHuman Head**

取出模擬人類的標頭。

**PerceptionSimulation. ISimulatedHuman. Move (PerceptionSimulation. Vector3)**

將模擬的人移至其目前位置（以計量為單位）。

參數
* 轉譯-要移動的轉譯（相對於目前的位置）。

**PerceptionSimulation. ISimulatedHuman. (System.object 旋轉)**

以順時針方向對 Y 軸旋轉模擬的人，相對於其目前方向

參數
* 弧度-繞著 Y 軸旋轉的量。

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>PerceptionSimulation. ISimulatedHuman2

將 ISimulatedHuman 轉換成 ISimulatedHuman2，即可使用其他屬性

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**PerceptionSimulation. ISimulatedHuman2. LeftController**

取出左方 6 DOF 控制器。

**PerceptionSimulation. ISimulatedHuman2. RightController**

取出右邊的 6 DOF 控制器。


### <a name="microsoftperceptionsimulationisimulatedhand"></a>PerceptionSimulation. ISimulatedHand

描述模擬人手的介面

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**PerceptionSimulation. ISimulatedHand. WorldPosition**

以計量表的關聯性抓取節點的位置。

**PerceptionSimulation. ISimulatedHand. Position**

取得和設定模擬手相對於人類的位置，以量表為單位。

**PerceptionSimulation. ISimulatedHand。已啟用**

取得並設定是否目前已啟用手形。

**PerceptionSimulation. ISimulatedHand 可見**

取出 >simulateddevice 的目前是否看得到手 (也就是，是否在 HandTracker) 偵測到位置。

**PerceptionSimulation. ISimulatedHand. EnsureVisible**

將手上移，讓 >simulateddevice 可以看到它。

**PerceptionSimulation. ISimulatedHand. Move (PerceptionSimulation. Vector3)**

移動模擬手相對於其目前位置的位置（以計量為單位）。

參數
* 轉譯-要轉譯模擬手的數量。

**PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**

使用模擬的手勢來執行筆勢。  只有在已啟用手形的情況下，系統才會偵測到此情況。

參數
* 手勢-要執行的手勢。

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>PerceptionSimulation. ISimulatedHand2

將 ISimulatedHand 轉換成 ISimulatedHand2，即可使用其他屬性。
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**PerceptionSimulation. ISimulatedHand2 的方向**

取出或設定模擬手的旋轉。  當您沿著軸旋轉時，正弧度會順時針旋轉。

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>PerceptionSimulation. ISimulatedHand3

將 ISimulatedHand 轉換成 ISimulatedHand3，即可使用其他屬性
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

取得指定聯合的聯合設定。

**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

設定指定之聯合的聯合設定。

**PerceptionSimulation. ISimulatedHand3. SetHandPose**

使用選擇性旗標將手設為已知的姿勢，以建立動畫。  注意：動畫並不會立即反映其最終的聯合設定。


### <a name="microsoftperceptionsimulationisimulatedhead"></a>PerceptionSimulation. ISimulatedHead

描述模擬人類標頭的介面。

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**PerceptionSimulation. ISimulatedHead. WorldPosition**

以計量表的關聯性抓取節點的位置。

**PerceptionSimulation. ISimulatedHead. 旋轉**

取出模擬標頭的旋轉。 當您沿著軸旋轉時，正弧度會順時針旋轉。

**PerceptionSimulation. ISimulatedHead. 直徑**

取出模擬的標頭直徑。 此值可用來判斷旋轉) 的前端 (點。

**PerceptionSimulation. ISimulatedHead (PerceptionSimulation. Rotation3)**

將模擬的標頭相對於其目前的旋轉旋轉。 當您沿著軸旋轉時，正弧度會順時針旋轉。

參數
* 旋轉-要旋轉的量。

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>PerceptionSimulation. ISimulatedHead2

將 ISimulatedHead 轉換成 ISimulatedHead2，即可使用其他屬性

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**PerceptionSimulation. ISimulatedHead2 眼睛**

取出模擬人類的眼睛。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>PerceptionSimulation. ISimulatedSixDofController

描述與模擬人類相關聯之 6 DOF 控制器的介面。

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

以計量表的關聯性抓取節點的位置。

**PerceptionSimulation. ISimulatedSixDofController。狀態**

取得或設定控制器的目前狀態。  控制器狀態必須設定為 [關閉] 以外的值，才能讓任何移動、旋轉或按下按鈕的動作都成功。

**PerceptionSimulation. ISimulatedSixDofController. Position**

取得或設定模擬控制器相對於人類的位置（以計量為單位）。

**PerceptionSimulation. ISimulatedSixDofController 的方向**

取得或設定模擬控制器的方向。

**PerceptionSimulation. ISimulatedSixDofController. Move (PerceptionSimulation. Vector3)**

移動模擬控制器相對於其目前位置的位置（以計量為單位）。

參數
* 轉譯-要轉譯模擬控制器的數量。

**PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**

按下模擬控制器上的按鈕。  只有在已啟用控制器的情況下，系統才會偵測到此情況。

參數
* 按鈕-要按的按鈕。

**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**

釋放模擬控制器上的按鈕。  只有在已啟用控制器的情況下，系統才會偵測到此情況。

參數
* 按鈕-要釋放的按鈕。

**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float，out float)**

取得模擬控制器的觸控板上模擬手指的位置。

參數
* x-指手指的水準位置。
* y-指手指的垂直位置。

**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float，float)**

在模擬控制器的觸控板上設定模擬手指的位置。

參數
* x-指手指的水準位置。
* y-指手指的垂直位置。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>PerceptionSimulation. ISimulatedSixDofController2

將 ISimulatedSixDofController 轉換成 ISimulatedSixDofController2，即可使用其他屬性和方法

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float，out float)**

取得模擬控制器上模擬之操縱杆的位置。

參數
* x-操縱杆的水準位置。
* y-操縱杆的垂直位置。

**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float，float)**

設定模擬控制器上模擬之操縱杆的位置。

參數
* x-操縱杆的水準位置。
* y-操縱杆的垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

取得或設定模擬控制器的電池音量。  值必須大於0.0 且小於或等於100.0。


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>PerceptionSimulation. ISimulatedEyes

描述模擬人類眼睛的介面。

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**PerceptionSimulation. ISimulatedEyes. 旋轉**

取出模擬眼睛的旋轉。 當您沿著軸旋轉時，正弧度會順時針旋轉。

**PerceptionSimulation. ISimulatedEyes (PerceptionSimulation. Rotation3)**

相對於目前的旋轉旋轉模擬眼睛。 當您沿著軸旋轉時，正弧度會順時針旋轉。

參數
* 旋轉-要旋轉的量。

**PerceptionSimulation. ISimulatedEyes. CalibrationState**

抓取或設定模擬眼睛的校正狀態。

**PerceptionSimulation. ISimulatedEyes. WorldPosition**

以計量表的關聯性抓取節點的位置。


### <a name="microsoftperceptionsimulationisimulationrecording"></a>PerceptionSimulation. ISimulationRecording

用來與載入以播放的單一錄製互動的介面。

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**PerceptionSimulation. ISimulationRecording 資料類型**

抓取錄製中的資料類型清單。

**PerceptionSimulation. ISimulationRecording. 州**

捕獲錄製的目前狀態。

**PerceptionSimulation. ISimulationRecording. Play**

開始播放。 如果錄製暫停，播放將從暫停的位置繼續;如果已停止，播放會從一開始開始。 如果已經在播放，則會忽略此呼叫。

**PerceptionSimulation. ISimulationRecording. Pause**

在目前的位置暫停播放。 如果記錄已停止，則會忽略呼叫。

**PerceptionSimulation. ISimulationRecording. Seek (System.object)**

搜尋指定時間的記錄 (從開始) 的 100-毫微秒間隔，然後在該位置暫停。 如果時間超過錄製的結尾，則會在最後一個畫面上暫停。

參數
* 刻度-要搜尋的時間。

**PerceptionSimulation. ISimulationRecording. Stop**

停止播放，並將位置重設為開頭。

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>PerceptionSimulation. ISimulationRecordingCallback

在播放期間接收狀態變更的介面。

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**

在 ISimulationRecording 的播放狀態變更時呼叫。

參數
* newState-錄製的新狀態。

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>PerceptionSimulation. PerceptionSimulationManager

用來建立感知模擬物件的根物件。

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**

在物件上建立以產生模擬的封包，並將其傳遞至提供的接收。

參數
* 接收-將接收所有產生的封包的接收。

傳回值

建立的管理員。

**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**

建立接收，以將所有收到的封包儲存在指定路徑的檔案中。

參數
* 路徑-要建立之檔案的路徑。

傳回值

建立的接收。

**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string，PerceptionSimulation. ISimulationStreamSinkFactory)**

從指定的檔案載入錄製。

參數
* 路徑-要載入之檔案的路徑。
* factory-記錄用來在必要時建立 ISimulationStreamSink 的 factory。

傳回值

載入的記錄。

**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string、PerceptionSimulation. ISimulationStreamSinkFactory、PerceptionSimulation. ISimulationRecordingCallback)**

從指定的檔案載入錄製。

參數
* 路徑-要載入之檔案的路徑。
* factory-記錄用來在必要時建立 ISimulationStreamSink 的 factory。
* 回呼-回呼，可接收更新 regrading 記錄的狀態。

傳回值

載入的記錄。

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>PerceptionSimulation. StreamDataTypes

描述不同類型的資料流程資料。

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**PerceptionSimulation. StreamDataTypes. None**

用來指出沒有資料流程資料類型的 sentinel 值。

**PerceptionSimulation. StreamDataTypes Head**

標頭的位置和方向的資料流程。

**PerceptionSimulation. StreamDataTypes**

資料串流以取得手的位置和手勢。

**PerceptionSimulation. StreamDataTypes. SpatialMapping**

環境的空間對應資料串流。

**PerceptionSimulation. StreamDataTypes. 校正**

用於校正裝置的資料流程。 只有在遠端模式的系統才會接受校正封包。

**PerceptionSimulation. StreamDataTypes. 環境**

裝置環境的資料流程。

**PerceptionSimulation. StreamDataTypes. SixDofControllers**

動作控制器的資料流程。

**PerceptionSimulation. StreamDataTypes 眼睛**

以模擬人類的眼睛來串流資料。

**PerceptionSimulation. StreamDataTypes. DisplayConfiguration**

以裝置的顯示設定來串流資料。

**PerceptionSimulation. StreamDataTypes**

用來表示所有記錄資料類型的 sentinel 值。

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>PerceptionSimulation. ISimulationStreamSink

物件，這個物件會接收來自模擬資料流程的資料封包。

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint length，byte [] 封包)**

接收在內部輸入和建立版本的單一封包。

參數
* 長度-封包的長度。
* 封包-封包的資料。

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>PerceptionSimulation. ISimulationStreamSinkFactory

建立 ISimulationStreamSink 的物件。

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**

建立 ISimulationStreamSink 的單一實例。

傳回值

建立的接收。
