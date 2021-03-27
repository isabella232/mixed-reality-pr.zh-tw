---
title: Unity 中的相片攝影機
description: 瞭解如何將相片拍攝至檔案或 Texture2D、如何捕獲相片並與原始位元組互動，以及如何捕獲影片。
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: 相片、影片、hololens、攝影機、unity、定位、PVC、相片攝影機、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、網路攝影機、相片拍攝、影片捕獲
ms.openlocfilehash: 1cae796a793036ed59c1d0805df76cb8ac143027
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636210"
---
# <a name="photo-video-camera-in-unity"></a><span data-ttu-id="a26bf-104">Unity 中的相片攝影機</span><span class="sxs-lookup"><span data-stu-id="a26bf-104">Photo Video camera in Unity</span></span>

## <a name="enabling-the-capability-for-camera-access"></a><span data-ttu-id="a26bf-105">啟用相機存取的功能</span><span class="sxs-lookup"><span data-stu-id="a26bf-105">Enabling the capability for camera access</span></span>

<span data-ttu-id="a26bf-106">必須為應用程式宣告「網路攝影機」功能才能使用 [相機](../platform-capabilities-and-apis/locatable-camera.md)。</span><span class="sxs-lookup"><span data-stu-id="a26bf-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>

1. <span data-ttu-id="a26bf-107">在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定] 頁面，移至播放機設定</span><span class="sxs-lookup"><span data-stu-id="a26bf-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="a26bf-108">選取 [Windows 存放區] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="a26bf-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="a26bf-109">在 [發佈設定 > 功能] 區段中，檢查 **網路** 攝影機和 **麥克風** 功能</span><span class="sxs-lookup"><span data-stu-id="a26bf-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="a26bf-110">攝影機一次只能有一種操作。</span><span class="sxs-lookup"><span data-stu-id="a26bf-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="a26bf-111">您可以 `UnityEngine.XR.WSA.WebCam.Mode` 在 unity 2018 及更早版本或 `UnityEngine.Windows.WebCam.Mode` unity 2019 和更新版本中，檢查相機目前所在的模式。</span><span class="sxs-lookup"><span data-stu-id="a26bf-111">You can check which mode the camera is currently in with `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 and earlier or `UnityEngine.Windows.WebCam.Mode` in Unity 2019  and later.</span></span> <span data-ttu-id="a26bf-112">可用的模式為 [相片]、[影片] 或 [無]。</span><span class="sxs-lookup"><span data-stu-id="a26bf-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="a26bf-113">相片捕獲</span><span class="sxs-lookup"><span data-stu-id="a26bf-113">Photo capture</span></span>

<span data-ttu-id="a26bf-114">**Unity 2019) ： UnityEngine 之前的命名空間 (：** *. XR*</span><span class="sxs-lookup"><span data-stu-id="a26bf-114">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="a26bf-115">**命名空間 (Unity 2019 和更新版本) ：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="a26bf-115">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="a26bf-116">**類型：** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="a26bf-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="a26bf-117">*PhotoCapture* 型別可讓您以照片攝影機拍攝相片。</span><span class="sxs-lookup"><span data-stu-id="a26bf-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="a26bf-118">使用 *PhotoCapture* 拍攝相片的一般模式如下：</span><span class="sxs-lookup"><span data-stu-id="a26bf-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>

1. <span data-ttu-id="a26bf-119">建立 *PhotoCapture* 物件</span><span class="sxs-lookup"><span data-stu-id="a26bf-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="a26bf-120">使用您想要的設定來建立 *CameraParameters* 物件</span><span class="sxs-lookup"><span data-stu-id="a26bf-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="a26bf-121">透過 *StartPhotoModeAsync* 啟動相片模式</span><span class="sxs-lookup"><span data-stu-id="a26bf-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="a26bf-122">拍攝您想要的相片</span><span class="sxs-lookup"><span data-stu-id="a26bf-122">Take the photo you want</span></span>
    * <span data-ttu-id="a26bf-123"> (選擇性) 與該圖片互動</span><span class="sxs-lookup"><span data-stu-id="a26bf-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="a26bf-124">停止相片模式並清除資源</span><span class="sxs-lookup"><span data-stu-id="a26bf-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="a26bf-125">PhotoCapture 的一般設定</span><span class="sxs-lookup"><span data-stu-id="a26bf-125">Common set-up for PhotoCapture</span></span>

<span data-ttu-id="a26bf-126">針對這三種用途，請從上述的前三個步驟開始</span><span class="sxs-lookup"><span data-stu-id="a26bf-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="a26bf-127">一開始先建立 *PhotoCapture* 物件</span><span class="sxs-lookup"><span data-stu-id="a26bf-127">Start by creating a *PhotoCapture* object</span></span>

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

<span data-ttu-id="a26bf-128">接下來，儲存您的物件、設定您的參數和啟動相片模式</span><span class="sxs-lookup"><span data-stu-id="a26bf-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
private PhotoCapture photoCaptureObject = null;

void OnPhotoCaptureCreated(PhotoCapture captureObject)
{
    photoCaptureObject = captureObject;

    Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

    CameraParameters c = new CameraParameters();
    c.hologramOpacity = 0.0f;
    c.cameraResolutionWidth = cameraResolution.width;
    c.cameraResolutionHeight = cameraResolution.height;
    c.pixelFormat = CapturePixelFormat.BGRA32;

    captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
}
```

