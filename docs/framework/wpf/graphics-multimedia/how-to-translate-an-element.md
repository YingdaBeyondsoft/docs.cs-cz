---
title: 'Postupy: Překlad elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 0089f294c54662d1ea4929ec25c08464072cbdde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561935"
---
# <a name="how-to-translate-an-element"></a>Postupy: Překlad elementu
Tento příklad ukazuje, jak převede (přesunout) element pomocí <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Třída je užitečná zejména při přesouvání elementů uvnitř panely, které nepodporují absolutní umístění. Například při použití <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu, můžete přesunout prvek v rámci <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel>.  
  
 Použití <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> nastavte velikost, v pixelech, chcete-li přesunout element podél osy x. Použití <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti a určit velikost, tak v pixelech, chcete-li přesunout element podél osy y. Nakonec použít <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.  
  
 Následující příklad používá <xref:System.Windows.Media.TranslateTransform> přesunout elementu 50 pixelů do vpravo a 50 pixelů.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
