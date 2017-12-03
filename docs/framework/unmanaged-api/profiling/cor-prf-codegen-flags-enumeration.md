---
title: "COR_PRF_CODEGEN_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODEGEN_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODEGEN_FLAGS
helpviewer_keywords: COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2c97510077fefd730827ac00326d267fd1c62ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="ccbe9-102">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="ccbe9-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="ccbe9-103">Definuje příznaky generování kódu, které lze nastavit pomocí [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ccbe9-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbe9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccbe9-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ccbe9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ccbe9-105">Members</span></span>  
  
|<span data-ttu-id="ccbe9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ccbe9-106">Member</span></span>|<span data-ttu-id="ccbe9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ccbe9-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="ccbe9-108">Žádné funkce bude vložená do těla tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="ccbe9-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="ccbe9-109">Samotná funkce však může být vložená do jeho volající.</span><span class="sxs-lookup"><span data-stu-id="ccbe9-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="ccbe9-110">Všechny optimalizace pro tělo tato funkce bude zakázáno.</span><span class="sxs-lookup"><span data-stu-id="ccbe9-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="ccbe9-111">Však samotná funkce může být stále vložená do jeho volající.</span><span class="sxs-lookup"><span data-stu-id="ccbe9-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccbe9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccbe9-112">Remarks</span></span>  
 <span data-ttu-id="ccbe9-113">`COR_PRF_CODEGEN_FLAGS` Výčet je používán [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) způsob povolení profileru k řízení generování kódu pro funkce překompilovat JIT.</span><span class="sxs-lookup"><span data-stu-id="ccbe9-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccbe9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccbe9-114">Requirements</span></span>  
 <span data-ttu-id="ccbe9-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccbe9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccbe9-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ccbe9-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ccbe9-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccbe9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccbe9-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccbe9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbe9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccbe9-119">See Also</span></span>  
 [<span data-ttu-id="ccbe9-120">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="ccbe9-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)