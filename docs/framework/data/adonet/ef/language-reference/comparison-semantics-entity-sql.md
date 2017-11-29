---
title: "Porovnání sémantiku (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="6117b-102">Porovnání sémantiku (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="6117b-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="6117b-103">Provádění některý z těchto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory zahrnuje porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="6117b-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="6117b-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="6117b-104">Explicit comparison</span></span>  
 <span data-ttu-id="6117b-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="6117b-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="6117b-106">!=</span><span class="sxs-lookup"><span data-stu-id="6117b-106">!=</span></span>  
  
 <span data-ttu-id="6117b-107">Řazení operace:</span><span class="sxs-lookup"><span data-stu-id="6117b-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="6117b-108">Možnost použití hodnoty Null operace:</span><span class="sxs-lookup"><span data-stu-id="6117b-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="6117b-109">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="6117b-109">IS NULL</span></span>  
  
-   <span data-ttu-id="6117b-110">NEMÁ HODNOTU NULL</span><span class="sxs-lookup"><span data-stu-id="6117b-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="6117b-111">Explicitní rozdíl</span><span class="sxs-lookup"><span data-stu-id="6117b-111">Explicit distinction</span></span>  
 <span data-ttu-id="6117b-112">Rovnost rozdíl:</span><span class="sxs-lookup"><span data-stu-id="6117b-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="6117b-113">ODLIŠNÉ</span><span class="sxs-lookup"><span data-stu-id="6117b-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="6117b-114">SESKUPIT PODLE</span><span class="sxs-lookup"><span data-stu-id="6117b-114">GROUP BY</span></span>  
  
 <span data-ttu-id="6117b-115">Řazení rozdíl:</span><span class="sxs-lookup"><span data-stu-id="6117b-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="6117b-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="6117b-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="6117b-117">Implicitní rozdíl</span><span class="sxs-lookup"><span data-stu-id="6117b-117">Implicit distinction</span></span>  
 <span data-ttu-id="6117b-118">Nastavit operace a predikáty (rovnosti):</span><span class="sxs-lookup"><span data-stu-id="6117b-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="6117b-119">UNION</span><span class="sxs-lookup"><span data-stu-id="6117b-119">UNION</span></span>  
  
-   <span data-ttu-id="6117b-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="6117b-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="6117b-121">S VÝJIMKOU</span><span class="sxs-lookup"><span data-stu-id="6117b-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="6117b-122">NASTAVENÍ</span><span class="sxs-lookup"><span data-stu-id="6117b-122">SET</span></span>  
  
-   <span data-ttu-id="6117b-123">PŘEKRYTÍ.</span><span class="sxs-lookup"><span data-stu-id="6117b-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="6117b-124">Položka predikáty (rovnosti):</span><span class="sxs-lookup"><span data-stu-id="6117b-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="6117b-125">V</span><span class="sxs-lookup"><span data-stu-id="6117b-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="6117b-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="6117b-126">Supported Combinations</span></span>  
 <span data-ttu-id="6117b-127">Následující tabulka uvádí podporované kombinace operátory porovnání pro jednotlivé typy typu:</span><span class="sxs-lookup"><span data-stu-id="6117b-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="6117b-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="6117b-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="6117b-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="6117b-129">**!=**</span></span>|<span data-ttu-id="6117b-130">**SESKUPIT PODLE**</span><span class="sxs-lookup"><span data-stu-id="6117b-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="6117b-131">**ODLIŠNÉ**</span><span class="sxs-lookup"><span data-stu-id="6117b-131">**DISTINCT**</span></span>|<span data-ttu-id="6117b-132">**SJEDNOCENÍ**</span><span class="sxs-lookup"><span data-stu-id="6117b-132">**UNION**</span></span><br /><br /> <span data-ttu-id="6117b-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="6117b-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="6117b-134">**S VÝJIMKOU**</span><span class="sxs-lookup"><span data-stu-id="6117b-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="6117b-135">**NASTAVENÍ**</span><span class="sxs-lookup"><span data-stu-id="6117b-135">**SET**</span></span><br /><br /> <span data-ttu-id="6117b-136">**PŘEKRYTÍ.**</span><span class="sxs-lookup"><span data-stu-id="6117b-136">**OVERLAPS**</span></span>|<span data-ttu-id="6117b-137">**V**</span><span class="sxs-lookup"><span data-stu-id="6117b-137">**IN**</span></span>|<span data-ttu-id="6117b-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="6117b-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="6117b-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="6117b-139">**>   >=**</span></span>|<span data-ttu-id="6117b-140">**ŘADIT PODLE**</span><span class="sxs-lookup"><span data-stu-id="6117b-140">**ORDER BY**</span></span>|<span data-ttu-id="6117b-141">**MÁ HODNOTU NULL.**</span><span class="sxs-lookup"><span data-stu-id="6117b-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="6117b-142">**NEMÁ HODNOTU NULL**</span><span class="sxs-lookup"><span data-stu-id="6117b-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="6117b-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="6117b-143">Entity type</span></span>|<span data-ttu-id="6117b-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="6117b-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="6117b-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="6117b-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="6117b-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="6117b-151">Komplexní typ</span><span class="sxs-lookup"><span data-stu-id="6117b-151">Complex type</span></span>|<span data-ttu-id="6117b-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="6117b-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="6117b-159">Row</span></span>|<span data-ttu-id="6117b-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="6117b-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="6117b-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="6117b-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="6117b-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="6117b-167">primitivní typ</span><span class="sxs-lookup"><span data-stu-id="6117b-167">Primitive type</span></span>|<span data-ttu-id="6117b-168">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-168">Provider-specific</span></span>|<span data-ttu-id="6117b-169">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-169">Provider-specific</span></span>|<span data-ttu-id="6117b-170">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-170">Provider-specific</span></span>|<span data-ttu-id="6117b-171">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-171">Provider-specific</span></span>|<span data-ttu-id="6117b-172">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-172">Provider-specific</span></span>|<span data-ttu-id="6117b-173">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-173">Provider-specific</span></span>|<span data-ttu-id="6117b-174">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="6117b-174">Provider-specific</span></span>|  
