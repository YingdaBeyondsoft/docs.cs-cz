---
title: "Zahození – průvodce v C#"
description: "Popisuje C# pro podporu zahození, které nepřiřazené, discardable proměnné a způsoby, ve které je možné zahození."
keywords: "Rozhraní .NET, .NET core"
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 800a27d2d186c738dceb6838aa669377a0c07b01
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2017
---
# <a name="discards---c-guide"></a><span data-ttu-id="ea0b1-104">Zahození – průvodce v C#</span><span class="sxs-lookup"><span data-stu-id="ea0b1-104">Discards - C# Guide</span></span>

<span data-ttu-id="ea0b1-105">Od verze jazyka C# 7, C# podporuje zahodí, které jsou dočasné, fiktivní proměnné, které jsou záměrně nepoužívané v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-105">Starting with C# 7, C# supports discards, which are temporary, dummy variables that are intentionally unused in application code.</span></span> <span data-ttu-id="ea0b1-106">Zahození odpovídají nepřiřazené proměnné; nemají hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-106">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="ea0b1-107">Protože je pouze jeden zahození proměnnou, a tuto proměnnou i nelze přidělit úložiště, můžete snížit zahození přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-107">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="ea0b1-108">Protože záměr vymazat kódu, zvýšit jeho přehlednosti a jeho udržovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-108">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="ea0b1-109">Můžete znamenat, že proměnné zahození přiřazením podtržítko (`_`) jako její název.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-109">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="ea0b1-110">Například následující volání metody, které vrací 3 řazenou kolekci členů ve kterém jsou hodnoty první a druhý zahození a *oblasti* je dříve deklarované proměnné na hodnotu odpovídající třetí součást vrácený  *GetCityInformation*:</span><span class="sxs-lookup"><span data-stu-id="ea0b1-110">For example, the following method call returns a 3-tuple in which the first and second values are discards and *area* is a previously declared variable to be set to the corresponding third component returned by *GetCityInformation*:</span></span>

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="ea0b1-111">V jazyce C# 7 zahození jsou podporovány v přiřazení v kontextech následující:</span><span class="sxs-lookup"><span data-stu-id="ea0b1-111">In C# 7, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="ea0b1-112">Řazené kolekce členů a objekt [deconstruction](deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="ea0b1-112">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="ea0b1-113">Porovnávání vzorů s [je](language-reference/keywords/is.md) a [přepínač](language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="ea0b1-113">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="ea0b1-114">Volání metody s `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-114">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="ea0b1-115">Samostatný `_` při ne `_` nachází v oboru.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-115">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="ea0b1-116">Když `_` je platný zahození, pokusu o načtení její hodnota nebo použít v operaci přiřazení vygeneruje Chyba kompilátoru CS0301, "název"\_' neexistuje v aktuálním kontextu ".</span><span class="sxs-lookup"><span data-stu-id="ea0b1-116">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="ea0b1-117">Důvodem je, že `_` není přiřazenou hodnotu a nemusí dají přiřadit dokonce i umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-117">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="ea0b1-118">By měla skutečná proměnná, nelze zrušit více než jednu hodnotu, jako předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-118">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="ea0b1-119">Řazené kolekce členů a objekt deconstruction</span><span class="sxs-lookup"><span data-stu-id="ea0b1-119">Tuple and object deconstruction</span></span>

<span data-ttu-id="ea0b1-120">Zahození jsou obzvláště užitečná při práci s řazenými kolekcemi členů, pokud kód aplikace používá některé prvky řazené kolekce členů, ale ignoruje ostatní.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-120">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="ea0b1-121">Například následující `QueryCityDataForYears` metoda vrátí hodnotu 6-řazené kolekce členů s názvem města, jeho oblasti, rok, název města plnění pro tento rok, druhý roku a název města plnění pro tento druhý roku.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-121">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="ea0b1-122">Příklad ukazuje změnu v plnění mezi tyto dva roky.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-122">The example shows the change in population between those two years.</span></span> <span data-ttu-id="ea0b1-123">Data k dispozici z řazenou kolekci členů, jsme unconcerned oblasti města a víme název města a kalendářní data v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-123">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="ea0b1-124">V důsledku toho jsme se pouze zajímá dvě naplnění hodnotami uloženými v řazené kolekci členů a jeho zbývající hodnoty jako zahození dokáže zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-124">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="ea0b1-125">Další informace o deconstructing řazené kolekce členů s zahození najdete v tématu [Deconstructing řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-tuple-elements-with-discards).</span><span class="sxs-lookup"><span data-stu-id="ea0b1-125">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="ea0b1-126">`Deconstruct` Metoda třída, struktura nebo rozhraní také umožňuje načíst a deconstruct konkrétní sadu dat z objektu.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-126">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="ea0b1-127">Zahození můžete použít, pokud vás zajímá jenom podmnožinu deconstructed hodnoty práce.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-127">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="ea0b1-128">Následující příklad deconstructs Ihe `Person` objektu do čtyř řetězce (první a poslední názvů, Město a stav), ale zahodí příjmení a stavu.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-128">Ihe following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

