---
title: "Souběžné spouštění v .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a5092da1526bc266c5cc483cc3cd81d2ac3385
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="side-by-side-execution-in-the-net-framework"></a><span data-ttu-id="0d508-102">Souběžné spouštění v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d508-102">Side-by-Side Execution in the .NET Framework</span></span>
<span data-ttu-id="0d508-103">Souběžné spouštění je možnost spuštění několika verzí aplikace nebo komponenty v jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="0d508-103">Side-by-side execution is the ability to run multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="0d508-104">V jednom počítači lze nainstalovat více verzí modulu CLR (Common Language Runtime) a několik verzí aplikací a komponent, které využívají verzi modulu runtime ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="0d508-104">You can have multiple versions of the common language runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span>  
  
 <span data-ttu-id="0d508-105">Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze modulu runtime v jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="0d508-105">The following illustration shows several applications using two different versions of the runtime on the same computer.</span></span> <span data-ttu-id="0d508-106">Aplikace A, B a C používají modul runtime verze 1.0, zatímco aplikace D používá modul runtime verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="0d508-106">Applications A, B, and C use runtime version 1.0, while application D uses runtime version 1.1.</span></span>  
  
 <span data-ttu-id="0d508-107">![Straně & č. 45; pomocí & č. 45; straně](../../../docs/framework/deployment/media/simplesbs.gif "simplesbs")</span><span class="sxs-lookup"><span data-stu-id="0d508-107">![Side&#45;by&#45;side execution](../../../docs/framework/deployment/media/simplesbs.gif "simplesbs")</span></span>  
<span data-ttu-id="0d508-108">Souběžné spouštění dvou verzí modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0d508-108">Side-by-side execution of two versions of the runtime</span></span>  
  
 <span data-ttu-id="0d508-109">Rozhraní .NET Framework zahrnuje modul CLR (Common Language Runtime) a kolekci sestavení, která obsahují typy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0d508-109">The .NET Framework consists of the common language runtime and a collection of assemblies that contain the API types.</span></span> <span data-ttu-id="0d508-110">Modul runtime a sestavení rozhraní .NET Framework jsou opatřeny samostatnými verzemi.</span><span class="sxs-lookup"><span data-stu-id="0d508-110">The runtime and the .NET Framework assemblies are versioned separately.</span></span> <span data-ttu-id="0d508-111">Například verze 4.0 modulu runtime je ve skutečnosti verzí 4.0.319, zatímco verze 1.0 sestavení rozhraní .NET Framework je verzí 1.0.3300.0.</span><span class="sxs-lookup"><span data-stu-id="0d508-111">For example, version 4.0 of the runtime is actually version 4.0.319, while version 1.0 of the .NET Framework assemblies is version 1.0.3300.0.</span></span>  
  
 <span data-ttu-id="0d508-112">Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze komponenty na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="0d508-112">The following illustration shows several applications using two different versions of a component on the same computer.</span></span> <span data-ttu-id="0d508-113">Aplikace A a B používá verzi komponenty 1.0, zatímco aplikace C používá verzi 2.0 stejné komponenty.</span><span class="sxs-lookup"><span data-stu-id="0d508-113">Application A and B use version 1.0 of the component while Application C uses version 2.0 of the same component.</span></span>  
  
 <span data-ttu-id="0d508-114">![Straně & č. 45; pomocí & č. 45; straně](../../../docs/framework/deployment/media/compsbs.gif "compsbs")</span><span class="sxs-lookup"><span data-stu-id="0d508-114">![Side&#45;by&#45;side execution](../../../docs/framework/deployment/media/compsbs.gif "compsbs")</span></span>  
<span data-ttu-id="0d508-115">Souběžné spouštění dvou verzí komponenty</span><span class="sxs-lookup"><span data-stu-id="0d508-115">Side-by-side execution of two versions of a component</span></span>  
  
 <span data-ttu-id="0d508-116">Souběžné spouštění dává větší kontrolu nad tím, s jakou verzí komponenty je aplikace propojena, a větší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="0d508-116">Side-by-side execution gives you more control over which versions of a component an application binds to, and more control over which version of the runtime an application uses.</span></span>  
  
## <a name="benefits-of-side-by-side-execution"></a><span data-ttu-id="0d508-117">Výhody souběžného spouštění</span><span class="sxs-lookup"><span data-stu-id="0d508-117">Benefits of Side-by-Side Execution</span></span>  
 <span data-ttu-id="0d508-118">Před příchodem systému Windows XP a rozhraní .NET Framework docházelo ke konfliktům knihoven DLL, protože aplikace nebyla schopna rozlišovat mezi nekompatibilními verzemi stejného kódu.</span><span class="sxs-lookup"><span data-stu-id="0d508-118">Prior to Windows XP and the .NET Framework, DLL conflicts occurred because applications were unable to distinguish between incompatible versions of the same code.</span></span> <span data-ttu-id="0d508-119">Informace o typu obsažené v knihovně DLL byly propojeny pouze s názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="0d508-119">Type information contained in a DLL was bound only to a file name.</span></span> <span data-ttu-id="0d508-120">Aplikace neměla žádnou možnost zjistit, zda typy obsažené v knihovně DLL jsou stejné jako ty, pomocí kterých byla aplikace sestavena.</span><span class="sxs-lookup"><span data-stu-id="0d508-120">An application had no way of knowing if the types contained in a DLL were the same types that the application was built with.</span></span> <span data-ttu-id="0d508-121">Ve výsledku mohla nová verze komponenty přepsat starší verzi a aplikace poškodit.</span><span class="sxs-lookup"><span data-stu-id="0d508-121">As a result, a new version of a component could overwrite an older version and break applications.</span></span>  
  
 <span data-ttu-id="0d508-122">Souběžné spouštění a rozhraní .NET Framework poskytují následující funkce, které pomáhají předcházet konfliktům knihoven DLL:</span><span class="sxs-lookup"><span data-stu-id="0d508-122">Side-by-side execution and the .NET Framework provide the following features to eliminate DLL conflicts:</span></span>  
  
-   <span data-ttu-id="0d508-123">Sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0d508-123">Strong-named assemblies.</span></span>  
  
     <span data-ttu-id="0d508-124">Souběžné spouštění používá sestavení se silným názvem k vytvoření vazby informací o typu ke konkrétní verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d508-124">Side-by-side execution uses strong-named assemblies to bind type information to a specific version of an assembly.</span></span> <span data-ttu-id="0d508-125">Díky tomu aplikace nebo součást nevytvoří vazbu k neplatné verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d508-125">This prevents an application or component from binding to an invalid version of an assembly.</span></span> <span data-ttu-id="0d508-126">Sestavení se silným názvem také umožňují, aby na stejném počítači existovalo více verzí souboru a aby je mohly využívat aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-126">Strong-named assemblies also allow multiple versions of a file to exist on the same computer and to be used by applications.</span></span> <span data-ttu-id="0d508-127">Další informace najdete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0d508-127">For more information, see [Strong-Named Assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>  
  
-   <span data-ttu-id="0d508-128">Úložiště kódu podporující verze.</span><span class="sxs-lookup"><span data-stu-id="0d508-128">Version-aware code storage.</span></span>  
  
     <span data-ttu-id="0d508-129">Rozhraní .NET Framework poskytuje úložiště kódu podporující verze v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0d508-129">The .NET Framework provides version-aware code storage in the global assembly cache.</span></span> <span data-ttu-id="0d508-130">Globální mezipaměť sestavení (GAC) je mezipaměť kódu pro celý počítač, která je k dispozici na všech počítačích s nainstalovaným rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d508-130">The global assembly cache is a computer-wide code cache present on all computers with the .NET Framework installed.</span></span> <span data-ttu-id="0d508-131">Jsou v ní uložena sestavení na základě informací o verzi, jazykové verzi a vydavateli a podporuje více verzí komponent a aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d508-131">It stores assemblies based on version, culture, and publisher information, and supports multiple versions of components and applications.</span></span> <span data-ttu-id="0d508-132">Další informace najdete v tématu [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="0d508-132">For more information, see [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
-   <span data-ttu-id="0d508-133">Izolace.</span><span class="sxs-lookup"><span data-stu-id="0d508-133">Isolation.</span></span>  
  
     <span data-ttu-id="0d508-134">Pomocí rozhraní .NET Framework lze vytvořit aplikace a komponenty, které jsou spouštěny v izolaci.</span><span class="sxs-lookup"><span data-stu-id="0d508-134">Using the .NET Framework, you can create applications and components that execute in isolation.</span></span> <span data-ttu-id="0d508-135">Izolace je základní součástí souběžného spouštění.</span><span class="sxs-lookup"><span data-stu-id="0d508-135">Isolation is an essential component of side-by-side execution.</span></span> <span data-ttu-id="0d508-136">Zahrnuje znalost prostředků, které využíváte, a zkušenosti se sdílením prostředků napříč několika verzemi aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="0d508-136">It involves being aware of the resources you are using and sharing resources with confidence among multiple versions of an application or component.</span></span> <span data-ttu-id="0d508-137">Izolace zahrnuje také ukládání souborů na základě verze.</span><span class="sxs-lookup"><span data-stu-id="0d508-137">Isolation also includes storing files in a version-specific way.</span></span> <span data-ttu-id="0d508-138">Další informace o izolaci najdete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="0d508-138">For more information about isolation, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="version-compatibility"></a><span data-ttu-id="0d508-139">Kompatibilita verzí</span><span class="sxs-lookup"><span data-stu-id="0d508-139">Version Compatibility</span></span>  
 <span data-ttu-id="0d508-140">Verze 1.0 a 1.1 rozhraní .NET Framework jsou navrženy tak, aby byly navzájem kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="0d508-140">Versions 1.0 and 1.1 of the .NET Framework are designed to be compatible with one another.</span></span> <span data-ttu-id="0d508-141">Aplikaci sestavenou pomocí verze 1.0 rozhraní .NET Framework lze spustit ve verzi 1.1 a aplikaci sestavenou pomocí verze 1.1 rozhraní .NET Framework lze spustit ve verzi 1.0.</span><span class="sxs-lookup"><span data-stu-id="0d508-141">An application built with the .NET Framework version 1.0 should run on version 1.1, and an application built with the .NET Framework version 1.1 should run on version 1.0.</span></span> <span data-ttu-id="0d508-142">Funkce rozhraní API, které byly přidány ve verzi 1.1 rozhraní .NET Framework, však nebudou fungovat v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="0d508-142">Note, however, that API features added in version 1.1 of the .NET Framework will not work with version 1.0 of the .NET Framework.</span></span> <span data-ttu-id="0d508-143">Aplikace vytvořené pro verzi 2.0 lze spouštět pouze ve verzi 2.0.</span><span class="sxs-lookup"><span data-stu-id="0d508-143">Applications created with version 2.0 will run on version 2.0 only.</span></span> <span data-ttu-id="0d508-144">Aplikace pro verzi 2.0 nelze spustit ve verzi 1.1 nebo starší.</span><span class="sxs-lookup"><span data-stu-id="0d508-144">Version 2.0 applications will not run on version 1.1 or earlier.</span></span>  
  
 <span data-ttu-id="0d508-145">Verze rozhraní .NET Framework jsou považovány za celek, který sestává z modulu runtime a přidružených sestavení rozhraní .NET Framework (koncept se označuje jako sjednocení sestavení).</span><span class="sxs-lookup"><span data-stu-id="0d508-145">Versions of the .NET Framework are treated as a single unit consisting of the runtime and its associated .NET Framework assemblies (a concept referred to as assembly unification).</span></span> <span data-ttu-id="0d508-146">Vazbu sestavení lze přesměrovat tak, aby zahrnovala další verze sestavení rozhraní .NET Framework. Přepsání výchozích vazeb sestavení však může být nebezpečné a je nutné je před nasazením pečlivě otestovat.</span><span class="sxs-lookup"><span data-stu-id="0d508-146">You can redirect assembly binding to include other versions of the .NET Framework assemblies, but overriding the default assembly binding can be risky and must be rigorously tested before deployment.</span></span>  
  
## <a name="locating-runtime-version-information"></a><span data-ttu-id="0d508-147">Vyhledání informací o verzi běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0d508-147">Locating Runtime Version Information</span></span>  
 <span data-ttu-id="0d508-148">Informace, na které runtime verze aplikace nebo součásti bylo kompilováno s a jaké verze modulu runtime aplikace vyžaduje ke spuštění jsou uloženy ve dvou umístěních.</span><span class="sxs-lookup"><span data-stu-id="0d508-148">Information on which runtime version an application or component was compiled with and which versions of the runtime the application requires to run are stored in two locations.</span></span> <span data-ttu-id="0d508-149">Při kompilaci aplikace nebo součásti, informace o verzi modulu runtime používá ke kompilaci je uloženo v spravované spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="0d508-149">When an application or component is compiled, information on the runtime version used to compile it is stored in the managed executable.</span></span> <span data-ttu-id="0d508-150">Informace o požadovaných aplikací nebo součástí modulu runtime verze je uložené v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-150">Information on the runtime versions the application or component requires is stored in the application configuration file.</span></span>  
  
### <a name="runtime-version-information-in-the-managed-executable"></a><span data-ttu-id="0d508-151">Informace o verzi modulu runtime v spravované spustitelný soubor</span><span class="sxs-lookup"><span data-stu-id="0d508-151">Runtime Version Information in the Managed Executable</span></span>  
 <span data-ttu-id="0d508-152">Přenosné záhlaví spustitelného souboru (PE) souboru každé spravované aplikace a součásti obsahuje informace o verzi modulu runtime, který byl sestaven s.</span><span class="sxs-lookup"><span data-stu-id="0d508-152">The portable executable (PE) file header of each managed application and component contains information about the runtime version it was built with.</span></span> <span data-ttu-id="0d508-153">Modul CLR používá tyto informace k určení nejpravděpodobnější verzi modulu runtime, které aplikace potřebuje ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="0d508-153">The common language runtime uses this information to determine the most likely version of the runtime the application needs to run.</span></span>  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a><span data-ttu-id="0d508-154">Informace o verzi modulu runtime v konfiguračním souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="0d508-154">Runtime Version Information in the Application Configuration File</span></span>  
 <span data-ttu-id="0d508-155">Kromě informací v záhlaví souboru PE lze nasadit aplikace s konfigurační soubor aplikace, která poskytuje informace o verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0d508-155">In addition to the information in the PE file header, an application can be deployed with an application configuration file that provides runtime version information.</span></span> <span data-ttu-id="0d508-156">Konfigurační soubor aplikace je soubor na základě XML vytvořený vývojářem aplikace a který je součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-156">The application configuration file is an XML-based file that is created by the application developer and that ships with an application.</span></span> <span data-ttu-id="0d508-157">[ \<RequiredRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) z [ \<spuštění > části](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), pokud je k dispozici v tomto souboru Určuje, jaké verze modulu runtime a jaké verze součást aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="0d508-157">The [\<requiredRuntime> Element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) of the [\<startup> section](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), if it is present in this file, specifies which versions of the runtime and which versions of a component the application supports.</span></span> <span data-ttu-id="0d508-158">Tento soubor testování můžete použít také k testování kompatibility aplikace s různými verzemi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0d508-158">You can also use this file in testing to test an application's compatibility with different versions of the runtime.</span></span>  
  
 <span data-ttu-id="0d508-159">Nespravovaný kód, včetně aplikace modelu COM a modelu COM +, může mít konfigurační soubory aplikace, které používá modul runtime pro interakci se spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="0d508-159">Unmanaged code, including COM and COM+ applications, can have application configuration files that the runtime uses for interacting with managed code.</span></span> <span data-ttu-id="0d508-160">Konfigurační soubor aplikace ovlivňuje spravovaný kód, který je aktivovat pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0d508-160">The application configuration file affects any managed code that you activate through COM.</span></span> <span data-ttu-id="0d508-161">Soubor můžete určit, které podporuje verze modulu runtime, jakož i sestavení přesměruje.</span><span class="sxs-lookup"><span data-stu-id="0d508-161">The file can specify which runtime versions it supports, as well as assembly redirects.</span></span> <span data-ttu-id="0d508-162">Ve výchozím nastavení spravované aplikace spolupráce COM volání do kódu používat nejnovější verzi modulu runtime v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="0d508-162">By default, COM interop applications calling to managed code use the latest version of the runtime installed on the computer.</span></span>  
  
 <span data-ttu-id="0d508-163">Další informace o konfigurační soubory aplikace najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d508-163">For more information about the application configuration files, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a><span data-ttu-id="0d508-164">Určení verze běhového prostředí, která má být načtena</span><span class="sxs-lookup"><span data-stu-id="0d508-164">Determining Which Version of the Runtime to Load</span></span>  
 <span data-ttu-id="0d508-165">Modul common language runtime používá k určení načíst pro aplikaci, kterou verzi modulu runtime následující informace:</span><span class="sxs-lookup"><span data-stu-id="0d508-165">The common language runtime uses the following information to determine which version of the runtime to load for an application:</span></span>  
  
-   <span data-ttu-id="0d508-166">Verze runtime, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0d508-166">The runtime versions that are available.</span></span>  
  
-   <span data-ttu-id="0d508-167">Verze runtime, které podporuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-167">The runtime versions that an application supports.</span></span>  
  
### <a name="supported-runtime-versions"></a><span data-ttu-id="0d508-168">Podporované Runtime verze</span><span class="sxs-lookup"><span data-stu-id="0d508-168">Supported Runtime Versions</span></span>  
 <span data-ttu-id="0d508-169">Modul runtime používá k určení, kterou verzi modulu runtime aplikace podporuje konfigurační soubor aplikace a přenosné hlavičky spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="0d508-169">The runtime uses the application configuration file and the portable executable (PE) file header to determine which version of the runtime an application supports.</span></span> <span data-ttu-id="0d508-170">Pokud se nachází žádný konfigurační soubor aplikace, načte modul runtime runtime verze zadaná v záhlaví souboru PE aplikace, pokud tato verze je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0d508-170">If no application configuration file is present, the runtime loads the runtime version specified in the application's PE file header, if that version is available.</span></span>  
  
 <span data-ttu-id="0d508-171">Pokud se konfigurační soubor aplikace, modul runtime určuje verze odpovídající runtime k načtení podle výsledky následující proces:</span><span class="sxs-lookup"><span data-stu-id="0d508-171">If an application configuration file is present, the runtime determines the appropriate runtime version to load based on the results of the following process:</span></span>  
  
1.  <span data-ttu-id="0d508-172">Modul runtime zkoumá [ \<supportedRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-172">The runtime examines the [\<supportedRuntime> Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element in the application configuration file.</span></span> <span data-ttu-id="0d508-173">Pokud jeden nebo více podporované runtime verze zadané v  **\<supportedRuntime >** element jsou k dispozici, načte modul runtime verze runtime – určení prvním  **\< supportedRuntime >** element.</span><span class="sxs-lookup"><span data-stu-id="0d508-173">If one or more of the supported runtime versions specified in the **\<supportedRuntime>** element are present, the runtime loads the runtime version specified by the first **\<supportedRuntime>** element.</span></span> <span data-ttu-id="0d508-174">Pokud tato verze není k dispozici, modul runtime zkoumá Další  **\<supportedRuntime >** element a pokusí se načíst verze runtime – určení.</span><span class="sxs-lookup"><span data-stu-id="0d508-174">If this version is not available, the runtime examines the next **\<supportedRuntime>** element and attempts to load the runtime version specified.</span></span> <span data-ttu-id="0d508-175">Pokud tato verze modulu runtime není k dispozici, následných  **\<supportedRuntime >** se zkontrolují elementy.</span><span class="sxs-lookup"><span data-stu-id="0d508-175">If this runtime version is not available, subsequent **\<supportedRuntime>** elements are examined.</span></span> <span data-ttu-id="0d508-176">Pokud žádná z podporovaných runtime verzí jsou k dispozici, modul runtime nepodaří načíst verzi modulu runtime a zobrazí zprávu pro uživatele (viz krok 3).</span><span class="sxs-lookup"><span data-stu-id="0d508-176">If none of the supported runtime versions are available, the runtime fails to load a runtime version and displays a message to the user (see step 3).</span></span>  
  
2.  <span data-ttu-id="0d508-177">Modul runtime přečte soubor záhlaví PE spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-177">The runtime reads the PE file header of the application's executable file.</span></span> <span data-ttu-id="0d508-178">Pokud je k dispozici modul runtime verze zadaná v hlavičce souboru PE, načte modul runtime této verze.</span><span class="sxs-lookup"><span data-stu-id="0d508-178">If the runtime version specified by the PE file header is available, the runtime loads that version.</span></span> <span data-ttu-id="0d508-179">Pokud verze runtime – určení není k dispozici, modul runtime prohledá pro verzi modulu runtime aplikací Microsoft za kompatibilní s verzí runtime v záhlaví PE.</span><span class="sxs-lookup"><span data-stu-id="0d508-179">If the runtime version specified is not available, the runtime searches for a runtime version determined by Microsoft to be compatible with the runtime version in the PE header.</span></span> <span data-ttu-id="0d508-180">Pokud není nalezen této verze, proces pokračuje ke kroku 3.</span><span class="sxs-lookup"><span data-stu-id="0d508-180">If that version is not found, the process continues to step 3.</span></span>  
  
3.  <span data-ttu-id="0d508-181">Modul runtime zobrazí zprávu s oznámením, že verze runtime podporováno v aplikaci je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0d508-181">The runtime displays a message stating that the runtime version supported by the application is unavailable.</span></span> <span data-ttu-id="0d508-182">Modul runtime není načtená.</span><span class="sxs-lookup"><span data-stu-id="0d508-182">The runtime is not loaded.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d508-183">Zobrazení této zprávy můžete potlačit pomocí hodnoty NoGuiFromShim v klíči registru HKLM\Software\Microsoft\\. NETFramework nebo pomocí proměnné prostředí COMPLUS_NoGuiFromShim.</span><span class="sxs-lookup"><span data-stu-id="0d508-183">You can suppress the display of this message by using the NoGuiFromShim value under the registry key HKLM\Software\Microsoft\\.NETFramework or using the environment variable COMPLUS_NoGuiFromShim.</span></span> <span data-ttu-id="0d508-184">Můžete například potlačení zprávy s pro aplikace, které nejsou obvykle interakci s uživatelem, jako je bezobslužná instalace nebo služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0d508-184">For example, you can suppress the message for applications that do not typically interact with the user, such as unattended installations or Windows services.</span></span> <span data-ttu-id="0d508-185">Pokud je toto zobrazení zpráv potlačeno, modul runtime zapíše zprávu do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="0d508-185">When this message display is suppressed, the runtime writes a message to the event log.</span></span>  <span data-ttu-id="0d508-186">Nastavte hodnotu registru NoGuiFromShim na 1 pro potlačení této zprávy pro všechny aplikace v počítači.</span><span class="sxs-lookup"><span data-stu-id="0d508-186">Set the registry value NoGuiFromShim to 1 to suppress this message for all applications on a computer.</span></span> <span data-ttu-id="0d508-187">Alternativně nastavte proměnnou prostředí COMPLUS_NoGuiFromShim 1 k potlačení zprávy s pro aplikace spuštěné v kontextu určitého uživatele.</span><span class="sxs-lookup"><span data-stu-id="0d508-187">Alternately, set the COMPLUS_NoGuiFromShim environment variable to 1 to suppress the message for applications running in a particular user context.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d508-188">Po načtení verzi modulu runtime, můžete zadat sestavení – přesměrování vazby načíst jinou verzi jednotlivých sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d508-188">After a runtime version is loaded, assembly binding redirects can specify that a different version of an individual .NET Framework assembly be loaded.</span></span> <span data-ttu-id="0d508-189">Tyto přesměrování vazby vliv pouze konkrétní sestavení, které přesměrována.</span><span class="sxs-lookup"><span data-stu-id="0d508-189">These binding redirects affect only the specific assembly that is redirected.</span></span>  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a><span data-ttu-id="0d508-190">Částečně kvalifikované názvy sestavení a souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="0d508-190">Partially Qualified Assembly Names and Side-by-Side Execution</span></span>  
 <span data-ttu-id="0d508-191">Protože jsou zdroji potenciální problémy vedle sebe, odkazy na sestavení částečně kvalifikovaný slouží pouze k vytvoření vazby sestavení v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d508-191">Because they are a potential source of side-by-side problems, partially qualified assembly references can be used only to bind to assemblies within an application directory.</span></span> <span data-ttu-id="0d508-192">Nepoužívejte odkazy na sestavení částečně kvalifikovaný v kódu.</span><span class="sxs-lookup"><span data-stu-id="0d508-192">Avoid partially qualified assembly references in your code.</span></span>  
  
 <span data-ttu-id="0d508-193">Pro zmírnění odkazy na sestavení částečně kvalifikovaný v kódu, můžete použít [ \<qualifyassembly – >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) element v konfiguračním souboru aplikace k plnému určení částečně kvalifikované odkazy na sestavení, ke kterým došlo v kódu.</span><span class="sxs-lookup"><span data-stu-id="0d508-193">To mitigate partially qualified assembly references in code, you can use the [\<qualifyAssembly>](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) element in an application configuration file to fully qualify partially qualified assembly references that occur in code.</span></span> <span data-ttu-id="0d508-194">Použití  **\<qualifyassembly – >** element zadat pouze pole, které nebyly nastaveny v odkaz na částečné.</span><span class="sxs-lookup"><span data-stu-id="0d508-194">Use the **\<qualifyAssembly>** element to specify only fields that were not set in the partial reference.</span></span> <span data-ttu-id="0d508-195">Uvedené v identity sestavení **fullName** atribut musí obsahovat veškeré informace potřebné k plnému určení název sestavení: název sestavení, veřejný klíč, jazykové verze a verze.</span><span class="sxs-lookup"><span data-stu-id="0d508-195">The assembly identity listed in the **fullName** attribute must contain all the information needed to fully qualify the assembly name: assembly name, public key, culture, and version.</span></span>  
  
 <span data-ttu-id="0d508-196">Následující příklad ukazuje soubor položku konfigurace aplikace k plnému určení sestavení nazvané `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="0d508-196">The following example shows the application configuration file entry to fully qualify an assembly called `myAssembly`.</span></span>  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 <span data-ttu-id="0d508-197">Vždy, když načtení sestavení odkazů příkaz `myAssembly`, tato nastavení konfigurace souboru způsobit modulu runtime automaticky převede částečně kvalifikovaný `myAssembly` odkaz na plně kvalifikovaný odkaz.</span><span class="sxs-lookup"><span data-stu-id="0d508-197">Whenever an assembly load statement references `myAssembly`, these configuration file settings cause the runtime to automatically translate the partially qualified `myAssembly` reference to a fully qualified reference.</span></span> <span data-ttu-id="0d508-198">Například Assembly.Load("myAssembly") bude Assembly.Load ("myAssembly, verze = 1.0.0.0, publicKeyToken =..., culture = neutral").</span><span class="sxs-lookup"><span data-stu-id="0d508-198">For example, Assembly.Load("myAssembly") becomes Assembly.Load("myAssembly, version=1.0.0.0, publicKeyToken=..., culture=neutral").</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d508-199">Můžete použít **loadwithpartialname –** metoda obejít běžné omezení runtime jazyka, které zakazuje částečně odkazovaná sestavení z načítá z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d508-199">You can use the **LoadWithPartialName** method to bypass the common language runtime restriction that prohibits partially referenced assemblies from being loaded from the global assembly cache.</span></span> <span data-ttu-id="0d508-200">Tato metoda by měla použít jenom v situacích, vzdálenou komunikaci, jako je snadno může způsobit problémy při provádění vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="0d508-200">This method should be used only in remoting scenarios as it can easily cause problems in side-by-side execution.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="0d508-201">Související témata</span><span class="sxs-lookup"><span data-stu-id="0d508-201">Related Topics</span></span>  
  
|<span data-ttu-id="0d508-202">Název</span><span class="sxs-lookup"><span data-stu-id="0d508-202">Title</span></span>|<span data-ttu-id="0d508-203">Popis</span><span class="sxs-lookup"><span data-stu-id="0d508-203">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0d508-204">Postupy: povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="0d508-204">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|<span data-ttu-id="0d508-205">Popisuje způsob propojení aplikace s konkrétní verzí sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d508-205">Describes how to bind an application to a specific version of an assembly.</span></span>|  
|[<span data-ttu-id="0d508-206">Konfigurace přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="0d508-206">Configuring Assembly Binding Redirection</span></span>](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|<span data-ttu-id="0d508-207">Objasňuje způsob, jakým lze odkazy vazby přesměrovat na určitou verzi sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d508-207">Explains how to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span>|  
|[<span data-ttu-id="0d508-208">Proces spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="0d508-208">In-Process Side-by-Side Execution</span></span>](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|<span data-ttu-id="0d508-209">Popisuje způsob používání souběžného spouštění aktivace hostitele v jednom procesu, který je určen pro spouštění více verzí modulu CLR (Common Language Runtime) v rámci jednoho procesu.</span><span class="sxs-lookup"><span data-stu-id="0d508-209">Discusses how you can use in-process side-by-side runtime host activation to run multiple versions of the CLR in a single process.</span></span>|  
|[<span data-ttu-id="0d508-210">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="0d508-210">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|<span data-ttu-id="0d508-211">Poskytuje koncepční přehled sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d508-211">Provides a conceptual overview of assemblies.</span></span>|  
|[<span data-ttu-id="0d508-212">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="0d508-212">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)|<span data-ttu-id="0d508-213">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d508-213">Provides a conceptual overview of application domains.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="0d508-214">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0d508-214">Reference</span></span>  
 [<span data-ttu-id="0d508-215">\<supportedRuntime > elementu</span><span class="sxs-lookup"><span data-stu-id="0d508-215">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)