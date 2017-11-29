---
title: "Aggregate – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47017414a92bfbca0df4ce6e2b70398a01762d37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="a7855-102">Aggregate – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7855-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="a7855-103">Jeden nebo více agregační funkce se vztahuje na kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7855-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7855-104">Syntax</span></span>  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="a7855-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a7855-105">Parts</span></span>  
  
|<span data-ttu-id="a7855-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a7855-106">Term</span></span>|<span data-ttu-id="a7855-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a7855-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="a7855-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a7855-108">Required.</span></span> <span data-ttu-id="a7855-109">Proměnná použít k iteraci v rámci prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="a7855-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="a7855-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a7855-110">Optional.</span></span> <span data-ttu-id="a7855-111">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="a7855-111">The type of `element`.</span></span> <span data-ttu-id="a7855-112">Pokud není zadán žádný typ., typ `element` je odvozeno z `collection`.</span><span class="sxs-lookup"><span data-stu-id="a7855-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="a7855-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a7855-113">Required.</span></span> <span data-ttu-id="a7855-114">Odkazuje na kolekci má být použito.</span><span class="sxs-lookup"><span data-stu-id="a7855-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="a7855-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a7855-115">Optional.</span></span> <span data-ttu-id="a7855-116">Nejméně jeden dotaz klauzule, například `Where` klauzule upřesněte touto aggregate – klauzule nebo klauzule do výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7855-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="a7855-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a7855-117">Required.</span></span> <span data-ttu-id="a7855-118">Jeden nebo více oddělených čárkou výrazů identifikují agregační funkci chcete použít pro kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="a7855-119">Alias můžete použít pro agregační funkci zadat jméno člena pro výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7855-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="a7855-120">Pokud je zadaný žádný alias se používá název agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="a7855-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="a7855-121">Příklady najdete v části o agregační funkce později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="a7855-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7855-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7855-122">Remarks</span></span>  
 <span data-ttu-id="a7855-123">`Aggregate` Klauzule lze zahrnout agregačních funkcí v dotazech.</span><span class="sxs-lookup"><span data-stu-id="a7855-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="a7855-124">Agregační funkce provádět kontroly a výpočtů v rámci sady hodnot a vrátí jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7855-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="a7855-125">Vypočtená hodnota můžete přistupovat pomocí členem výsledný typ dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7855-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="a7855-126">Jsou standardní agregační funkce, které můžete použít `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, a `Sum` funkce.</span><span class="sxs-lookup"><span data-stu-id="a7855-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="a7855-127">Tyto funkce jsou pro vývojáře, kteří mají zkušenosti se agregace v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="a7855-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="a7855-128">Jsou popsány v následující části tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a7855-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="a7855-129">Výsledek agregační funkci je součástí výsledek dotazu jako pole výsledný typ dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7855-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="a7855-130">Můžete zadat alias pro výsledek agregační funkce zadat název člena výsledný typ dotazu, který bude obsahovat celkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7855-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="a7855-131">Pokud je zadaný žádný alias se používá název agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="a7855-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="a7855-132">`Aggregate` Klauzule můžete začít dotazu, nebo může být zahrnuta jako další klauzuli v dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7855-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="a7855-133">Pokud `Aggregate` klauzule začne dotazu, výsledkem je jediná hodnota, která je výsledkem zadanou v agregační funkci `Into` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a7855-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="a7855-134">Pokud je zadán více než jeden agregační funkci v `Into` klauzule, dotaz vrátí jeden typ s samostatné vlastností tak, aby odkazovaly výsledek každé agregační funkci v `Into` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a7855-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="a7855-135">Pokud `Aggregate` klauzule je zahrnuta jako další klauzuli v dotazu, typ vrácený v kolekci dotazu bude mít samostatné vlastnost, která má odkazovat na výsledek každé agregační funkci v `Into` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a7855-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="a7855-136">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="a7855-136">Aggregate Functions</span></span>  
 <span data-ttu-id="a7855-137">Následující seznam popisuje standardní agregační funkce, které lze použít s `Aggregate` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a7855-137">The following list describes the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
