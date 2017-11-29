---
title: "IActionOnCLREvent::OnEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b2f609969ccf67f07701d20578225f1618293968
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="2ff5d-102">IActionOnCLREvent::OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff5d-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="2ff5d-103">Zpětná volání provádí události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ff5d-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ff5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff5d-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="2ff5d-106">[v] Jeden z [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty, které určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="2ff5d-107">[v] Ukazatel na objekt, který obsahuje podrobnosti o `event`.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ff5d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ff5d-108">Return Value</span></span>  
  
|<span data-ttu-id="2ff5d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ff5d-109">HRESULT</span></span>|<span data-ttu-id="2ff5d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2ff5d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ff5d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ff5d-111">S_OK</span></span>|<span data-ttu-id="2ff5d-112">`OnEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2ff5d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ff5d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ff5d-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ff5d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ff5d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ff5d-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-116">The call timed out.</span></span>|  
|<span data-ttu-id="2ff5d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ff5d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ff5d-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ff5d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ff5d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ff5d-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ff5d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ff5d-121">E_FAIL</span></span>|<span data-ttu-id="2ff5d-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ff5d-123">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ff5d-124">Následující volání žádné hostování metoda vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ff5d-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ff5d-125">Remarks</span></span>  
 <span data-ttu-id="2ff5d-126">`data` Parametr je ukazatel na objekt neurčeného typu.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="2ff5d-127">Pokud `event` parametr `Event_DomainUnload`, `data` je číselný identifikátor <xref:System.AppDomain> , který byl odpojen.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="2ff5d-128">Hostitel moci provést vhodnou akci pomocí tento identifikátor jako klíč.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="2ff5d-129">Pokud `event` je `Event_MDAFired`, `data` je ukazatel na [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instanci, která obsahuje zprávy výstup z a spravované ladění Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="2ff5d-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="2ff5d-130">Mda jsou funkce modulu CLR, který pomoci vývojářům s laděním vygenerováním XML zprávy o událostech, které jsou jinak obtížné depeše.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="2ff5d-131">Takové zprávy může být obzvláště užitečný při ladění přechodů mezi spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="2ff5d-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="2ff5d-132">Další informace najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="2ff5d-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff5d-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ff5d-133">Requirements</span></span>  
 <span data-ttu-id="2ff5d-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff5d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff5d-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ff5d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ff5d-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ff5d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ff5d-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff5d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff5d-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff5d-138">See Also</span></span>  
 [<span data-ttu-id="2ff5d-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="2ff5d-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="2ff5d-140">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="2ff5d-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="2ff5d-141">Iactiononclrevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff5d-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="2ff5d-142">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff5d-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="2ff5d-143">Iclroneventmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff5d-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="2ff5d-144">Mdainfo – struktura</span><span class="sxs-lookup"><span data-stu-id="2ff5d-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)