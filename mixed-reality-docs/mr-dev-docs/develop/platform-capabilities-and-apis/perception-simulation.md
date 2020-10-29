---
title: 感知模擬
description: 使用認知模擬程式庫將沉浸式應用程式的模擬輸入自動化的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens、模擬、測試
ms.openlocfilehash: d4cd9497f9adcea03ece222f09124ce593ea73cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679928"
---
# <a name="perception-simulation"></a><span data-ttu-id="2d693-104">感知模擬</span><span class="sxs-lookup"><span data-stu-id="2d693-104">Perception simulation</span></span>

<span data-ttu-id="2d693-105">您是否要為您的應用程式建立自動化測試？</span><span class="sxs-lookup"><span data-stu-id="2d693-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="2d693-106">您是否想要讓您的測試超越元件層級的單元測試，並讓您的應用程式端對端實際執行？</span><span class="sxs-lookup"><span data-stu-id="2d693-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="2d693-107">認知模擬就是您要尋找的內容。</span><span class="sxs-lookup"><span data-stu-id="2d693-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="2d693-108">認知模擬程式庫會將人類和世界的輸入資料傳送到您的應用程式，以便讓您的測試自動化。</span><span class="sxs-lookup"><span data-stu-id="2d693-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="2d693-109">例如，您可以模擬人們的輸入，查看特定、可重複的位置，然後執行筆勢或使用移動控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="2d693-110">認知模擬可將這類模擬輸入傳送給實體 HoloLens、HoloLens 模擬器 (第一代) 、HoloLens 2 模擬器或已安裝混合實境入口的電腦。</span><span class="sxs-lookup"><span data-stu-id="2d693-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="2d693-111">認知模擬會略過混合現實裝置上的即時感應器，並將模擬的輸入傳送給裝置上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2d693-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="2d693-112">應用程式會透過其一律使用的相同 Api 來接收這些輸入事件，而且無法分辨與實際感應器執行之間的差異，與使用感知模擬執行之間的差異。</span><span class="sxs-lookup"><span data-stu-id="2d693-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="2d693-113">認知模擬是 HoloLens 模擬器用來將模擬的輸入傳送到 HoloLens 虛擬機器的相同技術。</span><span class="sxs-lookup"><span data-stu-id="2d693-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="2d693-114">若要開始在程式碼中使用模擬，請先建立 IPerceptionSimulationManager 物件。</span><span class="sxs-lookup"><span data-stu-id="2d693-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="2d693-115">您可以從該物件發出命令來控制模擬「人」的屬性，包括標頭位置、手形位置和手勢，也可以啟用和操作移動控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="2d693-116">設定 Visual Studio 專案以進行感知模擬</span><span class="sxs-lookup"><span data-stu-id="2d693-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="2d693-117">在您的開發電腦上[安裝 HoloLens 模擬器](../install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2d693-117">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="2d693-118">模擬器包含您將用於認知模擬的程式庫。</span><span class="sxs-lookup"><span data-stu-id="2d693-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="2d693-119">建立新的 Visual Studio c # 桌面專案 (主控台專案的效果很好，可以開始) 。</span><span class="sxs-lookup"><span data-stu-id="2d693-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="2d693-120">將下列二進位檔新增至您的專案，做為參考 (專案 >的 [新增 >參考 ...] ) 。您可以在% ProgramFiles (x86) % \ Microsoft XDE \\ (版本) 中找到它們，例如 (模擬器的 **% ProgramFiles) x86 HoloLens 2% \ microsoft XDE \\ 10.0.18362.0** 。</span><span class="sxs-lookup"><span data-stu-id="2d693-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="2d693-121"> (注意：雖然二進位檔是 HoloLens 2 模擬器的一部分，但它們也適用于桌面上的 Windows Mixed Reality。 ) a。</span><span class="sxs-lookup"><span data-stu-id="2d693-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="2d693-122">用於感知模擬的 PerceptionSimulationManager.Interop.dll 受控 c # 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="2d693-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="2d693-123">b.</span><span class="sxs-lookup"><span data-stu-id="2d693-123">b.</span></span> <span data-ttu-id="2d693-124">PerceptionSimulationRest.dll 程式庫，可將 web 通訊端通道設定為 HoloLens 或模擬器。</span><span class="sxs-lookup"><span data-stu-id="2d693-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="2d693-125">c.</span><span class="sxs-lookup"><span data-stu-id="2d693-125">c.</span></span> <span data-ttu-id="2d693-126">SimulationStream.Interop.dll-用於模擬的共用類型。</span><span class="sxs-lookup"><span data-stu-id="2d693-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="2d693-127">將「執行二進位 PerceptionSimulationManager.dll」新增至您的專案 a。</span><span class="sxs-lookup"><span data-stu-id="2d693-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="2d693-128">首先，將它新增為專案的二進位檔 (專案 >加入 >現有專案 ... ) 。將它儲存為連結，讓它不會將它複製到您的專案源資料夾。</span><span class="sxs-lookup"><span data-stu-id="2d693-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="2d693-129">![將 PerceptionSimulationManager.dll 新增至專案做為連結 ](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="2d693-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="2d693-130">然後，請確定它會複製到組建上的輸出檔案夾中。</span><span class="sxs-lookup"><span data-stu-id="2d693-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="2d693-131">這是在二進位檔的屬性工作表中。</span><span class="sxs-lookup"><span data-stu-id="2d693-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="2d693-132">![標示 PerceptionSimulationManager.dll 複製到輸出目錄](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="2d693-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="2d693-133">將使用中的方案平臺設定為 x64。</span><span class="sxs-lookup"><span data-stu-id="2d693-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="2d693-134"> (使用 Configuration Manager 來建立 x64 的平臺專案（如果尚不存在的話）。 ) </span><span class="sxs-lookup"><span data-stu-id="2d693-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="2d693-135">建立 IPerceptionSimulation 管理員物件</span><span class="sxs-lookup"><span data-stu-id="2d693-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="2d693-136">若要控制模擬，您要對從 IPerceptionSimulationManager 物件取出的物件發出更新。</span><span class="sxs-lookup"><span data-stu-id="2d693-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="2d693-137">第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="2d693-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="2d693-138">您可以按一下[工具列](using-the-hololens-emulator.md)中的裝置入口網站按鈕，取得模擬器的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="2d693-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="2d693-139">![開啟裝置入口網站圖示 ](images/emulator-deviceportal.png) **開啟裝置入口網站** ：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="2d693-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal** : Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="2d693-140">針對 Windows Mixed Reality，可以在 [設定 & 安全性] 底下的 [設定] 應用程式中，然後在 [啟用裝置入口網站] 下的 [使用下列方式連接：] 區段中，取得「適用于開發人員」。</span><span class="sxs-lookup"><span data-stu-id="2d693-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="2d693-141">請務必記下 IP 位址和埠。</span><span class="sxs-lookup"><span data-stu-id="2d693-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="2d693-142">首先，您會呼叫 RestSimulationStreamSink 來取得 RestSimulationStreamSink 物件。</span><span class="sxs-lookup"><span data-stu-id="2d693-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="2d693-143">這是您將透過 HTTP 連接控制的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="2d693-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="2d693-144">您的命令將會傳遞至裝置或模擬器上執行的 [Windows 裝置入口網站](using-the-windows-device-portal.md) ，並由其處理。</span><span class="sxs-lookup"><span data-stu-id="2d693-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="2d693-145">建立物件所需的四個參數如下：</span><span class="sxs-lookup"><span data-stu-id="2d693-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="2d693-146">Uri uri-目標裝置的 IP 位址 (例如 " https://123.123.123.123 " 或 " https://123.123.123.123:50080 " ) </span><span class="sxs-lookup"><span data-stu-id="2d693-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="2d693-147">NetworkCredential 認證-用來連接到目標裝置或模擬器上 [Windows 裝置入口網站](using-the-windows-device-portal.md) 的使用者名稱/密碼。</span><span class="sxs-lookup"><span data-stu-id="2d693-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="2d693-148">如果您透過本機位址連接到模擬器 (例如，168。 *.* .\* ) 在同一部電腦上，將會接受任何認證。</span><span class="sxs-lookup"><span data-stu-id="2d693-148">If you are connecting to the emulator via its local address (e.g., 168. *.* .\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="2d693-149">bool 標準-True 表示正常優先順序，false 表示低優先順序。</span><span class="sxs-lookup"><span data-stu-id="2d693-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="2d693-150">您通常會想要在測試案例中將此設為 *true* ，以允許您的測試取得控制權。</span><span class="sxs-lookup"><span data-stu-id="2d693-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="2d693-151">模擬器與 Windows Mixed Reality 模擬會使用低優先順序的連接。</span><span class="sxs-lookup"><span data-stu-id="2d693-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="2d693-152">如果您的測試也使用低優先順序連接，則最近建立的連接將會受到控制。</span><span class="sxs-lookup"><span data-stu-id="2d693-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="2d693-153">CancellationToken token-Token，以取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="2d693-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="2d693-154">其次，您將建立 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="2d693-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="2d693-155">這是您用來控制模擬的物件。</span><span class="sxs-lookup"><span data-stu-id="2d693-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="2d693-156">請注意，這也必須在非同步方法中完成。</span><span class="sxs-lookup"><span data-stu-id="2d693-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="2d693-157">控制模擬的人</span><span class="sxs-lookup"><span data-stu-id="2d693-157">Control the simulated Human</span></span>

