---
title: "ICorProfilerCallback::UnmanagedToManagedTransition – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.UnmanagedToManagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a2ceb53263e317c5c72695d6bc1e93f8f70bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="ff7be-102">ICorProfilerCallback::UnmanagedToManagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="ff7be-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="ff7be-103">Upozorní profileru došlo k chybě přechod z nespravovaného kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ff7be-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff7be-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff7be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff7be-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ff7be-106">[v] ID funkce, která je volána.</span><span class="sxs-lookup"><span data-stu-id="ff7be-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="ff7be-107">[v] Hodnota [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) výčtu, která určuje, zda přechodu nebo došlo k chybě z důvodu volání do spravovaného kódu z nespravovaného kódu, z důvodu zpětné z nespravované funkce volá spravované jeden.</span><span class="sxs-lookup"><span data-stu-id="ff7be-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff7be-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff7be-108">Remarks</span></span>  
 <span data-ttu-id="ff7be-109">Pokud hodnota `reason` je COR_PRF_TRANSITION_RETURN a `functionId` není null, funkce ID je, že nespravované funkce a se nikdy sestavili jsme pomocí kompilátoru v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="ff7be-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="ff7be-110">Nespravované funkce mají některé základní informace související s nimi, jako je například název a některá metadata.</span><span class="sxs-lookup"><span data-stu-id="ff7be-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="ff7be-111">Pokud hodnota `reason` je COR_PRF_TRANSITION_CALL, je možné, že volaná funkce (který je spravovaný funkce) dosud nebyla kompilována.</span><span class="sxs-lookup"><span data-stu-id="ff7be-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff7be-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff7be-112">Requirements</span></span>  
 <span data-ttu-id="ff7be-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff7be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff7be-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff7be-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff7be-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff7be-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff7be-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff7be-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff7be-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff7be-117">See Also</span></span>  
 [<span data-ttu-id="ff7be-118">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff7be-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ff7be-119">Managedtounmanagedtransition – metoda</span><span class="sxs-lookup"><span data-stu-id="ff7be-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [<span data-ttu-id="ff7be-120">Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="ff7be-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [<span data-ttu-id="ff7be-121">Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)</span><span class="sxs-lookup"><span data-stu-id="ff7be-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)