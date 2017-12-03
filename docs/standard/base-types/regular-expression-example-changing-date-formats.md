---
title: "Příklad regulární výraz: Změna formátů data"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eeaed0951018c989612691065c027ee46bd6655a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="bf4b0-102">Příklad regulární výraz: Změna formátů data</span><span class="sxs-lookup"><span data-stu-id="bf4b0-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="bf4b0-103">Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody lze nahradit kalendářních dat, které mají tvar *mm*/*dd*/*rr* s data, která mít formát *dd*-*mm*-*rr*.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf4b0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf4b0-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="bf4b0-105">Následující kód ukazuje jak `MDYToDMY` metodu lze volat v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="bf4b0-106">Komentáře</span><span class="sxs-lookup"><span data-stu-id="bf4b0-106">Comments</span></span>  
 <span data-ttu-id="bf4b0-107">Regulární výraz `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="bf4b0-108">Vzor</span><span class="sxs-lookup"><span data-stu-id="bf4b0-108">Pattern</span></span>|<span data-ttu-id="bf4b0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bf4b0-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="bf4b0-110">Začne porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="bf4b0-111">Odpovídat jedna nebo dvě desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-111">Match one or two decimal digits.</span></span> <span data-ttu-id="bf4b0-112">Toto je `month` zaznamenané skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="bf4b0-113">Porovná lomítko.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="bf4b0-114">Odpovídat jedna nebo dvě desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-114">Match one or two decimal digits.</span></span> <span data-ttu-id="bf4b0-115">Toto je `day` zaznamenané skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="bf4b0-116">Porovná lomítko.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="bf4b0-117">Odpovídat ze dvou na čtyři desítková číslice.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="bf4b0-118">Toto je `year` zaznamenané skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="bf4b0-119">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="bf4b0-120">Vzor `${day}-${month}-${year}` definuje náhradní řetězec, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="bf4b0-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="bf4b0-121">Pattern</span></span>|<span data-ttu-id="bf4b0-122">Popis</span><span class="sxs-lookup"><span data-stu-id="bf4b0-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="bf4b0-123">Přidejte řetězec zachyceny `day` zaznamenávání skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="bf4b0-124">Přidejte pomlčka.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="bf4b0-125">Přidejte řetězec zachyceny `month` zaznamenávání skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="bf4b0-126">Přidejte pomlčka.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="bf4b0-127">Přidejte řetězec zachyceny `year` zaznamenávání skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf4b0-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf4b0-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf4b0-128">See Also</span></span>  
 [<span data-ttu-id="bf4b0-129">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="bf4b0-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)