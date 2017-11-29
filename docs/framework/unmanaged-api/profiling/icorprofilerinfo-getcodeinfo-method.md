---
title: "ICorProfilerInfo::GetCodeInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCodeInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0b5c7b0d932200f04df0a1a84dd1f747b7945943
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="917b3-102">ICorProfilerInfo::GetCodeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="917b3-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="917b3-103">Získá rozsah nativní kód spojený s ID zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="917b3-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="917b3-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="917b3-104">This method is obsolete.</span></span> <span data-ttu-id="917b3-105">Použití [ICorProfilerInfo2::getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="917b3-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="917b3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="917b3-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="917b3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="917b3-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="917b3-108">[v] ID funkce, ke kterému je přiřazeno nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="917b3-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="917b3-109">[out] Ukazatel na pole bajtů, které tvoří nativní kód funkce.</span><span class="sxs-lookup"><span data-stu-id="917b3-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="917b3-110">[out] Ukazatel na celé číslo, které určuje velikost v bajtech nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="917b3-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="917b3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="917b3-111">Remarks</span></span>  
 <span data-ttu-id="917b3-112">Za účelem optimalizace výkonu modulu runtime v rozhraní .NET Framework verze 2.0 rozdělí kód předkompilovaných, nativní funkce do několika oblastí.</span><span class="sxs-lookup"><span data-stu-id="917b3-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="917b3-113">V důsledku toho `GetCodeInfo` metoda je zastaralé v rozhraní .NET Framework 2.0, protože se nepodařilo zpracovat rozsah nativního kódu funkce.</span><span class="sxs-lookup"><span data-stu-id="917b3-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="917b3-114">Profilery musí přejít k používání další Obecné `ICorProfilerInfo2::GetCodeInfo2` metoda místo.</span><span class="sxs-lookup"><span data-stu-id="917b3-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="917b3-115">Tato funkce využívá volající přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="917b3-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="917b3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="917b3-116">Requirements</span></span>  
 <span data-ttu-id="917b3-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="917b3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="917b3-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="917b3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="917b3-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="917b3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="917b3-120">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="917b3-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="917b3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="917b3-121">See Also</span></span>  
 [<span data-ttu-id="917b3-122">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="917b3-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="917b3-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="917b3-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="917b3-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="917b3-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)