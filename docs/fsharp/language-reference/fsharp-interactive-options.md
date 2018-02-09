---
title: "Interaktivní možnosti F#"
description: "Další informace o možnostech příkazového řádku F # interaktivní, nepodporuje fsi.exe."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: 0fc369993b3ee4c8a9139e4a365330197fe66946
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="f-interactive-options"></a><span data-ttu-id="180b6-104">Interaktivní možnosti F#</span><span class="sxs-lookup"><span data-stu-id="180b6-104">F# Interactive Options</span></span>

> [!NOTE]
<span data-ttu-id="180b6-105">Tento článek popisuje aktuálně prostředí jenom pro Windows.</span><span class="sxs-lookup"><span data-stu-id="180b6-105">This article currently describes the experience for Windows only.</span></span>  <span data-ttu-id="180b6-106">Bude přepsán.</span><span class="sxs-lookup"><span data-stu-id="180b6-106">It will be rewritten.</span></span>

<span data-ttu-id="180b6-107">Toto téma popisuje možnosti příkazového řádku F # interaktivní, nepodporuje `fsi.exe`.</span><span class="sxs-lookup"><span data-stu-id="180b6-107">This topic describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="180b6-108">F # interaktivní přijímá řadu stejné možnosti příkazového řádku jako kompilátor jazyka F #, ale také přijímá některé další možnosti.</span><span class="sxs-lookup"><span data-stu-id="180b6-108">F# Interactive accepts many of the same command line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="using-f-interactive-for-scripting"></a><span data-ttu-id="180b6-109">Pomocí F # interaktivní pro skriptování</span><span class="sxs-lookup"><span data-stu-id="180b6-109">Using F# Interactive for Scripting</span></span>
<span data-ttu-id="180b6-110">F # interaktivní, `fsi.exe`, může být spuštěn interaktivně, nebo může být spuštěn z příkazového řádku spustit skript.</span><span class="sxs-lookup"><span data-stu-id="180b6-110">F# Interactive, `fsi.exe`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="180b6-111">Syntaxe příkazového řádku je</span><span class="sxs-lookup"><span data-stu-id="180b6-111">The command line syntax is</span></span>

```
> fsi.exe [options] [ script-file [arguments] ]
```

<span data-ttu-id="180b6-112">Přípona souboru pro soubory skriptu F # je `.fsx`.</span><span class="sxs-lookup"><span data-stu-id="180b6-112">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="180b6-113">Tabulka interaktivní možnosti F #</span><span class="sxs-lookup"><span data-stu-id="180b6-113">Table of F# Interactive Options</span></span>
<span data-ttu-id="180b6-114">Následující tabulka shrnuje možnosti podporované F # interaktivní.</span><span class="sxs-lookup"><span data-stu-id="180b6-114">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="180b6-115">Tyto možnosti můžete nastavit na příkazovém řádku nebo pomocí prostředí Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="180b6-115">You can set these options on the command-line or through the Visual Studio IDE.</span></span> <span data-ttu-id="180b6-116">Chcete-li nastavit tyto možnosti v prostředí Visual Studio IDE, otevřete **nástroje** nabídce vyberte možnost **možnosti...** , pak rozbalte **nástroje F #** uzel a vyberte možnost **F # interaktivní**.</span><span class="sxs-lookup"><span data-stu-id="180b6-116">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options...**, then expand the **F# Tools** node and select **F# Interactive**.</span></span>

