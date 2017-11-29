---
title: "Postupy: Vytvoření tvaru použitím StreamGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caa97d0dbd4c847892e164ecb168349c38f7f271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="61bbc-102">Postupy: Vytvoření tvaru použitím StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="61bbc-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="61bbc-103"><xref:System.Windows.Media.StreamGeometry>šedé – alternativu, která umožňuje <xref:System.Windows.Media.PathGeometry> pro vytvoření geometrické obrazce.</span><span class="sxs-lookup"><span data-stu-id="61bbc-103"><xref:System.Windows.Media.StreamGeometry> is light-weight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="61bbc-104">Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete popisují komplexní geometry, ale nechcete, aby nároky na podporu vazby dat, animace nebo úpravy.</span><span class="sxs-lookup"><span data-stu-id="61bbc-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="61bbc-105">Například z důvodu jeho efektivitu <xref:System.Windows.Media.StreamGeometry> třída je vhodná pro popisující ozdobného prvku.</span><span class="sxs-lookup"><span data-stu-id="61bbc-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61bbc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="61bbc-106">Example</span></span>  
 <span data-ttu-id="61bbc-107">Následující příklad používá syntaxi atributů k vytvoření trojúhelníkovou <xref:System.Windows.Media.StreamGeometry> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61bbc-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="61bbc-108">Další informace o <xref:System.Windows.Media.StreamGeometry> atribut syntaxi najdete [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.</span><span class="sxs-lookup"><span data-stu-id="61bbc-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61bbc-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="61bbc-109">Example</span></span>  
 <span data-ttu-id="61bbc-110">Další příklad používá <xref:System.Windows.Media.StreamGeometry> k definování trojúhelník v kódu.</span><span class="sxs-lookup"><span data-stu-id="61bbc-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="61bbc-111">Nejprve v příkladu se vytváří <xref:System.Windows.Media.StreamGeometry>, pak získává <xref:System.Windows.Media.StreamGeometryContext> a používá ho k popisu trojúhelníku.</span><span class="sxs-lookup"><span data-stu-id="61bbc-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="61bbc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="61bbc-112">Example</span></span>  
 <span data-ttu-id="61bbc-113">Další příklad vytvoří metodu, která používá <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.StreamGeometryContext> k definování geometrické obrazce podle zadaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="61bbc-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="61bbc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="61bbc-114">See Also</span></span>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [<span data-ttu-id="61bbc-115">Vytvoření obrazce pomocí Objekt PathGeometry</span><span class="sxs-lookup"><span data-stu-id="61bbc-115">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [<span data-ttu-id="61bbc-116">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="61bbc-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)