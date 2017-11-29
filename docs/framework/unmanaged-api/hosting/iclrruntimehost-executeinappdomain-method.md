---
title: "ICLRRuntimeHost::ExecuteInAppDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da6e9b52c0ea6f2935aad70779e159db91a4f501
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="45b84-102">ICLRRuntimeHost::ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="45b84-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="45b84-103">Určuje <xref:System.AppDomain> ve kterém se má provést zadanou spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="45b84-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45b84-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45b84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45b84-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="45b84-106">[v] Číselné ID <xref:System.AppDomain> ve kterém se má provést zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="45b84-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="45b84-107">[v] Ukazatel na funkci provést v rámci zadaného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="45b84-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="45b84-108">[v] Ukazatel na neprůhledné paměti přidělené volajícího.</span><span class="sxs-lookup"><span data-stu-id="45b84-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="45b84-109">Tento parametr je modul CLR (CLR) předaná funkci zpětného volání domény.</span><span class="sxs-lookup"><span data-stu-id="45b84-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="45b84-110">Není paměť haldy spravovaného modulu runtime; přidělení i životnost tuto paměť jsou řízeny volající.</span><span class="sxs-lookup"><span data-stu-id="45b84-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45b84-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45b84-111">Return Value</span></span>  
  
|<span data-ttu-id="45b84-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45b84-112">HRESULT</span></span>|<span data-ttu-id="45b84-113">Popis</span><span class="sxs-lookup"><span data-stu-id="45b84-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45b84-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="45b84-114">S_OK</span></span>|<span data-ttu-id="45b84-115">`ExecuteInAppDomain`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="45b84-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="45b84-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45b84-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45b84-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="45b84-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45b84-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45b84-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45b84-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="45b84-119">The call timed out.</span></span>|  
|<span data-ttu-id="45b84-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45b84-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45b84-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="45b84-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45b84-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45b84-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45b84-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="45b84-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45b84-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45b84-124">E_FAIL</span></span>|<span data-ttu-id="45b84-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="45b84-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45b84-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="45b84-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45b84-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="45b84-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45b84-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45b84-128">Remarks</span></span>  
 <span data-ttu-id="45b84-129">`ExecuteInAppDomain`Umožňuje kontrolu využití hostiteli over, který spravuje <xref:System.AppDomain> zadanou metodu spravované se má provést v.</span><span class="sxs-lookup"><span data-stu-id="45b84-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="45b84-130">Hodnota identifikátoru doménu aplikace, který odpovídá hodnotě můžete získat <xref:System.AppDomain.Id%2A> vlastnost voláním [getcurrentappdomainid – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="45b84-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45b84-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45b84-131">Requirements</span></span>  
 <span data-ttu-id="45b84-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45b84-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45b84-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="45b84-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45b84-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45b84-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45b84-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45b84-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b84-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="45b84-136">See Also</span></span>  
 [<span data-ttu-id="45b84-137">Iclrruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45b84-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)