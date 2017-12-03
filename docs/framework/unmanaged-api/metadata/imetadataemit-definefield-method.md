---
title: "IMetaDataEmit::DefineField – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2a544d7e676b71fb00b8fd7a3d871867f7f55626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="e02df-102">IMetaDataEmit::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="e02df-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="e02df-103">Vytvoří definici pole s podpisem Zadaná metadata a získá token tuto definici pole.</span><span class="sxs-lookup"><span data-stu-id="e02df-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e02df-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e02df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e02df-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e02df-106">[v] `mdTypeDef` Tokenu pro nadřazených třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e02df-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="e02df-107">[v] Název pole ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="e02df-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="e02df-108">[v] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="e02df-108">[in] The field attributes.</span></span> <span data-ttu-id="e02df-109">Toto je bitová maska s `CorFieldAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e02df-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e02df-110">[v] Podpis pole jako objekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="e02df-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e02df-111">[v] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="e02df-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="e02df-112">[v] `ELEMENT_TYPE_`  *\**  Pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e02df-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="e02df-113">Toto je `CorElementType` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e02df-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="e02df-114">Pokud není definování konstantní hodnota pro pole, použijte `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="e02df-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e02df-115">[v] Hodnota konstanty pro pole.</span><span class="sxs-lookup"><span data-stu-id="e02df-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e02df-116">[v] Velikost v znaků (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e02df-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="e02df-117">[out] `mdFieldDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="e02df-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02df-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e02df-118">Requirements</span></span>  
 <span data-ttu-id="e02df-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02df-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02df-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e02df-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e02df-121">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e02df-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e02df-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e02df-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02df-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e02df-123">See Also</span></span>  
 [<span data-ttu-id="e02df-124">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e02df-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e02df-125">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e02df-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)