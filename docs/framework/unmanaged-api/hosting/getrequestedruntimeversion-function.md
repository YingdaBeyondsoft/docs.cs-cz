---
title: "GetRequestedRuntimeVersion – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersion
helpviewer_keywords: GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfac4e32841b8a8332a1f4124c1326f1ef7da1f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="f215b-102">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="f215b-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="f215b-103">Získá číslo verze common language runtime (CLR) potřebný pro zadanou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f215b-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="f215b-104">Pokud není nainstalovaná této verze, získá nejnovější verzi, který se nainstaloval před požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="f215b-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="f215b-105">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f215b-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f215b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f215b-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f215b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f215b-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="f215b-108">[v] Název aplikace.</span><span class="sxs-lookup"><span data-stu-id="f215b-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f215b-109">[out] Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="f215b-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f215b-110">[v] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="f215b-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="f215b-111">[out] Ukazatel na délku řetězce číslo verze.</span><span class="sxs-lookup"><span data-stu-id="f215b-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f215b-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f215b-112">Return Value</span></span>  
 <span data-ttu-id="f215b-113">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f215b-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f215b-114">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="f215b-114">Return code</span></span>|<span data-ttu-id="f215b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f215b-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f215b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f215b-116">S_OK</span></span>|<span data-ttu-id="f215b-117">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f215b-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="f215b-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f215b-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f215b-119">Verze vyrovnávací paměť není dostatečně velký pro uložení řetězec verze.</span><span class="sxs-lookup"><span data-stu-id="f215b-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="f215b-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f215b-120">E_POINTER</span></span>|<span data-ttu-id="f215b-121">`pdwLength`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f215b-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f215b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f215b-122">Requirements</span></span>  
 <span data-ttu-id="f215b-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f215b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f215b-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f215b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f215b-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f215b-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f215b-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f215b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f215b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f215b-127">See Also</span></span>  
 [<span data-ttu-id="f215b-128">Getrequestedruntimeinfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f215b-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="f215b-129">Getversionfromprocess – funkce</span><span class="sxs-lookup"><span data-stu-id="f215b-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="f215b-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f215b-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)