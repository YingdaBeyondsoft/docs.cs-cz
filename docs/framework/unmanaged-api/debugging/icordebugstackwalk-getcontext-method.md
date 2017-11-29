---
title: "ICorDebugStackWalk::GetContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bdd910862e7198d616e79ec732708f708959d26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="72fdb-102">ICorDebugStackWalk::GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="72fdb-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="72fdb-103">Vrátí kontext pro aktuální rámec v [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="72fdb-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72fdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72fdb-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72fdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72fdb-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="72fdb-106">[v] Příznaky, které indikují požadovaný obsah vyrovnávací paměti kontextu (definovanou v souboru WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="72fdb-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="72fdb-107">[v] Přidělená velikost vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="72fdb-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="72fdb-108">[out] Skutečná velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="72fdb-108">[out] The actual size of the context.</span></span> <span data-ttu-id="72fdb-109">Tato hodnota musí být menší než nebo rovna velikosti vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="72fdb-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="72fdb-110">[out] Vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="72fdb-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72fdb-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="72fdb-111">Return Value</span></span>  
 <span data-ttu-id="72fdb-112">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="72fdb-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="72fdb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72fdb-113">HRESULT</span></span>|<span data-ttu-id="72fdb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="72fdb-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72fdb-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="72fdb-115">S_OK</span></span>|<span data-ttu-id="72fdb-116">Kontext pro aktuální rámec byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="72fdb-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="72fdb-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72fdb-117">E_FAIL</span></span>|<span data-ttu-id="72fdb-118">Kontext nejde vrátit.</span><span class="sxs-lookup"><span data-stu-id="72fdb-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="72fdb-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="72fdb-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="72fdb-120">Vyrovnávací paměti kontextu je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="72fdb-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="72fdb-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="72fdb-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="72fdb-122">Ukazatel na rámec je již na konec zásobníku; Proto je přístupná žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="72fdb-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="72fdb-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="72fdb-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72fdb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72fdb-124">Remarks</span></span>  
 <span data-ttu-id="72fdb-125">Protože unwinding obnoví pouze podmnožinu registrů, jako je například nezávislé registry, kontext nemusí přesně odpovídat stav registrace v čase volání.</span><span class="sxs-lookup"><span data-stu-id="72fdb-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72fdb-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72fdb-126">Requirements</span></span>  
 <span data-ttu-id="72fdb-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72fdb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72fdb-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72fdb-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72fdb-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72fdb-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72fdb-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72fdb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fdb-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="72fdb-131">See Also</span></span>  
 [<span data-ttu-id="72fdb-132">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="72fdb-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="72fdb-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="72fdb-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)