---
title: "Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b4d53f16f046839d56bc1dc37f7b2d8816c5956f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="70f61-102">Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="70f61-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="70f61-103">V jazyce C# metoda v odvozené třídě, může mít stejný název jako metodu v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="70f61-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="70f61-104">Můžete určit, jak používat metody pomocí [nové](../../../csharp/language-reference/keywords/new.md) a [přepsat](../../../csharp/language-reference/keywords/override.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="70f61-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="70f61-105">`override` Modifikátor *rozšiřuje* metodu základní třídy a `new` modifikátor *skryje* ho.</span><span class="sxs-lookup"><span data-stu-id="70f61-105">The `override` modifier *extends* the base class method, and the `new` modifier *hides* it.</span></span> <span data-ttu-id="70f61-106">Rozdíl je předvedené v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="70f61-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="70f61-107">V konzolové aplikaci, deklarovat následující dvě třídy `BaseClass` a `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="70f61-108">`DerivedClass`dědí z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 <span data-ttu-id="70f61-109">V `Main` metody deklarujte proměnné `bc`, `dc`, a `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="70f61-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
-   <span data-ttu-id="70f61-110">`bc`je typu `BaseClass`, a jeho hodnota je typu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
-   <span data-ttu-id="70f61-111">`dc`je typu `DerivedClass`, a jeho hodnota je typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
-   <span data-ttu-id="70f61-112">`bcdc`je typu `BaseClass`, a jeho hodnota je typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="70f61-113">Jedná se o proměnnou věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="70f61-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="70f61-114">Protože `bc` a `bcdc` mít typ `BaseClass`, pouze přímo přístupem `Method1`, pokud nechcete použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="70f61-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="70f61-115">Proměnné `dc` k dispozici obě `Method1` a `Method2`.</span><span class="sxs-lookup"><span data-stu-id="70f61-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="70f61-116">Tyto relace jsou uvedené v následující kód.</span><span class="sxs-lookup"><span data-stu-id="70f61-116">These relationships are shown in the following code.</span></span>  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 <span data-ttu-id="70f61-117">V dalším kroku přidejte následující `Method2` metodu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="70f61-118">Tato metoda podpis neodpovídá podpisu `Method2` metoda v `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="70f61-119">Protože `BaseClass` má teď `Method2` metoda, druhé volání příkazu lze přidat pro `BaseClass` proměnné `bc` a `bcdc`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="70f61-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="70f61-120">Při sestavování projektu zobrazí přidání `Method2` metoda v `BaseClass` způsobí, že upozornění.</span><span class="sxs-lookup"><span data-stu-id="70f61-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="70f61-121">Upozornění, která `Method2` metoda v `DerivedClass` skryje `Method2` metoda v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="70f61-122">Doporučujeme používat `new` – klíčové slovo v `Method2` definice, pokud máte v úmyslu způsobit, že výsledek.</span><span class="sxs-lookup"><span data-stu-id="70f61-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="70f61-123">Alternativně může přejmenujte jeden z `Method2` metody k vyřešení upozornění, ale není vždy reálné.</span><span class="sxs-lookup"><span data-stu-id="70f61-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="70f61-124">Před přidáním `new`, spusťte program, který chcete zobrazit výstup vyprodukované další volání příkazy.</span><span class="sxs-lookup"><span data-stu-id="70f61-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="70f61-125">Zobrazí se následující výsledky.</span><span class="sxs-lookup"><span data-stu-id="70f61-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="70f61-126">`new` – Klíčové slovo uchovává vztahy, které vytvářejí tento výstup, ale jeho potlačí upozornění.</span><span class="sxs-lookup"><span data-stu-id="70f61-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="70f61-127">Proměnné, které mají typ `BaseClass` nadále přístup ke členům v `BaseClass`a proměnné, která má typ `DerivedClass` nadále přístup ke členům v `DerivedClass` první a pak zvažte členy zděděno z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="70f61-128">Chcete-li potlačit upozornění, přidejte `new` modifikátor definici `Method2` v `DerivedClass`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="70f61-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="70f61-129">Modifikátor lze přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="70f61-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="70f61-130">Spusťte program znovu k ověření, že se nezměnil výstup.</span><span class="sxs-lookup"><span data-stu-id="70f61-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="70f61-131">Také ověřte, že už se zobrazí upozornění.</span><span class="sxs-lookup"><span data-stu-id="70f61-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="70f61-132">Pomocí `new`, uplatňujete, že jste si vědomi, že člena, který upravuje skryje člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="70f61-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="70f61-133">Další informace o skrývání název prostřednictvím dědičnosti najdete v tématu [new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="70f61-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="70f61-134">K kontrastu tohoto chování důsledky použití `override`, přidejte následující metodu do `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="70f61-135">`override` Modifikátor lze přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="70f61-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="70f61-136">Přidat `virtual` modifikátor definici `Method1` v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="70f61-137">`virtual` Modifikátor lze přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="70f61-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="70f61-138">Spusťte projekt znovu.</span><span class="sxs-lookup"><span data-stu-id="70f61-138">Run the project again.</span></span> <span data-ttu-id="70f61-139">Všimněte si, zejména poslední dva řádky následující výstup.</span><span class="sxs-lookup"><span data-stu-id="70f61-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="70f61-140">Použití `override` modifikátor umožňuje `bcdc` pro přístup k `Method1` metoda, která je definována v `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="70f61-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="70f61-141">Obvykle, který je toto chování žádoucí v hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="70f61-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="70f61-142">Chcete objekty, které mají hodnoty, které jsou vytvořené z odvozené třídy používat metody, které jsou definovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="70f61-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="70f61-143">Dosažení tohoto chování pomocí `override` rozšířit metoda základní třídy.</span><span class="sxs-lookup"><span data-stu-id="70f61-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="70f61-144">Následující kód obsahuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="70f61-144">The following code contains the full example.</span></span>  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="70f61-145">Následující příklad ukazuje podobné chování v jiném kontextu.</span><span class="sxs-lookup"><span data-stu-id="70f61-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="70f61-146">V příkladu definuje tří tříd: základní třídu s názvem `Car` a dvě třídy, které jsou odvozeny od, `ConvertibleCar` a `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="70f61-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="70f61-147">Obsahuje základní třídy `DescribeCar` metoda.</span><span class="sxs-lookup"><span data-stu-id="70f61-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="70f61-148">Metoda zobrazí základní popis automobilu a pak zavolá `ShowDetails` můžete poskytnout dodatečné informace.</span><span class="sxs-lookup"><span data-stu-id="70f61-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="70f61-149">Všechny tři třídy definuje `ShowDetails` metoda.</span><span class="sxs-lookup"><span data-stu-id="70f61-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="70f61-150">`new` Modifikátor se používá k definování `ShowDetails` v `ConvertibleCar` třídy.</span><span class="sxs-lookup"><span data-stu-id="70f61-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="70f61-151">`override` Modifikátor se používá k definování `ShowDetails` v `Minivan` třídy.</span><span class="sxs-lookup"><span data-stu-id="70f61-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 <span data-ttu-id="70f61-152">V příkladu testuje, kterou verzi `ShowDetails` je volána.</span><span class="sxs-lookup"><span data-stu-id="70f61-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="70f61-153">Následující metoda `TestCars1`, deklaruje instancí každé třídy a pak zavolá `DescribeCar` na každou instanci.</span><span class="sxs-lookup"><span data-stu-id="70f61-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 <span data-ttu-id="70f61-154">`TestCars1`vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="70f61-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="70f61-155">Všimněte si, zejména výsledky pro `car2`, které jsou pravděpodobně není co očekává.</span><span class="sxs-lookup"><span data-stu-id="70f61-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="70f61-156">Typ objektu je `ConvertibleCar`, ale `DescribeCar` nepřistoupí verzi `ShowDetails` která je definovaná v `ConvertibleCar` třídy vzhledem k tomu, že metoda je deklarovaný s `new` modifikátor, není `override` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="70f61-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="70f61-157">V důsledku toho `ConvertibleCar` objekt zobrazí popis stejné jako `Car` objektu.</span><span class="sxs-lookup"><span data-stu-id="70f61-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="70f61-158">Porovnejte výsledky pro `car3`, který je `Minivan` objektu.</span><span class="sxs-lookup"><span data-stu-id="70f61-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="70f61-159">V takovém případě `ShowDetails` metoda, která je definována v `Minivan` třídy přepsání `ShowDetails` metoda, která je definována v `Car` třídy a popis, který se zobrazí popisuje minivan.</span><span class="sxs-lookup"><span data-stu-id="70f61-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="70f61-160">`TestCars2`Vytvoří seznam objektů, které mají typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="70f61-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="70f61-161">Instance hodnoty objekty z `Car`, `ConvertibleCar`, a `Minivan` třídy.</span><span class="sxs-lookup"><span data-stu-id="70f61-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="70f61-162">`DescribeCar`je volána pro každý element seznamu.</span><span class="sxs-lookup"><span data-stu-id="70f61-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="70f61-163">Následující kód ukazuje definici `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="70f61-163">The following code shows the definition of `TestCars2`.</span></span>  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 <span data-ttu-id="70f61-164">Zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="70f61-164">The following output is displayed.</span></span> <span data-ttu-id="70f61-165">Všimněte si, že je stejný jako výstup, který se zobrazí při `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="70f61-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="70f61-166">`ShowDetails` Metodu `ConvertibleCar` třída není volána bez ohledu na to, jestli je typ objektu `ConvertibleCar`jako v `TestCars1`, nebo `Car`jako v `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="70f61-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="70f61-167">Naopak `car3` volání `ShowDetails` metoda z `Minivan` třídy v obou případech, zda má typ `Minivan` nebo typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="70f61-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="70f61-168">Metody `TestCars3` a `TestCars4` dokončit v příkladu.</span><span class="sxs-lookup"><span data-stu-id="70f61-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="70f61-169">Tyto metody volání `ShowDetails` přímo, nejprve z objektů deklarovaný tak, aby měl typ `ConvertibleCar` a `Minivan` (`TestCars3`), pak z objektů deklarovaný tak, aby měl typ `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="70f61-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="70f61-170">Následující kód definuje tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="70f61-170">The following code defines these two methods.</span></span>  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 <span data-ttu-id="70f61-171">Metody vytvořit následující výstup, který odpovídá výsledky z prvního příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="70f61-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 <span data-ttu-id="70f61-172">Následující kód ukazuje dokončený projekt a její výstup.</span><span class="sxs-lookup"><span data-stu-id="70f61-172">The following code shows the complete project and its output.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="70f61-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="70f61-173">See Also</span></span>  
 [<span data-ttu-id="70f61-174">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="70f61-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="70f61-175">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="70f61-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="70f61-176">Správa verzí pomocí nové klíčových slov Override a</span><span class="sxs-lookup"><span data-stu-id="70f61-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="70f61-177">základní</span><span class="sxs-lookup"><span data-stu-id="70f61-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="70f61-178">abstraktní</span><span class="sxs-lookup"><span data-stu-id="70f61-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)