|<span data-ttu-id="6117b-175">Multimnožina</span><span class="sxs-lookup"><span data-stu-id="6117b-175">Multiset</span></span>|<span data-ttu-id="6117b-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="6117b-183">REF</span><span class="sxs-lookup"><span data-stu-id="6117b-183">Ref</span></span>|<span data-ttu-id="6117b-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="6117b-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="6117b-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="6117b-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="6117b-188">Throw</span><span class="sxs-lookup"><span data-stu-id="6117b-188">Throw</span></span>|<span data-ttu-id="6117b-189">Throw</span><span class="sxs-lookup"><span data-stu-id="6117b-189">Throw</span></span>|<span data-ttu-id="6117b-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="6117b-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="6117b-191">Association</span></span><br /><br /> <span data-ttu-id="6117b-192">– typ</span><span class="sxs-lookup"><span data-stu-id="6117b-192">type</span></span>|<span data-ttu-id="6117b-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-194">Throw</span><span class="sxs-lookup"><span data-stu-id="6117b-194">Throw</span></span>|<span data-ttu-id="6117b-195">Throw</span><span class="sxs-lookup"><span data-stu-id="6117b-195">Throw</span></span>|<span data-ttu-id="6117b-196">Throw</span><span class="sxs-lookup"><span data-stu-id="6117b-196">Throw</span></span>|<span data-ttu-id="6117b-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="6117b-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="6117b-200"><sup>1</sup>odkazy na danou entitu typu instancí jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6117b-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="6117b-201">Entity instance nelze porovnat s explicitní odkaz.</span><span class="sxs-lookup"><span data-stu-id="6117b-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="6117b-202">Pokud je tento pokus, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6117b-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="6117b-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="6117b-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="6117b-204"><sup>2</sup>vlastnosti komplexních typů se sloučí před odesláním do úložiště, tak, aby se stala porovnatelný z hlediska (pokud jsou jejich vlastnosti porovnatelný z hlediska).</span><span class="sxs-lookup"><span data-stu-id="6117b-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="6117b-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="6117b-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="6117b-206"><sup>3</sup>Entity Framework runtime zjistí nepodporované případ a vyvolá smysluplný výjimky bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="6117b-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="6117b-207"><sup>4</sup>je proveden pokus o porovnat všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6117b-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="6117b-208">Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je text, ntext nebo image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="6117b-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="6117b-209"><sup>5</sup>všechny jednotlivé elementy odkazy jsou porovnávány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).</span><span class="sxs-lookup"><span data-stu-id="6117b-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6117b-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="6117b-210">See Also</span></span>  
 [<span data-ttu-id="6117b-211">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="6117b-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)