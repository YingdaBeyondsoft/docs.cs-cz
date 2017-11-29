---
title: "EClrFailure – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94358fd0626fa17f1fd6d3c365aff79f89dde467
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="b298f-102">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="b298f-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="b298f-103">Popisuje sadu chyb, pro které hostitele může nastavit zásady akce.</span><span class="sxs-lookup"><span data-stu-id="b298f-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b298f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b298f-104">Syntax</span></span>  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="b298f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b298f-105">Members</span></span>  
  
|<span data-ttu-id="b298f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b298f-106">Member</span></span>|<span data-ttu-id="b298f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b298f-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="b298f-108">Došlo k chybě při pokusu o přidělení prostředků (například vlákno, blok paměti nebo zámek) v oblasti nekritické kódu.</span><span class="sxs-lookup"><span data-stu-id="b298f-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="b298f-109">Došlo k chybě při pokusu o přidělení prostředků (například vlákno, blok paměti nebo zámek) v oblasti kritické kódu.</span><span class="sxs-lookup"><span data-stu-id="b298f-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="b298f-110">Modul CLR (CLR) je již možné spouštět spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="b298f-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="b298f-111">Volání jakékoli hostování funkce vrací od nynějška, má hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b298f-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="b298f-112">Vlákno se nepodařilo uvolnit zámek při vrácení z <xref:System.AppDomain> objektu.</span><span class="sxs-lookup"><span data-stu-id="b298f-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="b298f-113">Hostitele nelze nastavit této chyby a způsobit, že vlákno k přerušení.</span><span class="sxs-lookup"><span data-stu-id="b298f-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="b298f-114">Došlo k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b298f-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="b298f-115">Došlo k pokusu o čtení nebo zápisu chráněné paměti.</span><span class="sxs-lookup"><span data-stu-id="b298f-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="b298f-116">Není podporováno v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b298f-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="b298f-117">Kontrakt kódu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="b298f-117">A code contract failure occurred.</span></span> <span data-ttu-id="b298f-118">V tématu [Code kontrakty](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b298f-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b298f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b298f-119">Remarks</span></span>  
 <span data-ttu-id="b298f-120">Najdete v článku [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda seznam [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou hostiteli můžete použít k určení akce zásad podmínky při selhání.</span><span class="sxs-lookup"><span data-stu-id="b298f-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="b298f-121">Další informace o oblastech kritické a nekritické kódu najdete v tématu [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b298f-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b298f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b298f-122">Requirements</span></span>  
 <span data-ttu-id="b298f-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b298f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b298f-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b298f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b298f-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b298f-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b298f-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b298f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b298f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b298f-127">See Also</span></span>  
 [<span data-ttu-id="b298f-128">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b298f-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="b298f-129">Setactiononfailure – metoda</span><span class="sxs-lookup"><span data-stu-id="b298f-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="b298f-130">Ihostpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b298f-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="b298f-131">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="b298f-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)