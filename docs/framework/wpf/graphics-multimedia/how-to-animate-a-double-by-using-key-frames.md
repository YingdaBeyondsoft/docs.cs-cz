---
title: 'Postupy: Animace dvojice použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 4adeb858ab1b69ef1b00f7bf3b6868dbcbbc4154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557430"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Postupy: Animace dvojice použitím klíčových snímků
Tento příklad ukazuje, jak animace hodnotu vlastnosti, která přijímá <xref:System.Double> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad přesune obdélníku napříč obrazovky. V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> u <xref:System.Windows.Shapes.Rectangle>. Tato animace, který se stále opakuje, používá tři klíčových snímků následujícím způsobem:  
  
1.  Během první tři sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> třídy přesuňte rámeček podél cesty konstantní rychlostí od počáteční pozice pro 500. Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> vytvořit hladký lineární přechod mezi hodnotami.  
  
2.  Na konci čtvrté second používá instanci <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> třídy najednou přesunout rámeček další místo. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> vytvoření nečekané přechodů mezi hodnotami. V tomto příkladu rámeček je počáteční pozice a potom najednou se objeví na 500 pozici.  
  
3.  Poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> třída k přesunutí rámeček zpátky na jeho počáteční pozice. Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu rámeček začne přesunutím pomalu a pak urychluje exponenciálnímu ke konci čas segmentu.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Z důvodu konzistence s další příklady animace verze kódu v tomto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt, který chcete použít <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternativně při použití jedné animace v kódu, je jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda místo použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
