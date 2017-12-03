---
title: "Postupy: Použití vlastností roztažení na obsah viewbox"
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
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6e93c744a8d7c294556e80f0ac4bf1f973ea5c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a><span data-ttu-id="0ded1-102">Postupy: Použití vlastností roztažení na obsah viewbox</span><span class="sxs-lookup"><span data-stu-id="0ded1-102">How to: Apply Stretch Properties to the Contents of a Viewbox</span></span>
## <a name="example"></a><span data-ttu-id="0ded1-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ded1-103">Example</span></span>  
 <span data-ttu-id="0ded1-104">Tento příklad ukazuje, jak chcete-li změnit hodnotu <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> a <xref:System.Windows.Controls.Viewbox.Stretch%2A> vlastnosti <xref:System.Windows.Controls.Viewbox>.</span><span class="sxs-lookup"><span data-stu-id="0ded1-104">This example shows how to change the value of the <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> and <xref:System.Windows.Controls.Viewbox.Stretch%2A> properties of a <xref:System.Windows.Controls.Viewbox>.</span></span>  
  
 <span data-ttu-id="0ded1-105">V prvním příkladu používá [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.Viewbox> elementu.</span><span class="sxs-lookup"><span data-stu-id="0ded1-105">The first example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.Viewbox> element.</span></span> <span data-ttu-id="0ded1-106">Přiřadí <xref:System.Windows.FrameworkElement.MaxWidth%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400.</span><span class="sxs-lookup"><span data-stu-id="0ded1-106">It assigns a <xref:System.Windows.FrameworkElement.MaxWidth%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> of 400.</span></span> <span data-ttu-id="0ded1-107">Příklad vnoří <xref:System.Windows.Controls.Image> v rámci <xref:System.Windows.Controls.Viewbox>.</span><span class="sxs-lookup"><span data-stu-id="0ded1-107">The example nests an <xref:System.Windows.Controls.Image> element within the <xref:System.Windows.Controls.Viewbox>.</span></span> <span data-ttu-id="0ded1-108"><xref:System.Windows.Controls.Button>elementy, které odpovídají hodnot vlastností pro <xref:System.Windows.Controls.Viewbox.Stretch%2A> a <xref:System.Windows.Controls.StretchDirection> výčty manipulaci roztažení chování vnořeného <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="0ded1-108"><xref:System.Windows.Controls.Button> elements that correspond to the property values for the <xref:System.Windows.Controls.Viewbox.Stretch%2A> and <xref:System.Windows.Controls.StretchDirection> enumerations manipulate the stretching behavior of the nested <xref:System.Windows.Controls.Image>.</span></span>  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="0ded1-109">Následující popisovače souborů kódu <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události, předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad definuje.</span><span class="sxs-lookup"><span data-stu-id="0ded1-109">The following code-behind file handles the <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events that the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example defines.</span></span>  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0ded1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ded1-110">See Also</span></span>  
 <xref:System.Windows.Controls.Viewbox>  
 <xref:System.Windows.Media.Stretch>  
 <xref:System.Windows.Controls.StretchDirection>