---
title: "#<a name=\"warning-c-reference\"></a>upozornění (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#warning'
helpviewer_keywords: '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a><span data-ttu-id="8f779-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8f779-102">#warning (C# Reference)</span></span>
<span data-ttu-id="8f779-103">`#warning`Umožňuje generovat varováním na úrovni jednoho z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="8f779-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="8f779-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8f779-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="8f779-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f779-105">Remarks</span></span>  
 <span data-ttu-id="8f779-106">Běžně se používají `#warning` v podmíněného direktivu.</span><span class="sxs-lookup"><span data-stu-id="8f779-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="8f779-107">Je také možné generovat uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="8f779-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f779-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f779-108">Example</span></span>  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f779-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f779-109">See Also</span></span>  
 [<span data-ttu-id="8f779-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8f779-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8f779-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8f779-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8f779-112">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="8f779-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)