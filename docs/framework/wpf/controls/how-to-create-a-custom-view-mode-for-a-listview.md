---
title: "Postupy: Vytvoření vlastního režimu zobrazení pro ListView"
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
helpviewer_keywords: ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c62bcb14f444490991b36dc21eb7676a67007906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="4584c-102">Postupy: Vytvoření vlastního režimu zobrazení pro ListView</span><span class="sxs-lookup"><span data-stu-id="4584c-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="4584c-103">Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Windows.Controls.ListView.View%2A> režim pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4584c-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4584c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4584c-104">Example</span></span>  
 <span data-ttu-id="4584c-105">Je nutné použít <xref:System.Windows.Controls.ViewBase> při vytváření vlastní zobrazení pro třídy <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4584c-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="4584c-106">Následující příklad ukazuje režim zobrazení, která je volána `PlainView`, který je odvozen z <xref:System.Windows.Controls.ViewBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="4584c-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="4584c-107">Chcete-li použít styl pro vlastní zobrazení, použijte <xref:System.Windows.Style> třídy.</span><span class="sxs-lookup"><span data-stu-id="4584c-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="4584c-108">V následujícím příkladu definuje <xref:System.Windows.Style> pro `PlainView` režimu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4584c-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="4584c-109">V předchozím příkladu, tento styl nastaven jako hodnotu <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> vlastnost, která je definována pro `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="4584c-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="4584c-110">Chcete-li definovat rozložení dat v režimu vlastní zobrazení, definovat <xref:System.Windows.DataTemplate> objektu.</span><span class="sxs-lookup"><span data-stu-id="4584c-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="4584c-111">V následujícím příkladu definuje <xref:System.Windows.DataTemplate> který lze použít k zobrazení dat v `PlainView` režimu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4584c-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="4584c-112">Následující příklad ukazuje, jak definovat <xref:System.Windows.ResourceKey> pro `PlainView` režim zobrazení, která používá <xref:System.Windows.DataTemplate> který je definován v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4584c-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="4584c-113">A <xref:System.Windows.Controls.ListView> řízení můžete použít vlastní zobrazení, pokud jste nastavili <xref:System.Windows.Controls.ListView.View%2A> vlastnost, která má klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="4584c-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="4584c-114">Následující příklad ukazuje, jak určit `PlainView` režim zobrazení pro <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="4584c-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="4584c-115">Kompletní příklad, najdete v části [ListView s ukázkou více zobrazení](http://go.microsoft.com/fwlink/?LinkID=160013).</span><span class="sxs-lookup"><span data-stu-id="4584c-115">For the complete sample, see [ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4584c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4584c-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="4584c-117">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="4584c-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="4584c-118">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="4584c-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="4584c-119">Rutina GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="4584c-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)