<span data-ttu-id="2d693-158">IPerceptionSimulationManager 具有會傳回 ISimulatedHuman 物件的人類屬性。</span><span class="sxs-lookup"><span data-stu-id="2d693-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="2d693-159">若要控制模擬的人，請在此物件上執行作業。</span><span class="sxs-lookup"><span data-stu-id="2d693-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="2d693-160">例如：</span><span class="sxs-lookup"><span data-stu-id="2d693-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="2d693-161">基本的 c # 主控台應用程式範例</span><span class="sxs-lookup"><span data-stu-id="2d693-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="2d693-162">擴充的範例 c # 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2d693-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="2d693-163">6 DOF 控制器上的附注</span><span class="sxs-lookup"><span data-stu-id="2d693-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="2d693-164">在模擬的 6 DOF 控制器上呼叫方法上的任何屬性之前，您必須先啟用控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="2d693-165">若未這麼做，將會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2d693-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="2d693-166">從 Windows 10 2019 年5月更新開始，只要將 ISimulatedSixDofController 物件的 Status 屬性設為 SimulatedSixDofControllerStatus，就可以安裝和啟用模擬的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="2d693-167">在 Windows 10 2018 年10月更新及更早的版本中，您必須先呼叫 PerceptionSimulationDevice 工具（位於 \Windows\System32 資料夾中），以個別安裝模擬的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="2d693-168">這項工具的使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="2d693-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="2d693-169">例如：</span><span class="sxs-lookup"><span data-stu-id="2d693-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="2d693-170">支援的動作包括：</span><span class="sxs-lookup"><span data-stu-id="2d693-170">Supported actions are:</span></span>
* <span data-ttu-id="2d693-171">i = 安裝</span><span class="sxs-lookup"><span data-stu-id="2d693-171">i = install</span></span>
* <span data-ttu-id="2d693-172">q = 查詢</span><span class="sxs-lookup"><span data-stu-id="2d693-172">q = query</span></span>
* <span data-ttu-id="2d693-173">r = 移除</span><span class="sxs-lookup"><span data-stu-id="2d693-173">r = remove</span></span>

