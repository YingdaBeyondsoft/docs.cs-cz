---
title: "Použití vnořených grafických kontejnerů"
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
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10c5a1b077e4339f17093e5eb935416bb1ae3d1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-nested-graphics-containers"></a><span data-ttu-id="ef8bc-102">Použití vnořených grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="ef8bc-102">Using Nested Graphics Containers</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ef8bc-103">poskytuje kontejnery, které můžete použít k dočasnému nahradit nebo posílení součástí se stavem v <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-103"> provides containers that you can use to temporarily replace or augment part of the state in a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef8bc-104">Vytvořte kontejner voláním <xref:System.Drawing.Graphics.BeginContainer%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-104">You create a container by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef8bc-105">Můžete volat <xref:System.Drawing.Graphics.BeginContainer%2A> opakovaně k vytvoření vnořené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-105">You can call <xref:System.Drawing.Graphics.BeginContainer%2A> repeatedly to form nested containers.</span></span> <span data-ttu-id="ef8bc-106">Každé volání <xref:System.Drawing.Graphics.BeginContainer%2A> musí být spárována s volání <xref:System.Drawing.Graphics.EndContainer%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-106">Each call to <xref:System.Drawing.Graphics.BeginContainer%2A> must be paired with a call to <xref:System.Drawing.Graphics.EndContainer%2A>.</span></span>  
  
## <a name="transformations-in-nested-containers"></a><span data-ttu-id="ef8bc-107">Transformace ve vnořených kontejnery</span><span class="sxs-lookup"><span data-stu-id="ef8bc-107">Transformations in Nested Containers</span></span>  
 <span data-ttu-id="ef8bc-108">Následující příklad vytvoří <xref:System.Drawing.Graphics> objekt a kontejner, jež se <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-108">The following example creates a <xref:System.Drawing.Graphics> object and a container within that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef8bc-109">Světové transformace <xref:System.Drawing.Graphics> objektu se překlad 100 jednotky ve směru osy x a 80 jednotky ve směru osy y.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-109">The world transformation of the <xref:System.Drawing.Graphics> object is a translation 100 units in the x direction and 80 units in the y direction.</span></span> <span data-ttu-id="ef8bc-110">Světové transformace kontejneru je rotaci 30 stupňů.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-110">The world transformation of the container is a 30-degree rotation.</span></span> <span data-ttu-id="ef8bc-111">Kód provede volání `DrawRectangle(pen, -60, -30, 120, 60)` dvakrát.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-111">The code makes the call `DrawRectangle(pen, -60, -30, 120, 60)` twice.</span></span> <span data-ttu-id="ef8bc-112">První volání <xref:System.Drawing.Graphics.DrawRectangle%2A> uvnitř kontejneru; volání je mezi volání <xref:System.Drawing.Graphics.BeginContainer%2A> a <xref:System.Drawing.Graphics.EndContainer%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-112">The first call to <xref:System.Drawing.Graphics.DrawRectangle%2A> is inside the container; that is, the call is in between the calls to <xref:System.Drawing.Graphics.BeginContainer%2A> and <xref:System.Drawing.Graphics.EndContainer%2A>.</span></span> <span data-ttu-id="ef8bc-113">Druhé volání <xref:System.Drawing.Graphics.DrawRectangle%2A> po volání <xref:System.Drawing.Graphics.EndContainer%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-113">The second call to <xref:System.Drawing.Graphics.DrawRectangle%2A> is after the call to <xref:System.Drawing.Graphics.EndContainer%2A>.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 <span data-ttu-id="ef8bc-114">V předchozí kód rámeček čerpají z uvnitř kontejneru převede první podle Světové transformace kontejneru (otočení) a poté podle Světové transformace <xref:System.Drawing.Graphics> objektu (překlad).</span><span class="sxs-lookup"><span data-stu-id="ef8bc-114">In the preceding code, the rectangle drawn from inside the container is transformed first by the world transformation of the container (rotation) and then by the world transformation of the <xref:System.Drawing.Graphics> object (translation).</span></span> <span data-ttu-id="ef8bc-115">Rámeček čerpají z mimo kontejner je transformovat pouze Světové transformace <xref:System.Drawing.Graphics> objektu (překlad).</span><span class="sxs-lookup"><span data-stu-id="ef8bc-115">The rectangle drawn from outside the container is transformed only by the world transformation of the <xref:System.Drawing.Graphics> object (translation).</span></span> <span data-ttu-id="ef8bc-116">Následující obrázek znázorňuje dvou tvaru.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-116">The following illustration shows the two rectangles.</span></span>  
  
 <span data-ttu-id="ef8bc-117">![Vnořené kontejnery](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")</span><span class="sxs-lookup"><span data-stu-id="ef8bc-117">![Nested Containers](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")</span></span>  
  
