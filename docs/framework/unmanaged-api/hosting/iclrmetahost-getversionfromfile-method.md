---
title: "ICLRMetaHost::GetVersionFromFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetVersionFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fcf5ca8306c4e91ff6b96bac36ad2639d81d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="6f22c-102">ICLRMetaHost::GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="6f22c-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="6f22c-103">Získá sestavení původní verze rozhraní .NET Framework kompilace (uložená v metadatech), zadána cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="6f22c-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="6f22c-104">Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6f22c-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f22c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f22c-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f22c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f22c-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="6f22c-107">[v] Cesta k souboru dokončení sestavení.</span><span class="sxs-lookup"><span data-stu-id="6f22c-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="6f22c-108">[out] Verze kompilace rozhraní .NET Framework, uložená v metadatech ve formátu "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="6f22c-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="6f22c-109">*A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní, vedlejší verze a číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="6f22c-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="6f22c-110">Délka tohoto řetězce je omezená na hodnotou MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="6f22c-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f22c-111">Tento výstup odpovídá název adresáře pro verzi rozhraní .NET Framework, jak se objevuje v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="6f22c-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="6f22c-112">Ukázkové hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na počtu sestavení nainstalována.</span><span class="sxs-lookup"><span data-stu-id="6f22c-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="6f22c-113">Všimněte si, že vyžaduje se předpona "v".</span><span class="sxs-lookup"><span data-stu-id="6f22c-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="6f22c-114">[ve out] Velikost `pwzbuffer` předejdete přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6f22c-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f22c-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f22c-115">Return Value</span></span>  
 <span data-ttu-id="6f22c-116">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="6f22c-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6f22c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f22c-117">HRESULT</span></span>|<span data-ttu-id="6f22c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6f22c-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f22c-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f22c-119">S_OK</span></span>|<span data-ttu-id="6f22c-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="6f22c-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="6f22c-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6f22c-121">E_POINTER</span></span>|<span data-ttu-id="6f22c-122">`pwzbuffer`nebo `pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6f22c-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="6f22c-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="6f22c-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="6f22c-124">Vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="6f22c-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f22c-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f22c-125">Requirements</span></span>  
 <span data-ttu-id="6f22c-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f22c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f22c-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6f22c-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6f22c-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f22c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f22c-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f22c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f22c-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f22c-130">See Also</span></span>  
 [<span data-ttu-id="6f22c-131">Iclrmetahost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f22c-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="6f22c-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="6f22c-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)