<span data-ttu-id="2d693-174">支援的實例如下：</span><span class="sxs-lookup"><span data-stu-id="2d693-174">Supported instances are:</span></span>
* <span data-ttu-id="2d693-175">1 = 左方 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="2d693-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="2d693-176">2 = 右邊的 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="2d693-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="2d693-177">進程的結束代碼會指出成功 (零傳回值) 或失敗 (非零傳回值) 。</span><span class="sxs-lookup"><span data-stu-id="2d693-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="2d693-178">使用 ' q ' 動作來查詢是否已安裝控制器時，如果尚未安裝控制器，則傳回值會是零 (0) ，如果控制器已安裝則為 1 (1) 。</span><span class="sxs-lookup"><span data-stu-id="2d693-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="2d693-179">移除 Windows 10 2018 年10月更新或更早版本上的控制器時，請先透過 API 將其狀態設定為 Off，然後再呼叫 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="2d693-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="2d693-180">請注意，此工具必須以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="2d693-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="2d693-181">應用程式開發介面參考</span><span class="sxs-lookup"><span data-stu-id="2d693-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="2d693-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="2d693-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="2d693-183">描述模擬裝置類型</span><span class="sxs-lookup"><span data-stu-id="2d693-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="2d693-184">**PerceptionSimulation. SimulatedDeviceType 參考**</span><span class="sxs-lookup"><span data-stu-id="2d693-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="2d693-185">虛構的參考裝置，預設值為 PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="2d693-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="2d693-186">PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="2d693-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="2d693-187">描述 head 追蹤器模式</span><span class="sxs-lookup"><span data-stu-id="2d693-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="2d693-188">**PerceptionSimulation. HeadTrackerMode. 預設值**</span><span class="sxs-lookup"><span data-stu-id="2d693-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="2d693-189">預設標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="2d693-189">Default Head Tracking.</span></span> <span data-ttu-id="2d693-190">這表示系統可能會根據執行時間條件來選取最佳的標頭追蹤模式。</span><span class="sxs-lookup"><span data-stu-id="2d693-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="2d693-191">**PerceptionSimulation. HeadTrackerMode 的方向**</span><span class="sxs-lookup"><span data-stu-id="2d693-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="2d693-192">僅限方向的標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="2d693-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="2d693-193">這表示追蹤的位置可能不可靠，而且某些相依于 head 位置的功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="2d693-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="2d693-194">**PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="2d693-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="2d693-195">位置標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="2d693-195">Positional Head Tracking.</span></span> <span data-ttu-id="2d693-196">這表示追蹤的標頭位置和方向都是可靠的</span><span class="sxs-lookup"><span data-stu-id="2d693-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="2d693-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="2d693-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="2d693-198">描述模擬的手勢</span><span class="sxs-lookup"><span data-stu-id="2d693-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="2d693-199">**PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="2d693-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="2d693-200">用來表示沒有手勢的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="2d693-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="2d693-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="2d693-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="2d693-202">以手指按的手勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-202">A finger pressed gesture.</span></span>

<span data-ttu-id="2d693-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="2d693-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="2d693-204">手指放開手勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-204">A finger released gesture.</span></span>

<span data-ttu-id="2d693-205">**PerceptionSimulation. SimulatedGesture 首頁**</span><span class="sxs-lookup"><span data-stu-id="2d693-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="2d693-206">Home/system 手勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-206">The home/system gesture.</span></span>

<span data-ttu-id="2d693-207">**PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="2d693-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="2d693-208">有效手勢的最大值。</span><span class="sxs-lookup"><span data-stu-id="2d693-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="2d693-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="2d693-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="2d693-210">模擬 6 DOF 控制器的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="2d693-211">**PerceptionSimulation. SimulatedSixDofControllerStatus. Off**</span><span class="sxs-lookup"><span data-stu-id="2d693-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="2d693-212">6 DOF 控制器已關閉。</span><span class="sxs-lookup"><span data-stu-id="2d693-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="2d693-213">**PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="2d693-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="2d693-214">已開啟並追蹤6個 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="2d693-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="2d693-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="2d693-216">6 DOF 控制器已開啟，但無法追蹤。</span><span class="sxs-lookup"><span data-stu-id="2d693-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="2d693-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="2d693-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="2d693-218">模擬的 6 DOF 控制器上支援的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="2d693-219">**PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="2d693-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="2d693-220">用來指出沒有按鈕的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="2d693-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="2d693-221">**PerceptionSimulation. SimulatedSixDofControllerButton 首頁**</span><span class="sxs-lookup"><span data-stu-id="2d693-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="2d693-222">[首頁] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="2d693-222">The Home button is pressed.</span></span>

<span data-ttu-id="2d693-223">**PerceptionSimulation. SimulatedSixDofControllerButton 功能表**</span><span class="sxs-lookup"><span data-stu-id="2d693-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="2d693-224">已按下功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-224">The Menu button is pressed.</span></span>

<span data-ttu-id="2d693-225">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="2d693-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="2d693-226">按下 [握住] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-226">The Grip button is pressed.</span></span>

<span data-ttu-id="2d693-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="2d693-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="2d693-228">已按下觸控板。</span><span class="sxs-lookup"><span data-stu-id="2d693-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="2d693-229">**PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="2d693-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="2d693-230">已按下 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-230">The Select button is pressed.</span></span>

<span data-ttu-id="2d693-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="2d693-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="2d693-232">觸碰觸控板。</span><span class="sxs-lookup"><span data-stu-id="2d693-232">The TouchPad is touched.</span></span>

<span data-ttu-id="2d693-233">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="2d693-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="2d693-234">已按下操縱杆。</span><span class="sxs-lookup"><span data-stu-id="2d693-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="2d693-235">**PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="2d693-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="2d693-236">有效的最大按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="2d693-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="2d693-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="2d693-238">模擬眼睛的校正狀態</span><span class="sxs-lookup"><span data-stu-id="2d693-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="2d693-239">**PerceptionSimulation. SimulatedEyesCalibrationState. 無法使用**</span><span class="sxs-lookup"><span data-stu-id="2d693-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="2d693-240">無法使用眼睛校正。</span><span class="sxs-lookup"><span data-stu-id="2d693-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="2d693-241">**PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="2d693-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="2d693-242">眼睛已經過校正。</span><span class="sxs-lookup"><span data-stu-id="2d693-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="2d693-243">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2d693-243">This is the default value.</span></span>

<span data-ttu-id="2d693-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Config是**</span><span class="sxs-lookup"><span data-stu-id="2d693-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="2d693-245">正在校正眼睛。</span><span class="sxs-lookup"><span data-stu-id="2d693-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="2d693-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="2d693-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="2d693-247">需要校正眼睛。</span><span class="sxs-lookup"><span data-stu-id="2d693-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="2d693-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="2d693-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="2d693-249">手邊的追蹤準確度。</span><span class="sxs-lookup"><span data-stu-id="2d693-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="2d693-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 無法使用**</span><span class="sxs-lookup"><span data-stu-id="2d693-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="2d693-251">未追蹤聯合。</span><span class="sxs-lookup"><span data-stu-id="2d693-251">The joint is not tracked.</span></span>

<span data-ttu-id="2d693-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy 近似值**</span><span class="sxs-lookup"><span data-stu-id="2d693-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="2d693-253">會推斷聯合位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-253">The joint position is inferred.</span></span>

