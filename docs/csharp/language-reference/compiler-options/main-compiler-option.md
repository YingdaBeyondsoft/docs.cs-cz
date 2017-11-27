---
title: "-main (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6dca6e62dbf69783babf2e16dc4e7c36c6705c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="main-c-compiler-options"></a><span data-ttu-id="58c75-102">/main (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="58c75-102">/main (C# Compiler Options)</span></span>
<span data-ttu-id="58c75-103">Tato možnost určuje třídu, která obsahuje položky, přejděte na program, pokud obsahuje více než jedné třídy **hlavní** metoda.</span><span class="sxs-lookup"><span data-stu-id="58c75-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58c75-104">Syntax</span></span>  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="58c75-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="58c75-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="58c75-106">Typ, který obsahuje **hlavní** metoda.</span><span class="sxs-lookup"><span data-stu-id="58c75-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58c75-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58c75-107">Remarks</span></span>  
 <span data-ttu-id="58c75-108">Pokud kompilace obsahuje více než jeden typ s [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metodu, můžete zadat typ, který obsahuje **hlavní** metodu, kterou chcete použít jako vstupní bod do programu.</span><span class="sxs-lookup"><span data-stu-id="58c75-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="58c75-109">Tato možnost je pro použití při kompilaci souboru s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="58c75-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="58c75-110">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58c75-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="58c75-111">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="58c75-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="58c75-112">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="58c75-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="58c75-113">Změnit **spouštěcí objekt** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58c75-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="58c75-114">Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="58c75-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58c75-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="58c75-115">Example</span></span>  
 <span data-ttu-id="58c75-116">Kompilace `t2.cs` a `t3.cs`, zadání, **hlavní** metoda najdete ve `Test2`:</span><span class="sxs-lookup"><span data-stu-id="58c75-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="58c75-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="58c75-117">See Also</span></span>  
 [<span data-ttu-id="58c75-118">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="58c75-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="58c75-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="58c75-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)