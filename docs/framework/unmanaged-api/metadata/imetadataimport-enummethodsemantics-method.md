---
title: "IMetaDataImport::EnumMethodSemantics – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d5ec79701f73b8beb7759d72b972fc347a339c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="725be-102">IMetaDataImport::EnumMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="725be-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="725be-103">Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým je související zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="725be-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="725be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="725be-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="725be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="725be-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="725be-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="725be-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="725be-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="725be-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="725be-108">[v] MethodDef token, který omezuje obor výčtu.</span><span class="sxs-lookup"><span data-stu-id="725be-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="725be-109">[out] Pole používá k ukládání událostí nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="725be-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="725be-110">[v] Maximální velikost `rEventProp` pole.</span><span class="sxs-lookup"><span data-stu-id="725be-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="725be-111">[out] Počet událostí nebo vlastnosti, vrátí se v `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="725be-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="725be-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="725be-112">Return Value</span></span>  
  
|<span data-ttu-id="725be-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="725be-113">HRESULT</span></span>|<span data-ttu-id="725be-114">Popis</span><span class="sxs-lookup"><span data-stu-id="725be-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="725be-115">`EnumMethodSemantics`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="725be-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="725be-116">Nejsou žádné události nebo vlastnosti, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="725be-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="725be-117">V takovém případě `pcEventProp` je nulová.</span><span class="sxs-lookup"><span data-stu-id="725be-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="725be-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="725be-118">Remarks</span></span>  
 <span data-ttu-id="725be-119">Definování mnoho běžných typů runtime jazyka *vlastnost* `Changed` události a `On` *vlastnost* `Changed` metody související s jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="725be-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="725be-120">Například <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definuje typ <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> události a <xref:System.Windows.Forms.Control.OnFontChanged%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="725be-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="725be-121">Metody přistupující objekt set <xref:System.Windows.Forms.Control.Font%2A> vlastnost volání <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodu, která zase vyvolá <xref:System.Windows.Forms.Control.FontChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="725be-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="725be-122">By volání `EnumMethodSemantics` pomocí MethodDef pro <xref:System.Windows.Forms.Control.OnFontChanged%2A> získat odkazy na <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.Control.FontChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="725be-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725be-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="725be-123">Requirements</span></span>  
 <span data-ttu-id="725be-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="725be-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725be-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="725be-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="725be-126">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="725be-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="725be-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725be-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725be-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="725be-128">See Also</span></span>  
 [<span data-ttu-id="725be-129">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="725be-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="725be-130">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="725be-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)