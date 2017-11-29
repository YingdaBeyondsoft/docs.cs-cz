---
title: "Postupy: Získání hodnoty z vlastnosti (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="55cec-102">Postupy: Získání hodnoty z vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55cec-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="55cec-103">Můžete načíst vlastnosti na hodnotu tak, že včetně názvu vlastnosti ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="55cec-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="55cec-104">Vlastnosti `Get` postup načte hodnotu, ale můžete explicitně ho nevolají podle názvu.</span><span class="sxs-lookup"><span data-stu-id="55cec-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="55cec-105">Stejně, jako by použijete proměnnou, použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="55cec-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="55cec-106">Díky volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55cec-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="55cec-107">K načtení hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="55cec-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="55cec-108">Pomocí názvu vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné.</span><span class="sxs-lookup"><span data-stu-id="55cec-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="55cec-109">Můžete použít vlastnost kdekoli můžete proměnné nebo konstantní.</span><span class="sxs-lookup"><span data-stu-id="55cec-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="55cec-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="55cec-110">-or-</span></span>  
  
     <span data-ttu-id="55cec-111">Použít následující rovná název vlastnosti (`=`) přihlásit příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="55cec-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="55cec-112">Následující příklad načte hodnotu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` vlastnost implicitně volání jeho `Get` postupu.</span><span class="sxs-lookup"><span data-stu-id="55cec-112">The following example reads the value of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  <span data-ttu-id="55cec-113">Pokud vlastnost přijímá argumenty, postupujte podle názvu vlastnosti v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="55cec-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="55cec-114">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="55cec-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="55cec-115">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="55cec-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="55cec-116">Ujistěte se, že zadáte argumenty ve stejném pořadí, vlastnost definuje odpovídajících parametrů.</span><span class="sxs-lookup"><span data-stu-id="55cec-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="55cec-117">Hodnota vlastnosti, na které se účastní výraz stejně jako proměnné Konstanta by nebo je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="55cec-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cec-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="55cec-118">See Also</span></span>  
 [<span data-ttu-id="55cec-119">Postupy</span><span class="sxs-lookup"><span data-stu-id="55cec-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="55cec-120">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="55cec-120">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="55cec-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="55cec-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="55cec-122">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="55cec-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="55cec-123">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55cec-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="55cec-124">Postupy: vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="55cec-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="55cec-125">Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="55cec-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="55cec-126">Postupy: volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="55cec-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="55cec-127">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55cec-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="55cec-128">Postupy: vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="55cec-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)