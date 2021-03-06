---
title: 'Postupy: Řazení dat v zobrazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 5c79261983fcf6200120bcfbf180d155aca3c3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556754"
---
# <a name="how-to-sort-data-in-a-view"></a>Postupy: Řazení dat v zobrazení
Tento příklad popisuje řazení dat v zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří jednoduchou <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obslužné rutiny události tlačítka obsahuje logiku seřadíte položky v <xref:System.Windows.Controls.ListBox> v sestupném pořadí. Můžete to provést, protože přidávání položek do <xref:System.Windows.Controls.ListBox> tímto způsobem přidá je do <xref:System.Windows.Controls.ItemCollection> z <xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.ItemCollection> je odvozena z <xref:System.Windows.Data.CollectionView> – třída. Pokud vytváříte vazbu vaše <xref:System.Windows.Controls.ListBox> do kolekce pomocí <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost, stejný postup můžete použít k seřazení.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Tak dlouho, dokud máte odkaz na objekt zobrazení, můžete použít stejný postup Seřadit obsah zobrazení jiné kolekce. Příklad toho, jak získat zobrazení, naleznete v části [získat výchozí zobrazení shromažďování dat](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Jiný příklad najdete v tématu [seřadit, rutina GridView sloupce při záhlaví po kliknutí na](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Další informace o zobrazení najdete v tématu vazbu na kolekce v [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Příklad toho, jak použít řazení logiku v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], najdete v části [řazení a skupinu dat pomocí zobrazení v jazyce XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [Řazení sloupce GridView při kliknutí na záhlaví](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
