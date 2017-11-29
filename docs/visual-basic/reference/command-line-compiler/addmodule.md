---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a><span data-ttu-id="eb634-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="eb634-102">/addmodule</span></span>
<span data-ttu-id="eb634-103">Způsobí, že kompilátor zkontrolujte všechny informace ze zadané soubory, které jsou k dispozici do projektu, které jsou aktuálně kompilování typu.</span><span class="sxs-lookup"><span data-stu-id="eb634-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb634-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb634-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb634-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb634-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="eb634-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="eb634-106">Required.</span></span> <span data-ttu-id="eb634-107">Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb634-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="eb634-108">Názvy souborů obsahujících mezery musí být uzavřena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="eb634-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb634-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb634-109">Remarks</span></span>  
 <span data-ttu-id="eb634-110">Soubory uvedené podle `fileList` parametr musí být vytvořeny s `/target:module` možnost, nebo s jinou kompilátoru ekvivalent `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="eb634-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="eb634-111">Všechny moduly přidané pomocí `/addmodule` musí být ve stejném adresáři jako výstupní soubor za běhu.</span><span class="sxs-lookup"><span data-stu-id="eb634-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="eb634-112">To znamená můžete zadat modul v libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="eb634-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="eb634-113">Pokud není, můžete získat <xref:System.TypeLoadException> chyby.</span><span class="sxs-lookup"><span data-stu-id="eb634-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="eb634-114">Pokud zadáte (implicitně nebo explicitně) žádné[/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) možnost jiné než `/target:module` s `/addmodule`, soubory, které předat `/addmodule` se stanou součástí sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="eb634-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="eb634-115">Sestavení se vyžaduje ke spuštění výstupního souboru, který má jeden nebo víc souborů se přidaly `/addmodule`.</span><span class="sxs-lookup"><span data-stu-id="eb634-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="eb634-116">Použití [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Import metadat ze souboru, který obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb634-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb634-117">`/addmodule` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="eb634-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb634-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb634-118">Example</span></span>  
 <span data-ttu-id="eb634-119">Následující kód vytvoří modul.</span><span class="sxs-lookup"><span data-stu-id="eb634-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="eb634-120">Následující kód importuje modulu typy.</span><span class="sxs-lookup"><span data-stu-id="eb634-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="eb634-121">Při spuštění `t1`, vyprodukuje `802`.</span><span class="sxs-lookup"><span data-stu-id="eb634-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb634-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb634-122">See Also</span></span>  
 [<span data-ttu-id="eb634-123">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="eb634-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="eb634-124">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb634-124">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="eb634-125">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb634-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="eb634-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="eb634-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)