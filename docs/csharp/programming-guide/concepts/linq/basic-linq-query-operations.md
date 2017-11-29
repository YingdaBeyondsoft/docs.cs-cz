---
title: "Základní operace dotazů LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7a258ae8d85425abb6d1474d2cb01b02f6deb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="5b8b0-102">Základní operace dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5b8b0-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="5b8b0-103">Toto téma poskytuje stručný úvod do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy a některé typické druhy operace, které můžete provádět v dotazu.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-103">This topic gives a brief introduction to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="5b8b0-104">Podrobnější informace jsou v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="5b8b0-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="5b8b0-105">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="5b8b0-105">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="5b8b0-106">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="5b8b0-106">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [<span data-ttu-id="5b8b0-107">Návod: Zápis dotazů v C#</span><span class="sxs-lookup"><span data-stu-id="5b8b0-107">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  <span data-ttu-id="5b8b0-108">Pokud jste již obeznámeni s dotazovací jazyk, jako je například SQL nebo XQuery, můžete přeskočit většinu tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="5b8b0-109">Přečtěte si informace o "`from` klauzule" v části Další informace o pořadí klauzule v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu výrazy.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-109">Read about the "`from` clause" in the next section to learn about the order of clauses in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="5b8b0-110">Získání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="5b8b0-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="5b8b0-111">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, prvním krokem je určit zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-111">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source.</span></span> <span data-ttu-id="5b8b0-112">Proměnné v jazyce C# stejně jako většinu programovacích jazyků musí být deklarován před použitím.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="5b8b0-113">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, `from` klauzule dodává nejdřív za účelem předložení zdroje dat (`customers`) a *proměnnou rozsahu* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-113">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 <span data-ttu-id="5b8b0-114">Proměnná rozsahu je jako proměnné iterace ve `foreach` cykly s tím rozdílem, že dojde k žádné skutečné iterace ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="5b8b0-115">Po provedení dotazu proměnnou rozsahu bude sloužit jako odkaz na všechny následné prvky v `customers`.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="5b8b0-116">Protože kompilátor lze odvodit typ `cust`, není nutné explicitně zadat.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="5b8b0-117">Další rozsah proměnné mohou být způsobeny `let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="5b8b0-118">Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-118">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b8b0-119">Pro data neobecné zdroje, jako <xref:System.Collections.ArrayList>, proměnnou rozsahu musí být explicitně zadán.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="5b8b0-120">Další informace najdete v tématu [postup: dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) a [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-120">For more information, see [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) and [from clause](../../../../csharp/language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="5b8b0-121">Filtrování</span><span class="sxs-lookup"><span data-stu-id="5b8b0-121">Filtering</span></span>  
 <span data-ttu-id="5b8b0-122">Nejběžnější operace dotazů je pravděpodobně použít filtr ve formě logický výraz.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="5b8b0-123">Filtr způsobí, že dotaz vrátil jenom elementy, pro které je výraz hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="5b8b0-124">Výsledkem je vytvořena pomocí `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="5b8b0-125">Filtr platí určuje prvky, které chcete vyloučit ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="5b8b0-126">V následujícím příkladu, pouze ty `customers` kdo mají adresu v Londýně jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 <span data-ttu-id="5b8b0-127">Můžete použít známé jazyka C# logické `AND` a `OR` operátory použít jako mnoho filtrovat výrazy v případě potřeby v `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="5b8b0-128">Chcete-li například vrátit pouze zákazníky z "Praha" `AND` jehož jméno je "Devon" by zápisu následující kód:</span><span class="sxs-lookup"><span data-stu-id="5b8b0-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 <span data-ttu-id="5b8b0-129">Vracení zákazníky z Londýna nebo Paříž, by zápisu následující kód:</span><span class="sxs-lookup"><span data-stu-id="5b8b0-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 <span data-ttu-id="5b8b0-130">Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-130">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="5b8b0-131">Řazení</span><span class="sxs-lookup"><span data-stu-id="5b8b0-131">Ordering</span></span>  
 <span data-ttu-id="5b8b0-132">Často je vhodnější seřaďte vrácená data.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="5b8b0-133">`orderby` Klauzule způsobí, že elementy vrácený postupně, který se má seřadit podle výchozí porovnávače pro typ řazen.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="5b8b0-134">Například následující dotaz lze rozšířit pro řazení výsledků na základě `Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="5b8b0-135">Protože `Name` je řetězec, porovnávače výchozí provede abecedním řazení z A do Z.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 <span data-ttu-id="5b8b0-136">Chcete-li v obráceném pořadí řazení výsledků z Z až A, použijte `orderby…descending` klauzule.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="5b8b0-137">Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-137">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="5b8b0-138">Seskupování</span><span class="sxs-lookup"><span data-stu-id="5b8b0-138">Grouping</span></span>  
 <span data-ttu-id="5b8b0-139">`group` Klauzule umožňují seskupit výsledky podle klíče, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="5b8b0-140">Například můžete zadat, že výsledky by měly být seskupené podle `City` tak, aby všechny zákazníky z Londýna nebo Paříž jsou v jednotlivých skupinách.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="5b8b0-141">V takovém případě `cust.City` je klíč.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 <span data-ttu-id="5b8b0-142">Při ukončení dotaz s `group` klauzuli výsledky mít formu seznam seznamů.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="5b8b0-143">Každý prvek v seznamu je objekt, který má `Key` člen a seznam prvky, které jsou seskupené v rámci tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="5b8b0-144">Pokud jste iterace v dotazu, který produkuje pořadí skupin, je nutné použít vnořený `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="5b8b0-145">Vnější smyčky iteruje nad každou skupinu a vnitřní smyčky iteruje nad členy každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="5b8b0-146">Pokud musí odkazovat na výsledky operace skupiny, můžete použít `into` – klíčové slovo vytvořit identifikátor, který může být dotazován na další.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="5b8b0-147">Následující dotaz vrátí jenom skupiny, které obsahují více než dva zákazníkům:</span><span class="sxs-lookup"><span data-stu-id="5b8b0-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 <span data-ttu-id="5b8b0-148">Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-148">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="5b8b0-149">Spojování</span><span class="sxs-lookup"><span data-stu-id="5b8b0-149">Joining</span></span>  
 <span data-ttu-id="5b8b0-150">Operace spojení vytvořit přidružení mezi pořadí, která nejsou explicitně modelován v datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="5b8b0-151">Například můžete provést připojení k vyhledání zákazníků a distributorů, kteří mají stejné umístění.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="5b8b0-152">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` klauzule vždy funguje s kolekcí objektů místo databázových tabulek přímo.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-152">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 <span data-ttu-id="5b8b0-153">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nemusíte používat `join` často uděláte v systému SQL, protože cizí klíče v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] jsou vyjádřené v modelu objektu vlastnosti, které mají kolekce položek.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-153">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] you do not have to use `join` as often as you do in SQL because foreign keys in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="5b8b0-154">Například `Customer` objektu obsahuje kolekci `Order` objekty.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="5b8b0-155">Místo provedení spojení, máte přístup k objednávky pomocí zápisu s tečkou:</span><span class="sxs-lookup"><span data-stu-id="5b8b0-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```  
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="5b8b0-156">Další informace najdete v tématu [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-156">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="5b8b0-157">Výběr (projekce)</span><span class="sxs-lookup"><span data-stu-id="5b8b0-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="5b8b0-158">`select` Klauzule vytváří výsledky dotazu a určuje "tvar" nebo typ každý vrácený element.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="5b8b0-159">Například můžete určit, jestli výsledky budou tvořeny dokončení `Customer` objekty, jenom jednoho člena, podmnožinu členů nebo nějaký typ úplně jiné výsledek podle výpočtů nebo vytvoření nového objektu.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="5b8b0-160">Když `select` klauzule vytvořil něco jiného než kopii source element, operace se nazývá *projekce*.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="5b8b0-161">Použití projekce k transformaci dat je výkonná funkce [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy.</span><span class="sxs-lookup"><span data-stu-id="5b8b0-161">The use of projections to transform data is a powerful capability of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5b8b0-162">Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) a [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5b8b0-162">For more information, see [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8b0-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b8b0-163">See Also</span></span>  
 [<span data-ttu-id="5b8b0-164">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="5b8b0-164">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="5b8b0-165">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="5b8b0-165">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="5b8b0-166">Návod: Zápis dotazů v C#</span><span class="sxs-lookup"><span data-stu-id="5b8b0-166">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [<span data-ttu-id="5b8b0-167">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5b8b0-167">Query Keywords (LINQ)</span></span>](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="5b8b0-168">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="5b8b0-168">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)