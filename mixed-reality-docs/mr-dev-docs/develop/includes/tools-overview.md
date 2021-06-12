---
ms.openlocfilehash: 1dc5f548df0c7628ade629c4b384c4d6144941eb
ms.sourcegitcommit: cf1c1a7cb67c850c61d3907a2519b51cd890a392
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2021
ms.locfileid: "112022808"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-recommended-unity-version"></a>1. 下載建議的 Unity 版本 

目前的混合現實開發建議版本是 **Unity 2019.4 LTS (長期支援)**。 安裝和管理 Unity 的最佳方式是透過 **Unity 中樞**。 

> [!NOTE]
>  如果您使用 Unity 2020 LTS，混合現實支援可供 HoloLens 2 開發之用。 不過，目前有一些已知問題。 這將會在今年稍後成為建議的 Unity 版本。 

請參閱 [選擇 unity 版本和 XR 外掛程式](../unity/choosing-unity-version.md) ，以瞭解有哪些混合現實支援可在不同的 Unity 引擎和 XR 外掛程式版本中使用。

> [!div class="nextstepaction"]
> [下載 Unity 中樞](https://unity3d.com/get-unity/download)

安裝 Unity 時，請務必檢查「 **平臺**」底下的下列元件。
* **通用 Windows 平臺組建支援** 
* **Windows Build 支援 (IL2CPP)**

![Unity 通用 Windows 平臺組建支援選項](../../develop/images/Unity_Install_Option_UWP.png)

如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項。

![Unity Windows Build 支援選項](../../develop/images/Unity_Install_Option_UWP2.png)


### <a name="2-install-the-mixed-reality-feature-tool"></a>2. 安裝 Mixed Reality 功能工具

「 [混合現實」功能工具](../unity/welcome-to-mr-feature-tool.md) 是一種新的方法，讓開發人員可以探索並將混合現實功能套件新增至 Unity 專案。 

您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。 驗證您想要的套件之後，混合實境功能工具會將這些套件下載到您選擇的專案。

#### <a name="importing-the-mixed-reality-toolkit"></a>匯入混合實境工具組

![MRTK](../../design/images/MRTK_UX_Hero.png)

[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。 

* 遵循 [安裝和使用方式指示](../unity/welcome-to-mr-feature-tool.md#system-requirements) ，並選取 **混合現實工具組基礎** 套件，以安裝混合現實工具組套件。

建議您在策劃 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 開發旅程中完成「開始使用」一節。 依循適用於 HoloLens 的 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。

> [!IMPORTANT]
> 請注意，安裝指示的目標是 MRTK 和 Unity 版本的最新穩定組合，也就是 **MRTK 2.7** 和 **unity 2020.3 LTS**。

> [!NOTE]
> 如果您不想要使用適用于 Unity 的 MRTK，您必須 [自行編寫所有互動和行為的腳本](../unity/configure-unity-project.md)。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)<br>**混合實境工具組-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>其他工具 [選用]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。

> [!NOTE]
> 您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。 視您的需求而定，請確定您符合下列需求。

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。 如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

#### <a name="hololens-troubleshooting"></a>HoloLens 疑難排解

##### <a name="setting-developer-mode-is-grayed-out"></a>設定開發人員模式呈現灰色

如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。 在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。 不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。

可能的解決方案包括：

* 在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式
* 建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。 
    * 此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定
* 使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。

##### <a name="i-cant-deploy-over-usb"></a>我無法透過 USB 部署

如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)。

#### <a name="immersive-vr-headset-requirements"></a>沈浸式 (VR) 頭戴式裝置需求

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 建議</th>
</tr><tr>
<td> 處理器</td><td> <b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</td><td> <b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</td>
</tr><tr>
<td> GPU</td><td> <b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</td><td><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</td>
</tr><tr>
<td> GPU 驅動程式 WDDM 版本</td><td colspan="2"> WDDM 2.2 驅動程式</td>
</tr><tr>
<td> 散熱設計功率</td><td colspan="2"> 15W 或更大</td>
</tr><tr>
<td> 圖形顯示連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</td>
</tr><tr>
<td> 顯示器解析度</td><td colspan="2"> 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 存放裝置</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：

> [!div class="nextstepaction"]
> [開始您適用於 HoloLens 的 Unity 開發旅程](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [開始您適用於 VR 的 Unity 開發旅程](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們所配置適用於 HoloLens 的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。

> [!div class="nextstepaction"]
> [HoloLens 2 教學課程系列](../unity/tutorials/mr-learning-base-01.md)

如果您要依循適用於 VR 的 Unity 旅程，下一個工作是設定您的專案。

> [!div class="nextstepaction"]
> [針對 WMR 設定您的專案](../unity/configure-unity-project.md)

您可以隨時回到適用於 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)的 Unity 開發檢查點。

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1.下載最新版本

建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。

移至長篇遊戲啟動器中的 [ **媒體** 櫃] 索引標籤，選取 [ **啟動** ] 旁的下拉箭號，然後按一下 [ **選項**]。 在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。
![Unreal 安裝選項 HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.匯入混合實境工具組 (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。 MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。 該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。

進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。 依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)<br>**混合實境工具組-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。

#### <a name="other-tools-optional"></a>其他工具 [選用]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。

> [!NOTE]
> 您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。 視您的需求而定，請確定您符合下列需求。

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。 如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

#### <a name="hololens-troubleshooting"></a>HoloLens 疑難排解

##### <a name="setting-developer-mode-is-grayed-out"></a>設定開發人員模式呈現灰色

如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。 在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。 不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。

可能的解決方案包括：

* 在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式
* 建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。 
    * 此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定
* 使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。

##### <a name="i-cant-deploy-over-usb"></a>我無法透過 USB 部署

如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unreal/tutorials/unreal-uxt-ch6.md)。

#### <a name="immersive-vr-headset-requirements"></a>沈浸式 (VR) 頭戴式裝置需求

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 建議</th>
</tr><tr>
<td> 處理器</td><td> <b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</td><td> <b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</td>
</tr><tr>
<td> GPU</td><td> <b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</td><td><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</td>
</tr><tr>
<td> GPU 驅動程式 WDDM 版本</td><td colspan="2"> WDDM 2.2 驅動程式</td>
</tr><tr>
<td> 散熱設計功率</td><td colspan="2"> 15W 或更大</td>
</tr><tr>
<td> 圖形顯示連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</td>
</tr><tr>
<td> 顯示器解析度</td><td colspan="2"> 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 存放裝置</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：

> [!div class="nextstepaction"]
> [開始您的 Unreal 旅程](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。

> [!div class="nextstepaction"]
> [HoloLens 2 教學課程系列](../unreal/tutorials/unreal-uxt-ch1.md)

您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。

# <a name="native-openxr"></a>[原生 (OpenXR)](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

原生 OpenXR 開發沒有可供您下載的引擎。 您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。 如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

> [!NOTE]
> 您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。 視您的需求而定，請確定您符合下列需求。

#### <a name="hololens-troubleshooting"></a>HoloLens 疑難排解

##### <a name="setting-developer-mode-is-grayed-out"></a>設定開發人員模式呈現灰色

如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。 在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。 不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。

可能的解決方案包括：

* 在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式
* 建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。 
    * 此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定
* 使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。

#### <a name="immersive-vr-headset-requirements"></a>沈浸式 (VR) 頭戴式裝置需求

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 建議</th>
</tr><tr>
<td> 處理器</td><td> <b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</td><td> <b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</td>
</tr><tr>
<td> GPU</td><td> <b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</td><td><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</td>
</tr><tr>
<td> GPU 驅動程式 WDDM 版本</td><td colspan="2"> WDDM 2.2 驅動程式</td>
</tr><tr>
<td> 散熱設計功率</td><td colspan="2"> 15W 或更大</td>
</tr><tr>
<td> 圖形顯示連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</td>
</tr><tr>
<td> 顯示器解析度</td><td colspan="2"> 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 存放裝置</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：

> [!div class="nextstepaction"]
> [開始您的原生旅程](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。

> [!div class="nextstepaction"]
> [設定 HoloLens 2](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。