<span data-ttu-id="a26bf-129">最後，您也會使用此處提供的相同清除程式碼</span><span class="sxs-lookup"><span data-stu-id="a26bf-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

<span data-ttu-id="a26bf-130">在這些步驟之後，您可以選擇要捕獲的相片類型。</span><span class="sxs-lookup"><span data-stu-id="a26bf-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="a26bf-131">將相片擷取到檔案</span><span class="sxs-lookup"><span data-stu-id="a26bf-131">Capture a photo to a file</span></span>

<span data-ttu-id="a26bf-132">最簡單的操作是直接將相片捕獲到檔案。</span><span class="sxs-lookup"><span data-stu-id="a26bf-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="a26bf-133">您可以將相片儲存為 JPG 或 PNG。</span><span class="sxs-lookup"><span data-stu-id="a26bf-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="a26bf-134">如果您已成功啟動相片模式，請拍攝相片，並將其儲存在磁片上</span><span class="sxs-lookup"><span data-stu-id="a26bf-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
        string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="a26bf-135">將相片捕獲到磁片之後，結束相片模式，然後清除您的物件</span><span class="sxs-lookup"><span data-stu-id="a26bf-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        Debug.Log("Saved Photo to disk!");
        photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
    }
    else
    {
        Debug.Log("Failed to save Photo to disk");
    }
}
```

### <a name="capture-a-photo-to-a-texture2d-with-location"></a><span data-ttu-id="a26bf-136">使用位置將相片捕捉至 Texture2D</span><span class="sxs-lookup"><span data-stu-id="a26bf-136">Capture a photo to a Texture2D with location</span></span>

<span data-ttu-id="a26bf-137">將資料捕捉至 Texture2D 時，此程式類似于捕捉至磁片。</span><span class="sxs-lookup"><span data-stu-id="a26bf-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="a26bf-138">依照上述的安裝程式進行操作。</span><span class="sxs-lookup"><span data-stu-id="a26bf-138">Follow the setup process above.</span></span>

<span data-ttu-id="a26bf-139">在 *OnPhotoModeStarted* 中，將框架捕獲到記憶體。</span><span class="sxs-lookup"><span data-stu-id="a26bf-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="a26bf-140">然後，您會將結果套用至材質，並使用上述的一般清除程式碼。</span><span class="sxs-lookup"><span data-stu-id="a26bf-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        // Create our Texture2D for use and set the correct resolution
        Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
        // Copy the raw image data into our target texture
        photoCaptureFrame.UploadImageDataToTexture(targetTexture);
        // Do as we wish with the texture such as apply it to a material, etc.
    }
    // Clean up
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

#### <a name="locatable-camera"></a><span data-ttu-id="a26bf-141">定位相機</span><span class="sxs-lookup"><span data-stu-id="a26bf-141">Locatable camera</span></span>

<span data-ttu-id="a26bf-142">若要將此材質放置在場景中，並使用可定位的相機矩陣來顯示，請將下列程式碼新增至 *OnCapturedPhotoToMemory* 的 `result.success` 檢查中：</span><span class="sxs-lookup"><span data-stu-id="a26bf-142">To place this texture in the scene and display it using the locatable camera matrices, add the following code to *OnCapturedPhotoToMemory* in the `result.success` check:</span></span>

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

<span data-ttu-id="a26bf-143">[Unity 已提供範例程式碼](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) ，將投射矩陣套用至其論壇上的特定著色器。</span><span class="sxs-lookup"><span data-stu-id="a26bf-143">[Unity has provided sample code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) for applying the projection matrix to a specific shader on their forums.</span></span>

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="a26bf-144">捕捉相片並與原始位元組互動</span><span class="sxs-lookup"><span data-stu-id="a26bf-144">Capture a photo and interact with the raw bytes</span></span>

<span data-ttu-id="a26bf-145">若要與記憶體內框架中的原始位元組互動，請遵循上述相同的設定步驟，並 *OnPhotoModeStarted* 以將相片捕捉至 Texture2D。</span><span class="sxs-lookup"><span data-stu-id="a26bf-145">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="a26bf-146">差異是在 *OnCapturedPhotoToMemory* 中，您可以在其中取得原始位元組並與其互動。</span><span class="sxs-lookup"><span data-stu-id="a26bf-146">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="a26bf-147">在此範例中，您將建立可透過 SetPixels 進一步處理或套用至材質的 *清單 <Color>* *()*</span><span class="sxs-lookup"><span data-stu-id="a26bf-147">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        List<byte> imageBufferList = new List<byte>();
        // Copy the raw IMFMediaBuffer data into our empty byte list.
        photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

        // In this example, we captured the image using the BGRA32 format.
        // So our stride will be 4 since we have a byte for each rgba channel.
        // The raw image data will also be flipped so we access our pixel data
        // in the reverse order.
        int stride = 4;
        float denominator = 1.0f / 255.0f;
        List<Color> colorArray = new List<Color>();
        for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
        {
            float a = (int)(imageBufferList[i - 0]) * denominator;
            float r = (int)(imageBufferList[i - 1]) * denominator;
            float g = (int)(imageBufferList[i - 2]) * denominator;
            float b = (int)(imageBufferList[i - 3]) * denominator;

            colorArray.Add(new Color(r, g, b, a));
        }
        // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
    }
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

## <a name="video-capture"></a><span data-ttu-id="a26bf-148">視訊擷取</span><span class="sxs-lookup"><span data-stu-id="a26bf-148">Video capture</span></span>

<span data-ttu-id="a26bf-149">**Unity 2019) ： UnityEngine 之前的命名空間 (：** *. XR*</span><span class="sxs-lookup"><span data-stu-id="a26bf-149">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="a26bf-150">**命名空間 (Unity 2019 和更新版本) ：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="a26bf-150">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="a26bf-151">**類型：** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="a26bf-151">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="a26bf-152">*VideoCapture* 的功能類似于 *PhotoCapture*。</span><span class="sxs-lookup"><span data-stu-id="a26bf-152">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="a26bf-153">唯一的兩個差異是您必須指定每秒的畫面格 (FPS) 值，而且您只能將磁片直接儲存為磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="a26bf-153">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="a26bf-154">使用 *VideoCapture* 的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="a26bf-154">The steps to use *VideoCapture* are as follows:</span></span>

1. <span data-ttu-id="a26bf-155">建立 *VideoCapture* 物件</span><span class="sxs-lookup"><span data-stu-id="a26bf-155">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="a26bf-156">使用您想要的設定來建立 *CameraParameters* 物件</span><span class="sxs-lookup"><span data-stu-id="a26bf-156">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="a26bf-157">透過 *StartVideoModeAsync* 啟動影片模式</span><span class="sxs-lookup"><span data-stu-id="a26bf-157">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="a26bf-158">開始錄製影片</span><span class="sxs-lookup"><span data-stu-id="a26bf-158">Start recording video</span></span>
5. <span data-ttu-id="a26bf-159">停止錄製影片</span><span class="sxs-lookup"><span data-stu-id="a26bf-159">Stop recording video</span></span>
6. <span data-ttu-id="a26bf-160">停止影片模式並清除資源</span><span class="sxs-lookup"><span data-stu-id="a26bf-160">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="a26bf-161">首先，建立我們的 *VideoCapture* 物件 *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="a26bf-161">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

<span data-ttu-id="a26bf-162">接下來，設定您想要錄製和啟動的參數。</span><span class="sxs-lookup"><span data-stu-id="a26bf-162">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
{
    if (videoCapture != null)
    {
        m_VideoCapture = videoCapture;

        Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

        CameraParameters cameraParameters = new CameraParameters();
        cameraParameters.hologramOpacity = 0.0f;
        cameraParameters.frameRate = cameraFramerate;
        cameraParameters.cameraResolutionWidth = cameraResolution.width;
        cameraParameters.cameraResolutionHeight = cameraResolution.height;
        cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

        m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                            VideoCapture.AudioState.None,
                                            OnStartedVideoCaptureMode);
    }
    else
    {
        Debug.LogError("Failed to create VideoCapture Instance!");
    }
}
```

