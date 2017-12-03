---
title: "#<a name=\"region-directive\"></a>Region – direktiva"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb308da6ad0ca6243f14e0d825ed7eb005d622bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="region-directive"></a><span data-ttu-id="6bbc3-102">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="6bbc3-102">#Region Directive</span></span>
<span data-ttu-id="6bbc3-103">Sbalí a skrytí sekcí kódu v souborech jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bbc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bbc3-104">Syntax</span></span>  
  
```  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="6bbc3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6bbc3-105">Parts</span></span>  
  
|<span data-ttu-id="6bbc3-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6bbc3-106">Term</span></span>|<span data-ttu-id="6bbc3-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6bbc3-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="6bbc3-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-108">Required.</span></span> <span data-ttu-id="6bbc3-109">Řetězec, který funguje jako název oblasti, když je sbalená.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="6bbc3-110">Ve výchozím nastavení jsou sbaleny oblasti.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="6bbc3-111">Ukončí `#Region` bloku.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bbc3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bbc3-112">Remarks</span></span>  
 <span data-ttu-id="6bbc3-113">Použití `#Region` – direktiva blok kódu rozbalit nebo sbalit, když používáte funkci osnovy z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="6bbc3-114">Můžete umístit, nebo *vnořit*, oblastem v jiných oblastech chcete seskupit podobné oblasti.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bbc3-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bbc3-115">Example</span></span>  
 <span data-ttu-id="6bbc3-116">Tento příklad používá `#Region` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="6bbc3-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6bbc3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bbc3-117">See Also</span></span>  
 [<span data-ttu-id="6bbc3-118">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="6bbc3-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="6bbc3-119">Osnova</span><span class="sxs-lookup"><span data-stu-id="6bbc3-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="6bbc3-120">Postupy: sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="6bbc3-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)