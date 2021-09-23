---
ms.openlocfilehash: 12634c1fc18366e28a51688b19fc739ea69d37ec
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184615"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| 選項 | 說明 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | 取得要作為連線目標的 HoloLens 2 裝置 IP 位址 (和選擇性連接埠)。 如果未提供連接埠，則預設為 8265。 |
| `-RemotingBitrate=<bitrate>` | (選擇性) 預設值 8000。 最大網路傳輸速率 (kb/s)。 |
| `-HoloLensRemotingListen` | (選擇性) 啟動接聽伺服器 |
| `-HoloLensRemotingListenPort=<port>` | (選擇性) 取得要接聽的連接埠。 用於從 HoloLens 裝置連線到電腦或 VM。 |
| `-HoloLens1Remoting=<IP address>` | (在 4.26 中已過時) 取得要作為連線目標的 HoloLens 1 裝置 IP 位址 |
| `-eyetracking=WindowsMixedRealityEyeTracker` |  (選用) 使用 Windows Mixed Reality 眼睛追蹤器 |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| 選項 | 說明 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | 取得要作為連線目標的 HoloLens 2 裝置 IP 位址 (和選擇性連接埠，預設值 8265)，或是應用程式應用來接聽連線的連接埠。 |
| `-EnableAudio` | (選擇性) 在遠端處理時使用來自電腦的音訊  |
| `-Listen` | (選擇性) 啟動接聽伺服器 |
| `-RemotingBitrate=<bitrate>` | (選擇性) 預設值 8000。 最大網路傳輸速率 (kb/s)。 |
| `-RemotingCodec=<codec>` | (選擇性) 連線轉碼器  |
| `-eyetracking=OpenXREyeTracker` |  (選擇性) 使用 OpenXR 眼追蹤器 |