<span data-ttu-id="2d693-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy 可見**</span><span class="sxs-lookup"><span data-stu-id="2d693-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="2d693-255">聯合已完全追蹤。</span><span class="sxs-lookup"><span data-stu-id="2d693-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="2d693-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="2d693-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="2d693-257">手邊的追蹤準確度。</span><span class="sxs-lookup"><span data-stu-id="2d693-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="2d693-258">**PerceptionSimulation. SimulatedHandPose. 關閉**</span><span class="sxs-lookup"><span data-stu-id="2d693-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="2d693-259">手形的手指設定為反映封閉的姿勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="2d693-260">**PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="2d693-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="2d693-261">手形的手指設定為反映開放式姿勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="2d693-262">**PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="2d693-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="2d693-263">手形的手指會設定為反映指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="2d693-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="2d693-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="2d693-265">手形的手指設定為反映捏合姿勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="2d693-266">**PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="2d693-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="2d693-267">SimulatedHandPose 的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="2d693-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="2d693-268">PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="2d693-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="2d693-269">描述播放的狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="2d693-270">**PerceptionSimulation. PlaybackState. 已停止**</span><span class="sxs-lookup"><span data-stu-id="2d693-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="2d693-271">錄製目前已停止並可供播放。</span><span class="sxs-lookup"><span data-stu-id="2d693-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="2d693-272">**PerceptionSimulation. PlaybackState. 播放**</span><span class="sxs-lookup"><span data-stu-id="2d693-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="2d693-273">錄製現正播放中。</span><span class="sxs-lookup"><span data-stu-id="2d693-273">The recording is currently playing.</span></span>

<span data-ttu-id="2d693-274">**PerceptionSimulation. PlaybackState. 暫停**</span><span class="sxs-lookup"><span data-stu-id="2d693-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="2d693-275">錄製目前已暫停。</span><span class="sxs-lookup"><span data-stu-id="2d693-275">The recording is currently paused.</span></span>

<span data-ttu-id="2d693-276">**PerceptionSimulation. PlaybackState. End**</span><span class="sxs-lookup"><span data-stu-id="2d693-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="2d693-277">錄製已到達結尾。</span><span class="sxs-lookup"><span data-stu-id="2d693-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="2d693-278">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="2d693-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="2d693-279">描述3個元件向量，可能會描述3D 空間中的點或向量。</span><span class="sxs-lookup"><span data-stu-id="2d693-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="2d693-280">**PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="2d693-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="2d693-281">此向量的 X 元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-281">The X component of the vector.</span></span>

<span data-ttu-id="2d693-282">**PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="2d693-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="2d693-283">此向量的 Y 元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-283">The Y component of the vector.</span></span>

<span data-ttu-id="2d693-284">**PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="2d693-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="2d693-285">此向量的 Z 元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-285">The Z component of the vector.</span></span>

<span data-ttu-id="2d693-286">**PerceptionSimulation. Vector3. #ctor (system.string、system. single)**</span><span class="sxs-lookup"><span data-stu-id="2d693-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="2d693-287">建立新的 Vector3。</span><span class="sxs-lookup"><span data-stu-id="2d693-287">Construct a new Vector3.</span></span>

<span data-ttu-id="2d693-288">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-288">Parameters</span></span>
* <span data-ttu-id="2d693-289">x-向量的 x 元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="2d693-290">y-向量的 y 元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="2d693-291">z-向量的 z 元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="2d693-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="2d693-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="2d693-293">描述3個元件旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="2d693-294">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="2d693-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="2d693-295">旋轉的音調元件，圍繞 X 軸。</span><span class="sxs-lookup"><span data-stu-id="2d693-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="2d693-296">**PerceptionSimulation. Rotation3. 偏擺**</span><span class="sxs-lookup"><span data-stu-id="2d693-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="2d693-297">旋轉的偏擺元件，位於 Y 軸的右方。</span><span class="sxs-lookup"><span data-stu-id="2d693-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="2d693-298">**PerceptionSimulation. Rotation3。**</span><span class="sxs-lookup"><span data-stu-id="2d693-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="2d693-299">旋轉的變換元件，位於 Z 軸的右方。</span><span class="sxs-lookup"><span data-stu-id="2d693-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="2d693-300">**PerceptionSimulation. Rotation3. #ctor (system.string、system. single)**</span><span class="sxs-lookup"><span data-stu-id="2d693-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="2d693-301">建立新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="2d693-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="2d693-302">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-302">Parameters</span></span>
* <span data-ttu-id="2d693-303">音調-旋轉的音調部分。</span><span class="sxs-lookup"><span data-stu-id="2d693-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="2d693-304">偏擺-旋轉的偏擺元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="2d693-305">向前復原：旋轉的變換元件。</span><span class="sxs-lookup"><span data-stu-id="2d693-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="2d693-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="2d693-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="2d693-307">描述模擬手上的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="2d693-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="2d693-308">**PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="2d693-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="2d693-309">聯合的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-309">The position of the joint.</span></span>

<span data-ttu-id="2d693-310">**PerceptionSimulation. SimulatedHandJointConfiguration. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="2d693-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="2d693-311">聯合的旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-311">The rotation of the joint.</span></span>

