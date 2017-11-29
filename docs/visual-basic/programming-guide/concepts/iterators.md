---
title: "Iterátory (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f02249f7f30d2cd6b43aa75530ace099286c7d7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="7b172-102">Iterátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b172-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="7b172-103">*Iterator* slouží k krok prostřednictvím kolekcí, jako například seznamy a maticových.</span><span class="sxs-lookup"><span data-stu-id="7b172-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="7b172-104">Metodu iterator nebo `get` přistupujícího objektu provede vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="7b172-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="7b172-105">Používá metodu iterator [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý element, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="7b172-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="7b172-106">Když `Yield` příkaz je dosaženo, uloží je aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="7b172-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="7b172-107">Provádění restartování z tohoto umístění při příštím iterator funkce je volána.</span><span class="sxs-lookup"><span data-stu-id="7b172-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="7b172-108">Využívat iterovat z klientského kódu pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) prohlášení, nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="7b172-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="7b172-109">V následujícím příkladu, první iterace `For Each` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` iterator – metoda dokud první `Yield` je dosaženo příkaz.</span><span class="sxs-lookup"><span data-stu-id="7b172-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="7b172-110">Tato iterace vrací hodnotu 3 a aktuální umístění v metodě iterator zůstane.</span><span class="sxs-lookup"><span data-stu-id="7b172-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="7b172-111">Na další iteraci smyčky, pokračuje spuštění v metodě iterator odkud bylo přerušeno, znovu zastavit při dosažení `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7b172-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="7b172-112">Tento iterace vrací hodnotu 5 a opakujte aktuální umístění v metodě iterator zůstane.</span><span class="sxs-lookup"><span data-stu-id="7b172-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="7b172-113">Když je dosaženo konce iterator metody dokončení smyčky.</span><span class="sxs-lookup"><span data-stu-id="7b172-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 <span data-ttu-id="7b172-114">Návratový typ metody iterator nebo `get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="7b172-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="7b172-115">Můžete použít `Exit Function` nebo `Return` příkaz k ukončení iterace.</span><span class="sxs-lookup"><span data-stu-id="7b172-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="7b172-116">Iterator funkci jazyka Visual Basic nebo `get` zahrnuje deklaraci přistupujícího objektu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7b172-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="7b172-117">Iterátory byly zavedeny v jazyce Visual Basic v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="7b172-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="7b172-118">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="7b172-118">**In this topic**</span></span>  
  
