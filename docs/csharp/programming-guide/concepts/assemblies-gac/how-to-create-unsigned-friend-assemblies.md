---
title: "Postupy: vytváření nepodepsaných přátelských sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 854df39394ef10bf2404fb3f762586fb102fba7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a><span data-ttu-id="b3e34-102">Postupy: vytváření nepodepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="b3e34-102">How to: Create Unsigned Friend Assemblies (C#)</span></span>
<span data-ttu-id="b3e34-103">Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které jsou bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="b3e34-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="b3e34-104">Chcete-li vytvořit sestavení a přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="b3e34-104">To create an assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="b3e34-105">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="b3e34-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b3e34-106">Vytvoření souboru C# s názvem `friend_signed_A.` obsahující následující kód.</span><span class="sxs-lookup"><span data-stu-id="b3e34-106">Create a C# file named `friend_signed_A.` that contains the following code.</span></span> <span data-ttu-id="b3e34-107">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3e34-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
    ```csharp  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="b3e34-108">Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="b3e34-108">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  <span data-ttu-id="b3e34-109">Vytvoření souboru C# s názvem `friend_unsigned_B` obsahující následující kód.</span><span class="sxs-lookup"><span data-stu-id="b3e34-109">Create a C# file named `friend_unsigned_B` that contains the following code.</span></span> <span data-ttu-id="b3e34-110">Protože friend_unsigned_A určuje friend_unsigned_B jako přátelského sestavení, můžete přístup k kód v friend_unsigned_B `internal` typy a členy z friend_unsigned_A.</span><span class="sxs-lookup"><span data-stu-id="b3e34-110">Because friend_unsigned_A specifies friend_unsigned_B as a friend assembly, the code in friend_unsigned_B can access `internal` types and members from friend_unsigned_A.</span></span>  
  
    ```csharp  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="b3e34-111">Zkompilujte friend_signed_B pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="b3e34-111">Compile friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     <span data-ttu-id="b3e34-112">Název sestavení, který je generovaný kompilátoru shodovat friend název sestavení, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="b3e34-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="b3e34-113">Musíte explicitně zadat název výstupu sestavení (.exe nebo .dll) pomocí `/out` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b3e34-113">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span> <span data-ttu-id="b3e34-114">Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b3e34-114">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
6.  <span data-ttu-id="b3e34-115">Spusťte soubor friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="b3e34-115">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="b3e34-116">Program vytiskne dva řetězce: "Class1.Test" a "Class2.Test".</span><span class="sxs-lookup"><span data-stu-id="b3e34-116">The program prints two strings: "Class1.Test" and "Class2.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b3e34-117">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3e34-117">.NET Framework Security</span></span>  
 <span data-ttu-id="b3e34-118">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="b3e34-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="b3e34-119">Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `internal` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="b3e34-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e34-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3e34-120">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="b3e34-121">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="b3e34-121">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="b3e34-122">Přátelská sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="b3e34-122">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="b3e34-123">Postupy: vytváření podepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="b3e34-123">How to: Create Signed Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="b3e34-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b3e34-124">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)