<span data-ttu-id="2d693-312">**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="2d693-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="2d693-313">聯合的追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="2d693-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="2d693-314">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="2d693-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="2d693-315">描述圖的視圖（像是相機一般使用的）。</span><span class="sxs-lookup"><span data-stu-id="2d693-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="2d693-316">**PerceptionSimulation，Near**</span><span class="sxs-lookup"><span data-stu-id="2d693-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="2d693-317">包含在截量中的最小距離。</span><span class="sxs-lookup"><span data-stu-id="2d693-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="2d693-318">**PerceptionSimulation 到目前為止**</span><span class="sxs-lookup"><span data-stu-id="2d693-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="2d693-319">包含在錐中的最大距離。</span><span class="sxs-lookup"><span data-stu-id="2d693-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="2d693-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="2d693-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="2d693-321">以弧度為單位之視圖的水準欄位， (小於 PI) 。</span><span class="sxs-lookup"><span data-stu-id="2d693-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="2d693-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="2d693-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="2d693-323">水準欄位對視圖的水準對齊比例。</span><span class="sxs-lookup"><span data-stu-id="2d693-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="2d693-324">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="2d693-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="2d693-325">描述模擬耳機顯示器的設定。</span><span class="sxs-lookup"><span data-stu-id="2d693-325">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="2d693-326">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="2d693-327">從頭部中央到左方的轉換，以利身歷聲轉譯的用途。</span><span class="sxs-lookup"><span data-stu-id="2d693-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="2d693-328">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="2d693-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="2d693-329">針對身歷聲轉譯用途的左方旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="2d693-330">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="2d693-331">從頭部中心到右邊的轉換，以提供身歷聲轉譯的目的。</span><span class="sxs-lookup"><span data-stu-id="2d693-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="2d693-332">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="2d693-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="2d693-333">適用于身歷聲轉譯用途的正確眼睛旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="2d693-334">**PerceptionSimulation. SimulatedDisplayConfiguration Ipd**</span><span class="sxs-lookup"><span data-stu-id="2d693-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="2d693-335">系統回報的 Ipd 值，用於身歷聲轉譯。</span><span class="sxs-lookup"><span data-stu-id="2d693-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="2d693-336">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="2d693-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="2d693-337">是否應將提供給左和右眼睛轉換的值視為有效，並套用到執行中的系統。</span><span class="sxs-lookup"><span data-stu-id="2d693-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="2d693-338">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="2d693-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="2d693-339">是否應將為 Ipd 提供的值視為有效，並套用到執行中的系統。</span><span class="sxs-lookup"><span data-stu-id="2d693-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="2d693-340">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="2d693-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="2d693-341">用來產生用來控制裝置的封包的根目錄。</span><span class="sxs-lookup"><span data-stu-id="2d693-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="2d693-342">**PerceptionSimulation. IPerceptionSimulationManager 裝置**</span><span class="sxs-lookup"><span data-stu-id="2d693-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="2d693-343">取出模擬的裝置物件，以解讀模擬的人類和模擬的世界。</span><span class="sxs-lookup"><span data-stu-id="2d693-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="2d693-344">**PerceptionSimulation. IPerceptionSimulationManager 人類**</span><span class="sxs-lookup"><span data-stu-id="2d693-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="2d693-345">取出控制模擬人類的物件。</span><span class="sxs-lookup"><span data-stu-id="2d693-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="2d693-346">**PerceptionSimulation. IPerceptionSimulationManager 重設**</span><span class="sxs-lookup"><span data-stu-id="2d693-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="2d693-347">將模擬重設為其預設狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="2d693-348">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="2d693-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="2d693-349">描述裝置的介面，該裝置會解釋模擬的世界和模擬的人類</span><span class="sxs-lookup"><span data-stu-id="2d693-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="2d693-350">**PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="2d693-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="2d693-351">從模擬裝置取出 Head 追蹤器。</span><span class="sxs-lookup"><span data-stu-id="2d693-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="2d693-352">**PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="2d693-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="2d693-353">從模擬裝置取出手形追蹤程式。</span><span class="sxs-lookup"><span data-stu-id="2d693-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="2d693-354">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="2d693-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="2d693-355">設定模擬裝置的屬性，使其符合提供的裝置類型。</span><span class="sxs-lookup"><span data-stu-id="2d693-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="2d693-356">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-356">Parameters</span></span>
* <span data-ttu-id="2d693-357">類型-模擬裝置的新類型</span><span class="sxs-lookup"><span data-stu-id="2d693-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="2d693-358">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="2d693-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="2d693-359">將 ISimulatedDevice 轉換成 ISimulatedDevice2，即可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="2d693-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="2d693-360">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="2d693-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="2d693-361">取得或設定模擬的人是否主動佩戴耳機。</span><span class="sxs-lookup"><span data-stu-id="2d693-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="2d693-362">**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="2d693-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="2d693-363">取得或設定模擬顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="2d693-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="2d693-364">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="2d693-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="2d693-365">描述模擬的裝置部分的介面，該部分會追蹤模擬人類的標頭。</span><span class="sxs-lookup"><span data-stu-id="2d693-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="2d693-366">**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="2d693-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="2d693-367">抓取並設定目前的 head 追蹤器模式。</span><span class="sxs-lookup"><span data-stu-id="2d693-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="2d693-368">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="2d693-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="2d693-369">描述模擬的裝置部分的介面，以追蹤模擬人類的手</span><span class="sxs-lookup"><span data-stu-id="2d693-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="2d693-370">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="2d693-371">以計量表的關聯性抓取節點的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="2d693-372">**PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="2d693-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="2d693-373">取得和設定模擬的手追蹤器相對於 head 中央的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="2d693-374">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="2d693-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="2d693-375">取出模擬的手追蹤器，並將其設定為向下。</span><span class="sxs-lookup"><span data-stu-id="2d693-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="2d693-376">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="2d693-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="2d693-377">取得並設定是否忽略模擬的手追蹤器的截量。</span><span class="sxs-lookup"><span data-stu-id="2d693-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="2d693-378">略過時，一律會顯示這兩個手。</span><span class="sxs-lookup"><span data-stu-id="2d693-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="2d693-379">未略過時 (預設) 手只會在其位於 [手形追蹤器] 的 [截量] 中時才會顯示。</span><span class="sxs-lookup"><span data-stu-id="2d693-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="2d693-380">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="2d693-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="2d693-381">取出並設定用來判斷模擬的手追蹤器是否可以看到手的錐屬性。</span><span class="sxs-lookup"><span data-stu-id="2d693-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="2d693-382">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="2d693-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="2d693-383">控制模擬人類的最上層介面。</span><span class="sxs-lookup"><span data-stu-id="2d693-383">Top level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="2d693-384">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="2d693-385">取得和設定與世界相關之節點的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d693-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="2d693-386">位置會對應到人類的點中央。</span><span class="sxs-lookup"><span data-stu-id="2d693-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="2d693-387">**PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="2d693-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="2d693-388">取得並設定模擬的人臉在世界中的方向。</span><span class="sxs-lookup"><span data-stu-id="2d693-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="2d693-389">0弧度會朝下負 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="2d693-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="2d693-390">正弧度旋轉 Y 軸的順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="2d693-391">**PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="2d693-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="2d693-392">取得和設定模擬人類的高度（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d693-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="2d693-393">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="2d693-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="2d693-394">取出模擬人類的左邊。</span><span class="sxs-lookup"><span data-stu-id="2d693-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="2d693-395">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="2d693-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="2d693-396">取出模擬人類的右手邊。</span><span class="sxs-lookup"><span data-stu-id="2d693-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="2d693-397">**PerceptionSimulation. ISimulatedHuman Head**</span><span class="sxs-lookup"><span data-stu-id="2d693-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="2d693-398">取出模擬人類的標頭。</span><span class="sxs-lookup"><span data-stu-id="2d693-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="2d693-399">**PerceptionSimulation. ISimulatedHuman. Move (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="2d693-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="2d693-400">將模擬的人移至其目前位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d693-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="2d693-401">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-401">Parameters</span></span>
* <span data-ttu-id="2d693-402">轉譯-要移動的轉譯（相對於目前的位置）。</span><span class="sxs-lookup"><span data-stu-id="2d693-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="2d693-403">**PerceptionSimulation. ISimulatedHuman. (System.object 旋轉)**</span><span class="sxs-lookup"><span data-stu-id="2d693-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="2d693-404">以順時針方向對 Y 軸旋轉模擬的人，相對於其目前方向</span><span class="sxs-lookup"><span data-stu-id="2d693-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="2d693-405">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-405">Parameters</span></span>
* <span data-ttu-id="2d693-406">弧度-繞著 Y 軸旋轉的量。</span><span class="sxs-lookup"><span data-stu-id="2d693-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="2d693-407">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="2d693-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="2d693-408">將 ISimulatedHuman 轉換成 ISimulatedHuman2，即可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="2d693-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="2d693-409">**PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="2d693-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="2d693-410">取出左方 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="2d693-411">**PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="2d693-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="2d693-412">取出右邊的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="2d693-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="2d693-413">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="2d693-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="2d693-414">描述模擬人手的介面</span><span class="sxs-lookup"><span data-stu-id="2d693-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="2d693-415">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="2d693-416">以計量表的關聯性抓取節點的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="2d693-417">**PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="2d693-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="2d693-418">取得和設定模擬手相對於人類的位置，以量表為單位。</span><span class="sxs-lookup"><span data-stu-id="2d693-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="2d693-419">**PerceptionSimulation. ISimulatedHand。已啟用**</span><span class="sxs-lookup"><span data-stu-id="2d693-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="2d693-420">取得並設定是否目前已啟用手形。</span><span class="sxs-lookup"><span data-stu-id="2d693-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="2d693-421">**PerceptionSimulation. ISimulatedHand 可見**</span><span class="sxs-lookup"><span data-stu-id="2d693-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="2d693-422">取出 >simulateddevice (ie 是否可以看到手形，不論它是否位於 HandTracker) 要偵測到的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="2d693-423">**PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="2d693-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="2d693-424">將手上移，讓 >simulateddevice 可以看到它。</span><span class="sxs-lookup"><span data-stu-id="2d693-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="2d693-425">**PerceptionSimulation. ISimulatedHand. Move (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="2d693-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="2d693-426">移動模擬手相對於其目前位置的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d693-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="2d693-427">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-427">Parameters</span></span>
* <span data-ttu-id="2d693-428">轉譯-要轉譯模擬手的數量。</span><span class="sxs-lookup"><span data-stu-id="2d693-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="2d693-429">**PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="2d693-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="2d693-430">使用模擬的手勢來執行筆勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="2d693-431">只有在已啟用手形的情況下，系統才會偵測到此情況。</span><span class="sxs-lookup"><span data-stu-id="2d693-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="2d693-432">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-432">Parameters</span></span>
* <span data-ttu-id="2d693-433">手勢-要執行的手勢。</span><span class="sxs-lookup"><span data-stu-id="2d693-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="2d693-434">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="2d693-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="2d693-435">將 ISimulatedHand 轉換成 ISimulatedHand2，即可使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="2d693-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="2d693-436">**PerceptionSimulation. ISimulatedHand2 的方向**</span><span class="sxs-lookup"><span data-stu-id="2d693-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="2d693-437">取出或設定模擬手的旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="2d693-438">當您沿著軸旋轉時，正弧度會順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="2d693-439">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="2d693-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="2d693-440">將 ISimulatedHand 轉換成 ISimulatedHand3，即可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="2d693-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="2d693-441">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="2d693-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="2d693-442">取得指定聯合的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="2d693-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="2d693-443">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="2d693-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="2d693-444">設定指定之聯合的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="2d693-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="2d693-445">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="2d693-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="2d693-446">使用選擇性旗標將手設為已知的姿勢，以建立動畫。</span><span class="sxs-lookup"><span data-stu-id="2d693-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="2d693-447">注意：動畫並不會立即反映其最終的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="2d693-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="2d693-448">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="2d693-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="2d693-449">描述模擬人類標頭的介面。</span><span class="sxs-lookup"><span data-stu-id="2d693-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="2d693-450">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="2d693-451">以計量表的關聯性抓取節點的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="2d693-452">**PerceptionSimulation. ISimulatedHead. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="2d693-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="2d693-453">取出模擬標頭的旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="2d693-454">當您沿著軸旋轉時，正弧度會順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="2d693-455">**PerceptionSimulation. ISimulatedHead. 直徑**</span><span class="sxs-lookup"><span data-stu-id="2d693-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="2d693-456">取出模擬的標頭直徑。</span><span class="sxs-lookup"><span data-stu-id="2d693-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="2d693-457">此值可用來判斷旋轉) 的前端 (點。</span><span class="sxs-lookup"><span data-stu-id="2d693-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="2d693-458">**PerceptionSimulation. ISimulatedHead (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="2d693-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="2d693-459">將模擬的標頭相對於其目前的旋轉旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="2d693-460">當您沿著軸旋轉時，正弧度會順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="2d693-461">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-461">Parameters</span></span>
* <span data-ttu-id="2d693-462">旋轉-要旋轉的量。</span><span class="sxs-lookup"><span data-stu-id="2d693-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="2d693-463">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="2d693-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="2d693-464">將 ISimulatedHead 轉換成 ISimulatedHead2，即可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="2d693-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="2d693-465">**PerceptionSimulation. ISimulatedHead2 眼睛**</span><span class="sxs-lookup"><span data-stu-id="2d693-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="2d693-466">取出模擬人類的眼睛。</span><span class="sxs-lookup"><span data-stu-id="2d693-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="2d693-467">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="2d693-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="2d693-468">描述與模擬人類相關聯之 6 DOF 控制器的介面。</span><span class="sxs-lookup"><span data-stu-id="2d693-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="2d693-469">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="2d693-470">以計量表的關聯性抓取節點的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="2d693-471">**PerceptionSimulation. ISimulatedSixDofController。狀態**</span><span class="sxs-lookup"><span data-stu-id="2d693-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="2d693-472">取得或設定控制器的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="2d693-473">控制器狀態必須設定為 [關閉] 以外的值，才能移動、[旋轉] 或 [按下] 按鈕將會成功。</span><span class="sxs-lookup"><span data-stu-id="2d693-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="2d693-474">**PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="2d693-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="2d693-475">取得或設定模擬控制器相對於人類的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d693-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="2d693-476">**PerceptionSimulation. ISimulatedSixDofController 的方向**</span><span class="sxs-lookup"><span data-stu-id="2d693-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="2d693-477">取得或設定模擬控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="2d693-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="2d693-478">**PerceptionSimulation. ISimulatedSixDofController. Move (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="2d693-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="2d693-479">移動模擬控制器相對於其目前位置的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d693-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="2d693-480">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-480">Parameters</span></span>
* <span data-ttu-id="2d693-481">轉譯-要轉譯模擬控制器的數量。</span><span class="sxs-lookup"><span data-stu-id="2d693-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="2d693-482">**PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="2d693-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="2d693-483">按下模擬控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="2d693-484">只有在已啟用控制器的情況下，系統才會偵測到此情況。</span><span class="sxs-lookup"><span data-stu-id="2d693-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="2d693-485">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-485">Parameters</span></span>
* <span data-ttu-id="2d693-486">按鈕-要按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-486">button - The button to press.</span></span>

<span data-ttu-id="2d693-487">**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="2d693-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="2d693-488">釋放模擬控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="2d693-489">只有在已啟用控制器的情況下，系統才會偵測到此情況。</span><span class="sxs-lookup"><span data-stu-id="2d693-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="2d693-490">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-490">Parameters</span></span>
* <span data-ttu-id="2d693-491">按鈕-要釋放的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2d693-491">button - The button to release.</span></span>

<span data-ttu-id="2d693-492">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float，out float)**</span><span class="sxs-lookup"><span data-stu-id="2d693-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="2d693-493">取得模擬控制器的觸控板上模擬手指的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="2d693-494">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-494">Parameters</span></span>
* <span data-ttu-id="2d693-495">x-指手指的水準位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="2d693-496">y-指手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="2d693-497">**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float，float)**</span><span class="sxs-lookup"><span data-stu-id="2d693-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="2d693-498">在模擬控制器的觸控板上設定模擬手指的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="2d693-499">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-499">Parameters</span></span>
* <span data-ttu-id="2d693-500">x-指手指的水準位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="2d693-501">y-指手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="2d693-502">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="2d693-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="2d693-503">將 ISimulatedSixDofController 轉換成 ISimulatedSixDofController2，即可使用其他屬性和方法</span><span class="sxs-lookup"><span data-stu-id="2d693-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="2d693-504">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float，out float)**</span><span class="sxs-lookup"><span data-stu-id="2d693-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="2d693-505">取得模擬控制器上模擬之操縱杆的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="2d693-506">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-506">Parameters</span></span>
* <span data-ttu-id="2d693-507">x-操縱杆的水準位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="2d693-508">y-操縱杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="2d693-509">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float，float)**</span><span class="sxs-lookup"><span data-stu-id="2d693-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="2d693-510">設定模擬控制器上模擬之操縱杆的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="2d693-511">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-511">Parameters</span></span>
* <span data-ttu-id="2d693-512">x-操縱杆的水準位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="2d693-513">y-操縱杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="2d693-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="2d693-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="2d693-515">取得或設定模擬控制器的電池音量。</span><span class="sxs-lookup"><span data-stu-id="2d693-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="2d693-516">值必須大於0.0 且小於或等於100.0。</span><span class="sxs-lookup"><span data-stu-id="2d693-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="2d693-517">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="2d693-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="2d693-518">描述模擬人類眼睛的介面。</span><span class="sxs-lookup"><span data-stu-id="2d693-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="2d693-519">**PerceptionSimulation. ISimulatedEyes. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="2d693-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="2d693-520">取出模擬眼睛的旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="2d693-521">當您沿著軸旋轉時，正弧度會順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="2d693-522">**PerceptionSimulation. ISimulatedEyes (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="2d693-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="2d693-523">相對於目前的旋轉旋轉模擬眼睛。</span><span class="sxs-lookup"><span data-stu-id="2d693-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="2d693-524">當您沿著軸旋轉時，正弧度會順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="2d693-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="2d693-525">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-525">Parameters</span></span>
* <span data-ttu-id="2d693-526">旋轉-要旋轉的量。</span><span class="sxs-lookup"><span data-stu-id="2d693-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="2d693-527">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="2d693-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="2d693-528">抓取或設定模擬眼睛的校正狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="2d693-529">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="2d693-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="2d693-530">以計量表的關聯性抓取節點的位置。</span><span class="sxs-lookup"><span data-stu-id="2d693-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="2d693-531">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="2d693-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="2d693-532">用來與載入以播放的單一錄製互動的介面。</span><span class="sxs-lookup"><span data-stu-id="2d693-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="2d693-533">**PerceptionSimulation. ISimulationRecording 資料類型**</span><span class="sxs-lookup"><span data-stu-id="2d693-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="2d693-534">抓取錄製中的資料類型清單。</span><span class="sxs-lookup"><span data-stu-id="2d693-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="2d693-535">**PerceptionSimulation. ISimulationRecording. 州**</span><span class="sxs-lookup"><span data-stu-id="2d693-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="2d693-536">捕獲錄製的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="2d693-537">**PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="2d693-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="2d693-538">開始播放。</span><span class="sxs-lookup"><span data-stu-id="2d693-538">Start the playback.</span></span> <span data-ttu-id="2d693-539">如果錄製暫停，播放將從暫停的位置繼續;如果已停止，播放會從一開始開始。</span><span class="sxs-lookup"><span data-stu-id="2d693-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="2d693-540">如果已經在播放，則會忽略此呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d693-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="2d693-541">**PerceptionSimulation. ISimulationRecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="2d693-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="2d693-542">在目前的位置暫停播放。</span><span class="sxs-lookup"><span data-stu-id="2d693-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="2d693-543">如果記錄已停止，則會忽略呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d693-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="2d693-544">**PerceptionSimulation. ISimulationRecording. Seek (System.object)**</span><span class="sxs-lookup"><span data-stu-id="2d693-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="2d693-545">將記錄搜尋至指定的時間 (從一開始) 算起的100毫微秒間隔，並在該位置暫停。</span><span class="sxs-lookup"><span data-stu-id="2d693-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="2d693-546">如果時間超過錄製的結尾，則會在最後一個畫面上暫停。</span><span class="sxs-lookup"><span data-stu-id="2d693-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="2d693-547">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-547">Parameters</span></span>
* <span data-ttu-id="2d693-548">刻度-要搜尋的時間。</span><span class="sxs-lookup"><span data-stu-id="2d693-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="2d693-549">**PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="2d693-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="2d693-550">停止播放，並將位置重設為開頭。</span><span class="sxs-lookup"><span data-stu-id="2d693-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="2d693-551">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="2d693-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="2d693-552">在播放期間接收狀態變更的介面。</span><span class="sxs-lookup"><span data-stu-id="2d693-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="2d693-553">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="2d693-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="2d693-554">在 ISimulationRecording 的播放狀態變更時呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d693-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="2d693-555">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-555">Parameters</span></span>
* <span data-ttu-id="2d693-556">newState-錄製的新狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="2d693-557">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="2d693-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="2d693-558">用來建立感知模擬物件的根物件。</span><span class="sxs-lookup"><span data-stu-id="2d693-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="2d693-559">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="2d693-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="2d693-560">在物件上建立以產生模擬的封包，並將其傳遞至提供的接收。</span><span class="sxs-lookup"><span data-stu-id="2d693-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="2d693-561">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-561">Parameters</span></span>
* <span data-ttu-id="2d693-562">接收-將接收所有產生的封包的接收。</span><span class="sxs-lookup"><span data-stu-id="2d693-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="2d693-563">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d693-563">Return value</span></span>

