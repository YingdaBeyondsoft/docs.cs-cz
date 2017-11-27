---
title: "ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e420d27fa1bf122b794489b00853555a7005e69e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="67a4e-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="67a4e-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="67a4e-103">Upozorní profileru, že byla dokončena fázi unwind výjimek unwinding funkce.</span><span class="sxs-lookup"><span data-stu-id="67a4e-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67a4e-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="67a4e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67a4e-105">Remarks</span></span>  
 <span data-ttu-id="67a4e-106">Když `ExceptionUnwindFunctionLeave` metoda je volána, instance funkce a jeho zásobníku data se odeberou ze zásobníku.</span><span class="sxs-lookup"><span data-stu-id="67a4e-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="67a4e-107">Profileru by neměly blokovat během toto volání, protože zásobníku nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="67a4e-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="67a4e-108">Pokud na profileru bloky a uvolnění paměti dojde k pokusu o, modul runtime zablokuje, dokud vrátí tuto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="67a4e-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="67a4e-109">Navíc během tohoto hovoru profileru nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="67a4e-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a4e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67a4e-110">Requirements</span></span>  
 <span data-ttu-id="67a4e-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a4e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a4e-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67a4e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67a4e-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67a4e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67a4e-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a4e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a4e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="67a4e-115">See Also</span></span>  
 [<span data-ttu-id="67a4e-116">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67a4e-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="67a4e-117">Exceptionunwindfunctionenter – metoda</span><span class="sxs-lookup"><span data-stu-id="67a4e-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)