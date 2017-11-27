---
title: "StrongNameHashSize – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameHashSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameHashSize
helpviewer_keywords: StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: baf9c9b2219ff3fb784972b1f54a2b50dcd8657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="06965-102">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="06965-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="06965-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="06965-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="06965-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="06965-104">This function has been deprecated.</span></span> <span data-ttu-id="06965-105">Použití [iclrstrongname::strongnamehashsize –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="06965-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06965-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06965-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06965-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="06965-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="06965-108">[v] Algoritmus hash, který slouží k výpočtu velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="06965-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="06965-109">[out] Vrácený vyrovnávací paměti velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="06965-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06965-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06965-110">Return Value</span></span>  
 <span data-ttu-id="06965-111">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="06965-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06965-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06965-112">Remarks</span></span>  
 <span data-ttu-id="06965-113">Pokud `StrongNameHashSize` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="06965-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06965-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06965-114">Requirements</span></span>  
 <span data-ttu-id="06965-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06965-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06965-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="06965-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="06965-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06965-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06965-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06965-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06965-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="06965-119">See Also</span></span>  
 [<span data-ttu-id="06965-120">Strongnamehashsize – metoda</span><span class="sxs-lookup"><span data-stu-id="06965-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="06965-121">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06965-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)