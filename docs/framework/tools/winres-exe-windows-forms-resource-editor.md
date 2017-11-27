---
title: "Winres.exe (editor prostředků Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8009f832434d6bbad2ad7bee9cbfd62c81d623c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="winresexe-windows-forms-resource-editor"></a><span data-ttu-id="d0359-102">Winres.exe (editor prostředků Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d0359-102">Winres.exe (Windows Forms Resource Editor)</span></span>
<span data-ttu-id="d0359-103">Windows Forms Resource Editor (Winres.exe) je nástroj pro tvorbu vizuálního rozložení, který pomáhá odborníkům přes lokalizaci lokalizovat prostředky uživatelského rozhraní (UI) nástroje Windows Forms používané formuláři.</span><span class="sxs-lookup"><span data-stu-id="d0359-103">The Windows Forms Resource Editor, Winres.exe, is a visual layout tool that helps localization experts localize Windows Forms user interface (UI) resources used by forms.</span></span> <span data-ttu-id="d0359-104">Soubor prostředků .resx nebo .resources sloužící jako vstup do nástroje Winres.exe lze vytvořit pomocí prostředí pro vizuální návrh, jako je například sada Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0359-104">The .resx or .resources files that are used as input to Winres.exe can be created using a visual design environment such as Microsoft Visual Studio.</span></span> <span data-ttu-id="d0359-105">Informace o nasazení prostředků v aplikacích rozhraní .NET Framework, najdete v části [prostředků v aplikacích plochy](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0359-105">For information on deploying resources in .NET Framework applications, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="d0359-106">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0359-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="d0359-107">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="d0359-107">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="d0359-108">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d0359-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="d0359-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="d0359-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0359-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0359-110">Syntax</span></span>  
  
```  
winres resourceFile   
winres /?   
```  
  
## <a name="remarks"></a><span data-ttu-id="d0359-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0359-111">Remarks</span></span>  
  
|<span data-ttu-id="d0359-112">Argument</span><span class="sxs-lookup"><span data-stu-id="d0359-112">Argument</span></span>|<span data-ttu-id="d0359-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d0359-113">Description</span></span>|  
|--------------|-----------------|  
|`resourceFile`|<span data-ttu-id="d0359-114">Soubor prostředků k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="d0359-114">The resource file to localize.</span></span> <span data-ttu-id="d0359-115">Tento soubor musí být formulář Windows Forms s příponou .resx nebo .resources vygenerovaný pomocí návrháře sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0359-115">This file must be a Windows Forms form .resx or .resources file generated by the Visual Studio designer.</span></span> <span data-ttu-id="d0359-116">Nástroj Winres.exe nedokáže otevřít obecné soubory .resx nebo .resources.</span><span class="sxs-lookup"><span data-stu-id="d0359-116">Winres.exe cannot open generic .resx or .resources files.</span></span>|  
  
|<span data-ttu-id="d0359-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="d0359-117">Option</span></span>|<span data-ttu-id="d0359-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d0359-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d0359-119">**/?**</span><span class="sxs-lookup"><span data-stu-id="d0359-119">**/?**</span></span>|<span data-ttu-id="d0359-120">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="d0359-120">Displays command syntax and options for the tool.</span></span>|  
  
 <span data-ttu-id="d0359-121">Stavy prvků UI z formuláře v projektu Windows Forms jsou obvykle uloženy v souborech prostředků s příponou .resx založených na XML nebo v souborech odpovídajících zkompilovaných binárních verzí s příponou .resources.</span><span class="sxs-lookup"><span data-stu-id="d0359-121">The state of UI elements from a form in a Windows Forms project are typically stored in resource files, which are either XML-based files with the extension .resx or the corresponding compiled, binary versions with the extension .resources.</span></span> <span data-ttu-id="d0359-122">Winres.exe je nástroj umožňující omezené úpravy obou typů souborů mimo návrhové prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0359-122">Winres.exe is a tool that enables limited editing of either type of file outside of the Visual Studio design environment.</span></span> <span data-ttu-id="d0359-123">Konkrétně umožňuje následující typy operací úprav:</span><span class="sxs-lookup"><span data-stu-id="d0359-123">Specifically, it allows the following types of editing operations:</span></span>  
  
