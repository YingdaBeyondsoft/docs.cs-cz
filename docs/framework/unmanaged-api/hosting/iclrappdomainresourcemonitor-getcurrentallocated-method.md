---
title: "ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dee616e1fbd071662a42af856fa2cd51f7bdd5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="969e6-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="969e6-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="969e6-103">Získá celková velikost v bajtech přidělených paměti, které jste provedli pro doménu aplikace, protože byl vytvořen bez odečtením paměti, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="969e6-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="969e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="969e6-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="969e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="969e6-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="969e6-106">[v] ID domény požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="969e6-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="969e6-107">[out] Ukazatel na celkovou velikost všech přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="969e6-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="969e6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="969e6-108">Return Value</span></span>  
 <span data-ttu-id="969e6-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="969e6-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="969e6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="969e6-110">HRESULT</span></span>|<span data-ttu-id="969e6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="969e6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="969e6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="969e6-112">S_OK</span></span>|<span data-ttu-id="969e6-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="969e6-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="969e6-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="969e6-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="969e6-115">Doména aplikace byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="969e6-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="969e6-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="969e6-116">Remarks</span></span>  
 <span data-ttu-id="969e6-117">Tato metoda je ekvivalentem nespravované spravované <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="969e6-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="969e6-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="969e6-118">Requirements</span></span>  
 <span data-ttu-id="969e6-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="969e6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="969e6-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="969e6-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="969e6-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="969e6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="969e6-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="969e6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969e6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="969e6-123">See Also</span></span>  
 [<span data-ttu-id="969e6-124">Iclrappdomainresourcemonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="969e6-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="969e6-125">Prostředků domény aplikace monitorování</span><span class="sxs-lookup"><span data-stu-id="969e6-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="969e6-126">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="969e6-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="969e6-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="969e6-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)