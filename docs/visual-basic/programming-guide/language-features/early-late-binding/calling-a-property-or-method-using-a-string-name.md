---
title: "Volání vlastnosti nebo metody pomocí názvu řetězce (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5974257fb82fe83c66a480225da200c14338898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="35de8-102">Volání vlastnosti nebo metody pomocí názvu řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35de8-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="35de8-103">Ve většině případů můžete zjistit vlastnosti a metody objektu v době návrhu a napsat kód pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="35de8-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="35de8-104">Ale v některých případech nemusí víte o vlastnosti a metody objektu předem, nebo chcete může jenom možnost povolení koncový uživatel zadat vlastnosti nebo metody provést v době běhu.</span><span class="sxs-lookup"><span data-stu-id="35de8-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="35de8-105">CallByName – funkce</span><span class="sxs-lookup"><span data-stu-id="35de8-105">CallByName Function</span></span>  
 <span data-ttu-id="35de8-106">Zvažte například klientskou aplikaci, která vyhodnotí výrazy zadané uživatelem pomocí předání operátor komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="35de8-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="35de8-107">Předpokládejme, že neustále přidáváte nové funkce pro součásti, které vyžadují nové operátory.</span><span class="sxs-lookup"><span data-stu-id="35de8-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="35de8-108">Při použití standardní objekt přístup techniky, musíte znovu zkompiluje a znovu distribuovat klientskou aplikaci, než by mohl použít novou operátory.</span><span class="sxs-lookup"><span data-stu-id="35de8-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="35de8-109">Chcete-li předejít, můžete použít `CallByName` funkce k předání nových operátorů jako řetězce, aniž byste museli měnit aplikace.</span><span class="sxs-lookup"><span data-stu-id="35de8-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="35de8-110">`CallByName` Funkce vám umožní používat řetězec zadat vlastnosti nebo metody za běhu.</span><span class="sxs-lookup"><span data-stu-id="35de8-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="35de8-111">Podpis pro `CallByName` funkce vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="35de8-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="35de8-112">*Výsledek* = `CallByName`(*objekt*, *ProcedureName*, *Typ_volání*, *argumenty*())</span><span class="sxs-lookup"><span data-stu-id="35de8-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="35de8-113">První argument *objekt*, přebírá název objektu, kterou chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="35de8-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="35de8-114">*ProcedureName* argument přebírá řetězec, který obsahuje název procedury metody nebo vlastnosti, které má být volána.</span><span class="sxs-lookup"><span data-stu-id="35de8-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="35de8-115">*Typ_volání* argument trvá konstanta, která představuje typ postup vyvolání: metody (`Microsoft.VisualBasic.CallType.Method`), číst vlastnosti (`Microsoft.VisualBasic.CallType.Get`), nebo nastavte vlastnost (`Microsoft.VisualBasic.CallType.Set`).</span><span class="sxs-lookup"><span data-stu-id="35de8-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="35de8-116">*Argumenty* argument, který je volitelný a přijímá pole typu `Object` obsahující všechny argumenty k postupu.</span><span class="sxs-lookup"><span data-stu-id="35de8-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="35de8-117">Můžete použít `CallByName` s třídami v aktuálním řešení, ale se nejčastěji používá pro přístup COM – objekty nebo objekty z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="35de8-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="35de8-118">Předpokládejme, že přidáte odkaz na sestavení obsahující třídu s názvem `MathClass`, která obsahuje novou funkci s názvem `SquareRoot`, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="35de8-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 <span data-ttu-id="35de8-119">Vaše aplikace může používat ovládací prvky text k řízení, která metoda bude volána a jeho argumenty.</span><span class="sxs-lookup"><span data-stu-id="35de8-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="35de8-120">Například pokud `TextBox1` obsahuje výraz, který se má vyhodnotit, a `TextBox2` je použít k zadání názvu funkce, můžete použít následující kód k vyvolání `SquareRoot` funkce na výrazu v `TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="35de8-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 <span data-ttu-id="35de8-121">Pokud zadáte "64" v `TextBox1`, "SquareRoot" v `TextBox2`a pak zavolají `CallMath` postup, druhou odmocninu čísla v `TextBox1` vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="35de8-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="35de8-122">Vyvolá kód v ukázce `SquareRoot` funkce (což trvá řetězec, který obsahuje výraz, který má být vyhodnocen jako požadovaný argument) a vrátí "8" `TextBox1` (druhou odmocninu 64).</span><span class="sxs-lookup"><span data-stu-id="35de8-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="35de8-123">Samozřejmě, pokud uživatel zadá neplatný řetězec v `TextBox2`, řetězec obsahuje název vlastnosti místo metodu nebo metodu měli další požadovaný argument, nastane chyba spuštění.</span><span class="sxs-lookup"><span data-stu-id="35de8-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="35de8-124">Budete muset přidat robustní kód pro ošetření chyb při použití `CallByName` odhadnout tyto nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="35de8-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35de8-125">Když `CallByName` funkce můžou být užitečné v některých případech se musí naváží jeho užitečnost proti vliv na výkon – pomocí `CallByName` vyvolat proceduru se nepatrně pomalejší v porovnání pozdní vazbou volání.</span><span class="sxs-lookup"><span data-stu-id="35de8-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="35de8-126">Pokud jsou volání funkce, která je volána opakovaně, například jako uvnitř smyčku, `CallByName` může mít závažné vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="35de8-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35de8-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="35de8-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [<span data-ttu-id="35de8-128">Určení typu objektu</span><span class="sxs-lookup"><span data-stu-id="35de8-128">Determining Object Type</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)