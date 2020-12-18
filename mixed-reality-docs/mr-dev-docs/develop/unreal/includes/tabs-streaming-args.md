---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855877"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="c6e2f-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c6e2f-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="c6e2f-102">選項</span><span class="sxs-lookup"><span data-stu-id="c6e2f-102">Option</span></span> | <span data-ttu-id="c6e2f-103">說明</span><span class="sxs-lookup"><span data-stu-id="c6e2f-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="c6e2f-104">取得要作為連線目標的 HoloLens 2 裝置 IP 位址 (和選擇性連接埠)。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="c6e2f-105">如果未提供連接埠，則預設為 8265。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="c6e2f-106">(選擇性) 預設值 8000。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-106">(optional) Default 8000.</span></span> <span data-ttu-id="c6e2f-107">最大網路傳輸速率 (kb/s)。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="c6e2f-108">(選擇性) 啟動接聽伺服器</span><span class="sxs-lookup"><span data-stu-id="c6e2f-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="c6e2f-109">(選擇性) 取得要接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="c6e2f-110">用於從 HoloLens 裝置連線到電腦或 VM。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="c6e2f-111">(在 4.26 中已過時) 取得要作為連線目標的 HoloLens 1 裝置 IP 位址</span><span class="sxs-lookup"><span data-stu-id="c6e2f-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="c6e2f-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c6e2f-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="c6e2f-113">選項</span><span class="sxs-lookup"><span data-stu-id="c6e2f-113">Option</span></span> | <span data-ttu-id="c6e2f-114">說明</span><span class="sxs-lookup"><span data-stu-id="c6e2f-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="c6e2f-115">取得要作為連線目標的 HoloLens 2 裝置 IP 位址 (和選擇性連接埠，預設值 8265)，或是應用程式應用來接聽連線的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="c6e2f-116">(選擇性) 在遠端處理時使用來自電腦的音訊</span><span class="sxs-lookup"><span data-stu-id="c6e2f-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="c6e2f-117">(選擇性) 啟動接聽伺服器</span><span class="sxs-lookup"><span data-stu-id="c6e2f-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="c6e2f-118">(選擇性) 預設值 8000。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-118">(optional) Default 8000.</span></span> <span data-ttu-id="c6e2f-119">最大網路傳輸速率 (kb/s)。</span><span class="sxs-lookup"><span data-stu-id="c6e2f-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="c6e2f-120">(選擇性) 連線轉碼器</span><span class="sxs-lookup"><span data-stu-id="c6e2f-120">(optional) Connection codec</span></span>  |