<span data-ttu-id="2d693-564">建立的管理員。</span><span class="sxs-lookup"><span data-stu-id="2d693-564">The created Manager.</span></span>

<span data-ttu-id="2d693-565">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**</span><span class="sxs-lookup"><span data-stu-id="2d693-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="2d693-566">建立一個接收，將所有收到的封包儲存在指定路徑的檔案中。</span><span class="sxs-lookup"><span data-stu-id="2d693-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="2d693-567">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-567">Parameters</span></span>
* <span data-ttu-id="2d693-568">路徑-要建立之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d693-568">path - The path of the file to create.</span></span>

<span data-ttu-id="2d693-569">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d693-569">Return value</span></span>

<span data-ttu-id="2d693-570">建立的接收。</span><span class="sxs-lookup"><span data-stu-id="2d693-570">The created sink.</span></span>

<span data-ttu-id="2d693-571">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string，PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="2d693-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="2d693-572">從指定的檔案載入錄製。</span><span class="sxs-lookup"><span data-stu-id="2d693-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="2d693-573">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-573">Parameters</span></span>
* <span data-ttu-id="2d693-574">路徑-要載入之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d693-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="2d693-575">factory-記錄用來在必要時建立 ISimulationStreamSink 的 factory。</span><span class="sxs-lookup"><span data-stu-id="2d693-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="2d693-576">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d693-576">Return value</span></span>