<span data-ttu-id="a26bf-163">啟動後，開始錄製</span><span class="sxs-lookup"><span data-stu-id="a26bf-163">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format("MyVideo_{0}.mp4", Time.time);
        string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
    }
}
```

<span data-ttu-id="a26bf-164">錄製開始之後，您可以更新您的 UI 或行為以啟用停止。</span><span class="sxs-lookup"><span data-stu-id="a26bf-164">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="a26bf-165">您只需記錄即可。</span><span class="sxs-lookup"><span data-stu-id="a26bf-165">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

<span data-ttu-id="a26bf-166">在稍後，您會想要使用計時器或使用者輸入來停止錄製。</span><span class="sxs-lookup"><span data-stu-id="a26bf-166">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

<span data-ttu-id="a26bf-167">記錄停止後，請停止影片模式並清除您的資源。</span><span class="sxs-lookup"><span data-stu-id="a26bf-167">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Stopped Recording Video!");
    m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
}

void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    m_VideoCapture.Dispose();
    m_VideoCapture = null;
}
```

## <a name="troubleshooting"></a><span data-ttu-id="a26bf-168">疑難排解</span><span class="sxs-lookup"><span data-stu-id="a26bf-168">Troubleshooting</span></span>

* <span data-ttu-id="a26bf-169">沒有任何可用的解決方案</span><span class="sxs-lookup"><span data-stu-id="a26bf-169">No resolutions are available</span></span>
  * <span data-ttu-id="a26bf-170">確定您的專案中已指定 **網路** 攝影機功能。</span><span class="sxs-lookup"><span data-stu-id="a26bf-170">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a26bf-171">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="a26bf-171">Next Development Checkpoint</span></span>

<span data-ttu-id="a26bf-172">如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實平臺功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="a26bf-172">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="a26bf-173">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="a26bf-173">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a26bf-174">對焦點</span><span class="sxs-lookup"><span data-stu-id="a26bf-174">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="a26bf-175">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="a26bf-175">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a26bf-176">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="a26bf-176">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="a26bf-177">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-advanced-features)。</span><span class="sxs-lookup"><span data-stu-id="a26bf-177">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a26bf-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a26bf-178">See Also</span></span>

* [<span data-ttu-id="a26bf-179">定位相機</span><span class="sxs-lookup"><span data-stu-id="a26bf-179">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)