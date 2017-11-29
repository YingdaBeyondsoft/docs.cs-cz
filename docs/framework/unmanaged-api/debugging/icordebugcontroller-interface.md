---
title: ICorDebugController Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b1484d6bcfa77b8bf5fe45b2f83d5dcbff02f907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="7470b-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="7470b-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="7470b-103">Představuje obor, buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu se dá řídit kontextu.</span><span class="sxs-lookup"><span data-stu-id="7470b-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7470b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7470b-104">Methods</span></span>  
  
|<span data-ttu-id="7470b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-105">Method</span></span>|<span data-ttu-id="7470b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7470b-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="7470b-107">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="7470b-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="7470b-108">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="7470b-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="7470b-109">Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="7470b-110">Pokračuje v provádění spravovaných vláknech po volání [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="7470b-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="7470b-111">Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="7470b-112">Umožňuje odpojit ladicí program z domény procesů nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="7470b-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="7470b-113">Enumeratethreads – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="7470b-114">Získá enumerátor pro aktivní spravovaných vláken v procesu.</span><span class="sxs-lookup"><span data-stu-id="7470b-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="7470b-115">Hasqueuedcallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="7470b-116">Získá hodnotu, která určuje, zda všechny spravované zpětná volání jsou aktuálně ve frontě pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="7470b-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="7470b-117">Isrunning – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="7470b-118">Získá hodnotu, která určuje, zda vláken v procesu jsou aktuálně spuštěny volně.</span><span class="sxs-lookup"><span data-stu-id="7470b-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="7470b-119">Setallthreadsdebugstate – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="7470b-120">Nastaví ladění stav všech spravovaných vláken v procesu.</span><span class="sxs-lookup"><span data-stu-id="7470b-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="7470b-121">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="7470b-122">Provede spolupráci zastavení všech vláken, které jsou spuštěny spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="7470b-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="7470b-123">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="7470b-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="7470b-124">Ukončí proces uvedený ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="7470b-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7470b-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7470b-125">Remarks</span></span>  
 <span data-ttu-id="7470b-126">Pokud `ICorDebugController` je proces řízení, oboru zahrnuje všechny podprocesy procesu.</span><span class="sxs-lookup"><span data-stu-id="7470b-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="7470b-127">Pokud `ICorDebugController` je řízení doménu aplikace, rozsah obsahuje pouze vláken této domény konkrétní aplikace.</span><span class="sxs-lookup"><span data-stu-id="7470b-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7470b-128">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7470b-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7470b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7470b-129">Requirements</span></span>  
 <span data-ttu-id="7470b-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7470b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7470b-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7470b-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7470b-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7470b-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7470b-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7470b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7470b-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7470b-134">See Also</span></span>  
 [<span data-ttu-id="7470b-135">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7470b-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)