---
title: "Postupy: Načtení sestavení do domény aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90e1d16b47e1f603ac7faaa582388ec682591850
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="d8d22-102">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d8d22-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="d8d22-103">Existuje několik způsobů načtení sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8d22-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="d8d22-104">Doporučeným způsobem je použití `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.Load%2A> metodu <xref:System.Reflection.Assembly?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="d8d22-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d8d22-105">Další způsoby, které lze načíst sestavení patří:</span><span class="sxs-lookup"><span data-stu-id="d8d22-105">Other ways assemblies can be loaded include:</span></span>  
  
-   <span data-ttu-id="d8d22-106"><xref:System.Reflection.Assembly.LoadFrom%2A> Metodu <xref:System.Reflection.Assembly> třída načte sestavení zadané jeho umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="d8d22-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="d8d22-107">Načtení sestavení se tato metoda používá jiný zatížení kontextu.</span><span class="sxs-lookup"><span data-stu-id="d8d22-107">Loading assemblies with this method uses a different load context.</span></span>  
  
-   <span data-ttu-id="d8d22-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody načtení sestavení do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="d8d22-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="d8d22-109">Sestavení načtená do tohoto kontextu můžete zkontrolovat, ale nebyl proveden, povolení zkoumání sestavení, která cílí na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="d8d22-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="d8d22-110">V tématu [postupy: načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="d8d22-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8d22-111">Kontext pouze pro reflexi je v rozhraní .NET Framework verze 2.0 nová.</span><span class="sxs-lookup"><span data-stu-id="d8d22-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
-   <span data-ttu-id="d8d22-112">Metody, jako <xref:System.AppDomain.CreateInstance%2A> a <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> z <xref:System.AppDomain> třídy lze načíst sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8d22-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
-   <span data-ttu-id="d8d22-113"><xref:System.Type.GetType%2A> Metodu <xref:System.Type> třída může načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8d22-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
-   <span data-ttu-id="d8d22-114"><xref:System.AppDomain.Load%2A> Metodu <xref:System.AppDomain?displayProperty=nameWithType> třída může načíst sestavení, ale používá se především pro interoperabilita modelů COM.</span><span class="sxs-lookup"><span data-stu-id="d8d22-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="d8d22-115">Není vhodné používat k načtení sestavení do domény aplikace než doménu aplikace, ze kterého se označuje jako.</span><span class="sxs-lookup"><span data-stu-id="d8d22-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8d22-116">Od verze rozhraní .NET Framework verze 2.0, modul runtime nenačte sestavení, které bylo kompilováno s verzi rozhraní .NET Framework, který má vyšší číslo verze než aktuálně načtených modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d8d22-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="d8d22-117">To platí pro soubor součástí hlavní a vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="d8d22-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="d8d22-118">Můžete zadat způsob, jakým v běhu (JIT) zkompilovaný kód z načíst sestavení jsou sdílena mezi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="d8d22-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="d8d22-119">Další informace najdete v tématu [doménám a sestavením aplikací](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346).</span><span class="sxs-lookup"><span data-stu-id="d8d22-119">For more information, see [Application Domains and Assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8d22-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8d22-120">Example</span></span>  
 <span data-ttu-id="d8d22-121">Následující kód načte sestavení s názvem "example.exe" nebo "example.dll" do aktuální domény aplikace získá typ s názvem `Example` od sestavení, získá metodu bez parametrů s názvem `MethodA` pro tohoto typu a provede metodu.</span><span class="sxs-lookup"><span data-stu-id="d8d22-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="d8d22-122">Úplné informace o získání informací z načíst sestavení, najdete v části [dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="d8d22-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d8d22-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8d22-123">See Also</span></span>  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [<span data-ttu-id="d8d22-124">Programování s doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="d8d22-124">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="d8d22-125">Reflexe</span><span class="sxs-lookup"><span data-stu-id="d8d22-125">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="d8d22-126">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="d8d22-126">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 [<span data-ttu-id="d8d22-127">Postupy: načtení sestavení do kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="d8d22-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [<span data-ttu-id="d8d22-128">Aplikační domény a sestavení</span><span class="sxs-lookup"><span data-stu-id="d8d22-128">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)