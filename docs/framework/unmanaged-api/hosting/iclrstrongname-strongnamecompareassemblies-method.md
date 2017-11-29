---
title: "ICLRStrongName::StrongNameCompareAssemblies – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab69a0d0bb5894c2393e240b4f89b9a16dd98939
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="88d3a-102">ICLRStrongName::StrongNameCompareAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="88d3a-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="88d3a-103">Určuje, zda dva sestavení liší pouze jejich podpisy silným názvem.</span><span class="sxs-lookup"><span data-stu-id="88d3a-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88d3a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88d3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88d3a-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="88d3a-106">[v] Cesta k první sestavení.</span><span class="sxs-lookup"><span data-stu-id="88d3a-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="88d3a-107">[v] Cesta k sestavení druhý.</span><span class="sxs-lookup"><span data-stu-id="88d3a-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="88d3a-108">[out] Jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="88d3a-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="88d3a-109">`SN_CMP_DIFFERENT`(0) - určuje, že sestavení obsahovat různé data.</span><span class="sxs-lookup"><span data-stu-id="88d3a-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="88d3a-110">`SN_CMP_IDENTICAL`(1) - určuje, že sestavení jsou stejné, včetně jejich podpisy a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="88d3a-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="88d3a-111">`SN_CMP_SIGONLY`(2) - určuje, že sestavení liší pouze podpisu a kontrolních součtů.</span><span class="sxs-lookup"><span data-stu-id="88d3a-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88d3a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="88d3a-112">Return Value</span></span>  
 <span data-ttu-id="88d3a-113">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="88d3a-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88d3a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88d3a-114">Requirements</span></span>  
 <span data-ttu-id="88d3a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88d3a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88d3a-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="88d3a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="88d3a-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88d3a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88d3a-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88d3a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88d3a-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88d3a-119">Remarks</span></span>  
 <span data-ttu-id="88d3a-120">Podpis silného názvu sestavení se skládá z textu název sestavení, verzi, jazykovou verzi a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="88d3a-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d3a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="88d3a-121">See Also</span></span>  
 [<span data-ttu-id="88d3a-122">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88d3a-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)