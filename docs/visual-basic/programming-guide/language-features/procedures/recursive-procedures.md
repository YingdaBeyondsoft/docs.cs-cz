---
title: "Rekurzivní procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 444eeaf043cf3710c5154fd7e8577590e3ce7d1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="a1d05-102">Rekurzivní procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1d05-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="a1d05-103">A *rekurzivní* postup je ten, který volá sám sebe.</span><span class="sxs-lookup"><span data-stu-id="a1d05-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="a1d05-104">Obecně toto není jedním z nejúčinnějších způsobů zápis [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="a1d05-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
 <span data-ttu-id="a1d05-105">Následující postup používá rekurze vypočítat faktoriál jeho původní argumentem.</span><span class="sxs-lookup"><span data-stu-id="a1d05-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="a1d05-106">Informace o rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="a1d05-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="a1d05-107">**Omezení podmínky**.</span><span class="sxs-lookup"><span data-stu-id="a1d05-107">**Limiting Conditions**.</span></span> <span data-ttu-id="a1d05-108">Je třeba navrhnout rekurzivní postup testování pro alespoň jednu podmínku, která může obsluhovat rekurze a také musí zpracovávat tento případ, kde je splněna žádná taková podmínka během přiměřené počtu volání rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="a1d05-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="a1d05-109">Bez nejméně jedné podmínky, které nelze splnit bez selže spustí procedura vysoce rizikové provedení v nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="a1d05-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="a1d05-110">**Využití paměti**.</span><span class="sxs-lookup"><span data-stu-id="a1d05-110">**Memory Usage**.</span></span> <span data-ttu-id="a1d05-111">Aplikace má omezené množství místa pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="a1d05-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="a1d05-112">Pokaždé, když proceduru volá samostatně, používá více toto místo pro další kopie jeho místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="a1d05-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="a1d05-113">Pokud tento proces pokračuje bez omezení, se může způsobit, že <xref:System.StackOverflowException> chyby.</span><span class="sxs-lookup"><span data-stu-id="a1d05-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="a1d05-114">**Efektivita**.</span><span class="sxs-lookup"><span data-stu-id="a1d05-114">**Efficiency**.</span></span> <span data-ttu-id="a1d05-115">Můžete nahradit téměř vždy smyčku pro rekurze.</span><span class="sxs-lookup"><span data-stu-id="a1d05-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="a1d05-116">Smyčka nemá režii předávání argumentů, inicializace další úložiště a vrácení hodnot.</span><span class="sxs-lookup"><span data-stu-id="a1d05-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="a1d05-117">Výkon může být mnohem lepší bez rekurzivní volání.</span><span class="sxs-lookup"><span data-stu-id="a1d05-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="a1d05-118">**Vzájemná rekurze**.</span><span class="sxs-lookup"><span data-stu-id="a1d05-118">**Mutual Recursion**.</span></span> <span data-ttu-id="a1d05-119">Si můžete všimnout velmi nízký výkon nebo i nekonečnou smyčku, pokud dva postupy volání sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="a1d05-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="a1d05-120">Takový návrh přináší stejné problémy jako jeden rekurzivní postup, ale může být těžší ke zjišťování a ladění.</span><span class="sxs-lookup"><span data-stu-id="a1d05-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="a1d05-121">**Volání metody s závorkách**.</span><span class="sxs-lookup"><span data-stu-id="a1d05-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="a1d05-122">Když `Function` postup volá rekurzivně sama sebe, je třeba provést název procedury v závorkách, i když neprobíhá žádná seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="a1d05-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="a1d05-123">Jinak název funkce je převzat jako představující vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="a1d05-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="a1d05-124">**Testování**.</span><span class="sxs-lookup"><span data-stu-id="a1d05-124">**Testing**.</span></span> <span data-ttu-id="a1d05-125">Pokud píšete rekurzivní procedury, měli byste otestovat se velmi pečlivě a ujistěte se, že splňuje vždy nějaká omezení podmínka.</span><span class="sxs-lookup"><span data-stu-id="a1d05-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="a1d05-126">Také se ujistěte, že nelze spustit nedostatek paměti z důvodu s příliš mnoha volání rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="a1d05-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d05-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1d05-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="a1d05-128">Postupy</span><span class="sxs-lookup"><span data-stu-id="a1d05-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="a1d05-129">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="a1d05-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="a1d05-130">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="a1d05-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="a1d05-131">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="a1d05-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="a1d05-132">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a1d05-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="a1d05-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="a1d05-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="a1d05-134">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="a1d05-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="a1d05-135">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="a1d05-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="a1d05-136">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="a1d05-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="a1d05-137">Řešení potíží s výjimkami: System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="a1d05-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)