-   [<span data-ttu-id="7b172-119">Jednoduché iterátorů</span><span class="sxs-lookup"><span data-stu-id="7b172-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="7b172-120">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="7b172-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="7b172-121">Try – bloky</span><span class="sxs-lookup"><span data-stu-id="7b172-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
-   [<span data-ttu-id="7b172-122">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="7b172-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
-   [<span data-ttu-id="7b172-123">Pomocí seznamu obecné iterátory</span><span class="sxs-lookup"><span data-stu-id="7b172-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="7b172-124">Informace ze syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b172-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="7b172-125">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="7b172-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="7b172-126">Použití iterátory</span><span class="sxs-lookup"><span data-stu-id="7b172-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="7b172-127">Všechny příklady v tomto tématu, s výjimkou Iterator jednoduchý příklad, zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro příkazy `System.Collections` a `System.Collections.Generic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7b172-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <span data-ttu-id="7b172-128"><a name="BKMK_SimpleIterator"></a>Jednoduché iterátorů</span><span class="sxs-lookup"><span data-stu-id="7b172-128"><a name="BKMK_SimpleIterator"></a> Simple Iterator</span></span>  
 <span data-ttu-id="7b172-129">V následujícím příkladu má jeden `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="7b172-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="7b172-130">V `Main`, každé iteraci `For Each` těla příkazu vytvoří volání funkce iterator, který bude pokračovat na další `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7b172-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <span data-ttu-id="7b172-131"><a name="BKMK_CollectionClass"></a>Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="7b172-131"><a name="BKMK_CollectionClass"></a> Creating a Collection Class</span></span>  
 <span data-ttu-id="7b172-132">V následujícím příkladu `DaysOfTheWeek` třída implementuje <xref:System.Collections.IEnumerable> rozhraní, což vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7b172-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="7b172-133">Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="7b172-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="7b172-134">`GetEnumerator` Metoda vrátí každý řetězec jeden současně pomocí `Yield` příkaz a `Iterator` se modifikátor v deklaraci funkce.</span><span class="sxs-lookup"><span data-stu-id="7b172-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 <span data-ttu-id="7b172-135">Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.</span><span class="sxs-lookup"><span data-stu-id="7b172-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="7b172-136">`For Each` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metoda.</span><span class="sxs-lookup"><span data-stu-id="7b172-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="7b172-137">`For Each` Příkazy, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem iterator – metoda.</span><span class="sxs-lookup"><span data-stu-id="7b172-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <span data-ttu-id="7b172-138"><a name="BKMK_TryBlocks"></a>Try – bloky</span><span class="sxs-lookup"><span data-stu-id="7b172-138"><a name="BKMK_TryBlocks"></a> Try Blocks</span></span>  
 <span data-ttu-id="7b172-139">Umožňuje jazyka Visual Basic `Yield` příkaz v `Try` blokovat z [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b172-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="7b172-140">A `Try` blok, který má `Yield` příkaz může mít `Catch` blokuje a může mít `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b172-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="7b172-141">Následující příklad obsahuje `Try`, `Catch`, a `Finally` blokuje v iterator funkci.</span><span class="sxs-lookup"><span data-stu-id="7b172-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="7b172-142">`Finally` Bloku ve funkci iterator provede před `For Each` iterace dokončení.</span><span class="sxs-lookup"><span data-stu-id="7b172-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 <span data-ttu-id="7b172-143">A `Yield` příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b172-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="7b172-144">Pokud `For Each` textu (místo metody iterator) vyvolá výjimku, `Catch` bloku ve funkci iterator není proveden, ale `Finally` bloku ve funkci iterator se spustí.</span><span class="sxs-lookup"><span data-stu-id="7b172-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="7b172-145">A `Catch` bloku uvnitř funkce iterator zachytí pouze výjimky, které nastat uvnitř funkce iterator.</span><span class="sxs-lookup"><span data-stu-id="7b172-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
##  <span data-ttu-id="7b172-146"><a name="BKMK_AnonymousMethods"></a>Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="7b172-146"><a name="BKMK_AnonymousMethods"></a> Anonymous Methods</span></span>  
 <span data-ttu-id="7b172-147">V jazyce Visual Basic může být anonymní funkce iterator funkce.</span><span class="sxs-lookup"><span data-stu-id="7b172-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="7b172-148">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7b172-148">The following example illustrates this.</span></span>  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 <span data-ttu-id="7b172-149">V následujícím příkladu má jiný iterator metodu, která ověří argumenty.</span><span class="sxs-lookup"><span data-stu-id="7b172-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="7b172-150">Metoda vrací výsledek anonymní iterator, který popisuje elementy z kolekce.</span><span class="sxs-lookup"><span data-stu-id="7b172-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 <span data-ttu-id="7b172-151">Pokud se ověření místo uvnitř funkce iterator, ověření nelze provést, dokud nebude spuštění první iterace `For Each` textu.</span><span class="sxs-lookup"><span data-stu-id="7b172-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
##  <span data-ttu-id="7b172-152"><a name="BKMK_GenericList"></a>Pomocí seznamu obecné iterátory</span><span class="sxs-lookup"><span data-stu-id="7b172-152"><a name="BKMK_GenericList"></a> Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="7b172-153">V následujícím příkladu `Stack(Of T)` – obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b172-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="7b172-154">`Push` Metoda přiřadí hodnoty do pole typu `T`.</span><span class="sxs-lookup"><span data-stu-id="7b172-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="7b172-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot pomocí `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7b172-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="7b172-156">Kromě obecná <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, neobecnou <xref:System.Collections.IEnumerable.GetEnumerator%2A> také musí být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="7b172-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="7b172-157">Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="7b172-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="7b172-158">Implementace neobecnou odkládat údaje pro obecnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="7b172-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="7b172-159">Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory.</span><span class="sxs-lookup"><span data-stu-id="7b172-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="7b172-160">Jsou to s názvem iterátory `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.</span><span class="sxs-lookup"><span data-stu-id="7b172-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="7b172-161">`BottomToTop` Zahrnuje deklarace vlastnosti `Iterator` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7b172-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
```  
  
##  <span data-ttu-id="7b172-162"><a name="BKMK_SyntaxInformation"></a>Informace ze syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b172-162"><a name="BKMK_SyntaxInformation"></a> Syntax Information</span></span>  
 <span data-ttu-id="7b172-163">Může dojít iterator jako metodu nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="7b172-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="7b172-164">Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.</span><span class="sxs-lookup"><span data-stu-id="7b172-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="7b172-165">Musí existovat implicitní převod z typu výrazu v `Yield` příkaz, který má návratový typ iteraci.</span><span class="sxs-lookup"><span data-stu-id="7b172-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="7b172-166">V jazyce Visual Basic, nemůže obsahovat metodu iterator ani `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="7b172-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="7b172-167">V jazyce Visual Basic "Výnos" není vyhrazené slovo a má zvláštní význam jenom v případě, že je používán `Iterator` metoda nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="7b172-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
##  <span data-ttu-id="7b172-168"><a name="BKMK_Technical"></a>Technická implementace</span><span class="sxs-lookup"><span data-stu-id="7b172-168"><a name="BKMK_Technical"></a> Technical Implementation</span></span>  
 <span data-ttu-id="7b172-169">I když napíšete iterovat jako metodu, kompilátor převede jej do vnořené třídy ve výsledku, který je stav počítače.</span><span class="sxs-lookup"><span data-stu-id="7b172-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="7b172-170">Tato třída uchovává informace o umístění iterator jako dlouho `For Each...Next` pokračuje smyčky v kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="7b172-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="7b172-171">Pokud chcete zobrazit, jaké kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který se vygeneruje pro metodu iterator.</span><span class="sxs-lookup"><span data-stu-id="7b172-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="7b172-172">Při vytváření iterace pro [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), není nutné implementovat celek <xref:System.Collections.IEnumerator> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b172-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="7b172-173">Zjistí-li kompilátor iteraci, automaticky vygeneruje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b172-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="7b172-174">Při každém opakování následných `For Each…Next` smyčky (nebo přímé volání `IEnumerator.MoveNext`), těle další kód iterator obnoví po předchozí `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7b172-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="7b172-175">Bude pokračovat na další `Yield` prohlášení, dokud je dosaženo konce iterator text, nebo dokud se `Exit Function` nebo `Return` příkaz je zjistil.</span><span class="sxs-lookup"><span data-stu-id="7b172-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="7b172-176">Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="7b172-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7b172-177">Chcete-li procházení znovu od začátku, je nutné získat nové iterator.</span><span class="sxs-lookup"><span data-stu-id="7b172-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="7b172-178">Další informace najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7b172-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
##  <span data-ttu-id="7b172-179"><a name="BKMK_UseOfIterators"></a>Použití iterátory</span><span class="sxs-lookup"><span data-stu-id="7b172-179"><a name="BKMK_UseOfIterators"></a> Use of Iterators</span></span>  
 <span data-ttu-id="7b172-180">Iterátory umožňují zachovat jednoduchost `For Each` cykly, když potřebujete použít složitý kód pro naplnění seznamu pořadí.</span><span class="sxs-lookup"><span data-stu-id="7b172-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="7b172-181">To může být užitečné, pokud chcete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="7b172-181">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="7b172-182">Změňte pořadí seznamu po první `For Each` cykly iterací.</span><span class="sxs-lookup"><span data-stu-id="7b172-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
-   <span data-ttu-id="7b172-183">Vyhněte se plně načítání velkých seznamu před první iterace `For Each` smyčky.</span><span class="sxs-lookup"><span data-stu-id="7b172-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="7b172-184">Příkladem je stránkové fetch načíst dávku řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="7b172-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="7b172-185">Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b172-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="7b172-186">Zapouzdření vytváření seznamu v iteraci.</span><span class="sxs-lookup"><span data-stu-id="7b172-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="7b172-187">V metodě iterator můžete sestavit v seznamu a pak yield každý výsledek ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="7b172-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b172-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b172-188">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="7b172-189">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="7b172-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="7b172-190">YIELD – příkaz</span><span class="sxs-lookup"><span data-stu-id="7b172-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [<span data-ttu-id="7b172-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="7b172-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)