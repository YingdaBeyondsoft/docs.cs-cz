---
title: "Přístup k atributům pomocí reflexe (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 162bdd6b968def391a2f3413596ee8c2a8b01cc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="7de35-102">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="7de35-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="7de35-103">Nízké hodnoty bez nějakým způsobem načtení těchto informací a funguje na něm může být skutečnost, že můžete definovat vlastní atributy a umístěte je do vašeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="7de35-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="7de35-104">Pomocí reflexe můžete načíst informace, které je definovaný s vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="7de35-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="7de35-105">Metoda klíče je `GetCustomAttributes`, která vrací pole objektů, které jsou ekvivalenty běhu atributů zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="7de35-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="7de35-106">Tato metoda má několik přetížené verzí.</span><span class="sxs-lookup"><span data-stu-id="7de35-106">This method has several overloaded versions.</span></span> <span data-ttu-id="7de35-107">Další informace naleznete v tématu <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="7de35-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="7de35-108">Specifikace atributu jako:</span><span class="sxs-lookup"><span data-stu-id="7de35-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="7de35-109">je ekvivalentní k tomuto:</span><span class="sxs-lookup"><span data-stu-id="7de35-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="7de35-110">Však není kód spustí, dokud `SampleClass` je dotazován na atributy.</span><span class="sxs-lookup"><span data-stu-id="7de35-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="7de35-111">Volání metody `GetCustomAttributes` na `SampleClass` způsobí, že `Author` objekt, který má být vytvořená a inicializovat jako výše.</span><span class="sxs-lookup"><span data-stu-id="7de35-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="7de35-112">Pokud třída má další atributy, se vytvářejí podobně jako jiné objekty atribut.</span><span class="sxs-lookup"><span data-stu-id="7de35-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="7de35-113">`GetCustomAttributes`Vrátí `Author` objekt a všechny další objekty atribut v matici.</span><span class="sxs-lookup"><span data-stu-id="7de35-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="7de35-114">Pak můžete Iterujte přes toto pole, určit atributy, které byly použity na základě typu jednotlivých prvků pole a extrahovat informace z atributů objektů.</span><span class="sxs-lookup"><span data-stu-id="7de35-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de35-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7de35-115">Example</span></span>  
 <span data-ttu-id="7de35-116">Zde je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="7de35-116">Here is a complete example.</span></span> <span data-ttu-id="7de35-117">Vlastní atribut je definován, použít pro několik entit a načteny prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="7de35-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="7de35-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7de35-118">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="7de35-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="7de35-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7de35-120">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="7de35-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="7de35-121">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="7de35-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="7de35-122">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="7de35-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="7de35-123">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="7de35-123">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)