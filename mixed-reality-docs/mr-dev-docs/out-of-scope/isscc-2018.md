---
title: 深度相機白皮書-ISSCC 2018
description: 技術白皮書討論在 Project Kinect for Azure 和下一版 HoloLens 中使用的深度相機。
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: 活動、iscc、電腦視覺、研究、kinect、hololens、深度、tof
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683013"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="caa1e-104">深度相機白皮書-ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="caa1e-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="caa1e-105">**標題：** 1MPIXEL 65Nm BSI 320MHZ Demodulated TOF 映射感應器與3.5 μμ Global 快門圖元和類比分類收納</span><span class="sxs-lookup"><span data-stu-id="caa1e-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="caa1e-106">**參與者：** Cyrus S Bamji、Swati Mehta、Barry Thompson、Tamer Elkhatib、Stefan Wurster、Onur Akkaya、Andrew Payne、John Godbaz、Mike Fenton、Vijay Rajasekaran、Larry Prather、Satya Nagaraja、Vishali Mogallapu、來雪、Rich McCauley、Mustansir Mukadam、Iskender Agi、Shaun McCarthy、Zhanping Xu、Travis Perry、William Qian、Vei Chan、Prabhu Adepu、Gazi Muneeb、Ahmed Aditya、Mukherjee Sheethal、Nayak Dave、Gampell Sunil、Acharya Lou、Kordus O'Connor、、</span><span class="sxs-lookup"><span data-stu-id="caa1e-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="caa1e-107">**顯示于 ISSCC 2018，並以 ISSCC 技術白皮書，2018年2月的形式發行。**</span><span class="sxs-lookup"><span data-stu-id="caa1e-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="caa1e-108">C.</span><span class="sxs-lookup"><span data-stu-id="caa1e-108">C.</span></span> <span data-ttu-id="caa1e-109">Bamji et al.，"1Mpixel 65nm BSI 320MHz Demodulated TOF Image 感應器 with 3.5 μμ Global 快門圖元 and 類比分類收納" ISSCC 度</span><span class="sxs-lookup"><span data-stu-id="caa1e-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="caa1e-110">技術。</span><span class="sxs-lookup"><span data-stu-id="caa1e-110">Tech.</span></span> <span data-ttu-id="caa1e-111">論文，94-95，2018年2月。</span><span class="sxs-lookup"><span data-stu-id="caa1e-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="caa1e-112">IEEE 探索連結： https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="caa1e-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="caa1e-113">© 2018 IEEE。</span><span class="sxs-lookup"><span data-stu-id="caa1e-113">© 2018 IEEE.</span></span> <span data-ttu-id="caa1e-114">允許個人使用此材質。</span><span class="sxs-lookup"><span data-stu-id="caa1e-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="caa1e-115">您必須在任何目前或未來的媒體中取得 IEEE 的所有其他用途的許可權，包括 reprinting/重新發行此資料以供廣告或促銷之用、建立新的集體作品、轉售或轉散發至伺服器或清單，或重複使用此工作中任何受著作權保護的元件。</span><span class="sxs-lookup"><span data-stu-id="caa1e-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="caa1e-116">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="caa1e-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="caa1e-117">![白皮書預覽](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="caa1e-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="caa1e-118">下載深度攝影機白皮書</span><span class="sxs-lookup"><span data-stu-id="caa1e-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
