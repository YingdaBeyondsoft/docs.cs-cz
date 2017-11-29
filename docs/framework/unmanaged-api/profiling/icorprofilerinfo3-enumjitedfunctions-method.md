---
title: "ICorProfilerInfo3::EnumJITedFunctions – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c367ae29cc0daa406356a245f3dc16a671d3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="39e9a-102">ICorProfilerInfo3::EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="39e9a-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="39e9a-103">Vrátí enumerátor pro všechny funkce, které byly dříve kompilována.</span><span class="sxs-lookup"><span data-stu-id="39e9a-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39e9a-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39e9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39e9a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="39e9a-106">[out] Ukazatel [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerátor.</span><span class="sxs-lookup"><span data-stu-id="39e9a-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39e9a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39e9a-107">Remarks</span></span>  
 <span data-ttu-id="39e9a-108">Tato metoda se mohou překrývat s `JITCompilation` zpětná volání, jako [icorprofilercallback::jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="39e9a-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="39e9a-109">Tato metoda vrátí enumerátor neobsahuje funkce, které jsou načteny z vygeneroval s Ngen.exe nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="39e9a-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39e9a-110">Vrácený výčtu obsahuje pouze "0" pro hodnotu `COR_PRF_FUNCTION::reJitId` pole.</span><span class="sxs-lookup"><span data-stu-id="39e9a-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="39e9a-111">Pokud budete potřebovat platný `COR_PRF_FUNCTION::reJitId` hodnoty, použijte [icorprofilerinfo4::enumjitedfunctions2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="39e9a-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39e9a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39e9a-112">Requirements</span></span>  
 <span data-ttu-id="39e9a-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39e9a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39e9a-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="39e9a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39e9a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39e9a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39e9a-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39e9a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e9a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="39e9a-117">See Also</span></span>  
 [<span data-ttu-id="39e9a-118">Icorprofilerinfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39e9a-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="39e9a-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="39e9a-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="39e9a-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="39e9a-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)