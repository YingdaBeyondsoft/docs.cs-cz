---
title: "EPolicyAction – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f2c3a4138adfa354de07bc6df4e51d7697598b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="b1cb6-102">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="b1cb6-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="b1cb6-103">Popisuje akce zásad, které jsou hostiteli můžete nastavit pro operace popsaného [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a selhání popsaného [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b1cb6-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1cb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1cb6-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="b1cb6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b1cb6-105">Members</span></span>  
  
|<span data-ttu-id="b1cb6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b1cb6-106">Member</span></span>|<span data-ttu-id="b1cb6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1cb6-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="b1cb6-108">Určuje, že modul CLR (CLR) by měl abort vlákno řádně.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="b1cb6-109">Řádné přerušení zahrnuje pokusí spustit všechny `finally` blokuje, všechny `catch` bloky související s vlákno přerušení a finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="b1cb6-110">Určuje, že modulu CLR by měla zadat zakázaném stavu.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="b1cb6-111">Žádné další spravovaného kódu, mohou být provedeny v ovlivněných procesu a vláken jsou zablokované ve vstupu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="b1cb6-112">Určuje, že modulu CLR pokusit o řádné ukončení procesu, včetně spouštění finalizační metody a vyčištění a operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="b1cb6-113">Určuje, že modulu CLR by měla opustí proces okamžitě, bez spuštění finalizační metody nebo vyčištění a operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="b1cb6-114">Nowever, oznámení se odesílá do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="b1cb6-115">Určuje, že by měla být provedena žádná akce.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="b1cb6-116">Určuje, že modulu CLR by měla provádět přerušení článku neslušní vlákno.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="b1cb6-117">Pouze ty `catch` a `finally` bloky označené jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provedení.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="b1cb6-118">Určuje, že modulu CLR by měla opustí proces bez spuštění finalizační metody nebo protokolování operace.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="b1cb6-119">Určuje, že modulu CLR by měla provádět článku neslušní uvolnění z <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="b1cb6-120">Pouze finalizační metody označené jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provedení.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="b1cb6-121">Podobně všechna vlákna s tímto <xref:System.AppDomain> v jejich zásobníku přijímat `ThreadAbortException`, ale pouze ty `catch` a `finally` bloky označené jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provedení.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="b1cb6-122">Určuje, že by měl vyvolána výjimka příslušné podmínky, například z důvodu nedostatku paměti, přetečení vyrovnávací paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="b1cb6-123">Určuje, že <xref:System.AppDomain> by měla být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="b1cb6-124">Modul CLR pokusí o spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1cb6-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1cb6-125">Remarks</span></span>  
 <span data-ttu-id="b1cb6-126">Hostitel nastaví akce zásad voláním metod [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="b1cb6-127">Informace o článku neslušní a řádné přerušení najdete v tématu [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1cb6-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1cb6-128">Requirements</span></span>  
 <span data-ttu-id="b1cb6-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1cb6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1cb6-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1cb6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1cb6-131">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1cb6-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1cb6-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1cb6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cb6-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1cb6-133">See Also</span></span>  
 [<span data-ttu-id="b1cb6-134">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="b1cb6-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="b1cb6-135">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1cb6-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="b1cb6-136">Ihostpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1cb6-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="b1cb6-137">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="b1cb6-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)