## <a name="clipping-in-nested-containers"></a><span data-ttu-id="ef8bc-118">Výstřižek ve vnořené kontejnery</span><span class="sxs-lookup"><span data-stu-id="ef8bc-118">Clipping in Nested Containers</span></span>  
 <span data-ttu-id="ef8bc-119">Následující příklad ukazuje, jak vnořené kontejnery zpracování výstřižek oblasti.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-119">The following example demonstrates how nested containers handle clipping regions.</span></span> <span data-ttu-id="ef8bc-120">Kód vytvoří <xref:System.Drawing.Graphics> objekt a kontejner, jež se <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-120">The code creates a <xref:System.Drawing.Graphics> object and a container within that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef8bc-121">Výstřižek oblast <xref:System.Drawing.Graphics> objektu je obdélníku a oblast ořezu kontejneru elipsy.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-121">The clipping region of the <xref:System.Drawing.Graphics> object is a rectangle, and the clipping region of the container is an ellipse.</span></span> <span data-ttu-id="ef8bc-122">Kód vytvoří dvě volání <xref:System.Drawing.Graphics.DrawLine%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-122">The code makes two calls to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="ef8bc-123">První volání <xref:System.Drawing.Graphics.DrawLine%2A> je uvnitř kontejneru a druhé volání <xref:System.Drawing.Graphics.DrawLine%2A> je mimo kontejner (po volání <xref:System.Drawing.Graphics.EndContainer%2A>).</span><span class="sxs-lookup"><span data-stu-id="ef8bc-123">The first call to <xref:System.Drawing.Graphics.DrawLine%2A> is inside the container, and the second call to <xref:System.Drawing.Graphics.DrawLine%2A> is outside the container (after the call to <xref:System.Drawing.Graphics.EndContainer%2A>).</span></span> <span data-ttu-id="ef8bc-124">První řádek je oříznut podle průnik dvou výstřižek oblasti.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-124">The first line is clipped by the intersection of the two clipping regions.</span></span> <span data-ttu-id="ef8bc-125">Druhý řádek je oříznut pouze pomocí výstřižek obdélníkovou oblast <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-125">The second line is clipped only by the rectangular clipping region of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 <span data-ttu-id="ef8bc-126">Následující obrázek znázorňuje oříznutí dva řádky.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-126">The following illustration shows the two clipped lines.</span></span>  
  
 <span data-ttu-id="ef8bc-127">![Vnořený kontejner](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")</span><span class="sxs-lookup"><span data-stu-id="ef8bc-127">![Nested Container](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")</span></span>  
  
 <span data-ttu-id="ef8bc-128">Dva předchozí příklady ukazují, transformace a oblastí, výstřižek jsou kumulativní ve vnořené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-128">As the two preceding examples show, transformations and clipping regions are cumulative in nested containers.</span></span> <span data-ttu-id="ef8bc-129">Pokud nastavíte Světové transformace kontejneru a <xref:System.Drawing.Graphics> objektu obě transformace uplatní na položky čerpají z uvnitř kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-129">If you set the world transformations of the container and the <xref:System.Drawing.Graphics> object, both transformations will apply to items drawn from inside the container.</span></span> <span data-ttu-id="ef8bc-130">Transformace kontejneru bude použité první a transformace <xref:System.Drawing.Graphics> objektu se použije druhý.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-130">The transformation of the container will be applied first, and the transformation of the <xref:System.Drawing.Graphics> object will be applied second.</span></span> <span data-ttu-id="ef8bc-131">Pokud nastavíte oblasti výstřižek kontejneru a <xref:System.Drawing.Graphics> objektu položky čerpají z uvnitř kontejneru bude oříznut podle průnik dvou výstřižek oblasti.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-131">If you set the clipping regions of the container and the <xref:System.Drawing.Graphics> object, items drawn from inside the container will be clipped by the intersection of the two clipping regions.</span></span>  
  
