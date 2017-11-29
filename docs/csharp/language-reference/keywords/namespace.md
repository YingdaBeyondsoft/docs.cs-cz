---
title: "namespace (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a><span data-ttu-id="468da-102">namespace (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="468da-102">namespace (C# Reference)</span></span>
<span data-ttu-id="468da-103">`namespace` – Klíčové slovo se používá k deklaraci obor, který obsahuje sadu související objekty.</span><span class="sxs-lookup"><span data-stu-id="468da-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="468da-104">Obor názvů můžete použít k uspořádání elementy kódu a vytvoření typů globálně jedinečný.</span><span class="sxs-lookup"><span data-stu-id="468da-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="468da-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="468da-105">Remarks</span></span>  
 <span data-ttu-id="468da-106">V oboru názvů můžou deklarovat minimálně jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="468da-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="468da-107">jiný obor názvů</span><span class="sxs-lookup"><span data-stu-id="468da-107">another namespace</span></span>  
  
-   [<span data-ttu-id="468da-108">– Třída</span><span class="sxs-lookup"><span data-stu-id="468da-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="468da-109">rozhraní</span><span class="sxs-lookup"><span data-stu-id="468da-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="468da-110">Struktura</span><span class="sxs-lookup"><span data-stu-id="468da-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="468da-111">výčet</span><span class="sxs-lookup"><span data-stu-id="468da-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="468da-112">Delegát</span><span class="sxs-lookup"><span data-stu-id="468da-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="468da-113">Zda je explicitně deklarovat obor názvů ve zdrojovém souboru C#, kompilátor přidá výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="468da-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="468da-114">Tento nepojmenované obor názvů, označovaných také jako globální obor názvů, je v každý soubor.</span><span class="sxs-lookup"><span data-stu-id="468da-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="468da-115">Všechny identifikátor v globálním oboru názvů je k dispozici pro použití v s názvem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="468da-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="468da-116">Obory názvů implicitně mít veřejný přístup a nejedná se upravitelnými.</span><span class="sxs-lookup"><span data-stu-id="468da-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="468da-117">Informace o modifikátory přístupu můžete přiřadit k prvkům v oboru názvů, najdete v části [modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="468da-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="468da-118">Je možné definovat ve dvou nebo více deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="468da-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="468da-119">Například v následujícím příkladu definuje dvě třídy jako součást `MyCompany` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="468da-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="468da-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="468da-120">Example</span></span>  
 <span data-ttu-id="468da-121">Následující příklad ukazuje, jak volat statickou metodu v vnořené oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="468da-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="468da-122">Další informace</span><span class="sxs-lookup"><span data-stu-id="468da-122">For More Information</span></span>  
 <span data-ttu-id="468da-123">Další informace o použití oboru názvů najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="468da-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="468da-124">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="468da-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="468da-125">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="468da-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="468da-126">Postupy: použití aliasu globálního Namespace</span><span class="sxs-lookup"><span data-stu-id="468da-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="468da-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="468da-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="468da-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="468da-128">See Also</span></span>  
 [<span data-ttu-id="468da-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="468da-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="468da-130">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="468da-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="468da-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="468da-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="468da-132">Namespace klíčová slova</span><span class="sxs-lookup"><span data-stu-id="468da-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="468da-133">pomocí</span><span class="sxs-lookup"><span data-stu-id="468da-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)