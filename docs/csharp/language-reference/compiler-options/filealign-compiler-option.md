---
title: "-filealign (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe2d1df6d88baa2957068514abe728f29cb74636
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="filealign-c-compiler-options"></a><span data-ttu-id="08e51-102">/filealign (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="08e51-102">/filealign (C# Compiler Options)</span></span>
<span data-ttu-id="08e51-103">**/Filealign** možnost umožňuje zadat velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="08e51-103">The **/filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08e51-104">Syntax</span></span>  
  
```console  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="08e51-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="08e51-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="08e51-106">Hodnota, která určuje velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="08e51-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="08e51-107">Platné hodnoty jsou 512, 1024, 2048, 4096 až 8192.</span><span class="sxs-lookup"><span data-stu-id="08e51-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="08e51-108">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="08e51-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08e51-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08e51-109">Remarks</span></span>  
 <span data-ttu-id="08e51-110">Každý oddíl bude zarovnán na hranici, která je násobkem **/filealign** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="08e51-110">Each section will be aligned on a boundary that is a multiple of the **/filealign** value.</span></span> <span data-ttu-id="08e51-111">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="08e51-111">There is no fixed default.</span></span> <span data-ttu-id="08e51-112">Pokud **/filealign** není zadán, modul common language runtime zvolí výchozí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="08e51-112">If **/filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="08e51-113">Zadáním velikost části vliv velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="08e51-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="08e51-114">Změna velikosti oddílu může být užitečné pro programy, které se spustí na menší zařízení.</span><span class="sxs-lookup"><span data-stu-id="08e51-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="08e51-115">Použití [DUMPBIN](/cpp/build/reference/dumpbin-options) zobrazíte informace o oddílech ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="08e51-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="08e51-116">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08e51-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="08e51-117">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="08e51-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="08e51-118">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="08e51-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="08e51-119">Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="08e51-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="08e51-120">Změnit **zarovnání souboru** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="08e51-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="08e51-121">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="08e51-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e51-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="08e51-122">See Also</span></span>  
 [<span data-ttu-id="08e51-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="08e51-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="08e51-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="08e51-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)