|<span data-ttu-id="a7855-138">Funkce</span><span class="sxs-lookup"><span data-stu-id="a7855-138">Function</span></span>|<span data-ttu-id="a7855-139">Popis</span><span class="sxs-lookup"><span data-stu-id="a7855-139">Description</span></span>|  
|---|---|  
|`All`|<span data-ttu-id="a7855-140">Vrátí `true` Pokud všechny elementy v kolekci splňují zadanou podmínku; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="a7855-140">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="a7855-141">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-141">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|<span data-ttu-id="a7855-142">Vrátí `true` Pokud libovolný element v kolekci splňuje zadanou podmínku; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="a7855-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="a7855-143">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-143">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|<span data-ttu-id="a7855-144">Vypočítá průměrnou hodnotu všechny elementy v kolekci nebo ve výrazu výpočtů zadaný pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-144">Computes the average of all elements in the collection, or a computes supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a7855-145">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-145">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|<span data-ttu-id="a7855-146">Spočítá počet elementů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-146">Counts the number of elements in the collection.</span></span> <span data-ttu-id="a7855-147">Můžete zadat volitelný `Boolean` výraz, který má určený počet elementů v kolekci, které splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="a7855-147">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="a7855-148">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-148">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|<span data-ttu-id="a7855-149">Odkazuje na výsledky dotazu, které jsou seskupeny na základě těchto `Group By` nebo `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a7855-149">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="a7855-150">`Group` Funkce je platná pouze v `Into` klauzuli `Group By` nebo `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a7855-150">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="a7855-151">Další informace a příklady naleznete v tématu [skupiny pomocí klauzule](../../../visual-basic/language-reference/queries/group-by-clause.md) a [Group Join – klauzule](../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7855-151">For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>|  
|`LongCount`|<span data-ttu-id="a7855-152">Spočítá počet elementů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-152">Counts the number of elements in the collection.</span></span> <span data-ttu-id="a7855-153">Můžete zadat volitelný `Boolean` výraz, který má určený počet elementů v kolekci, které splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="a7855-153">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="a7855-154">Vrátí výsledek jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="a7855-154">Returns the result as a `Long`.</span></span> <span data-ttu-id="a7855-155">Příklad, naleznete v části `Count` agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="a7855-155">For an example, see the `Count` aggregate function.</span></span>|  
|`Max`|<span data-ttu-id="a7855-156">Vypočítá maximální hodnota z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-156">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a7855-157">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-157">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|<span data-ttu-id="a7855-158">Vypočítá minimální hodnota z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-158">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a7855-159">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-159">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|<span data-ttu-id="a7855-160">Vypočítá součet všech elementů v kolekci nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7855-160">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a7855-161">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="a7855-161">Following is an example:</span></span><br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a><span data-ttu-id="a7855-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7855-162">Example</span></span>  
 <span data-ttu-id="a7855-163">Následující příklad kódu ukazuje, jak používat `Aggregate` klauzule pro použití agregační funkce výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7855-163">The following code example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="a7855-164">Vytváření vlastní agregační funkce</span><span class="sxs-lookup"><span data-stu-id="a7855-164">Creating User-Defined Aggregate Functions</span></span>  
 <span data-ttu-id="a7855-165">Přidáním rozšiřující metody, které můžete zahrnout vlastní agregační funkce ve výrazu dotazu <xref:System.Collections.Generic.IEnumerable%601> typu.</span><span class="sxs-lookup"><span data-stu-id="a7855-165">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="a7855-166">Vlastní metoda pak můžete provádět výpočtu nebo operace na vyčíslitelná kolekci, která má odkazovat na agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="a7855-166">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="a7855-167">Další informace o metodách rozšíření najdete v tématu [rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a7855-167">For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="a7855-168">Například následující příklad kódu ukazuje vlastní agregační funkce pro výpočet Medián kolekce čísel.</span><span class="sxs-lookup"><span data-stu-id="a7855-168">For example, the following code example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="a7855-169">Existují dvě přetížení `Median` metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a7855-169">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="a7855-170">První přetížení přijme jako vstup, kolekci typu `IEnumerable(Of Double)`.</span><span class="sxs-lookup"><span data-stu-id="a7855-170">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="a7855-171">Pokud `Median` agregační funkce je volána pro dotaz pole typu `Double`, tato metoda bude volána.</span><span class="sxs-lookup"><span data-stu-id="a7855-171">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="a7855-172">Druhý přetížení `Median` metoda se dá předat všechny obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a7855-172">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="a7855-173">Obecné přetížení `Median` metoda přebírá druhý parametr, který odkazuje `Func(Of T, Double)` výrazu lambda do projektu typ (z kolekce) na hodnotu jako odpovídající hodnota typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="a7855-173">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="a7855-174">Potom postoupí výpočtu Medián další přetížení `Median` metoda.</span><span class="sxs-lookup"><span data-stu-id="a7855-174">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="a7855-175">Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a7855-175">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 <span data-ttu-id="a7855-176">Následující příklad ukazuje ukázkové dotazy, které volají kód `Median` agregační funkce na kolekci typu `Integer`a kolekci typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="a7855-176">The following code example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="a7855-177">Dotaz, který volá `Median` agregační funkce na kolekci typu `Double` volá přetížení `Median` metodu, která přijímá jako vstup, kolekci typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="a7855-177">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="a7855-178">Dotaz, který volá `Median` agregační funkce na kolekci typu `Integer` volá obecné přetížení `Median` metoda.</span><span class="sxs-lookup"><span data-stu-id="a7855-178">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a7855-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7855-179">See Also</span></span>  
 [<span data-ttu-id="a7855-180">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7855-180">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="a7855-181">Dotazy</span><span class="sxs-lookup"><span data-stu-id="a7855-181">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="a7855-182">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="a7855-182">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="a7855-183">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="a7855-183">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="a7855-184">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="a7855-184">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="a7855-185">Group By – klauzule</span><span class="sxs-lookup"><span data-stu-id="a7855-185">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)