<span data-ttu-id="180b6-117">Kde seznamy se zobrazují v F # interaktivní možnost argumenty, seznamu elementů oddělených středníky (`;`).</span><span class="sxs-lookup"><span data-stu-id="180b6-117">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="180b6-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="180b6-118">Option</span></span>|<span data-ttu-id="180b6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="180b6-119">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="180b6-120">Používá se udělit pokyny F # interaktivní považovat za zbývající argumenty argumenty příkazového řádku F # program nebo skript, kterým můžete přistupovat v kódu pomocí seznamu **fsi.CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="180b6-120">Used to instruct F# Interactive to treat remaining arguments as command line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="180b6-121">**--checked**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-121">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-122">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-123">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-124">**codepage –:&lt;int&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-124">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="180b6-125">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-125">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-126">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-126">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-127">**--crossoptimize**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-127">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-128">Povolit nebo zakázat optimalizace cross-module.</span><span class="sxs-lookup"><span data-stu-id="180b6-128">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="180b6-129">**--debug**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-129">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="180b6-130">**--debug:**[**full**&#124;**pdbonly**]</span><span class="sxs-lookup"><span data-stu-id="180b6-130">**--debug:**[**full**&#124;**pdbonly**]</span></span><br /><br /><span data-ttu-id="180b6-131">**-g**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-131">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="180b6-132">**-g:**[**full**&#124;**pdbonly**]</span><span class="sxs-lookup"><span data-stu-id="180b6-132">**-g:**[**full**&#124;**pdbonly**]</span></span>|<span data-ttu-id="180b6-133">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-133">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-134">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-134">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-135">**--definovat:&lt;řetězec&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-135">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="180b6-136">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-136">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-137">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-137">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-138">**--exec**</span><span class="sxs-lookup"><span data-stu-id="180b6-138">**--exec**</span></span>|<span data-ttu-id="180b6-139">Dá pokyn, F # interaktivní ukončíte po načtení souborů nebo spuštění souboru skriptu zadána na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="180b6-139">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="180b6-140">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="180b6-140">**--fullpaths**</span></span>|<span data-ttu-id="180b6-141">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-141">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-142">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-142">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-143">**--gui**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-143">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-144">Povolí nebo zakáže smyčky událostí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="180b6-144">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="180b6-145">Výchozí hodnota je povoleno.</span><span class="sxs-lookup"><span data-stu-id="180b6-145">The default is enabled.</span></span>|
|<span data-ttu-id="180b6-146">**--help**</span><span class="sxs-lookup"><span data-stu-id="180b6-146">**--help**</span></span><br /><br /><span data-ttu-id="180b6-147">**-?**</span><span class="sxs-lookup"><span data-stu-id="180b6-147">**-?**</span></span>|<span data-ttu-id="180b6-148">Slouží k zobrazení syntaxe příkazového řádku a stručný popis jednotlivých možností.</span><span class="sxs-lookup"><span data-stu-id="180b6-148">Used to display the command line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="180b6-149">**--lib:&lt;folder-list&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-149">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="180b6-150">**-I:&lt;seznamu složek&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-150">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="180b6-151">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-151">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-152">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-152">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-153">**--načíst:&lt;filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-153">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="180b6-154">Kompilovaný kód zadaná zdrojová při spuštění a načte kompilované konstrukce F # do relace.</span><span class="sxs-lookup"><span data-stu-id="180b6-154">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span> <span data-ttu-id="180b6-155">Pokud cílový zdroj obsahuje skriptování direktivy, jako **#use** nebo **#load**, pak musíte použít **– použít** nebo **#use** místo **– načíst** nebo **#load**.</span><span class="sxs-lookup"><span data-stu-id="180b6-155">If the target source contains scripting directives such as **#use** or **#load**, then you must use **--use** or **#use** instead of **--load** or **#load**.</span></span>|
|<span data-ttu-id="180b6-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="180b6-156">**--mlcompatibility**</span></span>|<span data-ttu-id="180b6-157">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-158">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="180b6-159">**--noframework**</span></span>|<span data-ttu-id="180b6-160">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-161">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="180b6-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="180b6-162">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="180b6-162">**--nologo**</span></span>|<span data-ttu-id="180b6-163">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-164">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-165">**nowarn –:&lt;seznam upozornění&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="180b6-166">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-167">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-168">**--optimize**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-169">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-170">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-171">**preferreduilang –:&lt;jazyk&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="180b6-172">Určuje název jazykové verze jazyka upřednostňované výstup (například es-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="180b6-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="180b6-173">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="180b6-173">**--quiet**</span></span>|<span data-ttu-id="180b6-174">Potlačit F # interaktivní na výstup do **stdout** datového proudu.</span><span class="sxs-lookup"><span data-stu-id="180b6-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="180b6-175">**--quotations-debug**</span><span class="sxs-lookup"><span data-stu-id="180b6-175">**--quotations-debug**</span></span>|<span data-ttu-id="180b6-176">Určuje, že by měl pro výrazy, které jsou odvozeny od uvozovek literály F # a reflektován definice vygenerované velmi ladicí informace.</span><span class="sxs-lookup"><span data-stu-id="180b6-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="180b6-177">Informace o ladění se přidá do vlastní atributy uzlu stromu výraz F #.</span><span class="sxs-lookup"><span data-stu-id="180b6-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="180b6-178">V tématu [Code uvozovky](code-quotations.md) a [Expr.CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="180b6-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="180b6-179">**--readline**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-180">Povolit nebo zakázat dokončování pomocí tabulátorů v interaktivním režimu.</span><span class="sxs-lookup"><span data-stu-id="180b6-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="180b6-181">**--reference:&lt;filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="180b6-182">**-r:&lt;filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="180b6-183">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-184">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-185">**tailcalls –**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-186">Povolí nebo zakáže použití pokyn IL tail, což způsobí, že rámce zásobníku znovu použije pro rekurzivní funkce tail.</span><span class="sxs-lookup"><span data-stu-id="180b6-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="180b6-187">Tato možnost je povolená ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="180b6-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="180b6-188">**--použít:&lt;filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-188">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="180b6-189">Informuje překladač použít daný soubor při spuštění jako počáteční vstup.</span><span class="sxs-lookup"><span data-stu-id="180b6-189">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="180b6-190">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="180b6-190">**--utf8output**</span></span>|<span data-ttu-id="180b6-191">Stejné jako možnost fsc.exe kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-191">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="180b6-192">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-192">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-193">**--warn:&lt;warning-level&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-193">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="180b6-194">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-194">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-195">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-195">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-196">**--warnaserror**[**+**&#124;**-**]</span><span class="sxs-lookup"><span data-stu-id="180b6-196">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="180b6-197">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-197">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-198">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-198">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="180b6-199">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span><span class="sxs-lookup"><span data-stu-id="180b6-199">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="180b6-200">Stejné jako **fsc.exe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="180b6-200">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="180b6-201">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="180b6-201">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="related-topics"></a><span data-ttu-id="180b6-202">Související témata</span><span class="sxs-lookup"><span data-stu-id="180b6-202">Related Topics</span></span>

|<span data-ttu-id="180b6-203">Název</span><span class="sxs-lookup"><span data-stu-id="180b6-203">Title</span></span>|<span data-ttu-id="180b6-204">Popis</span><span class="sxs-lookup"><span data-stu-id="180b6-204">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="180b6-205">Možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="180b6-205">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="180b6-206">Popisuje možnosti příkazového řádku, které jsou k dispozici pro kompilátor F # **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="180b6-206">Describes command line options available for the F# compiler, **fsc.exe**.</span></span>|