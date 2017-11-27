---
title: "Interpolované řetězce (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b8a1fe0be82a0e09d61c66ed463199ff626c9faa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="c0f72-102">Interpolované řetězce (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c0f72-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="c0f72-103">Umožňuje vytvářet řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0f72-103">Used to construct strings.</span></span>  <span data-ttu-id="c0f72-104">Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="c0f72-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="c0f72-105">Interpolované řetězce vrátí řetězec, který nahradí jejich řetězcové vyjádření interpolované výrazy, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="c0f72-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="c0f72-106">Tato funkce je k dispozici v C# 6 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="c0f72-106">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="c0f72-107">Argumenty interpolované řetězce jsou srozumitelnější než [složený formátovací řetězec](../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="c0f72-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="c0f72-108">Například interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="c0f72-108">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
<span data-ttu-id="c0f72-109">obsahuje dva interpolované výrazy {name}' a '{hodina: hh}'.</span><span class="sxs-lookup"><span data-stu-id="c0f72-109">contains two interpolated expressions, '{name}' and '{hour:hh}'.</span></span> <span data-ttu-id="c0f72-110">Je ekvivalentní složený formátovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="c0f72-110">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="c0f72-111">Struktura interpolované řetězce je:</span><span class="sxs-lookup"><span data-stu-id="c0f72-111">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="c0f72-112">kde:</span><span class="sxs-lookup"><span data-stu-id="c0f72-112">where:</span></span> 

- <span data-ttu-id="c0f72-113">*Šířka pole* se znaménkem, která určuje počet znaků v poli.</span><span class="sxs-lookup"><span data-stu-id="c0f72-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="c0f72-114">Pokud je kladné, je pole vpravo zarovnaný; záporná, zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="c0f72-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="c0f72-115">*řetězec formátu* je vhodný pro typ objektu, který je formátován řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="c0f72-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="c0f72-116">Například <xref:System.DateTime> hodnotu, může to být standardní hodnoty data a řetězec formátu času, například "D" nebo "d".</span><span class="sxs-lookup"><span data-stu-id="c0f72-116">For example, for a <xref:System.DateTime> value, it could be a standard date and time format string such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0f72-117">Nemůže mít žádné mezery mezi `$` a `"` , začíná řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0f72-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="c0f72-118">To způsobí, že chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c0f72-118">Doing so causes a compile time error.</span></span>

 <span data-ttu-id="c0f72-119">Interpolované řetězce můžete použít kdekoli můžete řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="c0f72-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="c0f72-120">Interpolované řetězce je vyhodnocován pokaždé, když spustí kód s interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0f72-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="c0f72-121">To umožňuje oddělit definice a vyhodnocení interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0f72-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="c0f72-122">Zahrnout složené závorky ("{" nebo "}") v interpolované řetězce, pomocí dvou složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="c0f72-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="c0f72-123">Implicitní převody části Další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="c0f72-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="c0f72-124">Pokud interpolované řetězec obsahuje jiné znaky s zvláštní význam interpolované řetězce, jako je například uvozovky ("), dvojtečkou (:) ani čárky (,), že by měly být ukončeny Pokud se vyskytují v literálu text, nebo by měl být součástí výrazu oddělená závorky, pokud jsou součástí interpolované výrazu prvků jazyka.</span><span class="sxs-lookup"><span data-stu-id="c0f72-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="c0f72-125">Následující příklad řídicí sekvence znaky uvozovek pro zahrnutí ve výsledném řetězci a používá kulaté závorky a tím vymezit výraz `(age == 1 ? "" : "s")` tak, aby dvojtečkou není interpretována jako od řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="c0f72-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

<span data-ttu-id="c0f72-126">Doslovné interpolované řetězce použití `$` následuje znak `@` znak.</span><span class="sxs-lookup"><span data-stu-id="c0f72-126">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="c0f72-127">Další informace o typu verbatim řetězců najdete v tématu [řetězec](string.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="c0f72-127">For more information about verbatim strings, see the [string](string.md) topic.</span></span> <span data-ttu-id="c0f72-128">Následující kód je upravenou verzi fragmentu předchozí pomocí typu verbatim interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="c0f72-128">The following code is a modified version of the previous snippet using a verbatim interpolated string:</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

<span data-ttu-id="c0f72-129">Změny formátování jsou nutné, protože není orientují typu verbatim řetězce `\` řídicí sekvence.</span><span class="sxs-lookup"><span data-stu-id="c0f72-129">The formatting changes are necessary because verbatim strings do not obey `\` escape sequences.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0f72-130">`$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0f72-130">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>


## <a name="implicit-conversions"></a><span data-ttu-id="c0f72-131">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="c0f72-131">Implicit Conversions</span></span>  

<span data-ttu-id="c0f72-132">Existují tři typu implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="c0f72-132">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="c0f72-133">Interpolované řetězce pro převod <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c0f72-133">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="c0f72-134">Následující příklad vrátí řetězec, jehož interpolované řetězce výrazy nahradil jejich řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="c0f72-134">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="c0f72-135">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c0f72-135">For example:</span></span>

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   <span data-ttu-id="c0f72-136">Toto je poslední výsledek interpretace řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0f72-136">This is the final result of a string interpretation.</span></span> <span data-ttu-id="c0f72-137">Všechny výskyty dvojité složené závorky ("{{" a "}}") se převedou na jednom složených závorek.</span><span class="sxs-lookup"><span data-stu-id="c0f72-137">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="c0f72-138">Interpolované řetězce pro převod <xref:System.IFormattable> proměnné, která umožňuje vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="c0f72-138">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="c0f72-139">To je užitečné pro jako jsou správné číselné a číselné formáty pro jednotlivé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="c0f72-139">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="c0f72-140">Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud se naformátovat řetězec voláním explicitně nebo implicitně <xref:System.Object.ToString> metoda.</span><span class="sxs-lookup"><span data-stu-id="c0f72-140">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="c0f72-141">Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c0f72-141">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="c0f72-142">Následující příklad používá reflexe k zobrazení členů, jakož i pole a vlastnosti hodnoty <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0f72-142">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="c0f72-143">Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="c0f72-143">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   <span data-ttu-id="c0f72-144">Všimněte si, že může být prověřovány interpolované řetězce pouze pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="c0f72-144">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="c0f72-145">Pokud je předán řetězec formátování metoda, jako například <xref:System.Console.WriteLine(System.String)>, jeho položky formátu jsou vyřešeny a vrátí výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0f72-145">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="c0f72-146">Interpolované řetězce pro převod <xref:System.FormattableString> proměnné, která představuje složený formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0f72-146">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="c0f72-147">Probíhá kontrola složený formátovací řetězec a jak se vykreslí v důsledku řetězec, například vám můžou pomoct chránit před útoky, vkládání, pokud vytváříte dotazu.</span><span class="sxs-lookup"><span data-stu-id="c0f72-147">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="c0f72-148"><xref:System.FormattableString>také zahrnuje <xref:System.FormattableString.ToString> přetížení, které vám umožní vytvořit výsledek řetězce pro <xref:System.Globalization.CultureInfo.InvariantCulture> a <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="c0f72-148"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the <xref:System.Globalization.CultureInfo.InvariantCulture> and <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>  <span data-ttu-id="c0f72-149">Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud formátovat.</span><span class="sxs-lookup"><span data-stu-id="c0f72-149">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="c0f72-150">Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c0f72-150">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a><span data-ttu-id="c0f72-151">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="c0f72-151">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0f72-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0f72-152">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="c0f72-153">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0f72-153">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c0f72-154">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c0f72-154">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)