-   <span data-ttu-id="d0359-124">Chcete-li změnit vlastnosti uživatelského rozhraní (UI) formuláře, můžete upravit soubor prostředků neutrální nebo konkrétní jazykové verze nebo jeho ovládací prvky jako například text, velikost či umístění.</span><span class="sxs-lookup"><span data-stu-id="d0359-124">A neutral or specific culture resource file can be edited to change the UI properties of the form or its controls, such as their text, size, or position.</span></span>  
  
-   <span data-ttu-id="d0359-125">Soubory prostředků neutrální nebo konkrétní jazykové verze mohou být generovány z výchozího souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="d0359-125">Neutral or specific culture resource files can be generated from the default resource file.</span></span>  
  
-   <span data-ttu-id="d0359-126">Soubor prostředků jazykové verze lze uložit jako soubor prostředků jiné jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="d0359-126">A culture resource file can be saved as another culture resource file.</span></span> <span data-ttu-id="d0359-127">Například soubor prostředků pro angličtinu (USA) může být uložen jako soubor prostředků pro polštinu.</span><span class="sxs-lookup"><span data-stu-id="d0359-127">For example, an English (U.S.) resource file could be saved as a Polish resource file.</span></span> <span data-ttu-id="d0359-128">Nový soubor bude obvykle upraven tak, aby byl kompatibilní s novou jazykovou verzí.</span><span class="sxs-lookup"><span data-stu-id="d0359-128">Typically the new file would subsequently be edited to be compatible with the new culture.</span></span>  
  
 <span data-ttu-id="d0359-129">Viz také [hierarchická organizace zdrojů pro lokalizaci](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\)) nebo [hierarchická organizace zdrojů pro lokalizaci](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\)).</span><span class="sxs-lookup"><span data-stu-id="d0359-129">Also see [Hierarchical Organization of Resources for Localization](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\)) or [Hierarchical Organization of Resources for Localization](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\)).</span></span>  
  
 <span data-ttu-id="d0359-130">Nástroj Winres.exe nemůže převést soubor .resx na dopovídající soubor .resources; použijte místo něj nástroj Resgen.exe.</span><span class="sxs-lookup"><span data-stu-id="d0359-130">Winres.exe cannot convert a .resx file into its corresponding .resources file; use the Resgen.exe tool instead.</span></span> <span data-ttu-id="d0359-131">Další informace o Resgen.exe najdete v tématu [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="d0359-131">For more information about Resgen.exe, see [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).</span></span>  
  
 <span data-ttu-id="d0359-132">Nástroj Winres.exe je grafická aplikace, která obnoví verzi návrhu formuláře Windows Forms pouze ze souboru prostředků, aniž by měla přístup ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="d0359-132">Winres.exe is a graphical application that recreates a design-time version of a Windows Forms form from just the resource file, without having access to the source code.</span></span> <span data-ttu-id="d0359-133">Nástroj Winres.exe obsahuje nástroj Windows Forms Form Designer ze sady Visual Studio a okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d0359-133">Winres.exe hosts Visual Studio's Windows Forms Form Designer and Properties window.</span></span> <span data-ttu-id="d0359-134">Tyto funkce umožňují provádět vizuální úpravy souboru .resources nebo .resx obsahujícího formulář Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d0359-134">These features enable visual editing of a .resources or .resx file containing a Windows Forms form.</span></span> <span data-ttu-id="d0359-135">Lokalizátoři obvykle používají nástroj Winres.exe k úpravě popisků ovládacích prvků a nastavení umístění a velikosti ovládacích prvků tak, aby vyhovovaly velikosti popisků cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="d0359-135">Typically localizers use Winres.exe to edit control labels and adjust the location and size of controls to accommodate the labels for the target culture.</span></span>  
  
 <span data-ttu-id="d0359-136">Pokud nástroj Winres.exe nedokáže rozlišit verzi ovládacího prvku, vytvoří v lokalizovaném souboru .resx nebo .resources zástupný text ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0359-136">If Winres.exe cannot resolve the type of a control, it creates a placeholder control in the localized .resx or .resources file.</span></span> <span data-ttu-id="d0359-137">Zástupný text ovládacího prvku se zobrazí ve formuláři Windows Forms jako šrafované okno.</span><span class="sxs-lookup"><span data-stu-id="d0359-137">The placeholder control appears on the Windows Forms form as a hatched window.</span></span> <span data-ttu-id="d0359-138">Velikost a umístění šrafovaného okna odpovídá skutečnému ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="d0359-138">The size and position of the hatched window matches that of the actual control.</span></span> <span data-ttu-id="d0359-139">Všechny dostupné lokalizovatelné vlastnosti zástupného textu ovládacího prvku se zobrazí v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d0359-139">All the available localizable properties for the placeholder control appear in the Properties window.</span></span> <span data-ttu-id="d0359-140">Veškeré změny provedené v zástupném textu ovládacího prvku se uloží pro skutečný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d0359-140">Any changes that you make to the placeholder control are saved for the actual control.</span></span>  
  
## <a name="winresexe-versus-visual-studio"></a><span data-ttu-id="d0359-141">Srovnání nástroje Winres.exe a sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0359-141">Winres.exe versus Visual Studio</span></span>  
 <span data-ttu-id="d0359-142">Obecně platí, že dříve než začnete lokalizovat formuláře Windows Forms pro určitou aplikaci, měli byste se rozhodnout, zda chcete k lokalizaci použít sadu Visual Studio, nebo nástroj Winres.exe.</span><span class="sxs-lookup"><span data-stu-id="d0359-142">In general, before you begin to localize an application's Windows Forms forms, you should decide whether you want to use Visual Studio or Winres.exe as the localization tool.</span></span> <span data-ttu-id="d0359-143">Kompatibilita verzí, jak je popsáno dále, může bránit přepínání z jednoho nástroje na druhý.</span><span class="sxs-lookup"><span data-stu-id="d0359-143">Version compatibility, as described later, may prevent you from switching from one tool to the other.</span></span>  
  
 <span data-ttu-id="d0359-144">Výhodou sady Visual Studio je, že ji můžete použít k vývoji i lokalizaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="d0359-144">The advantage of Visual Studio is that you can use it to both develop and localize an application.</span></span> <span data-ttu-id="d0359-145">O lokalizaci formuláře, po dokončení vývoj, nastavte jeho <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** vlastnost v editoru vlastnosti) k `true` a změňte jeho **jazyk** vlastnost, která má požadované cílové jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="d0359-145">To localize a form, after development is complete, set the form's <xref:System.ComponentModel.LocalizableAttribute> (the **Localizable** property in the Properties Editor) to `true` and change its **Language** property to the desired target culture.</span></span> <span data-ttu-id="d0359-146">Poté změňte řetězce a upravte umístění a velikost ovládacích prvků tak, aby vyhovovaly řetězcům cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="d0359-146">Then, edit strings and adjust the location and size of controls to accommodate the strings for the target culture.</span></span> <span data-ttu-id="d0359-147">Při ukládání lokalizovaného souboru .resx sada Visual Studio do souboru zapíše pouze lokalizovatelné vlastnosti (vlastnosti, které se v cílové jazykové verzi změnily).</span><span class="sxs-lookup"><span data-stu-id="d0359-147">When you save the localized .resx file, Visual Studio writes only the localizable properties (properties that changed in the target culture) to the file.</span></span> <span data-ttu-id="d0359-148">Sada Visual Studio automaticky vytvoří satelitní sestavení pro lokalizovaný soubor .resx ve správném adresáři.</span><span class="sxs-lookup"><span data-stu-id="d0359-148">Visual Studio automatically creates a satellite assembly for the localized .resx file in the correct directory location.</span></span>  <span data-ttu-id="d0359-149">Viz také [návod: lokalizace Windows Forms](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d0359-149">Also see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="d0359-150">Přestože sada Visual Studio poskytuje integrované vývojové a lokalizační prostředí, v případě, že lokalizaci budou provádět externí překladatelé, doporučujeme použít nástroj Winres.exe.</span><span class="sxs-lookup"><span data-stu-id="d0359-150">Although Visual Studio provides an integrated development and localization environment, Winres.exe is the recommended tool to use if localization will be done by third-party localizers.</span></span> <span data-ttu-id="d0359-151">Protože Winres.exe je pouze lokalizační nástroj, umožňuje jasnější oddělení kódu aplikace od formulářů určených k lokalizaci, což je při řízení velkých projektů praktičtější.</span><span class="sxs-lookup"><span data-stu-id="d0359-151">Because Winres.exe is a localization tool only, it allows for a cleaner separation of an application's code from the forms to be localized, which is more practical for managing large projects.</span></span>  
  
