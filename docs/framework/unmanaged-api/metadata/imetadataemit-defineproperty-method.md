---
title: "IMetaDataEmit::DefineProperty – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc0403fd51f028510eb60d93ff96fc7d05606366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="69731-102">IMetaDataEmit::DefineProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="69731-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="69731-103">Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a `set` metody přístupových objektů a získá token pro tuto definici vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69731-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69731-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69731-104">Syntax</span></span>  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69731-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69731-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="69731-106">[v] Token pro třídy nebo rozhraní, na kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="69731-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="69731-107">[v] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69731-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="69731-108">[v] Příznaky vlastnost.</span><span class="sxs-lookup"><span data-stu-id="69731-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="69731-109">[v] Vlastnost podpis.</span><span class="sxs-lookup"><span data-stu-id="69731-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="69731-110">[v] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="69731-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="69731-111">[v] Typ vlastnosti na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="69731-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="69731-112">[v] Výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="69731-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="69731-113">[v] Počet (Unicode) znaků v `pValue`.</span><span class="sxs-lookup"><span data-stu-id="69731-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="69731-114">[v] Metoda, která nastavuje hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69731-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="69731-115">[v] Metoda, která se získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69731-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="69731-116">[v] Pole jiné metody související s vlastností.</span><span class="sxs-lookup"><span data-stu-id="69731-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="69731-117">Terminate – pole se `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="69731-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="69731-118">[out] `mdProperty` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="69731-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69731-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69731-119">Requirements</span></span>  
 <span data-ttu-id="69731-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69731-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69731-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="69731-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69731-122">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69731-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69731-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69731-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69731-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="69731-124">See Also</span></span>  
 [<span data-ttu-id="69731-125">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69731-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="69731-126">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69731-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)