## <a name="quality-settings-in-nested-containers"></a><span data-ttu-id="ef8bc-132">Nastavení kvality ve vnořené kontejnery</span><span class="sxs-lookup"><span data-stu-id="ef8bc-132">Quality Settings in Nested Containers</span></span>  
 <span data-ttu-id="ef8bc-133">Nastavení kvality (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>a podobně) ve vnořené kontejnery nejsou kumulativní; místo toho nastavení kvality kontejneru dočasně nahradit nastavení kvality <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-133">Quality settings (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>, and the like) in nested containers are not cumulative; rather, the quality settings of the container temporarily replace the quality settings of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef8bc-134">Když vytvoříte nový kontejner, nastavení kvality pro tento kontejner je nastaveno na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-134">When you create a new container, the quality settings for that container are set to default values.</span></span> <span data-ttu-id="ef8bc-135">Předpokládejme například, že máte <xref:System.Drawing.Graphics> objekt s režim vyhlazování <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-135">For example, suppose you have a <xref:System.Drawing.Graphics> object with a smoothing mode of <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>.</span></span> <span data-ttu-id="ef8bc-136">Když vytvoříte kontejner, režim vyhlazování uvnitř kontejneru je výchozí režim vyhlazování.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-136">When you create a container, the smoothing mode inside the container is the default smoothing mode.</span></span> <span data-ttu-id="ef8bc-137">Můžete nastavit režim vyhlazování kontejneru a všechny položky čerpají z uvnitř kontejneru budou vykreslovat podle režim, který nastavíte.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-137">You are free to set the smoothing mode of the container, and any items drawn from inside the container will be drawn according to the mode you set.</span></span> <span data-ttu-id="ef8bc-138">Položky, které jsou vykreslovány po zavolání <xref:System.Drawing.Graphics.EndContainer%2A> budou vykreslovat podle režim vyhlazování (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>), který byl na místě před volání <xref:System.Drawing.Graphics.BeginContainer%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-138">Items drawn after the call to <xref:System.Drawing.Graphics.EndContainer%2A> will be drawn according to the smoothing mode (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) that was in place before the call to <xref:System.Drawing.Graphics.BeginContainer%2A>.</span></span>  
  
## <a name="several-layers-of-nested-containers"></a><span data-ttu-id="ef8bc-139">Několik vrstev vnořené kontejnery</span><span class="sxs-lookup"><span data-stu-id="ef8bc-139">Several Layers of Nested Containers</span></span>  
 <span data-ttu-id="ef8bc-140">Nejste omezený na jeden kontejner v <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-140">You are not limited to one container in a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef8bc-141">Můžete vytvořit pořadí kontejnerů, každé vnořené v předchozím a můžete zadat Světové transformace, oblast ořezu a nastavení kvality každého z těchto vnořené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-141">You can create a sequence of containers, each nested in the preceding, and you can specify the world transformation, clipping region, and quality settings of each of those nested containers.</span></span> <span data-ttu-id="ef8bc-142">Pokud z kontejneru nejvnitřnější kreslení metodu lze volat transformace se použijí v pořadí, počínaje nejvnitřnější kontejneru a konče nejkrajnější kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-142">If you call a drawing method from inside the innermost container, the transformations will be applied in order, starting with the innermost container and ending with the outermost container.</span></span> <span data-ttu-id="ef8bc-143">Položky čerpají z uvnitř kontejneru nejvnitřnější bude oříznut průsečíkem všech oblastech výstřižek.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-143">Items drawn from inside the innermost container will be clipped by the intersection of all the clipping regions.</span></span>  
  
 <span data-ttu-id="ef8bc-144">Následující příklad vytvoří <xref:System.Drawing.Graphics> objektu a nastaví její Rady pro vykreslování textu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-144">The following example creates a <xref:System.Drawing.Graphics> object and sets its text rendering hint to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>.</span></span> <span data-ttu-id="ef8bc-145">Kód vytvoří dvě kontejnery, jeden vnořených ve druhé.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-145">The code creates two containers, one nested within the other.</span></span> <span data-ttu-id="ef8bc-146">Rady pro vykreslování textu vnější kontejneru je nastaven na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, a Rady pro vykreslování textu vnitřní kontejneru je nastavena na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-146">The text rendering hint of the outer container is set to <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, and the text rendering hint of the inner container is set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>.</span></span> <span data-ttu-id="ef8bc-147">Kód nevykresluje tři řetězce: jedné z kontejneru vnitřní, jeden z vnějšího kontejneru a jedné z <xref:System.Drawing.Graphics> samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-147">The code draws three strings: one from the inner container, one from the outer container, and one from the <xref:System.Drawing.Graphics> object itself.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 <span data-ttu-id="ef8bc-148">Následující obrázek znázorňuje tři řetězce.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-148">The following illustration shows the three strings.</span></span> <span data-ttu-id="ef8bc-149">Řetězce vykreslovat z kontejneru vnitřní a <xref:System.Drawing.Graphics> podle vyhlazení jsou vyhlazené objektu.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-149">The strings drawn from the inner container and from the <xref:System.Drawing.Graphics> object are smoothed by antialiasing.</span></span> <span data-ttu-id="ef8bc-150">Řetězec čerpají z kontejneru vnější není vyhlazené podle vyhlazení, protože <xref:System.Drawing.Graphics.TextRenderingHint%2A> je nastavena na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.</span><span class="sxs-lookup"><span data-stu-id="ef8bc-150">The string drawn from the outer container is not smoothed by antialiasing because the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property is set to <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.</span></span>  
  
 <span data-ttu-id="ef8bc-151">![Vnořené kontejnery](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")</span><span class="sxs-lookup"><span data-stu-id="ef8bc-151">![Nested Containers](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8bc-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef8bc-152">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 [<span data-ttu-id="ef8bc-153">Správa stavu grafického objektu</span><span class="sxs-lookup"><span data-stu-id="ef8bc-153">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)