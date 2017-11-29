---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 421cff28e84106c0859889e6f9e99e870b469a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="64569-102">ICorDebugDataTarget2::CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="64569-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="64569-103">Vytvoří nový unwinder zásobníku, která se spouští unwinding z kontextu počáteční (který není nutně listu vlákna).</span><span class="sxs-lookup"><span data-stu-id="64569-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64569-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64569-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64569-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64569-105">Parameters</span></span>  
 <span data-ttu-id="64569-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="64569-106">nativeThreadID</span></span>  
 <span data-ttu-id="64569-107">[v] Nativní vlákno ID vlákna, jejichž zásobník má být oddělen.</span><span class="sxs-lookup"><span data-stu-id="64569-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="64569-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="64569-108">contextFlags</span></span>  
 <span data-ttu-id="64569-109">[v] Příznaky, které určují, jaké části kontextu jsou definovány v `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="64569-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="64569-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="64569-110">cbContext</span></span>  
 <span data-ttu-id="64569-111">[v] Velikost `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="64569-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="64569-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="64569-112">initialContext</span></span>  
 <span data-ttu-id="64569-113">[v] Data v kontextu.</span><span class="sxs-lookup"><span data-stu-id="64569-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="64569-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="64569-114">ppUnwinder</span></span>  
 <span data-ttu-id="64569-115">[out] Ukazatel na adresu objekt rozhraní ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="64569-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64569-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64569-116">Return Value</span></span>  
 <span data-ttu-id="64569-117">`S_OK`Pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="64569-117">`S_OK` if successful.</span></span> <span data-ttu-id="64569-118">Žádné jiné `HRESULT` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="64569-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="64569-119">Všechny selhání `HRESULT` přijatých mscordbi považuje za závažné a způsobí, že [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody vrátit `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="64569-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64569-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64569-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64569-121">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="64569-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64569-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64569-122">Requirements</span></span>  
 <span data-ttu-id="64569-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64569-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64569-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64569-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64569-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64569-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64569-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64569-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64569-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="64569-127">See Also</span></span>  
 [<span data-ttu-id="64569-128">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="64569-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="64569-129">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="64569-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)