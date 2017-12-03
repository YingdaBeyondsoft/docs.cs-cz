---
title: "Postupy: Zobrazení milisekund v hodnotách data a času"
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
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="6a6b9-102">Postupy: Zobrazení milisekund v hodnotách data a času</span><span class="sxs-lookup"><span data-stu-id="6a6b9-102">How to: Display Milliseconds in Date and Time Values</span></span>
<span data-ttu-id="6a6b9-103">Výchozí metody pro formátování hodnot data a času, jako například <xref:System.DateTime.ToString?displayProperty=nameWithType>, zahrnují hodiny, minuty a sekundy příslušné časové hodnoty, ale neobsahují komponentu milisekund.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-103">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="6a6b9-104">Toto téma popisuje způsob začlenění komponenty milisekund do příslušné hodnoty data a času ve formátovaných řetězcích data a času.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-104">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="6a6b9-105">Zobrazení komponenty milisekund hodnoty DateTime</span><span class="sxs-lookup"><span data-stu-id="6a6b9-105">To display the millisecond component of a DateTime value</span></span>  
  
1.  <span data-ttu-id="6a6b9-106">Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-106">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="6a6b9-107">Chcete-li extrahovat řetězcovou reprezentaci komponenty milisekund, zavolejte metodu hodnot data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%2A> a předejte vzor vlastního formátu `fff` nebo `FFF` buď samostatně, nebo s dalšími specifikátory vlastního formátu jako parametr `format`.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-107">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a6b9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a6b9-108">Example</span></span>  
 <span data-ttu-id="6a6b9-109">Příklad zobrazí komponentu milisekund hodnot <xref:System.DateTime> a <xref:System.DateTimeOffset> do konzoly samostatně i jako součást delšího řetězce data a času.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-109">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="6a6b9-110">Vzor formátu `fff` zahrnuje všechny koncové nuly v hodnotě milisekund.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-110">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="6a6b9-111">Vzor formátu `FFF` je potlačí.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-111">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="6a6b9-112">Rozdíl je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-112">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="6a6b9-113">Problém s definováním kompletního specifikátoru vlastního formátu, který zahrnuje komponentu milisekund příslušného data a času, spočívá v tom, že definuje pevně zakódovaný formát, který nemusí odpovídat uspořádání prvků času v aktuální jazykové verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-113">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="6a6b9-114">Lepší alternativou je načíst jeden ze vzorů zobrazení data a času, které jsou definovány v objektu aktuální jazykové verze <xref:System.Globalization.DateTimeFormatInfo>, a upravit je tak, aby milisekundy obsahovaly.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-114">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="6a6b9-115">Tento příklad znázorňuje také tento přístup.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-115">The example also illustrates this approach.</span></span> <span data-ttu-id="6a6b9-116">Načte úplný vzor data a času pro aktuální jazykovou verzi z vlastnosti <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> a poté za vzor sekund vloží vlastní vzor `.ffff`.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-116">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="6a6b9-117">Příklad používá pro provedení této operace v rámci jednoho volání metody regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-117">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="6a6b9-118">Pro zobrazení jiné části sekundového údaje než milisekund lze použít také specifikátor vlastního formátu.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-118">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="6a6b9-119">Například specifikátor vlastního formátu `f` nebo `F` zobrazí desetiny sekundy, specifikátor vlastního formátu `ff` nebo `FF` zobrazí setiny sekundy a specifikátor vlastního formátu `ffff` nebo `FFFF` zobrazí desetitisíciny sekundy.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-119">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="6a6b9-120">Zlomkové části milisekundy jsou ve vráceném řetězci namísto zaokrouhlení zkráceny.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-120">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="6a6b9-121">Tyto specifikátory formátu se používají v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-121">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="6a6b9-122">Je možné zobrazit velmi malé zlomkové jednotky sekundy, jako například desetitisíciny sekundy nebo stotisíciny sekundy.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-122">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="6a6b9-123">Tyto hodnoty však nemusí být smysluplné.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-123">However, these values may not be meaningful.</span></span> <span data-ttu-id="6a6b9-124">Přesnost hodnot data a času závisí na rozlišení systémových hodin.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-124">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="6a6b9-125">V systému Windows NT 3.5 a novějších verzích a v operačním systému [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] je rozlišení hodin přibližně 10–15 milisekund.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-125">On Windows NT 3.5 and later, and [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a6b9-126">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6a6b9-126">Compiling the Code</span></span>  
 <span data-ttu-id="6a6b9-127">Je možné zkompilovat kód v příkazovém řádku pomocí souboru csc.exe nebo vb.exe.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-127">Compile the code at the command line using csc.exe or vb.exe.</span></span> <span data-ttu-id="6a6b9-128">Chcete-li kód zkompilovat v rámci [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vložte jej do šablony projektu konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a6b9-128">To compile the code in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], put it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6b9-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a6b9-129">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="6a6b9-130">Řetězce formátu vlastní hodnota data a času</span><span class="sxs-lookup"><span data-stu-id="6a6b9-130">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)