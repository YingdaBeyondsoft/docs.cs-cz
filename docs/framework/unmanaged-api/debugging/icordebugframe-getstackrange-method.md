---
title: "ICorDebugFrame::GetStackRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1db7617d52e07489ade339b76023e21816835ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="1c138-102">ICorDebugFrame::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="1c138-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="1c138-103">Získá absolutní adresu rozsahu tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1c138-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c138-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c138-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c138-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c138-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="1c138-106">[out] Ukazatel `CORDB_ADDRESS` určující počáteční adresa rámce zásobníku reprezentována to `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="1c138-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="1c138-107">[out] Ukazatel `CORDB_ADDRESS` určující koncová adresa rámce zásobníku reprezentována to `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="1c138-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c138-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c138-108">Remarks</span></span>  
 <span data-ttu-id="1c138-109">Rozsah adres v zásobníku je užitečné pro piecing společně trasování prokládaná zásobníku získané z více ladění webů.</span><span class="sxs-lookup"><span data-stu-id="1c138-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="1c138-110">Číselný rozsah poskytuje žádné informace o obsahu rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1c138-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="1c138-111">Je smysl jenom pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1c138-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c138-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c138-112">Requirements</span></span>  
 <span data-ttu-id="1c138-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c138-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c138-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c138-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c138-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c138-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c138-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c138-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>