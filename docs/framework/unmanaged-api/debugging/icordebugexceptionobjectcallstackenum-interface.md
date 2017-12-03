---
title: "ICorDebugExceptionObjectCallStackEnum::Next – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords: ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4814de2de71ba0fa4d1400f0be27fa4942febf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="e1f35-102">ICorDebugExceptionObjectCallStackEnum::Next – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1f35-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="e1f35-103">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="e1f35-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="e1f35-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="e1f35-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1f35-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e1f35-105">Methods</span></span>  
  
|<span data-ttu-id="e1f35-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e1f35-106">Method</span></span>|<span data-ttu-id="e1f35-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e1f35-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1f35-108">Icordebugexceptionobjectcallstackenum::Next –</span><span class="sxs-lookup"><span data-stu-id="e1f35-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="e1f35-109">Získá zadaný počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objekty, které obsahují informace o zásobník volání objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="e1f35-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1f35-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1f35-110">Remarks</span></span>  
 <span data-ttu-id="e1f35-111">`ICorDebugExceptionObjectCallStackEnum` Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="e1f35-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e1f35-112">`ICorDebugExceptionObjectCallStackEnum` Se zobrazí v instanci [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objekty voláním [icordebugexceptionobjectvalue::enumerateexceptioncallstack –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="e1f35-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="e1f35-113">Mohou být uvedené položky zásobníku volání v kolekci voláním [icordebugexceptionobjectcallstackenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) – metoda</span><span class="sxs-lookup"><span data-stu-id="e1f35-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1f35-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1f35-114">Requirements</span></span>  
 <span data-ttu-id="e1f35-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1f35-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f35-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1f35-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1f35-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1f35-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1f35-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f35-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f35-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1f35-119">See Also</span></span>  
 [<span data-ttu-id="e1f35-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1f35-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e1f35-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="e1f35-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)