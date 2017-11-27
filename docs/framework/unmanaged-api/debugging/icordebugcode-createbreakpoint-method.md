---
title: "ICorDebugCode::CreateBreakpoint – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 214d032129613230b8c55cdd286ea637227a626e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="f97b2-102">ICorDebugCode::CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="f97b2-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="f97b2-103">Vytvoří zarážky v tomto segmentu kódu na zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="f97b2-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f97b2-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f97b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f97b2-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="f97b2-106">[v] Posun, pro kterou chcete vytvořit bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="f97b2-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="f97b2-107">[out] Ukazatel na adresu "ICorDebugFunctionBreakpoint" objekt, který představuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="f97b2-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f97b2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f97b2-108">Remarks</span></span>  
 <span data-ttu-id="f97b2-109">Předtím, než je aktivní bod přerušení, musí být přidané na objekt procesu.</span><span class="sxs-lookup"><span data-stu-id="f97b2-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="f97b2-110">Pokud tento kód je kód Microsoft intermediate language (MSIL), a dojde v běhu (JIT)-kompilované, nativní verzi kód zarážce se použijí v kompilována kódu.</span><span class="sxs-lookup"><span data-stu-id="f97b2-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="f97b2-111">(Stejná je hodnota true, pokud kód je kompilována později.)</span><span class="sxs-lookup"><span data-stu-id="f97b2-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f97b2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f97b2-112">Requirements</span></span>  
 <span data-ttu-id="f97b2-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f97b2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f97b2-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f97b2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f97b2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f97b2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f97b2-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f97b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97b2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f97b2-117">See Also</span></span>  
 