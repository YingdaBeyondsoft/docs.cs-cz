---
title: "&lt;Zkušební fáze&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7dd829fbbfbaa6f26b59e26d5a8b1d2b36593f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="6c7ed-102">&lt;Zkušební fáze&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="6c7ed-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="6c7ed-103">Určuje základní podadresáře aplikace pro modul common language runtime pro vyhledávání při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="6c7ed-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="6c7ed-104">\<configuration></span></span>  
<span data-ttu-id="6c7ed-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="6c7ed-105">\<runtime></span></span>  
<span data-ttu-id="6c7ed-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="6c7ed-106">\<assemblyBinding></span></span>  
<span data-ttu-id="6c7ed-107">\<Zkušební fáze ></span><span class="sxs-lookup"><span data-stu-id="6c7ed-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c7ed-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c7ed-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c7ed-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6c7ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c7ed-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c7ed-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c7ed-111">Attributes</span></span>  
  
|<span data-ttu-id="6c7ed-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c7ed-112">Attribute</span></span>|<span data-ttu-id="6c7ed-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6c7ed-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="6c7ed-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6c7ed-115">Určuje základní adresáře aplikace, který může obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="6c7ed-116">Omezte každý podadresáři středníkem.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c7ed-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6c7ed-117">Child Elements</span></span>  
 <span data-ttu-id="6c7ed-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="6c7ed-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c7ed-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6c7ed-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6c7ed-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c7ed-120">Element</span></span>|<span data-ttu-id="6c7ed-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6c7ed-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="6c7ed-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="6c7ed-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6c7ed-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c7ed-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c7ed-125">Example</span></span>  
 <span data-ttu-id="6c7ed-126">Následující příklad ukazuje, jak zadat základní podadresářích aplikace, které modul runtime program hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c7ed-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c7ed-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c7ed-127">See Also</span></span>  
 [<span data-ttu-id="6c7ed-128">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="6c7ed-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6c7ed-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6c7ed-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6c7ed-130">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="6c7ed-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="6c7ed-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="6c7ed-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)