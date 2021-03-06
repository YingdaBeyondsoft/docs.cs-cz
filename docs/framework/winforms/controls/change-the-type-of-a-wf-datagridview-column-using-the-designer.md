---
title: 'Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: b5d395575ac486307625fbdf2f236b6a588cc3ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527012"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít změnit typ sloupce, který již byl přidán do Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Můžete například změnit některé sloupce, které se generují automaticky po vytvoření vazby ovládacího prvku ke zdroji dat typy. To je užitečné, když má sloupců obsahujících cizí klíče na řádky v tabulce související tabulky, které můžete zobrazit. V takovém případě můžete nahradit sloupce textové pole, které zobrazují tyto cizí klíče s sloupce pole se seznamem, které zobrazují smysluplnější hodnoty z související tabulky.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Změna typu sloupce pomocí návrháře  
  
1.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a potom vyberte **upravit sloupce**.  
  
2.  Vyberte sloupce z **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, nastavte `ColumnType` vlastnost na nový typ sloupce.  
  
    > [!NOTE]
    >  `ColumnType` Je pouze pro návrh vlastnost, která určuje Třída reprezentující typ sloupce. Nejedná se o skutečný vlastnost definovaný ve třídě sloupec.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