## <a name="using-winresexe"></a><span data-ttu-id="d0359-152">Používání nástroje Winres.exe</span><span class="sxs-lookup"><span data-stu-id="d0359-152">Using Winres.exe</span></span>  
 <span data-ttu-id="d0359-153">Abyste mohli provádět lokalizaci pomocí nástroje Winres.exe, je třeba nejprve vytvořit aplikaci pomocí návrháře, jako je například nástroj Návrhář v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0359-153">To localize using Winres.exe, you must first develop an application using a visual designer like the Forms Designer in Visual Studio.</span></span> <span data-ttu-id="d0359-154">Po dokončení vývoj nastavit formuláře <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** vlastnost v editoru vlastnosti) k `true`a pak předá soubor .resx pro výchozí jazykovou verzi na lokalizátora třetích stran.</span><span class="sxs-lookup"><span data-stu-id="d0359-154">When development is complete, set the form's <xref:System.ComponentModel.LocalizableAttribute> (the **Localizable** property in the Properties Editor) to `true`, and then hand off the .resx file for the default culture to a third-party localizer.</span></span> <span data-ttu-id="d0359-155">Tento soubor .resx obsahuje další informace, které nástroj Winres.exe použije k obnovení verze návrhu původního formuláře.</span><span class="sxs-lookup"><span data-stu-id="d0359-155">This .resx file contains extra information that Winres.exe uses to recreate a design-time version of the original form.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d0359-156">Nástroj Winres.exe nelze použít k úpravě výchozího souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="d0359-156">Winres.exe cannot be used to edit the default resource file.</span></span> <span data-ttu-id="d0359-157">Nástroj Winres.exe interpretuje všechny změněné vlastnosti jako lokalizované vlastnosti a ukládá je do souboru prostředků cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="d0359-157">Winres.exe interprets all changed properties as localized properties and saves them to the target culture resource file.</span></span>  
  
 <span data-ttu-id="d0359-158">Konečné verze souborů prostředků jazykové verze lze nakonec použít k vytvoření lokalizovaných verzí aplikace.</span><span class="sxs-lookup"><span data-stu-id="d0359-158">The final versions of the culture resource files can finally be used to create localized versions of the application.</span></span> <span data-ttu-id="d0359-159">Další informace najdete v tématu [prostředků v aplikacích plochy](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0359-159">For more information, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="d0359-160">Nástroj Winres.exe verze 2.0 obsahuje následující funkce a možnosti:</span><span class="sxs-lookup"><span data-stu-id="d0359-160">Version 2.0 of Winres.exe has the following features and capabilities:</span></span>  
  
-   <span data-ttu-id="d0359-161">Nástroj Winres může pracovat v režimu Single File Mode (SFM) nebo v režimu Visual Studio File Mode (VSFM).</span><span class="sxs-lookup"><span data-stu-id="d0359-161">Winres can operate in Single File Mode (SFM) or Visual Studio File Mode (VSFM).</span></span> <span data-ttu-id="d0359-162">SFM je starší režim, ve kterém jsou úplné informace o formuláři a jeho obsahu uloženy do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="d0359-162">SFM is the legacy mode where complete information about the form and its contents is stored to the resource file.</span></span> <span data-ttu-id="d0359-163">Režim VSFM ukládá pouze změny jazykové verze v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="d0359-163">VSFM only stores only the cultural changes in the resource file.</span></span>  
  
-   <span data-ttu-id="d0359-164">Do rozhraní bylo přidáno okno hlášení chyb ukotvené v levé dolní části hlavního okna.</span><span class="sxs-lookup"><span data-stu-id="d0359-164">An error-reporting window, docked to the bottom-left of the main window, has been added to the interface.</span></span>  
  
-   <span data-ttu-id="d0359-165">Klávesové zkratky jde Zkontrolovat duplikáty: z nabídky Formát, klikněte na tlačítko **zkontrolovat klávesové zkratky** příkaz.</span><span class="sxs-lookup"><span data-stu-id="d0359-165">Hotkeys can be checked for duplicates: from the Format menu, click the **Check HotKeys** command.</span></span>  
  
## <a name="version-compatibility"></a><span data-ttu-id="d0359-166">Kompatibilita verzí</span><span class="sxs-lookup"><span data-stu-id="d0359-166">Version Compatibility</span></span>  
 <span data-ttu-id="d0359-167">Protože došlo ke změně formátu souborů prostředků mezi sadou Visual Studio .NET 2002 a Visual Studio 2005, nástroj Winres.exe byl rovněž změněn tak, aby byla zajištěna kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="d0359-167">Because the format of resource files changed between Visual Studio .NET 2002 and Visual Studio 2005, Winres.exe was likewise changed to be compatible.</span></span> <span data-ttu-id="d0359-168">Proto byste měli používat verzi nástroje Winres.exe vydanou s rozhraním .NET Framework, které používáte k vytvoření aplikace.</span><span class="sxs-lookup"><span data-stu-id="d0359-168">Therefore, as a general rule, you should use the version of Winres.exe that was released with the .NET Framework you are using to create the application.</span></span> <span data-ttu-id="d0359-169">Následující tabulka uvádí kompatibilní verze.</span><span class="sxs-lookup"><span data-stu-id="d0359-169">The following table lists the compatible versions.</span></span>  
  
|<span data-ttu-id="d0359-170">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0359-170">Visual Studio</span></span>|<span data-ttu-id="d0359-171">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0359-171">.NET Framework</span></span>|<span data-ttu-id="d0359-172">Winres.exe</span><span class="sxs-lookup"><span data-stu-id="d0359-172">Winres.exe</span></span>|  
|-------------------|--------------------|----------------|  
|<span data-ttu-id="d0359-173">Visual Studio .NET 2002</span><span class="sxs-lookup"><span data-stu-id="d0359-173">Visual Studio .NET 2002</span></span>|<span data-ttu-id="d0359-174">1.0</span><span class="sxs-lookup"><span data-stu-id="d0359-174">1.0</span></span>|<span data-ttu-id="d0359-175">1.0</span><span class="sxs-lookup"><span data-stu-id="d0359-175">1.0</span></span>|  
|<span data-ttu-id="d0359-176">Visual Studio .NET 2003</span><span class="sxs-lookup"><span data-stu-id="d0359-176">Visual Studio .NET 2003</span></span>|<span data-ttu-id="d0359-177">1.1</span><span class="sxs-lookup"><span data-stu-id="d0359-177">1.1</span></span>|<span data-ttu-id="d0359-178">1.1</span><span class="sxs-lookup"><span data-stu-id="d0359-178">1.1</span></span>|  
|<span data-ttu-id="d0359-179">Visual Studio 2005</span><span class="sxs-lookup"><span data-stu-id="d0359-179">Visual Studio 2005</span></span>|<span data-ttu-id="d0359-180">2.0</span><span class="sxs-lookup"><span data-stu-id="d0359-180">2.0</span></span>|<span data-ttu-id="d0359-181">2.0</span><span class="sxs-lookup"><span data-stu-id="d0359-181">2.0</span></span>|  
|<span data-ttu-id="d0359-182">Visual Studio 2008</span><span class="sxs-lookup"><span data-stu-id="d0359-182">Visual Studio 2008</span></span>|<span data-ttu-id="d0359-183">3.0 a 3.5</span><span class="sxs-lookup"><span data-stu-id="d0359-183">3.0 and 3.5</span></span>|<span data-ttu-id="d0359-184">3.0 a 3.5</span><span class="sxs-lookup"><span data-stu-id="d0359-184">3.0 and 3.5</span></span>|  
|<span data-ttu-id="d0359-185">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="d0359-185">Visual Studio 2010</span></span>|<span data-ttu-id="d0359-186">4.0</span><span class="sxs-lookup"><span data-stu-id="d0359-186">4.0</span></span>|<span data-ttu-id="d0359-187">4.0</span><span class="sxs-lookup"><span data-stu-id="d0359-187">4.0</span></span>|  
  
 <span data-ttu-id="d0359-188">Pokud se pokusíte otevřít starší soubor prostředků v nástroji Winres.exe verze 2.0, budete vyzváni k upgradu na formát souboru, který bude kompatibilní s rozhraním .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d0359-188">If you attempt to open an older resource file with version 2.0 of Winres.exe, you will be prompted to upgrade the format of the file to be compatible with version 2.0 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d0359-189">Ve verzích rozhraní .NET Framework starších než verze 2.0 nástroj Winres.exe a Návrhář formulářů sady Visual Studio vytváří nekompatibilní soubory prostředků nezávislé a závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="d0359-189">In versions of the .NET Framework prior to version 2.0, Winres.exe and the Forms Designer of Visual Studio created incompatible culture-neutral and culture-specific resource files.</span></span> <span data-ttu-id="d0359-190">Proto, jakmile zahájíte proces lokalizace, musíte pokračovat pouze se stejným nástrojem.</span><span class="sxs-lookup"><span data-stu-id="d0359-190">Therefore, once the localization process began, you had to continue using only the same tool.</span></span> <span data-ttu-id="d0359-191">V nástroji Winres.exe verze 2.0 byl přidán režim Visual Studio File Mode (VSFM).</span><span class="sxs-lookup"><span data-stu-id="d0359-191">However, with version 2.0 of Winres.exe, the Visual Studio File Mode (VSFM) was added.</span></span> <span data-ttu-id="d0359-192">Jak již název napovídá, soubor prostředků uložený v tomto režimu kompatibility lze upravovat pomocí kteréhokoli z těchto nástrojů.</span><span class="sxs-lookup"><span data-stu-id="d0359-192">As the name implies, a resource file saved in this compatibility mode can be edited with either tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0359-193">Ačkoli se režim VSFM vyznačuje výhodou kompatibility se sadou Visual Studio, tak vzhledem k tomu, že do souboru prostředků jsou uloženy pouze změněné hodnoty, nástroj Winres.exe vyžaduje, aby se soubory nadřazené aktuálnímu souboru prostředků nacházely ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="d0359-193">Although VSFM has the advantage of being compatible with Visual Studio, since it stores only changed values in the resource file, Winres.exe requires that the parents of the current resource file be located in the same directory.</span></span> <span data-ttu-id="d0359-194">Například úpravy `TestApp.de-DE.resources`, němčina v souboru prostředků Německo, vyžaduje výchozí soubor prostředků `TestApp.resx`a pravděpodobně se soubor prostředků neutrální jazykové verze `TestApp.de.resources`.</span><span class="sxs-lookup"><span data-stu-id="d0359-194">For example, editing `TestApp.de-DE.resources`, a German in Germany resource file, requires the presence of the default resource file, `TestApp.resx`, and possibly the culture-neutral resource file, `TestApp.de.resources`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d0359-195">Příklady</span><span class="sxs-lookup"><span data-stu-id="d0359-195">Examples</span></span>  
  
#### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a><span data-ttu-id="d0359-196">Lokalizace souborů .resx nebo .resources spojených s formulářem</span><span class="sxs-lookup"><span data-stu-id="d0359-196">To localize a .resx or .resources file associated with a form</span></span>  
  
1.  <span data-ttu-id="d0359-197">Typ `winres` v příkazovém řádku vývojáře ke spuštění Winres.exe.</span><span class="sxs-lookup"><span data-stu-id="d0359-197">Type `winres` in the developer command prompt to run Winres.exe.</span></span>  
  
2.  <span data-ttu-id="d0359-198">Chcete-li otevřít výchozí prostředky pro formulář k lokalizaci, klikněte na tlačítko **otevřete** příkaz na **souboru** nabídky a přejděte k souboru a ten se otevře.</span><span class="sxs-lookup"><span data-stu-id="d0359-198">To open the default resources for a form to localize, click the **Open** command on the **File** menu and navigate to the file to open it.</span></span>  
  
     <span data-ttu-id="d0359-199">-nebo-</span><span class="sxs-lookup"><span data-stu-id="d0359-199">-or-</span></span>  
  
     <span data-ttu-id="d0359-200">Při spouštění nástroje Winres.exe do příkazového řádku zadejte název otevíraného souboru.</span><span class="sxs-lookup"><span data-stu-id="d0359-200">Specify the file to open at the command line when you start Winres.exe.</span></span>  
  
     <span data-ttu-id="d0359-201">Tento příkaz spustí Winres.exe a načte formulář přidružený `TestApp.resx` v návrháři formuláře.</span><span class="sxs-lookup"><span data-stu-id="d0359-201">The following command starts Winres.exe and loads the form associated with `TestApp.resx` in the Form Designer.</span></span>  
  
    ```  
    winres TestApp.resx  
    ```  
  
     <span data-ttu-id="d0359-202">Tento příkaz spustí Winres.exe a načte formulář přidružený `TestApp.resources` v návrháři formuláře.</span><span class="sxs-lookup"><span data-stu-id="d0359-202">The following command starts Winres.exe and loads the form associated with `TestApp.resources` in the Form Designer.</span></span>  
  
    ```  
    winres TestApp.resources  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d0359-203">Jestliže je formulář, jehož prostředky upravujete, zděděným formulářem, sestavení obsahující zděděný formulář i sestavení obsahující odvozený formulář musí být zaregistrována v globální mezipaměti sestavení (GAC) nebo musí být umístěna ve stejném adresáři jako nástroj WinRes.exe.</span><span class="sxs-lookup"><span data-stu-id="d0359-203">If the form whose resources you are editing is an inherited form, both the assembly contained the inherited form and the assembly containing the inheriting (derived) form must either be registered in the Global Assembly Cache (GAC), or must reside in the same directory as WinRes.exe.</span></span> <span data-ttu-id="d0359-204">Další informace o instalaci součásti rozhraní .NET Framework do mezipaměti GAC najdete v tématu [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="d0359-204">For more information about installing .NET Framework components into the GAC, see [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
3.  <span data-ttu-id="d0359-205">Vyberte ovládací prvky na formuláři a změnit jejich <xref:System.Windows.Forms.Control.Text%2A> a dalších vlastností tak, aby odrážela lokalizované jazykovou verzi a její jazyk.</span><span class="sxs-lookup"><span data-stu-id="d0359-205">Select controls on the form and change their <xref:System.Windows.Forms.Control.Text%2A> and other properties to reflect the localized culture and its language.</span></span> <span data-ttu-id="d0359-206">Přesuňte ovládací prvky nebo změňte jejich velikost tak, aby vyhovovaly lokalizovanému textu.</span><span class="sxs-lookup"><span data-stu-id="d0359-206">Move or resize controls as necessary to accommodate the localized text.</span></span>  
  
4.  <span data-ttu-id="d0359-207">Lokalizované verzi souboru RESX nebo .resources uložit, klikněte **Uložit** ikony nebo stejný příkaz na **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d0359-207">To save the localized version of the .resx or .resources file, click the **Save** icon or the same command on the **File** menu.</span></span> <span data-ttu-id="d0359-208">Nástroj zobrazí **vyberte jazykovou verzi** okno.</span><span class="sxs-lookup"><span data-stu-id="d0359-208">The tool displays the **Select Culture** window.</span></span>  
  
5.  <span data-ttu-id="d0359-209">Vyberte odpovídající režim jazykovou verzi a soubor a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d0359-209">Select the appropriate culture and file mode then click **OK**.</span></span> <span data-ttu-id="d0359-210">Nástroj uloží soubor s použitím konvence vytváření názvů, kterou modul pro lokalizované soubory prostředků očekává.</span><span class="sxs-lookup"><span data-stu-id="d0359-210">The tool saves the file, using the naming convention that the run time expects for localized resource files.</span></span> <span data-ttu-id="d0359-211">Například, pokud je lokalizovat `TestApp.resources` pro němčinu v Německu nástroj uloží soubor jako `TestApp.de-DE.resources`.</span><span class="sxs-lookup"><span data-stu-id="d0359-211">For example, if you localize `TestApp.resources` for German in Germany, the tool saves the file as `TestApp.de-DE.resources`.</span></span> <span data-ttu-id="d0359-212">Pokud je lokalizovat `TestApp.resx` pro němčinu v Německu nástroj uloží soubor jako `TestApp.de-DE.resx`.</span><span class="sxs-lookup"><span data-stu-id="d0359-212">If you localize `TestApp.resx` for German in Germany, the tool saves the file as `TestApp.de-DE.resx`.</span></span> <span data-ttu-id="d0359-213">Další informace o zásady vytváření názvů prostředků najdete v tématu [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d0359-213">For more information about resource naming conventions, see [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span> <span data-ttu-id="d0359-214">Seznam předdefinovaných jazykovou verzi názvy používané čas spuštění, naleznete v části <xref:System.Globalization.CultureInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="d0359-214">For a list of the predefined culture names used by the run time, see the <xref:System.Globalization.CultureInfo> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0359-215">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0359-215">See Also</span></span>  
 <xref:System.ComponentModel.LocalizableAttribute>  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Resources.ResourceManager>  
 <xref:System.Resources.ResourceReader>  
 <xref:System.Resources.ResourceWriter>  
 [<span data-ttu-id="d0359-216">Nástroje</span><span class="sxs-lookup"><span data-stu-id="d0359-216">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="d0359-217">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="d0359-217">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)  
 [<span data-ttu-id="d0359-218">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="d0359-218">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)