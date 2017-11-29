---
title: "ICLRTask2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2
helpviewer_keywords: ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f2312d193031eae556f55b061a36259531d013b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="d82e0-102">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82e0-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="d82e0-103">Obsahuje všechny funkce [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní; kromě toho poskytuje metody, které umožňují zrušení vláken na opožděno na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="d82e0-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d82e0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d82e0-104">Methods</span></span>  
  
|<span data-ttu-id="d82e0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d82e0-105">Method</span></span>|<span data-ttu-id="d82e0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d82e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d82e0-107">Beginpreventasyncabort – metoda</span><span class="sxs-lookup"><span data-stu-id="d82e0-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="d82e0-108">Zpoždění nové vlákno abort požadavky na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="d82e0-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="d82e0-109">Endpreventasyncabort – metoda</span><span class="sxs-lookup"><span data-stu-id="d82e0-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="d82e0-110">Umožňuje nové nebo nevyřízené žádosti o zrušení vláken za následek vlákno zruší na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="d82e0-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d82e0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d82e0-111">Remarks</span></span>  
 <span data-ttu-id="d82e0-112">`ICLRTask2` Dědí rozhraní `ICLRTask` rozhraní a přidá metody, které umožňují hostitele do zpoždění přerušení způsobených vlákno k ochraně oblasti kód, který nesmí nezdaří.</span><span class="sxs-lookup"><span data-stu-id="d82e0-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="d82e0-113">Volání metody `BeginPreventAsyncAbort` zvýší čítač přerušení podprocesu zpoždění pro aktuální vlákno a volání `EndPreventAsyncAbort` snižuje ho.</span><span class="sxs-lookup"><span data-stu-id="d82e0-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="d82e0-114">Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` mohou být použity.</span><span class="sxs-lookup"><span data-stu-id="d82e0-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="d82e0-115">Tak dlouho, dokud hodnota čítače je větší než nula, jsou odložené přerušení přístup z více vláken pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="d82e0-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="d82e0-116">Pokud volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` není spárovat, je možné dosáhnout stavu, ve které vlákno přerušení nelze doručit do aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="d82e0-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="d82e0-117">Zpoždění není dodržení pro vlákno, které zruší sám sebe.</span><span class="sxs-lookup"><span data-stu-id="d82e0-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="d82e0-118">Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM).</span><span class="sxs-lookup"><span data-stu-id="d82e0-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="d82e0-119">Zneužití z těchto metod může způsobit neurčené chování ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="d82e0-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="d82e0-120">Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač může nastavit na hodnotu nula, pokud virtuální počítač má dříve se zvýší.</span><span class="sxs-lookup"><span data-stu-id="d82e0-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="d82e0-121">Podobně není čítač interní kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="d82e0-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="d82e0-122">Pokud překročí limitu integrální vzhledem k tomu, že se zvýší o hostitel a virtuální počítač, neurčené jejich výsledné chování.</span><span class="sxs-lookup"><span data-stu-id="d82e0-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="d82e0-123">Pro informace o členech zděděno z `ICLRTask` a o dalších použití tohoto rozhraní, najdete v článku [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d82e0-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82e0-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d82e0-124">Requirements</span></span>  
 <span data-ttu-id="d82e0-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82e0-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82e0-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d82e0-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d82e0-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d82e0-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d82e0-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82e0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82e0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d82e0-129">See Also</span></span>  
 [<span data-ttu-id="d82e0-130">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82e0-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d82e0-131">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82e0-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d82e0-132">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82e0-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d82e0-133">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82e0-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="d82e0-134">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="d82e0-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)