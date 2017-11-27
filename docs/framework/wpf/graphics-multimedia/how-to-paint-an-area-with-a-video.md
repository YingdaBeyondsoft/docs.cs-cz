---
title: "Postupy: Vykreslení videa v oblasti"
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
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 362231bbd1f4e95c260370a99233b7e8c2617ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a>Postupy: Vykreslení videa v oblasti
Tento příklad ukazuje, jak k vyplnění oblast s média. Jedním ze způsobů malovat oblast s média je používat <xref:System.Windows.Controls.MediaElement> společně s <xref:System.Windows.Media.VisualBrush>. Použít <xref:System.Windows.Controls.MediaElement> k načtení a přehrávání média a použít jej nastavit <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost <xref:System.Windows.Media.VisualBrush>. Pak můžete použít <xref:System.Windows.Media.VisualBrush> k vyplnění oblast s vložená média.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.VisualBrush> k vyplnění <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> ovládacího prvku pomocí video. Tento příklad nastaví <xref:System.Windows.Controls.MediaElement.IsMuted%2A> vlastnost <xref:System.Windows.Controls.MediaElement> k `true` tak, aby vyvolá žádné zvuku.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>Příklad  
 Protože <xref:System.Windows.Media.VisualBrush> dědí z <xref:System.Windows.Media.TileBrush> třída, poskytuje několik dlaždic režimy. Nastavením <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.VisualBrush> k <xref:System.Windows.Media.TileMode.Tile> a nastavením jeho <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost na hodnotu menší než k oblasti, která jsou vykreslování, můžete vytvořit vzorek za sebou.  
  
 Následující příklad je stejný jako předchozí příklad, vyjma toho, že <xref:System.Windows.Media.VisualBrush> generuje vzorek z videa.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Informace o tom, jak přidat do vaší aplikace, soubor s obsahem, jako je například soubor média, najdete v článku [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md). Když přidáte soubor média, je třeba přidat ji jako soubor obsahu, nikoli jako soubor prostředků.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.VisualBrush>  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Přehled TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [Multimediální – přehled](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)