<span data-ttu-id="2d693-577">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="2d693-577">The loaded recording.</span></span>

<span data-ttu-id="2d693-578">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string、PerceptionSimulation. ISimulationStreamSinkFactory、PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="2d693-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="2d693-579">從指定的檔案載入錄製。</span><span class="sxs-lookup"><span data-stu-id="2d693-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="2d693-580">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-580">Parameters</span></span>
* <span data-ttu-id="2d693-581">路徑-要載入之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d693-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="2d693-582">factory-記錄用來在必要時建立 ISimulationStreamSink 的 factory。</span><span class="sxs-lookup"><span data-stu-id="2d693-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="2d693-583">回呼-接收更新的回呼，regrading 記錄的狀態。</span><span class="sxs-lookup"><span data-stu-id="2d693-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="2d693-584">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d693-584">Return value</span></span>

<span data-ttu-id="2d693-585">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="2d693-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="2d693-586">PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="2d693-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="2d693-587">描述不同類型的資料流程資料。</span><span class="sxs-lookup"><span data-stu-id="2d693-587">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="2d693-588">**PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="2d693-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="2d693-589">用來指出沒有資料流程資料類型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="2d693-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="2d693-590">**PerceptionSimulation. StreamDataTypes Head**</span><span class="sxs-lookup"><span data-stu-id="2d693-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="2d693-591">關於頭部位置和方向的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="2d693-592">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="2d693-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="2d693-593">關於手的位置和手勢的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="2d693-594">**PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="2d693-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="2d693-595">關於環境空間對應的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="2d693-596">**PerceptionSimulation. StreamDataTypes. 校正**</span><span class="sxs-lookup"><span data-stu-id="2d693-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="2d693-597">與裝置校正相關的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="2d693-598">只有在遠端模式的系統才會接受校正封包。</span><span class="sxs-lookup"><span data-stu-id="2d693-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="2d693-599">**PerceptionSimulation. StreamDataTypes. 環境**</span><span class="sxs-lookup"><span data-stu-id="2d693-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="2d693-600">與裝置環境相關的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="2d693-601">**PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="2d693-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="2d693-602">關於運動控制器的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="2d693-603">**PerceptionSimulation. StreamDataTypes 眼睛**</span><span class="sxs-lookup"><span data-stu-id="2d693-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="2d693-604">有關模擬人類眼睛的資料串流。</span><span class="sxs-lookup"><span data-stu-id="2d693-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="2d693-605">**PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="2d693-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="2d693-606">與裝置的顯示設定相關的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2d693-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="2d693-607">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="2d693-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="2d693-608">用來表示所有記錄資料類型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="2d693-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="2d693-609">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="2d693-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="2d693-610">物件，這個物件會接收來自模擬資料流程的資料封包。</span><span class="sxs-lookup"><span data-stu-id="2d693-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="2d693-611">**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint length，byte [] 封包)**</span><span class="sxs-lookup"><span data-stu-id="2d693-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="2d693-612">接收在內部輸入和建立版本的單一封包。</span><span class="sxs-lookup"><span data-stu-id="2d693-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="2d693-613">參數</span><span class="sxs-lookup"><span data-stu-id="2d693-613">Parameters</span></span>
* <span data-ttu-id="2d693-614">長度-封包的長度。</span><span class="sxs-lookup"><span data-stu-id="2d693-614">length - The length of the packet.</span></span>
* <span data-ttu-id="2d693-615">封包-封包的資料。</span><span class="sxs-lookup"><span data-stu-id="2d693-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="2d693-616">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="2d693-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="2d693-617">建立 ISimulationStreamSink 的物件。</span><span class="sxs-lookup"><span data-stu-id="2d693-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="2d693-618">**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ( # B1**</span><span class="sxs-lookup"><span data-stu-id="2d693-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="2d693-619">建立 ISimulationStreamSink 的單一實例。</span><span class="sxs-lookup"><span data-stu-id="2d693-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="2d693-620">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d693-620">Return value</span></span>

<span data-ttu-id="2d693-621">建立的接收。</span><span class="sxs-lookup"><span data-stu-id="2d693-621">The created sink.</span></span>
