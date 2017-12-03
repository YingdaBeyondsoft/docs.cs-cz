---
title: "Postupy: Vložení hodnoty do vlastnosti (Visual Basic)"
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
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44e7c4a92ea3d087c12e74aa2ede33a52c8730cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="c9a7f-102">Postupy: Vložení hodnoty do vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9a7f-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="c9a7f-103">Hodnota uložená v vlastnost umístěním název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="c9a7f-104">Vlastnosti `Set` postup ukládá hodnotu, ale můžete explicitně ho nevolají podle názvu.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="c9a7f-105">Stejně, jako by použijete proměnnou, použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c9a7f-106">Díky volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="c9a7f-107">K uložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9a7f-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="c9a7f-108">Na levé straně příkazu přiřazení pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="c9a7f-109">Nastaví hodnotu v následujícím příkladu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` vlastnost poledne, implicitně volání jeho `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-109">The following example sets the value of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="c9a7f-110">Pokud vlastnost přijímá argumenty, postupujte podle názvu vlastnosti v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="c9a7f-111">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="c9a7f-112">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="c9a7f-113">Ujistěte se, že zadáte argumenty ve stejném pořadí, vlastnost definuje odpovídajících parametrů.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="c9a7f-114">Hodnota generovaná na pravé straně přiřazení příkazu je uložené v určité vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c9a7f-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a7f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9a7f-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="c9a7f-116">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="c9a7f-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="c9a7f-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="c9a7f-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c9a7f-118">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="c9a7f-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="c9a7f-119">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9a7f-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="c9a7f-120">Postupy: vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9a7f-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="c9a7f-121">Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="c9a7f-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="c9a7f-122">Postupy: volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9a7f-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="c9a7f-123">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9a7f-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="c9a7f-124">Postupy: získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9a7f-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)