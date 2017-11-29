---
title: "ICorDebugProcess::IsTransitionStub – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60f6e4116768d2d855edd941df796167754b3ab4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="536e9-102">ICorDebugProcess::IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="536e9-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="536e9-103">Získá hodnotu, která určuje, zda je adresa uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="536e9-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="536e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="536e9-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="536e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="536e9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="536e9-106">[v] A `CORDB_ADDRESS` hodnotu, která určuje adresu nejistá.</span><span class="sxs-lookup"><span data-stu-id="536e9-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="536e9-107">[out] Ukazatel na logickou hodnotu, která je `true` Pokud zadaná adresa je uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu; v opačném případě *`pbTransitionStub` je `false`.</span><span class="sxs-lookup"><span data-stu-id="536e9-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise *`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="536e9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="536e9-108">Remarks</span></span>  
 <span data-ttu-id="536e9-109">`IsTransitionStub` Metoda lze pomocí nespravovaného kódu taktování při rozhodování, kdy se vraťte do spravovaných krokovač taktování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="536e9-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="536e9-110">Můžete také zástupných procedur přechod identity prohlížením informace do přenosného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="536e9-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="536e9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="536e9-111">Requirements</span></span>  
 <span data-ttu-id="536e9-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="536e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="536e9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="536e9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="536e9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="536e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="536e9-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="536e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>