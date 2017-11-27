---
title: "C# struktury - přehled používání jazyka C#"
description: "Informace, že typů, názvem struktury hodnot Základy C#"
keywords: "Rozhraní .NET, C#, struktura, typu hodnoty"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="structs"></a><span data-ttu-id="874c2-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="874c2-104">Structs</span></span>

<span data-ttu-id="874c2-105">Jako jsou třídy, ***struktury*** jsou datové struktury, které mohou obsahovat členy data a funkce členy, ale na rozdíl od třídy, struktury, jsou typy hodnot a nevyžadují přidělení haldy.</span><span class="sxs-lookup"><span data-stu-id="874c2-105">Like classes, ***structs*** are data structures that can contain data members and function members, but unlike classes, structs are value types and do not require heap allocation.</span></span> <span data-ttu-id="874c2-106">Proměnné typu Struktura přímo ukládá data struktura, zatímco proměnná typu třídy ukládá odkaz na objekt dynamicky přidělené.</span><span class="sxs-lookup"><span data-stu-id="874c2-106">A variable of a struct type directly stores the data of the struct, whereas a variable of a class type stores a reference to a dynamically allocated object.</span></span> <span data-ttu-id="874c2-107">Struktura typy nepodporují dědičnosti definované uživatelem, a všechny typy struktura implicitně dědí od typu <xref:System.ValueType>, který v zapnout implicitně dědí z `object`.</span><span class="sxs-lookup"><span data-stu-id="874c2-107">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type <xref:System.ValueType>, which in turn implicitly inherits from `object`.</span></span>

<span data-ttu-id="874c2-108">Struktury jsou obzvláště užitečná pro malé datové struktury, které mají hodnotu sémantiku.</span><span class="sxs-lookup"><span data-stu-id="874c2-108">Structs are particularly useful for small data structures that have value semantics.</span></span> <span data-ttu-id="874c2-109">Komplexní čísla, body v souřadnicový systém nebo páry klíč hodnota ve slovníku jsou všechny dobrými příklady struktury.</span><span class="sxs-lookup"><span data-stu-id="874c2-109">Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs.</span></span> <span data-ttu-id="874c2-110">Použití struktur místo třídy pro malé datové struktury provádět velký rozdíl v počtu přidělení paměti aplikace provede.</span><span class="sxs-lookup"><span data-stu-id="874c2-110">The use of structs rather than classes for small data structures can make a large difference in the number of memory allocations an application performs.</span></span> <span data-ttu-id="874c2-111">Například následující program vytvoří a inicializuje pole 100 bodů.</span><span class="sxs-lookup"><span data-stu-id="874c2-111">For example, the following program creates and initializes an array of 100 points.</span></span> <span data-ttu-id="874c2-112">S `Point` implementována jako třída, 101 samostatných objektech instance – jednu pro pole a jeden pro 100 elementy.</span><span class="sxs-lookup"><span data-stu-id="874c2-112">With `Point` implemented as a class, 101 separate objects are instantiated—one for the array and one each for the 100 elements.</span></span>

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

<span data-ttu-id="874c2-113">Alternativou je aby bod struktury.</span><span class="sxs-lookup"><span data-stu-id="874c2-113">An alternative is to make Point a struct.</span></span>

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

<span data-ttu-id="874c2-114">Nyní pouze jeden objekt je vytvořena instance – jednu pro pole – a `Point` instance jsou uložené v řádku v poli.</span><span class="sxs-lookup"><span data-stu-id="874c2-114">Now, only one object is instantiated—the one for the array—and the `Point` instances are stored in-line in the array.</span></span>

<span data-ttu-id="874c2-115">Konstruktory struktury jsou spuštěny se operátor new, ale neznamená, že paměť je právě přiděleny.</span><span class="sxs-lookup"><span data-stu-id="874c2-115">Struct constructors are invoked with the new operator, but that does not imply that memory is being allocated.</span></span> <span data-ttu-id="874c2-116">Místo dynamické přidělování objektu a vrátí odkaz na jeho struktura konstruktor jednoduše vrátí hodnotu – struktura (obvykle do dočasného umístění v zásobníku) a tato hodnota je pak zkopíruje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="874c2-116">Instead of dynamically allocating an object and returning a reference to it, a struct constructor simply returns the struct value itself (typically in a temporary location on the stack), and this value is then copied as necessary.</span></span>

<span data-ttu-id="874c2-117">Pomocí třídy je možné pro dvě proměnné tak, aby odkazovaly na stejný objekt a proto možná pro operace na jednu proměnnou ovlivnit objekt odkazují jiné proměnné.</span><span class="sxs-lookup"><span data-stu-id="874c2-117">With classes, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="874c2-118">S struktury proměnné každý mají své vlastní kopii dat a není možné pro operace na jeden, který bude mít vliv na druhý.</span><span class="sxs-lookup"><span data-stu-id="874c2-118">With structs, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other.</span></span> <span data-ttu-id="874c2-119">Například výstup vytvořený podle následující fragment kódu závisí na tom bodu třídu nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="874c2-119">For example, the output produced by the following code fragment depends on whether Point is a class or a struct.</span></span>

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

<span data-ttu-id="874c2-120">Pokud `Point` je třída, výstup je 20, protože a b odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="874c2-120">If `Point` is a class, the output is 20 because a and b reference the same object.</span></span> <span data-ttu-id="874c2-121">Pokud je bod struktury, výstup je 10, protože přiřazení `a` k `b` vytvoří kopii hodnoty, a tato kopie není ovlivněna následné přiřazení `a.x`.</span><span class="sxs-lookup"><span data-stu-id="874c2-121">If Point is a struct, the output is 10 because the assignment of `a` to `b` creates a copy of the value, and this copy is unaffected by the subsequent assignment to `a.x`.</span></span>

<span data-ttu-id="874c2-122">Předchozí příklad označuje dvě omezení struktury.</span><span class="sxs-lookup"><span data-stu-id="874c2-122">The previous example highlights two of the limitations of structs.</span></span> <span data-ttu-id="874c2-123">Nejprve kopírování celá struktura je obvykle míň efektivní než kopírování odkaz na objekt, takže předávání přiřazení a hodnota parametru může být nákladnější s struktury než s odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="874c2-123">First, copying an entire struct is typically less efficient than copying an object reference, so assignment and value parameter passing can be more expensive with structs than with reference types.</span></span> <span data-ttu-id="874c2-124">Druhý, s výjimkou `ref` a `out` parametry, není možné vytvořit odkazy na struktury, která pravidla se jejich využití v mnoha situacích.</span><span class="sxs-lookup"><span data-stu-id="874c2-124">Second, except for `ref` and `out` parameters, it is not possible to create references to structs, which rules out their usage in a number of situations.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="874c2-125">[Předchozí](classes-and-objects.md)
[další](arrays.md)</span><span class="sxs-lookup"><span data-stu-id="874c2-125">[Previous](classes-and-objects.md)
[Next](arrays.md)</span></span>