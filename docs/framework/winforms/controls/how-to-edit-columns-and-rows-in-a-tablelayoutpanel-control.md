---
title: 'Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 763d5df6c49d45f7ee305f4a3be0a1f0a2539872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533504"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel
Můžete použít editor kolekce z <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, s názvem **styly řádku a sloupce** dialogové okno, chcete-li upravit řádků a sloupců pro vaše ovládací prvky.  
  
> [!NOTE]
>  Pokud chcete ovládacího prvku na více řádcích nebo sloupců, nastavte `RowSpan` a `ColumnSpan` vlastnosti na ovládací prvek. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Pokud chcete zarovnání ovládacího prvku v buňce nebo pokud chcete roztáhnout buňce ovládacího prvku, pomocí ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-edit-rows-and-columns"></a>Chcete-li upravit řádků a sloupců  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  Klikněte na tlačítko <xref:System.Windows.Forms.TableLayoutPanel> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **úpravy řádků a sloupců** otevřete  **Styly řádku a sloupce** dialogové okno. Vám může také klikněte pravým tlačítkem na <xref:System.Windows.Forms.TableLayoutPanel> řízení a vyberte **úpravy řádků a sloupců** z místní nabídky.  
  
3.  Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z **typ člena** rozevíracího seznamu.  
  
4.  Chcete-li přidat nebo odebrat řádky, vyberte **řádky** z **typ člena** rozevíracího seznamu.  
  
5.  Klikněte na tlačítko **přidat** tlačítko Přidat sloupce či řádku na konec **člen** seznamu.  
  
6.  Klikněte **vložit** tlačítko Přidat řádku nebo sloupce před aktuálně vybrané položky v seznamu.  
  
7.  Pokud přidáváte sloupce či řádku, vyberte **typ velikosti** pro nový řádek nebo sloupec. Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.  
  
8.  Chcete-li odebrat sloupce či řádku, klikněte na tlačítko **odebrat** tlačítko Odstranit aktuálně vybrané položky v **člen** seznamu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SizeType>  
 [Ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
