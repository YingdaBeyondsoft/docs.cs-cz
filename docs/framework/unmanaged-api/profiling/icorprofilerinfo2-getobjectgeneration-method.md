---
title: "ICorProfilerInfo2::GetObjectGeneration – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e90139f96638dbb1a183f98e754838ff52424fc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="e6d19-102">ICorProfilerInfo2::GetObjectGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d19-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="e6d19-103">Získá segment haldě, které obsahuje zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="e6d19-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6d19-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6d19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6d19-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e6d19-106">[v] ID objektu.</span><span class="sxs-lookup"><span data-stu-id="e6d19-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="e6d19-107">[out] Ukazatel [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktura, která popisuje rozsah (to znamená, blok) paměti v generaci, kterou právě probíhá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e6d19-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="e6d19-108">Tento rozsah obsahuje zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="e6d19-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6d19-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6d19-109">Remarks</span></span>  
 <span data-ttu-id="e6d19-110">`GetObjectGeneration` Může být volána metoda žádné profileru zpětné volání, za předpokladu, že není v průběhu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e6d19-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="e6d19-111">To znamená, může být volána z jakékoli zpětného volání kromě těch, které se vyskytnou mezi [icorprofilercallback2::garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) a [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="e6d19-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d19-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6d19-112">Requirements</span></span>  
 <span data-ttu-id="e6d19-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d19-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d19-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6d19-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6d19-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6d19-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6d19-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d19-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6d19-117">See Also</span></span>  
 [<span data-ttu-id="e6d19-118">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6d19-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e6d19-119">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6d19-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)