---
title: "CorDebugMappingResult – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 793158ef63a0de27786dc8bd9b306f10c228054e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="72771-102">CorDebugMappingResult – výčet</span><span class="sxs-lookup"><span data-stu-id="72771-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="72771-103">Poskytuje podrobnosti o tom, jak byla získána hodnota ukazatele instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="72771-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72771-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72771-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="72771-105">Členové</span><span class="sxs-lookup"><span data-stu-id="72771-105">Members</span></span>  
  
|<span data-ttu-id="72771-106">Člen</span><span class="sxs-lookup"><span data-stu-id="72771-106">Member</span></span>|<span data-ttu-id="72771-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72771-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="72771-108">Nativní kód je v prologu, takže IP hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="72771-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="72771-109">Nativní kód je v epilogu, takže hodnota IP adresa je adresa poslední pokyn metody.</span><span class="sxs-lookup"><span data-stu-id="72771-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="72771-110">Žádné informace o mapování není k dispozici v případě metody, takže IP hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="72771-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="72771-111">I když je informace o mapování pro metodu, s aktuální adresou nelze mapovat na kód Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="72771-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="72771-112">IP adresa hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="72771-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="72771-113">Buď metodu mapuje přesně MSIL kód, nebo byla interpretovat rámečku, tak hodnota IP je přesný.</span><span class="sxs-lookup"><span data-stu-id="72771-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="72771-114">Metoda byl úspěšně přiřazen, ale může být hodnota parametru IP přibližné.</span><span class="sxs-lookup"><span data-stu-id="72771-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72771-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72771-115">Remarks</span></span>  
 <span data-ttu-id="72771-116">Můžete použít [icordebugilframe::getip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodu k získání hodnoty ukazatele instrukcí.</span><span class="sxs-lookup"><span data-stu-id="72771-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72771-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72771-117">Requirements</span></span>  
 <span data-ttu-id="72771-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72771-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72771-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72771-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72771-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72771-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72771-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72771-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72771-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="72771-122">See Also</span></span>  
 [<span data-ttu-id="72771-123">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="72771-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)