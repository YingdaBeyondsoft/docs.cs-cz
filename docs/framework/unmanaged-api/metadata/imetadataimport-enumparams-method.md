---
title: "IMetaDataImport::EnumParams – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42555e1300016222e9ea8064e90fa3062d79db6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="dc5a1-102">IMetaDataImport::EnumParams – metoda</span><span class="sxs-lookup"><span data-stu-id="dc5a1-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="dc5a1-103">Vytvoří výčet představující parametry metody odkazuje zadaný token MethodDef tokeny ParamDef.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc5a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc5a1-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc5a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc5a1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="dc5a1-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dc5a1-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="dc5a1-108">[v] MethodDef token představující metodu s parametry, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="dc5a1-109">[out] Pole používá k ukládání ParamDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dc5a1-110">[v] Maximální velikost `rParams` pole.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dc5a1-111">[out] Počet ParamDef tokeny, vrátí se v `rParams`.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc5a1-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc5a1-112">Return Value</span></span>  
  
|<span data-ttu-id="dc5a1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc5a1-113">HRESULT</span></span>|<span data-ttu-id="dc5a1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dc5a1-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dc5a1-115">`EnumParams`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dc5a1-116">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="dc5a1-117">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="dc5a1-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc5a1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc5a1-118">Requirements</span></span>  
 <span data-ttu-id="dc5a1-119">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc5a1-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc5a1-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc5a1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc5a1-121">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc5a1-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc5a1-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc5a1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5a1-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc5a1-123">See Also</span></span>  
 [<span data-ttu-id="dc5a1-124">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc5a1-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dc5a1-125">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc5a1-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)