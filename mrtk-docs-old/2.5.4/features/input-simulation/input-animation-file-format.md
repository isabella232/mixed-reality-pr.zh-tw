---
title: InputAnimationFileFormat
description: MRTK 中輸入動畫二進位檔案格式規格的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 5ec2b3f3ac83ee0ca1923cb62b36fe80edc22120
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779908"
---
# <a name="input-animation-binary-file-format-specification"></a>輸入動畫二進位檔案格式規格

## <a name="overall-structure"></a>整體結構

輸入動畫二進位檔案的開頭為64位整數魔術數位。 這個數位的十六進位標記法值是 `0x6a8faf6e0f9e42c6` ，而且可以用來識別有效的輸入動畫檔案。

接下來八個位元組是兩個 Int32 值，用來宣告檔案的主要和次要版本號碼。

檔案的其餘部分是由動畫資料所佔用，可能會在版本號碼之間變更。

| 區段 | 類型 |
|---------|------|
| 魔術數位 | Int64 |
| 主要版本號碼 | Int32 |
| 次要版本號碼 | Int32 |
| 動畫資料 | _請參閱版本區段_ |

## <a name="version-10"></a>版本 1.0

輸入動畫資料包含一連串的動畫曲線。 動畫曲線的數目和意義是固定的，但每個曲線都可以有不同的主要畫面格數目。

| 區段 | 類型 |
|---------|------|
| 相機 | [姿勢曲線](#pose-curves) |
| 靠右追蹤 | [布林曲線](#boolean-curve) |
| 右側追蹤 | [布林曲線](#boolean-curve) |
| 向左捏合手 | [布林曲線](#boolean-curve) |
| 右手捏合 Right | [布林曲線](#boolean-curve) |
| 左邊的接點 | [聯合姿勢曲線](#joint-pose-curves) |
| 右邊 | [聯合姿勢曲線](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>聯合姿勢曲線

每次都會儲存一連串的聯合動畫曲線。 接點的數目是固定的，而且會針對每個聯合儲存一組姿勢曲線。

| 區段 | 類型 |
|---------|------|
| 無 | [姿勢曲線](#pose-curves) |
| 手腕 | [姿勢曲線](#pose-curves) |
| Palm | [姿勢曲線](#pose-curves) |
| ThumbMetacarpalJoint | [姿勢曲線](#pose-curves) |
| ThumbProximalJoint | [姿勢曲線](#pose-curves) |
| ThumbDistalJoint | [姿勢曲線](#pose-curves) |
| ThumbTip | [姿勢曲線](#pose-curves) |
| IndexMetacarpal | [姿勢曲線](#pose-curves) |
| IndexKnuckle | [姿勢曲線](#pose-curves) |
| IndexMiddleJoint | [姿勢曲線](#pose-curves) |
| IndexDistalJoint | [姿勢曲線](#pose-curves) |
| IndexTip | [姿勢曲線](#pose-curves) |
| MiddleMetacarpal | [姿勢曲線](#pose-curves) |
| MiddleKnuckle | [姿勢曲線](#pose-curves) |
| MiddleMiddleJoint | [姿勢曲線](#pose-curves) |
| MiddleDistalJoint | [姿勢曲線](#pose-curves) |
| MiddleTip | [姿勢曲線](#pose-curves) |
| RingMetacarpal | [姿勢曲線](#pose-curves) |
| RingKnuckle | [姿勢曲線](#pose-curves) |
| RingMiddleJoint | [姿勢曲線](#pose-curves) |
| RingDistalJoint | [姿勢曲線](#pose-curves) |
| RingTip | [姿勢曲線](#pose-curves) |
| PinkyMetacarpal | [姿勢曲線](#pose-curves) |
| PinkyKnuckle | [姿勢曲線](#pose-curves) |
| PinkyMiddleJoint | [姿勢曲線](#pose-curves) |
| PinkyDistalJoint | [姿勢曲線](#pose-curves) |
| PinkyTip | [姿勢曲線](#pose-curves) |

### <a name="pose-curves"></a>姿勢曲線

姿勢曲線是位置向量的三個動畫曲線序列，後面接著4個旋轉四元數的動畫曲線。

| 區段 | 類型 |
|---------|------|
| 位置 X | [浮點數曲線](#float-curve) |
| 位置 Y | [浮點數曲線](#float-curve) |
| 位置 Z | [浮點數曲線](#float-curve) |
| 旋轉 X | [浮點數曲線](#float-curve) |
| 旋轉 Y | [浮點數曲線](#float-curve) |
| 旋轉 Z | [浮點數曲線](#float-curve) |
| 旋轉 W | [浮點數曲線](#float-curve) |

### <a name="float-curve"></a>浮點數曲線

浮點數曲線是具有不定數目之主要畫面格的完備貝茲曲線。 每個主要畫面格都會儲存時間和曲線值，以及每個主要畫面格左右側邊的正切和加權。

| 區段 | 類型 |
|---------|------|
| 預先換行模式 | Int32、 [Wrap 模式](#wrap-mode) |
| 後置換行模式 | Int32、 [Wrap 模式](#wrap-mode) |
| 關鍵畫面數 | Int32 |
| 關鍵 幀 | [Float 主要畫面格](#float-keyframe) |

### <a name="float-keyframe"></a>Float 主要畫面格

Float 主要畫面格會在基本時間和值的旁邊儲存正切值和加權值。

| 區段 | 類型 |
|---------|------|
| Time | Float32 |
| 值 | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32、 [加權模式](#weighted-mode) |

### <a name="boolean-curve"></a>布林曲線

布林曲線是開啟/關閉值的簡單序列。 在每個主要畫面上，曲線的值會立即翻轉。

| 區段 | 類型 |
|---------|------|
| 預先換行模式 | Int32、 [Wrap 模式](#wrap-mode) |
| 後置換行模式 | Int32、 [Wrap 模式](#wrap-mode) |
| 關鍵畫面數 | Int32 |
| 關鍵 幀 | [布林主要畫面格](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>布林主要畫面格

布林值主要畫面格只會儲存時間和值。

| 區段 | 類型 |
|---------|------|
| Time | Float32 |
| 值 | Float32 |

### <a name="wrap-mode"></a>Wrap 模式

前置和後置換行模式的語法遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定義。 它們是下列位的組合：

| 值 | 意義 |
|-------|---------|
| 0 | 預設值：讀取設定為較高的預設重複模式。 |
| 1 | 一次：當時間到達動畫剪輯的結尾時，剪輯將會自動停止播放，而時間將會重設為剪輯的開頭。 |
| 2 | Loop：當時間達到動畫剪輯的結尾時，時間會在一開始就繼續進行。 |
| 4 | PingPong：當時間達到動畫剪輯的結尾時，時間會在開始與結束時 ping 一次。 |
| 8 | ClampForever：播放動畫。 到達結束時，它會繼續播放最後一個畫面格，而且永遠不會停止播放。 |

### <a name="weighted-mode"></a>加權模式

加權模式的語義遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定義。

| 值 | 意義 |
|-------|---------|
| 0 | None：在計算曲線區段時排除 inWeight 或 outWeight。 |
| 1 | 在中：在計算上一個曲線區段時包含 inWeight。 |
| 2 | Out：在計算下一個曲線區段時包含 outWeight。 |
| 3 | 兩者：在計算曲線區段時包含 inWeight 和 outWeight。 |
