---
title: DirectX 中的頭部和眼睛目光
description: 在原生 DirectX 應用程式中使用標頭注視和眼睛追蹤的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 眼睛、頭部眼、前端追蹤、眼睛追蹤、directx、輸入、全像投影、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 9ec54f5db33346c499582b54a0b3e36c129bf7ab
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678077"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="fc0ec-104">DirectX 中的列印頭和眼睛輸入</span><span class="sxs-lookup"><span data-stu-id="fc0ec-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="fc0ec-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="fc0ec-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="fc0ec-107">在 Windows Mixed Reality 中，眼睛和前端的輸入是用來判斷使用者所查看的內容。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="fc0ec-108">這可以用來驅動主要輸入模型，例如 [前端和認可](../../design/gaze-and-commit.md)，也可以提供互動類型的內容。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-108">This can be used to drive primary input models such as [head-gaze and commit](../../design/gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="fc0ec-109">有兩種類型的注視向量可透過 API 取得：標眼和眼睛。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="fc0ec-110">兩者都是以具有原點和方向的三維光線形式提供。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-110">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="fc0ec-111">然後，應用程式可以 raycast 到其幕後或真實世界，判斷使用者的目標。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="fc0ec-112">**前端看著** 表示使用者的標頭指向的方向。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="fc0ec-113">將此視為裝置本身的位置和轉寄方向，並將位置表示兩個顯示器之間的中心點。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-113">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="fc0ec-114">所有混合現實裝置都可使用前端。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="fc0ec-115">**眼睛** 表示使用者的眼睛朝的方向。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="fc0ec-116">原點位於使用者的眼睛之間。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="fc0ec-117">它可在包含眼睛追蹤系統的混合現實裝置上使用。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-117">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="fc0ec-118">前端和眼睛光線都可透過  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 存取。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="fc0ec-119">只要呼叫 [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) ，就能在指定的時間戳記和 [座標系統](coordinate-systems-in-directx.md)接收新的 SpatialPointerPose 物件。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-119">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="fc0ec-120">此 SpatialPointerPose 包含頭部的原點和方向。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="fc0ec-121">如果有眼睛追蹤，它也會包含眼睛的原點和方向。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="fc0ec-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="fc0ec-122">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="fc0ec-123"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="fc0ec-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="fc0ec-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fc0ec-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="fc0ec-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="fc0ec-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="fc0ec-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="fc0ec-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="fc0ec-127">頭部注視</span><span class="sxs-lookup"><span data-stu-id="fc0ec-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="fc0ec-128">✔️</span><span class="sxs-lookup"><span data-stu-id="fc0ec-128">✔️</span></span></td>
     <td><span data-ttu-id="fc0ec-129">✔️</span><span class="sxs-lookup"><span data-stu-id="fc0ec-129">✔️</span></span></td>
     <td><span data-ttu-id="fc0ec-130">✔️</span><span class="sxs-lookup"><span data-stu-id="fc0ec-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="fc0ec-131">眼睛</span><span class="sxs-lookup"><span data-stu-id="fc0ec-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="fc0ec-132">✔️</span><span class="sxs-lookup"><span data-stu-id="fc0ec-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="fc0ec-133">使用頭部</span><span class="sxs-lookup"><span data-stu-id="fc0ec-133">Using head-gaze</span></span>

