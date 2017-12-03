---
title: "ICorProfilerInfo::GetAppDomainInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c31d3c61a868bf741213f6e505d91524cc925207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="b4dbd-102">ICorProfilerInfo::GetAppDomainInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="b4dbd-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="b4dbd-103">Přijímá ID aplikačního domény.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-103">Accepts an application domain ID.</span></span> <span data-ttu-id="b4dbd-104">Vrátí název domény aplikace a ID procesu, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4dbd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4dbd-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4dbd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4dbd-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="b4dbd-107">[v] ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b4dbd-108">[v] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b4dbd-109">[out] Ukazatel na celkový počet znaků z názvu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="b4dbd-110">[out] Zadaný volající široká znaková vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="b4dbd-111">Po návratu metody `szName` bude obsahovat název domény celé nebo jeho část aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="b4dbd-112">[out] Ukazatel na ID procesu, který obsahuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4dbd-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4dbd-113">Remarks</span></span>  
 <span data-ttu-id="b4dbd-114">Po návratu tato metoda, musíte se ověřit, že `szName` vyrovnávací paměť byla dostatečně velký pro obsahovat úplný název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="b4dbd-115">K tomuto účelu porovnat hodnotu, `pcchName` body s hodnotou `cchName` parametr.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="b4dbd-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělit větší `szName` vyrovnávací paměti, aktualizujte `cchName` s novou, větší velikost a volání `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="b4dbd-117">Alternativně můžete nejdřív volat `GetAppDomainInfo` s nulovou délkou `szName` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b4dbd-118">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcchName` a volání `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="b4dbd-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4dbd-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4dbd-119">Requirements</span></span>  
 <span data-ttu-id="b4dbd-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4dbd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4dbd-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4dbd-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4dbd-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4dbd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4dbd-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4dbd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4dbd-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4dbd-124">See Also</span></span>  
 [<span data-ttu-id="b4dbd-125">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4dbd-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="b4dbd-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b4dbd-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="b4dbd-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="b4dbd-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)