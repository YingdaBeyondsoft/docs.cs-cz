---
title: "COR_GC_REFERENCE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11be45743bd215315139fb77f016e85bc9b592c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corgcreference-structure"></a><span data-ttu-id="5cfd9-102">COR_GC_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="5cfd9-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="5cfd9-103">Obsahuje informace o objekt, který má být uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cfd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cfd9-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="5cfd9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5cfd9-105">Members</span></span>  
  
|<span data-ttu-id="5cfd9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5cfd9-106">Member</span></span>|<span data-ttu-id="5cfd9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5cfd9-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="5cfd9-108">Ukazatel na doménu aplikace, do které patří popisovač nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="5cfd9-109">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="5cfd9-110">ICorDebugValue nebo ICorDebugReferenceValue rozhraní, které odpovídá objekt, který má být uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="5cfd9-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnota výčtu, která určuje, odkud pochází kořenu.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="5cfd9-112">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="5cfd9-113">Další data o objekt, který má být uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="5cfd9-114">Tyto informace závisí na zdroji objektu, jak `type` pole.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="5cfd9-115">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cfd9-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cfd9-116">Remarks</span></span>  
 <span data-ttu-id="5cfd9-117">`type` Pole [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnotu výčtu, která určuje, odkud pochází odkaz na.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="5cfd9-118">Konkrétní `COR_GC_REFERENCE` hodnota může vyjadřovat některé z následujících druhy spravované objekty:</span><span class="sxs-lookup"><span data-stu-id="5cfd9-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
-   <span data-ttu-id="5cfd9-119">Objekty z všechny spravované zásobníky (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="5cfd9-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="5cfd9-120">To zahrnuje za provozu odkazy ve spravovaném kódu a také objekty vytvořené modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="5cfd9-121">Objekty z tabulky popisovače (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="5cfd9-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="5cfd9-122">To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="5cfd9-123">Objekty z fronty finalizační metodu (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="5cfd9-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="5cfd9-124">Fronty finalizační metodu kořeny objekty, dokud finalizační metodu byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="5cfd9-125">`extraData` Pole obsahuje doplňující data v závislosti na zdroj (nebo typu) odkaz.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="5cfd9-126">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5cfd9-126">Possible values are:</span></span>  
  
-   <span data-ttu-id="5cfd9-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-127">`DependentSource`.</span></span> <span data-ttu-id="5cfd9-128">Pokud `type` je `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud je aktivní, kořeny objekt, který má být uvolněna při `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
-   <span data-ttu-id="5cfd9-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-129">`RefCount`.</span></span> <span data-ttu-id="5cfd9-130">Pokud `type` je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je počet odkazů popisovač.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
-   <span data-ttu-id="5cfd9-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-131">`Size`.</span></span> <span data-ttu-id="5cfd9-132">Pokud `type` je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektů, pro které má systém uvolňování vypočtena kořeny objektu.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="5cfd9-133">Všimněte si, že tento výpočet není nutně aktuální.</span><span class="sxs-lookup"><span data-stu-id="5cfd9-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cfd9-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cfd9-134">Requirements</span></span>  
 <span data-ttu-id="5cfd9-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cfd9-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cfd9-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cfd9-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cfd9-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cfd9-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cfd9-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cfd9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cfd9-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cfd9-139">See Also</span></span>  
 [<span data-ttu-id="5cfd9-140">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="5cfd9-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="5cfd9-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="5cfd9-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)