<span data-ttu-id="ea0b1-129">Další informace o deconstructing uživatelem definované typy s zahození najdete v tématu [Deconstructing řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span><span class="sxs-lookup"><span data-stu-id="ea0b1-129">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="ea0b1-130">Porovnávání vzorů s `switch` a`is`</span><span class="sxs-lookup"><span data-stu-id="ea0b1-130">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="ea0b1-131">*Zahodit vzor* mohou být používány s porovnávání vzorů [je](language-reference/keywords/is.md) a [přepínač](language-reference/keywords/switch.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-131">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="ea0b1-132">Každý výraz vždy zahození shodu.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-132">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="ea0b1-133">V následujícím příkladu definuje `ProvidesFormatInfo` metoda, která používá [je](language-reference/keywords/is.md) tvrzení, abyste zjistili, zda objekt poskytuje <xref:System.IFormatProvider> implementace a testy, jestli je objekt `null`.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-133">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="ea0b1-134">Také využívá vzor zahození k práci s objekty nesmí být nulová žádného jiného typu.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-134">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="ea0b1-135">Volání metody s výstupní parametry</span><span class="sxs-lookup"><span data-stu-id="ea0b1-135">Calls to methods with out parameters</span></span>

<span data-ttu-id="ea0b1-136">Při volání metody `Deconstruct` metodu deconstruct uživatelem definovaný typ (instance třídy, struktury nebo rozhraní), můžete zrušit hodnoty individuální `out` argumenty.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-136">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="ea0b1-137">Ale můžete také zahodit hodnotu `out` argumenty při voláním jakékoli metody se parametr typu out.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-137">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span> 

<span data-ttu-id="ea0b1-138">Následující příklad volání [DateTime.TryParse (řetězec, se data a času)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) metoda k určení, zda je řetězec představující datum platný v aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-138">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="ea0b1-139">Protože příklad se týká pouze s ověřování řetězce data a není analýza ho extrahovat data, `out` argumentu metody je zahození.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-139">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a><span data-ttu-id="ea0b1-140">Samostatné zahození</span><span class="sxs-lookup"><span data-stu-id="ea0b1-140">A standalone discard</span></span>

<span data-ttu-id="ea0b1-141">Samostatné zahození slouží k označení jakékoli proměnné, kterou jste se rozhodli ignorovat.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-141">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="ea0b1-142">Následující příklad používá samostatné zahození Ignorovat <xref:System.Threading.Tasks.Task> objekt vrácený asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-142">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="ea0b1-143">To má za následek potlačení výjimku, která vyvolá operaci, protože se jedná o k dokončení.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-143">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

<span data-ttu-id="ea0b1-144">Všimněte si, že `_` je také platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-144">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="ea0b1-145">Při použití mimo kontext-podporované `_` považuje, nikoli jako zahození ale jako platná proměnná.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-145">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="ea0b1-146">Pokud název identifikátor `_` je již v oboru, použití `_` jako samostatná zahození může mít za následek:</span><span class="sxs-lookup"><span data-stu-id="ea0b1-146">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="ea0b1-147">Náhodných změna hodnoty v oborem `_` proměnné přiřazením hodnotu určený zahození.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-147">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="ea0b1-148">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ea0b1-148">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- <span data-ttu-id="ea0b1-149">Chyba kompilátoru pro narušení zabezpečení typů.</span><span class="sxs-lookup"><span data-stu-id="ea0b1-149">A compiler error for violating type safety.</span></span> <span data-ttu-id="ea0b1-150">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ea0b1-150">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- <span data-ttu-id="ea0b1-151">Chyba kompilátoru CS0136, "místní instalační cestu nebo parametr s názvem '_' nelze deklarovat v tomto rozsahu vzhledem k tomu, že tento název se používá v nadřazených místní rozsah k definování místní instalační cestu nebo parametr."</span><span class="sxs-lookup"><span data-stu-id="ea0b1-151">Compiler error CS0136, "A local or parameter named '_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="ea0b1-152">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ea0b1-152">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a><span data-ttu-id="ea0b1-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea0b1-153">See also</span></span>
<span data-ttu-id="ea0b1-154">[Deconstructing řazených kolekcí členů a dalších typů](deconstruct.md) </span><span class="sxs-lookup"><span data-stu-id="ea0b1-154">[Deconstructing tuples and other types](deconstruct.md) </span></span>  
<span data-ttu-id="ea0b1-155">[`is`– klíčové slovo](language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="ea0b1-155">[`is` keyword](language-reference/keywords/is.md) </span></span>  
[<span data-ttu-id="ea0b1-156">`switch`– klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="ea0b1-156">`switch` keyword</span></span>](language-reference/keywords/switch.md)   