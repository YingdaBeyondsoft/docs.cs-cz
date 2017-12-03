---
title: "Sestavení se silným názvem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4165d968ff347dd9af3bff755be22484debc23c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strong-named-assemblies"></a><span data-ttu-id="d1097-102">Sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="d1097-102">Strong-Named Assemblies</span></span>
<span data-ttu-id="d1097-103">Silné názvy sestavení vytvoří jedinečnou identitu pro sestavení a může zabránit konfliktům sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1097-103">Strong-naming an assembly creates a unique identity for the assembly, and can prevent assembly conflicts.</span></span>  
  
## <a name="what-makes-a-strong-named-assembly"></a><span data-ttu-id="d1097-104">Díky sestavení se silným názvem?</span><span class="sxs-lookup"><span data-stu-id="d1097-104">What makes a strong-named assembly?</span></span>  
 <span data-ttu-id="d1097-105">Silně pojmenované sestavení je generována pomocí privátního klíče, který odpovídá veřejnému klíči distribuované s sestavení a sestavení sám sebe.</span><span class="sxs-lookup"><span data-stu-id="d1097-105">A strong named assembly is generated by using the private key that corresponds to the public key distributed with the assembly, and the assembly itself.</span></span> <span data-ttu-id="d1097-106">Sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1097-106">The assembly includes the assembly manifest, which contains the names and hashes of all the files that make up the assembly.</span></span> <span data-ttu-id="d1097-107">Sestavení, které mají stejný název silné musí být identické.</span><span class="sxs-lookup"><span data-stu-id="d1097-107">Assemblies that have the same strong name should be identical.</span></span>  
  
 <span data-ttu-id="d1097-108">Sestavení se silným názvem můžete pomocí sady Visual Studio nebo nástroj příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d1097-108">You can strong-name assemblies by using Visual Studio or a command-line tool.</span></span> <span data-ttu-id="d1097-109">Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) nebo [Sn.exe (nástroj silným názvem)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d1097-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) or [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
 <span data-ttu-id="d1097-110">Při vytváření sestavení se silným názvem, obsahuje jednoduchý textový název sestavení, číslo verze, informace o jazykové verzi volitelné, digitální podpis a veřejný klíč, který odpovídá privátní klíč použít pro podepisování.</span><span class="sxs-lookup"><span data-stu-id="d1097-110">When a strong-named assembly is created, it contains the simple text name of the assembly, the version number, optional culture information, a digital signature, and the public key that corresponds to the private key used for signing.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d1097-111">Nespoléhejte na silné názvy pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d1097-111">Do not rely on strong names for security.</span></span> <span data-ttu-id="d1097-112">Obsahují jenom jedinečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="d1097-112">They provide a unique identity only.</span></span>  
  
## <a name="why-strong-name-your-assemblies"></a><span data-ttu-id="d1097-113">Proč se silným názvem vaší sestavení?</span><span class="sxs-lookup"><span data-stu-id="d1097-113">Why strong-name your assemblies?</span></span>  
 <span data-ttu-id="d1097-114">Když odkazujete na sestavení se silným názvem, můžete očekávat určité výhody, jako je například Správa verzí a pojmenování ochrany.</span><span class="sxs-lookup"><span data-stu-id="d1097-114">When you reference a strong-named assembly, you can expect certain benefits, such as versioning and naming protection.</span></span> <span data-ttu-id="d1097-115">Sestavení se silným názvem lze nainstalovat do globální mezipaměti sestavení, které je potřeba povolit některé scénáře.</span><span class="sxs-lookup"><span data-stu-id="d1097-115">Strong-named assemblies can be installed in the Global Assembly Cache, which is required to enable some scenarios.</span></span>  
  
 <span data-ttu-id="d1097-116">Sestavení se silným názvem jsou užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="d1097-116">Strong-named assemblies are useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="d1097-117">Chcete povolit vaše sestavení, které může být odkazuje sestavení se silným názvem, nebo chcete poskytnout `friend` přístup k vaší sestavení od ostatních sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="d1097-117">You want to enable your assemblies to be referenced by strong-named assemblies, or you want to give `friend` access to your assemblies from other strong-named assemblies.</span></span>  
  
-   <span data-ttu-id="d1097-118">Aplikace potřebuje přístup pro různé verze stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1097-118">An app needs access to different versions of the same assembly.</span></span> <span data-ttu-id="d1097-119">To znamená, že potřebujete různé verze sestavení načíst vedle sebe ve stejné doméně aplikace bez konfliktů.</span><span class="sxs-lookup"><span data-stu-id="d1097-119">This means  you need different versions of an assembly to load side by side in the same app domain without conflict.</span></span> <span data-ttu-id="d1097-120">Například pokud je v sestavení, které mají stejný jednoduchý název různých rozšíření rozhraní API, silné názvy poskytuje jedinečnou identitu pro každou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1097-120">For example, if different extensions of an API exist in assemblies that have the same simple name, strong-naming provides a unique identity for each version of the assembly.</span></span>  
  
-   <span data-ttu-id="d1097-121">Nechcete negativně ovlivnit výkon aplikace sestavení, takže chcete sestavení do domény neutrální.</span><span class="sxs-lookup"><span data-stu-id="d1097-121">You do not want to negatively affect performance of apps using your assembly, so you want the assembly to be domain neutral.</span></span> <span data-ttu-id="d1097-122">To vyžaduje silné názvy protože domény jazykově neutrální sestavení v globální mezipaměti sestavení musí být nainstalován.</span><span class="sxs-lookup"><span data-stu-id="d1097-122">This requires strong-naming because a domain-neutral assembly must be installed in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="d1097-123">Pokud chcete centralizovat údržby pro vaši aplikaci s použitím zásad vydavatele, což znamená, že sestavení v globální mezipaměti sestavení musí nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="d1097-123">When you want to centralize servicing for your app by applying publisher policy, which means the assembly must be installed in the  global assembly cache.</span></span>  
  
 <span data-ttu-id="d1097-124">Pokud jste vývojář open source a chcete využít výhod identity sestavení se silným názvem, zvažte kontrolu v privátní klíč přidružený k sestavení do systému správy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="d1097-124">If you are an open-source developer and you want the identity benefits of a strong-named assembly, consider checking in the private key associated with an assembly into your source control system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1097-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1097-125">See Also</span></span>  
 [<span data-ttu-id="d1097-126">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="d1097-126">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="d1097-127">Postupy: podepsání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="d1097-127">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="d1097-128">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="d1097-128">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="d1097-129">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="d1097-129">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)