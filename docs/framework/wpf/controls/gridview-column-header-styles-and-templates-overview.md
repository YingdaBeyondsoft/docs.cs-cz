---
title: GridView Styly záhlaví sloupců a přehled šablon
ms.date: 03/30/2017
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
ms.openlocfilehash: 28b4a64a6c79b226b1ff4b3bfcbf9a55b6d8df78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553868"
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView Styly záhlaví sloupců a přehled šablon
Tento přehled popisuje pořadí priorit pro vlastnosti, které můžete použít k přizpůsobení v záhlaví sloupce <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>Přizpůsobení záhlaví sloupce v GridView  
 Vlastnosti, které definují obsah, rozvržení a stylu záhlaví sloupce v <xref:System.Windows.Controls.GridView> jsou k dispozici v mnoha související třídy. Některé z těchto vlastností mají podobné funkce nebo stejné.  
  
 Řádky v tabulce zobrazit skupiny vlastností, které provádí stejnou funkci. Tyto vlastnosti můžete použít k přizpůsobení záhlaví sloupců v <xref:System.Windows.Controls.GridView>. Pořadí priorit pro souvisejících vlastností je zprava doleva, kde vlastnost ve sloupci nejvíce vpravo má nejvyšší prioritu. Například pokud <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> je nastavený na <xref:System.Windows.Controls.GridViewColumnHeader> objektu a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> je nastavený na přidruženého <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> přednost. V tomto scénáři <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> nemá žádný vliv.  
  
 **Souvisejících vlastností pro záhlaví sloupců v GridView**  
  
|||||  
|-|-|-|-|  
|**Třídy**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**Vlastnosti místní nabídky**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|Nelze použít|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ToolTip**<br /><br /> **Vlastnosti**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|Nelze použít|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**Šablona záhlaví**<br /><br /> **Vlastnosti**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**Vlastnosti stylu**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>pro **vlastnosti šablony záhlaví**, pokud jste nastavili šablonu a vlastnosti pro výběr šablony, přednost šablony vlastnost. Nastavíte-li například <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> vlastnosti, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost má přednost před.  
  
## <a name="see-also"></a>Viz také  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
