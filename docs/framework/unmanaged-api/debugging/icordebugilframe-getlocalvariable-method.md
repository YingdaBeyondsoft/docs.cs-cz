---
title: "ICorDebugILFrame::GetLocalVariable – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetLocalVariable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 24b4ed62c3fb68306683d2199f901ec510f0da6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="3eb83-102">ICorDebugILFrame::GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="3eb83-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="3eb83-103">Získá hodnotu zadaného místní proměnné v rámci zásobníku tento Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="3eb83-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eb83-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3eb83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3eb83-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="3eb83-106">[v] Index místní proměnné v rámci této MSIL zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3eb83-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3eb83-107">[out] Ukazatel na adresu ICorDebugValue objekt, který reprezentuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3eb83-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eb83-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3eb83-108">Remarks</span></span>  
 <span data-ttu-id="3eb83-109">`GetLocalVariable` Metodu lze použít rámce zásobníku MSIL nebo v rámci kompilované v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="3eb83-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eb83-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3eb83-110">Requirements</span></span>  
 <span data-ttu-id="3eb83-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb83-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb83-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3eb83-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3eb83-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eb83-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eb83-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb83-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>