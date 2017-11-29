---
title: "Předávání parametrů typu odkazu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2cd862a9179e027ab82631631784203993d0465a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a><span data-ttu-id="9b959-102">Předávání parametrů typu odkazu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9b959-102">Passing Reference-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="9b959-103">Proměnná [odkazují na typ](../../../csharp/language-reference/keywords/reference-types.md) neobsahuje data přímo; obsahuje odkaz na jeho data.</span><span class="sxs-lookup"><span data-stu-id="9b959-103">A variable of a [reference type](../../../csharp/language-reference/keywords/reference-types.md) does not contain its data directly; it contains a reference to its data.</span></span> <span data-ttu-id="9b959-104">Pokud předáte parametr typu odkazu podle hodnoty, je možné změnit data, na kterou odkaz, jako je například hodnotu člena třídy odkazuje.</span><span class="sxs-lookup"><span data-stu-id="9b959-104">When you pass a reference-type parameter by value, it is possible to change the data pointed to by the reference, such as the value of a class member.</span></span> <span data-ttu-id="9b959-105">Však nelze změnit hodnotu odkaz sám; To znamená nelze použít odkaz na stejnou přidělit paměť pro novou třídu a jej zachovat mimo blok.</span><span class="sxs-lookup"><span data-stu-id="9b959-105">However, you cannot change the value of the reference itself; that is, you cannot use the same reference to allocate memory for a new class and have it persist outside the block.</span></span> <span data-ttu-id="9b959-106">Kvůli tomu předat pomocí parametru [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9b959-106">To do that, pass the parameter using the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) keyword.</span></span> <span data-ttu-id="9b959-107">Pro jednoduchost, použijte následující příklady `ref`.</span><span class="sxs-lookup"><span data-stu-id="9b959-107">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-reference-types-by-value"></a><span data-ttu-id="9b959-108">Typy odkazů předávání podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="9b959-108">Passing Reference Types by Value</span></span>  
 <span data-ttu-id="9b959-109">Následující příklad ukazuje předání parametru typu odkazu, `arr`, podle hodnoty, na metodu `Change`.</span><span class="sxs-lookup"><span data-stu-id="9b959-109">The following example demonstrates passing a reference-type parameter, `arr`, by value, to a method, `Change`.</span></span> <span data-ttu-id="9b959-110">Vzhledem k tomu, že je odkaz na parametr `arr`, je možné ke změně hodnot prvků pole.</span><span class="sxs-lookup"><span data-stu-id="9b959-110">Because the parameter is a reference to `arr`, it is possible to change the values of the array elements.</span></span> <span data-ttu-id="9b959-111">Ale pokus o přiřazení parametr pouze umístění různých paměti funguje uvnitř metody a nemá vliv na původní proměnná `arr`.</span><span class="sxs-lookup"><span data-stu-id="9b959-111">However, the attempt to reassign the parameter to a different memory location only works inside the method and does not affect the original variable, `arr`.</span></span>  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 <span data-ttu-id="9b959-112">V předchozím příkladu poli `arr`, který je typu odkazu je předaný metodě bez `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="9b959-112">In the preceding example, the array, `arr`, which is a reference type, is passed to the method without the `ref` parameter.</span></span> <span data-ttu-id="9b959-113">V takovém případě kopii odkaz, který odkazuje na `arr`, je předaná metodě.</span><span class="sxs-lookup"><span data-stu-id="9b959-113">In such a case, a copy of the reference, which points to `arr`, is passed to the method.</span></span> <span data-ttu-id="9b959-114">Výstup ukazuje, že je možné metody pro změnu obsahu elementu pole, v tomto případě z `1` k `888`.</span><span class="sxs-lookup"><span data-stu-id="9b959-114">The output shows that it is possible for the method to change the contents of an array element, in this case from `1` to `888`.</span></span> <span data-ttu-id="9b959-115">Však přidělování novou část paměti pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor uvnitř `Change` metoda umožňuje proměnnou `pArray` odkazovat na nové pole.</span><span class="sxs-lookup"><span data-stu-id="9b959-115">However, allocating a new portion of memory by using the [new](../../../csharp/language-reference/keywords/new.md) operator inside the `Change` method makes the variable `pArray` reference a new array.</span></span> <span data-ttu-id="9b959-116">Proto veškeré změny, po který nebude mít vliv na původní pole `arr`, který je vytvořen uvnitř `Main`.</span><span class="sxs-lookup"><span data-stu-id="9b959-116">Thus, any changes after that will not affect the original array, `arr`, which is created inside `Main`.</span></span> <span data-ttu-id="9b959-117">Ve skutečnosti dvě pole jsou vytvořené v tomto příkladu jeden uvnitř `Main` a jeden uvnitř `Change` metoda.</span><span class="sxs-lookup"><span data-stu-id="9b959-117">In fact, two arrays are created in this example, one inside `Main` and one inside the `Change` method.</span></span>  
  
## <a name="passing-reference-types-by-reference"></a><span data-ttu-id="9b959-118">Typy odkazů předávání odkazem</span><span class="sxs-lookup"><span data-stu-id="9b959-118">Passing Reference Types by Reference</span></span>  
 <span data-ttu-id="9b959-119">Následující příklad je stejný jako předchozí příklad, vyjma toho, že `ref` – klíčové slovo se přidá do hlavičky metoda a volání.</span><span class="sxs-lookup"><span data-stu-id="9b959-119">The following example is the same as the previous example, except that the `ref` keyword is added to the method header and call.</span></span> <span data-ttu-id="9b959-120">Veškeré změny, které probíhají ve metodu ovlivnit původní proměnné v volací program.</span><span class="sxs-lookup"><span data-stu-id="9b959-120">Any changes that take place in the method affect the original variable in the calling program.</span></span>  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 <span data-ttu-id="9b959-121">Všechny změny, které se uskuteční uvnitř metody ovlivnit původní pole v `Main`.</span><span class="sxs-lookup"><span data-stu-id="9b959-121">All of the changes that take place inside the method affect the original array in `Main`.</span></span> <span data-ttu-id="9b959-122">Ve skutečnosti původní pole je znovu přidělit, pomocí `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="9b959-122">In fact, the original array is reallocated using the `new` operator.</span></span> <span data-ttu-id="9b959-123">Proto po volání `Change` metody žádný odkaz na `arr` odkazuje na pole pět element, který je vytvořen v `Change` metoda.</span><span class="sxs-lookup"><span data-stu-id="9b959-123">Thus, after calling the `Change` method, any reference to `arr` points to the five-element array, which is created in the `Change` method.</span></span>  
  
## <a name="swapping-two-strings"></a><span data-ttu-id="9b959-124">Vzájemná záměna dva řetězce</span><span class="sxs-lookup"><span data-stu-id="9b959-124">Swapping Two Strings</span></span>  
 <span data-ttu-id="9b959-125">Vzájemná záměna řetězce je dobrým příkladem předávání parametrů typu odkazu odkazem.</span><span class="sxs-lookup"><span data-stu-id="9b959-125">Swapping strings is a good example of passing reference-type parameters by reference.</span></span> <span data-ttu-id="9b959-126">V příkladu dva řetězce `str1` a `str2`, jsou inicializovány v `Main` a předána `SwapStrings` jako parametry změnit metodu `ref` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9b959-126">In the example, two strings, `str1` and `str2`, are initialized in `Main` and passed to the `SwapStrings` method as parameters modified by the `ref` keyword.</span></span> <span data-ttu-id="9b959-127">Dva řetězce jsou vzájemně zaměněny uvnitř metoda a uvnitř `Main` také.</span><span class="sxs-lookup"><span data-stu-id="9b959-127">The two strings are swapped inside the method and inside `Main` as well.</span></span>  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 <span data-ttu-id="9b959-128">V tomto příkladu potřebovat parametry k předání odkazem ovlivnit proměnné v volací program.</span><span class="sxs-lookup"><span data-stu-id="9b959-128">In this example, the parameters need to be passed by reference to affect the variables in the calling program.</span></span> <span data-ttu-id="9b959-129">Pokud odeberete `ref` – klíčové slovo z hlavičky metoda a volání metody žádné změny bude probíhat v volací program.</span><span class="sxs-lookup"><span data-stu-id="9b959-129">If you remove the `ref` keyword from both the method header and the method call, no changes will take place in the calling program.</span></span>  
  
 <span data-ttu-id="9b959-130">Další informace o řetězcích najdete v tématu [řetězec](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="9b959-130">For more information about strings, see [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b959-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b959-131">See Also</span></span>  
 [<span data-ttu-id="9b959-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9b959-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9b959-133">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="9b959-133">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="9b959-134">Předávání polí pomocí parametrů ref a out</span><span class="sxs-lookup"><span data-stu-id="9b959-134">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
 [<span data-ttu-id="9b959-135">REF</span><span class="sxs-lookup"><span data-stu-id="9b959-135">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="9b959-136">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="9b959-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)