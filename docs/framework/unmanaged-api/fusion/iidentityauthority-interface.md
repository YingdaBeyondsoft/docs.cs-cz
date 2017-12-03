---
title: "IIdentityAuthority – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IIdentityAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IIdentityAuthority
helpviewer_keywords: IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3f38d932fa0376186e2c22232d21857d5fa128f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="bf1e7-102">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf1e7-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="bf1e7-103">Spravuje klíče identity pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf1e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bf1e7-104">Methods</span></span>  
  
|<span data-ttu-id="bf1e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf1e7-105">Method</span></span>|<span data-ttu-id="bf1e7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bf1e7-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="bf1e7-107">Získá hodnotu, která určuje, zda jsou obě zadané [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="bf1e7-108">Získá hodnotu, která určuje, zda jsou obě zadané [ireferenceidentity –](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instance jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="bf1e7-109">Získá hodnotu, která určuje, zda jsou dvě zadané řetězcové vyjádření identity definice stejné.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="bf1e7-110">Získá hodnotu, která určuje, zda jsou dvě zadané řetězcové vyjádření identity odkaz stejné.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="bf1e7-111">Získá ukazatel na nový `IDefinitionIdentity` instance, který představuje objekt kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="bf1e7-112">Získá ukazatel na nový `IReferenceIdentity` instance, který představuje objekt kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="bf1e7-113">Získá verzi formátovaný řetězec zadaného `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="bf1e7-114">Vyplní celé zadaný znak široké vyrovnávací paměti s verzí řetězce zadaného `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="bf1e7-115">Získá hodnotu, která určuje, zda zadaný `IDefinitionIdentity` a `IReferenceIdentity` instance odkazovat na stejný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="bf1e7-116">Získá hodnotu, která určuje, zda zadaný řetězce odkazovat na stejný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="bf1e7-117">Získá ukazatel na nově vytvořený řetězec klíč pro zadané `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="bf1e7-118">Získá ukazatel na nově vytvořený řetězec klíč pro zadané `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="bf1e7-119">Získá hodnotu hash pro zadaný `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="bf1e7-120">Získá hodnotu hash pro zadaný `IreferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="bf1e7-121">Získá verzi formátovaný řetězec zadaného `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="bf1e7-122">Vyplní celé zadaný znak široké vyrovnávací paměti s verzí řetězce zadaného `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="bf1e7-123">Získá ukazatele rozhraní k `IDefinitionIdentity` instance generované ze zadaného řetězec ve formátu.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="bf1e7-124">Získá ukazatele rozhraní k `IReferenceIdentity` instance generované ze zadaného řetězec ve formátu.</span><span class="sxs-lookup"><span data-stu-id="bf1e7-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf1e7-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf1e7-125">Requirements</span></span>  
 <span data-ttu-id="bf1e7-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf1e7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf1e7-127">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="bf1e7-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bf1e7-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf1e7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1e7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf1e7-129">See Also</span></span>  
 [<span data-ttu-id="bf1e7-130">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="bf1e7-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)