---
title: "IReferenceIdentity – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35c6152836adf02d541bacd149ed9ac053765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="60b77-102">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b77-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="60b77-103">Představuje odkaz na jedinečný podpis objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="60b77-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60b77-104">Metody</span><span class="sxs-lookup"><span data-stu-id="60b77-104">Methods</span></span>  
  
|<span data-ttu-id="60b77-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="60b77-105">Method</span></span>|<span data-ttu-id="60b77-106">Popis</span><span class="sxs-lookup"><span data-stu-id="60b77-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="60b77-107">Získá ukazatele rozhraní na nový `IReferenceIdentity` instanci, která je stejná jako to `IReferenceIdentity`, s výjimkou změny zadaného atributu.</span><span class="sxs-lookup"><span data-stu-id="60b77-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="60b77-108">Získá ukazatele rozhraní k `IEnumIDENTITY_ATTRIBUTE` instanci, která obsahuje atributy přidružené k tomuto `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="60b77-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="60b77-109">Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="60b77-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="60b77-110">Nastaví atribut, který má zadaný obor názvů a zadaný název se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="60b77-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60b77-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60b77-111">Requirements</span></span>  
 <span data-ttu-id="60b77-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60b77-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60b77-113">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="60b77-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="60b77-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60b77-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b77-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="60b77-115">See Also</span></span>  
 [<span data-ttu-id="60b77-116">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="60b77-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="60b77-117">Ienumidentity_attribute – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b77-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)