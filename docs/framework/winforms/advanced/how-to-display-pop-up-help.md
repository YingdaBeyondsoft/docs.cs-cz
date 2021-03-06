---
title: 'Postupy: Zobrazení místní nápovědy'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: 5751bcdb9fe7a16138680f34a4fcc1760f85a1d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523871"
---
# <a name="how-to-display-pop-up-help"></a>Postupy: Zobrazení místní nápovědy
Je možné zobrazit nápovědu pro Windows Forms pomocí **pomoci** tlačítko, které se nachází na pravé straně záhlaví, přístupný prostřednictvím <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost. Tento typ zobrazení nápovědy je vhodné pro použití s dialogová okna. Dialogová okna zobrazí modálně (s <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda) mít potíže při vyvolání externí nápovědy systémy, protože modálních dialogových oken, musí se napřed zavřít fokus můžete přesune na další okno. Kromě toho používání **pomoci** tlačítko vyžaduje, aby byl žádné **minimalizaci** tlačítko nebo **Maximalizovat** tlačítko zobrazené v záhlaví. Jedná se o standardní dialogové konvenci, zatímco forms obvykle mají **minimalizaci** a **Maximalizovat** tlačítka.  
  
 Uvědomte si, že můžete také použít <xref:System.Windows.Forms.HelpProvider> součást propojení ovládacích prvků do souborů v systému nápovědy, i v případě, že jste implementovali automaticky otevírané okno nápovědy. Další informace najdete v tématu [poskytnutí nápovědy v aplikaci Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-pop-up-help"></a>K zobrazení místní nápovědy  
  
1.  Přetáhněte [HelpProvider –](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) součásti z panelu nástrojů do svého formuláře.  
  
     Bude se nacházejí na hlavním panelu v dolní části Návrhář formulářů Windows.  
  
2.  V okně vlastnosti nastavit <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost `true`. Tlačítko s otazníkem v ní bude se zobrazovat na pravé straně záhlaví formuláře.  
  
3.  Aby <xref:System.Windows.Forms.Form.HelpButton%2A> k zobrazení, formuláře <xref:System.Windows.Forms.Form.MinimizeBox%2A> a <xref:System.Windows.Forms.Form.MaximizeBox%2A> vlastnosti musí být nastavena na `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> vlastnost nastavena na hodnotu `true`a <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost na jednu z následujících hodnot: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> nebo <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Vyberte ovládací prvek, pro který chcete zobrazit nápovědu ve formuláři a nastavte řetězec nápovědy v okně Vlastnosti. Toto je řetězec text, který se zobrazí v okně podobná [popisek](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).  
  
5.  Stiskněte klávesu **F5**.  
  
6.  Stiskněte **pomoci** tlačítko v záhlaví okna a klikněte na ovládací prvek, na které můžete určit řetězec nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Nápověda ovládacího prvku pomocí ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrace uživatelské nápovědy v modelu Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