<span data-ttu-id="fc0ec-134">若要存取標頭，請從呼叫  [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 開始，以接收新的 SpatialPointerPose 物件。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="fc0ec-135">您必須傳遞下列參數。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-135">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="fc0ec-136">[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) ，表示前端看著所需的座標系統。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-136">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="fc0ec-137">這會以下列程式碼中的 *coordinateSystem* 變數表示。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="fc0ec-138">如需詳細資訊，請造訪我們的 [座標系統](coordinate-systems-in-directx.md) 開發人員指南。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="fc0ec-139">表示所要求之 head 姿勢確切時間的 [時間戳記](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-139">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="fc0ec-140">一般來說，您會使用對應至目前畫面格顯示時間的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-140">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="fc0ec-141">您可以從  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 物件（可透過目前的 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)存取）取得這個預測的顯示時間戳記。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="fc0ec-142">這個 HolographicFramePrediction 物件是由下列程式碼中的 *預測* 變數表示。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="fc0ec-143">當您有有效的 SpatialPointerPose 之後，就可以將標頭位置和轉寄方向作為屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="fc0ec-144">下列程式碼顯示如何存取它們。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-144">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="fc0ec-145">使用眼睛</span><span class="sxs-lookup"><span data-stu-id="fc0ec-145">Using eye-gaze</span></span>

<span data-ttu-id="fc0ec-146">請注意，若要讓您的使用者使用眼睛輸入，每位使用者在第一次使用裝置時，都必須經歷 [眼睛追蹤使用者的校正](../../calibration.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-146">Please note that for your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](../../calibration.md) the first time they use the device.</span></span> <span data-ttu-id="fc0ec-147">眼睛的 API 非常類似于 head。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-147">The eye-gaze API is very similar to head-gaze.</span></span>
<span data-ttu-id="fc0ec-148">它會使用相同的 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，以提供您可以針對場景 raycast 的光線來源和方向。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-148">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="fc0ec-149">唯一的差別是您必須先明確啟用眼睛追蹤，再加以使用。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-149">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="fc0ec-150">為了達到此目的，您必須執行兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="fc0ec-150">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="fc0ec-151">要求使用者在您的應用程式中使用眼睛追蹤的許可權。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-151">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="fc0ec-152">啟用套件資訊清單中的「注視輸入」功能。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-152">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="fc0ec-153">要求存取眼睛輸入</span><span class="sxs-lookup"><span data-stu-id="fc0ec-153">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="fc0ec-154">當您的應用程式啟動時，請呼叫 [EyesPose：： RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 來要求存取眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-154">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="fc0ec-155">系統會視需要提示使用者，並在授與存取權之後傳回 [GazeInputAccessStatus：：「允許](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) 」。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-155">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="fc0ec-156">這是非同步呼叫，因此需要一些額外的管理。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-156">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="fc0ec-157">下列範例會啟動卸離的 std：： thread 以等候結果，而該結果會儲存至名為 *m_isEyeTrackingEnabled* 的成員變數。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-157">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="fc0ec-158">啟動卸離的執行緒只是一個處理非同步呼叫的選項。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-158">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="fc0ec-159">或者，您可以使用 c + + 所支援的新 [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 功能/winrt</span><span class="sxs-lookup"><span data-stu-id="fc0ec-159">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="fc0ec-160">以下是另一個要求使用者權限的範例：</span><span class="sxs-lookup"><span data-stu-id="fc0ec-160">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="fc0ec-161">EyesPose：： IsSupported ( # A1 可讓應用程式只有在有眼睛追蹤器時，才會觸發許可權對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-161">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="fc0ec-162">GazeInputAccessStatus m_gazeInputAccessStatus;這是為了防止再次彈出許可權提示。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-162">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="fc0ec-163">宣告 *注視輸入* 功能</span><span class="sxs-lookup"><span data-stu-id="fc0ec-163">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="fc0ec-164">按兩下 *方案總管* 中的 package.appxmanifest 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-164">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="fc0ec-165">然後流覽至 [ *功能* ] 區段，並檢查 [ *注視輸入* ] 功能。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-165">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![注視輸入功能](images/gaze-input-capability.png)

<span data-ttu-id="fc0ec-167">這會將下列幾行新增至 package.appxmanifest 檔案中的 *封裝* 區段：</span><span class="sxs-lookup"><span data-stu-id="fc0ec-167">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="fc0ec-168">取得眼睛光線</span><span class="sxs-lookup"><span data-stu-id="fc0ec-168">Getting the eye-gaze ray</span></span>
<span data-ttu-id="fc0ec-169">一旦您收到 ET 的存取權之後，就可以自由抓取每個畫面的眼睛光線。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-169">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="fc0ec-170">就像前端一樣，藉由呼叫[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)與所需的時間戳記和座標系統來取得[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-170">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="fc0ec-171">SpatialPointerPose 包含透過[眼睛](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)屬性的[EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose)物件。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-171">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="fc0ec-172">只有在已啟用眼睛追蹤的情況下，此值才會是 null。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-172">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="fc0ec-173">從該處，您可以藉由呼叫 [EyesPose：： IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)，檢查裝置中的使用者是否有眼睛追蹤校正。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-173">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="fc0ec-174">接下來，使用 [眼睛屬性來](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 取得包含眼睛的位置和方向的 [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-174">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="fc0ec-175">注視屬性有時可以是 null，因此請務必檢查此值。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-175">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="fc0ec-176">發生這種情況的原因是，已校正的使用者暫時關閉其眼睛。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-176">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="fc0ec-177">下列程式碼顯示如何存取眼睛光線。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-177">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-is-not-available"></a><span data-ttu-id="fc0ec-178">當眼睛追蹤無法使用時的 Fallback</span><span class="sxs-lookup"><span data-stu-id="fc0ec-178">Fallback when eye tracking is not available</span></span>
<span data-ttu-id="fc0ec-179">如同我們的 [眼睛追蹤設計](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)檔中所述，這兩個設計人員和開發人員都應該注意，您的應用程式可能會有可能無法使用眼睛追蹤資料的實例。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-179">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers as well as developers should be aware that there may be instances in which eye tracking data may not be available to your app.</span></span>
<span data-ttu-id="fc0ec-180">這種情況的原因有很多種，那就是使用者已拒絕應用程式存取其眼睛追蹤資料，或只是暫時干擾差異性 (例如 HoloLens 面板上的塗抹，或遮蔽使用者的眼睛) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-180">There are various reasons for this ranging from a user not being calibrated, the user having denied the app access to his/her eye tracking data or simply temporary interferences (such as smudges on the HoloLens visor or hair occluding the user's eyes).</span></span> <span data-ttu-id="fc0ec-181">雖然本檔中已提及部分 Api，但我們將在下列內容中提供一份摘要，說明如何偵測如何以快速參考的方式來使用眼睛追蹤：</span><span class="sxs-lookup"><span data-stu-id="fc0ec-181">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="fc0ec-182">檢查系統是否支援眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-182">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="fc0ec-183">呼叫下列 *方法*： [EyesPose. IsSupported ( # B1](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="fc0ec-183">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="fc0ec-184">檢查使用者是否已校正。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-184">Check that the user is calibrated.</span></span> <span data-ttu-id="fc0ec-185">呼叫下列 *屬性*： [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="fc0ec-185">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="fc0ec-186">確認使用者已為您的應用程式提供使用其眼睛追蹤資料的許可權：取出目前的 _' GazeInputAccessStatus '_。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-186">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="fc0ec-187">有關如何進行這項操作的範例，請參閱 [要求存取注視輸入](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)的說明。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-187">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="fc0ec-188">此外，您可能會想要在收到的眼睛追蹤資料更新之間加上超時時間，以檢查您的眼睛追蹤資料是否已過時，如以下所述。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-188">In addition, you may want to check that your eye tracking data is not stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>  
<span data-ttu-id="fc0ec-189">如需詳細資訊，請流覽我們的回溯 [設計考慮](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-189">Please visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="fc0ec-190">將注視與其他輸入相互關聯</span><span class="sxs-lookup"><span data-stu-id="fc0ec-190">Correlating gaze with other inputs</span></span>
<span data-ttu-id="fc0ec-191">有時您可能會發現您需要的 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) 與過去的事件相對應。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-191">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="fc0ec-192">比方說，如果使用者執行一下，您的應用程式可能會想要知道他們正在查看的內容。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-192">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="fc0ec-193">基於這個目的，只要將 [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 與預測的框架時間搭配使用，就會因為系統輸入處理和顯示時間之間的延遲而不正確。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-193">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="fc0ec-194">此外，如果使用眼睛來表示目標，我們的眼睛通常會在完成認可動作之前繼續進行。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-194">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="fc0ec-195">這對簡單的分流來說比較不成問題，但在結合長聲音命令與快速的移動時變得更重要。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-195">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="fc0ec-196">處理此案例的其中一種方式是使用對應至輸入事件的歷程時間戳記，對  [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)進行額外的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-196">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="fc0ec-197">不過，針對透過 SpatialInteractionManager 進行路由的輸入，有更簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-197">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="fc0ec-198">[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有它自己的[TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函數。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-198">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="fc0ec-199">呼叫以提供完全相關的 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) ，而不需要猜測。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-199">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="fc0ec-200">如需有關使用 SpatialInteractionSourceStates 的詳細資訊，請參閱 DirectX 檔 [中的手和移動控制器](hands-and-motion-controllers-in-directx.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-200">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="fc0ec-201">校正</span><span class="sxs-lookup"><span data-stu-id="fc0ec-201">Calibration</span></span>
<span data-ttu-id="fc0ec-202">為了讓眼睛追蹤能準確地運作，每位使用者都必須經過 [眼睛追蹤使用者的校正](../../calibration.md)。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-202">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](../../calibration.md).</span></span> <span data-ttu-id="fc0ec-203">這可讓裝置為使用者調整系統，以獲得更舒適且更高品質的觀賞體驗，並同時確保一致的眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-203">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="fc0ec-204">開發人員不需要在其端進行任何動作，即可管理使用者校正。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-204">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="fc0ec-205">系統會在下列情況下，確定使用者會收到校正裝置的提示：</span><span class="sxs-lookup"><span data-stu-id="fc0ec-205">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="fc0ec-206">使用者第一次使用裝置</span><span class="sxs-lookup"><span data-stu-id="fc0ec-206">The user is using the device for the first time</span></span>
* <span data-ttu-id="fc0ec-207">使用者先前退出宣告校正流程</span><span class="sxs-lookup"><span data-stu-id="fc0ec-207">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="fc0ec-208">上次使用者使用裝置時，校正程式未成功</span><span class="sxs-lookup"><span data-stu-id="fc0ec-208">The calibration process did not succeed the last time the user used the device</span></span>

<span data-ttu-id="fc0ec-209">開發人員應務必為可能無法使用眼睛追蹤資料的使用者提供適當的支援。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-209">Developers should make sure to provide adequate support for users for whom eye tracking data may not be available.</span></span> <span data-ttu-id="fc0ec-210">深入瞭解 [Hololens 2 上眼睛追蹤](../../design/eye-tracking.md)的回溯解決方案考慮。</span><span class="sxs-lookup"><span data-stu-id="fc0ec-210">Learn more about considerations for fallback solutions at [Eye tracking on Hololens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="fc0ec-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc0ec-211">See also</span></span>
* [<span data-ttu-id="fc0ec-212">校正</span><span class="sxs-lookup"><span data-stu-id="fc0ec-212">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="fc0ec-213">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="fc0ec-213">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="fc0ec-214">HoloLens 2 上的眼睛</span><span class="sxs-lookup"><span data-stu-id="fc0ec-214">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="fc0ec-215">注視和認可輸入模型</span><span class="sxs-lookup"><span data-stu-id="fc0ec-215">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="fc0ec-216">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="fc0ec-216">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="fc0ec-217">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="fc0ec-217">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
