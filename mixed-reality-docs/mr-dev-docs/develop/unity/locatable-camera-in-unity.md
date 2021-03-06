---
title: Unity 中的定位相機
description: 瞭解如何將相片拍攝至檔案或 Texture2D、如何捕獲相片並與原始位元組互動，以及如何捕獲影片。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 相片、影片、hololens、攝影機、unity、定位、PVC、相片攝影機、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、網路攝影機、相片拍攝、影片捕獲
ms.openlocfilehash: ccf0c17a5f419341e64a87fb9ef04ef0a40c2a33
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236899"
---
# <a name="locatable-camera-in-unity"></a>Unity 中的定位相機

## <a name="enabling-the-capability-for-photo-video-camera"></a>啟用相片攝影機的功能

必須為應用程式宣告「網路攝影機」功能才能使用 [相機](../platform-capabilities-and-apis/locatable-camera.md)。
1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定] 頁面，移至播放機設定
2. 選取 [Windows 存放區] 索引標籤
3. 在 [發佈設定 > 功能] 區段中，檢查 **網路** 攝影機和 **麥克風** 功能

攝影機一次只能有一種操作。 您可以使用 UnityEngine. XR 檢查相機目前所在的模式。 可用的模式為 [相片]、[影片] 或 [無]。

## <a name="photo-capture"></a>相片捕獲

**命名空間：**  
*UnityEngine. XR (Unity \~ 2018) UnityEngine (unity 2019 \~)*<br>
**類型：** *PhotoCapture*

*PhotoCapture* 型別可讓您以照片攝影機拍攝相片。 使用 *PhotoCapture* 拍攝相片的一般模式如下：
1. 建立 *PhotoCapture* 物件
2. 使用您想要的設定來建立 *CameraParameters* 物件
3. 透過 *StartPhotoModeAsync* 啟動相片模式
4. 拍攝您想要的相片
    *  (選擇性) 與該圖片互動
5. 停止相片模式並清除資源

### <a name="common-set-up-for-photocapture"></a>PhotoCapture 的一般設定

針對這三種用途，請從上述的前三個步驟開始

一開始先建立 *PhotoCapture* 物件

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

接下來，儲存您的物件、設定您的參數和啟動相片模式

```cs
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

最後，您也會使用此處提供的相同清除程式碼

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

在這些步驟之後，您可以選擇要捕獲的相片類型。

### <a name="capture-a-photo-to-a-file"></a>將相片拍攝至檔案

最簡單的操作是直接將相片捕獲到檔案。 您可以將相片儲存為 JPG 或 PNG。

如果您已成功啟動相片模式，請拍攝相片，並將其儲存在磁片上

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

將相片捕獲到磁片之後，結束相片模式，然後清除您的物件

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

### <a name="capture-a-photo-to-a-texture2d"></a>將相片拍攝至 Texture2D

將資料捕捉至 Texture2D 時，此程式類似于捕捉至磁片。

依照上述的安裝程式進行操作。

在 *OnPhotoModeStarted* 中，將框架捕獲到記憶體。

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

然後，您會將結果套用至材質，並使用上述的一般清除程式碼。

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>捕捉相片並與原始位元組互動

若要與記憶體內框架中的原始位元組互動，請遵循上述相同的設定步驟，並 *OnPhotoModeStarted* 以將相片捕捉至 Texture2D。 差異是在 *OnCapturedPhotoToMemory* 中，您可以在其中取得原始位元組並與其互動。

在此範例中，您將建立可透過 SetPixels 進一步處理或套用至材質的 *清單 <Color>* *()*

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

## <a name="video-capture"></a>影片捕獲

**命名空間：** *UnityEngine. XR*<br>
**類型：** *VideoCapture*

*VideoCapture* 的功能類似于 *PhotoCapture*。 唯一的兩個差異是您必須指定每秒的畫面格 (FPS) 值，而且您只能將磁片直接儲存為磁片磁碟機。 使用 *VideoCapture* 的步驟如下：
1. 建立 *VideoCapture* 物件
2. 使用您想要的設定來建立 *CameraParameters* 物件
3. 透過 *StartVideoModeAsync* 啟動影片模式
4. 開始錄製影片
5. 停止錄製影片
6. 停止影片模式並清除資源

首先，建立我們的 *VideoCapture* 物件 *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

接下來，設定您想要錄製和啟動的參數。

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
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

啟動後，開始錄製

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

錄製開始之後，您可以更新您的 UI 或行為以啟用停止。 您只需記錄即可。

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

在稍後，您會想要使用計時器或使用者輸入來停止錄製。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

記錄停止後，請停止影片模式並清除您的資源。

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

## <a name="troubleshooting"></a>疑難排解
* 沒有任何可用的解決方案
    * 確定您的專案中已指定 **網路** 攝影機功能。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實平臺功能和 Api。 接下來，您可以繼續進行下一個主題：

> [!div class="nextstepaction"]
> [對焦點](focus-point-in-unity.md)

或者，直接跳到在裝置或模擬器上部署應用程式的主題：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另請參閱
* [定位相機](../platform-capab ilities-and-apis/locatable-camera.md)
