---
title: "Přehled vektorové grafiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7bb3247f531a0dac83657e118fb53ebaf708ec9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="vector-graphics-overview"></a><span data-ttu-id="7d16d-102">Přehled vektorové grafiky</span><span class="sxs-lookup"><span data-stu-id="7d16d-102">Vector Graphics Overview</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="7d16d-103">Kreslení čar, obdélníků a ostatním tvarům na souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="7d16d-103"> draws lines, rectangles, and other shapes on a coordinate system.</span></span> <span data-ttu-id="7d16d-104">Můžete vybrat z různých souřadnicových systémů, ale výchozí souřadnicový systém má původ v levém horním rohu s osou x tvořenou hodnotami odkazující na ose y míří dolů a doprava.</span><span class="sxs-lookup"><span data-stu-id="7d16d-104">You can choose from a variety of coordinate systems, but the default coordinate system has the origin in the upper-left corner with the x-axis pointing to the right and the y-axis pointing down.</span></span> <span data-ttu-id="7d16d-105">Ve výchozím nastavení souřadnicový systém Měrná jednotka je pixelech.</span><span class="sxs-lookup"><span data-stu-id="7d16d-105">The unit of measure in the default coordinate system is the pixel.</span></span>  
  
## <a name="the-building-blocks-of-gdi"></a><span data-ttu-id="7d16d-106">Stavební bloky rozhraní GDI +</span><span class="sxs-lookup"><span data-stu-id="7d16d-106">The Building Blocks of GDI+</span></span>  
 <span data-ttu-id="7d16d-107">![Vektorová grafika](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span><span class="sxs-lookup"><span data-stu-id="7d16d-107">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span></span>  
  
 <span data-ttu-id="7d16d-108">Monitorování počítače vytvoří jeho zobrazení na obdélníkový pole teček označovaný jako obrázek elementy nebo pixelů.</span><span class="sxs-lookup"><span data-stu-id="7d16d-108">A computer monitor creates its display on a rectangular array of dots called picture elements or pixels.</span></span> <span data-ttu-id="7d16d-109">Počet pixelů, které se zobrazují na obrazovce se liší z jednoho monitoru na další a počet pixelů, která se zobrazují na jednotlivých monitorování lze nakonfigurovat obvykle do určité míry uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7d16d-109">The number of pixels that appear on the screen varies from one monitor to the next, and the number of pixels that appear on an individual monitor can usually be configured to some extent by the user.</span></span>  
  
 <span data-ttu-id="7d16d-110">![Vektorová grafika](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span><span class="sxs-lookup"><span data-stu-id="7d16d-110">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span></span>  
  
 <span data-ttu-id="7d16d-111">Při použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení čáry, obdélníku nebo křivky, zadáte určité klíčové informace o položce, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="7d16d-111">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, rectangle, or curve, you provide certain key information about the item to be drawn.</span></span> <span data-ttu-id="7d16d-112">Například můžete zadat řádek tím, že poskytuje dva body a zadáte obdélníku tím, že poskytuje bod, výšku a šířku.</span><span class="sxs-lookup"><span data-stu-id="7d16d-112">For example, you can specify a line by providing two points, and you can specify a rectangle by providing a point, a height, and a width.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="7d16d-113">funguje ve spojení s software ovladače zobrazení k určení, které pixelech musí být zapnutý zobrazíte řádku, obdélníku nebo křivky.</span><span class="sxs-lookup"><span data-stu-id="7d16d-113"> works in conjunction with the display driver software to determine which pixels must be turned on to show the line, rectangle, or curve.</span></span> <span data-ttu-id="7d16d-114">Následující obrázek znázorňuje pixelů, které jsou zapnuté pro zobrazení průběhu z bodu (4, 2) do bodu (12, 8).</span><span class="sxs-lookup"><span data-stu-id="7d16d-114">The following illustration shows the pixels that are turned on to display a line from the point (4, 2) to the point (12, 8).</span></span>  
  
 <span data-ttu-id="7d16d-115">![Vektorová grafika](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span><span class="sxs-lookup"><span data-stu-id="7d16d-115">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span></span>  
  
 <span data-ttu-id="7d16d-116">V průběhu času určité základní stavební bloky ukázaly jako velmi užitečné k vytváření dvourozměrná obrázků.</span><span class="sxs-lookup"><span data-stu-id="7d16d-116">Over time, certain basic building blocks have proven to be the most useful for creating two-dimensional pictures.</span></span> <span data-ttu-id="7d16d-117">Tyto stavební bloky, které jsou podporovány produktem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], jsou uvedeny v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="7d16d-117">These building blocks, which are all supported by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], are given in the following list:</span></span>  
  
-   <span data-ttu-id="7d16d-118">řádky</span><span class="sxs-lookup"><span data-stu-id="7d16d-118">Lines</span></span>  
  
-   <span data-ttu-id="7d16d-119">Obdélníků</span><span class="sxs-lookup"><span data-stu-id="7d16d-119">Rectangles</span></span>  
  
-   <span data-ttu-id="7d16d-120">Symbol tří teček</span><span class="sxs-lookup"><span data-stu-id="7d16d-120">Ellipses</span></span>  
  
-   <span data-ttu-id="7d16d-121">Oblouky</span><span class="sxs-lookup"><span data-stu-id="7d16d-121">Arcs</span></span>  
  
-   <span data-ttu-id="7d16d-122">Mnohoúhelníky</span><span class="sxs-lookup"><span data-stu-id="7d16d-122">Polygons</span></span>  
  
-   <span data-ttu-id="7d16d-123">Základní křivky vyhlazení</span><span class="sxs-lookup"><span data-stu-id="7d16d-123">Cardinal splines</span></span>  
  
-   <span data-ttu-id="7d16d-124">Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="7d16d-124">Bezier splines</span></span>  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a><span data-ttu-id="7d16d-125">Metody pro vykreslování s objektem grafiky</span><span class="sxs-lookup"><span data-stu-id="7d16d-125">Methods For Drawing with a Graphics Object</span></span>  
 <span data-ttu-id="7d16d-126"><xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro vykreslení položky v předchozím seznamu: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (pro základní křivky vyhlazení), a <xref:System.Drawing.Graphics.DrawBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d16d-126">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for drawing the items in the previous list: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (for cardinal splines), and <xref:System.Drawing.Graphics.DrawBezier%2A>.</span></span> <span data-ttu-id="7d16d-127">Každá z těchto metod je přetížena; To znamená jednotlivé metody podporují několik různých parametr seznamy.</span><span class="sxs-lookup"><span data-stu-id="7d16d-127">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="7d16d-128">Například jeden varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objekt a čtyři celá čísla, při jiné varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objektu a dvě <xref:System.Drawing.Point> objekty.</span><span class="sxs-lookup"><span data-stu-id="7d16d-128">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers, while another variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="7d16d-129">Metody pro kreslení čar, obdélníků a Bézierovy křivky mají množném čísle doprovodné metody, které kreslení několik položek v jediném volání: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, a <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d16d-129">The methods for drawing lines, rectangles, and Bézier splines have plural companion methods that draw several items in a single call: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, and <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span></span> <span data-ttu-id="7d16d-130">Také <xref:System.Drawing.Graphics.DrawCurve%2A> metoda obsahuje metodu doprovodné <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, že bodu křivky propojíte počáteční koncovému bodu křivky zavře.</span><span class="sxs-lookup"><span data-stu-id="7d16d-130">Also, the <xref:System.Drawing.Graphics.DrawCurve%2A> method has a companion method, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, that closes a curve by connecting the ending point of the curve to the starting point.</span></span>  
  
 <span data-ttu-id="7d16d-131">Všechny metody kreslení z <xref:System.Drawing.Graphics> třídy pracovní ve spojení s <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="7d16d-131">All of the drawing methods of the <xref:System.Drawing.Graphics> class work in conjunction with a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="7d16d-132">Kreslení nic, musíte vytvořit aspoň dva objekty: <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="7d16d-132">To draw anything, you must create at least two objects: a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="7d16d-133"><xref:System.Drawing.Pen> Ukládá atributy, jako například barvu položky, které se mají vykreslovat a šířku objektu.</span><span class="sxs-lookup"><span data-stu-id="7d16d-133">The <xref:System.Drawing.Pen> object stores attributes, such as line width and color, of the item to be drawn.</span></span> <span data-ttu-id="7d16d-134"><xref:System.Drawing.Pen> Objekt je předán jako jednoho z argumentů kreslení metodě.</span><span class="sxs-lookup"><span data-stu-id="7d16d-134">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the drawing method.</span></span> <span data-ttu-id="7d16d-135">Například jeden varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda obdrží <xref:System.Drawing.Pen> objekt a čtyři celá čísla, jak je znázorněno v následujícím příkladu, který vykreslí s šířky 100, výška 50 a levého horního rohu obdélníku (20, 10):</span><span class="sxs-lookup"><span data-stu-id="7d16d-135">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers as shown in the following example, which draws a rectangle with a width of 100, a height of 50 and an upper-left corner of (20, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="7d16d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d16d-136">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="7d16d-137">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="7d16d-137">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="7d16d-138">Postupy: vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="7d16d-138">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)