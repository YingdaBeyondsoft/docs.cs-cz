---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: d174492e380130ad35fbc20693e18416c48a50f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533832"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku
Ovládací prvky, které existují můžete přiřadit ve formuláři do ovládacího prvku nový kontejner.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>K přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
  
1.  Přetáhněte tři <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do formuláře.  
  
     Umístit je blízko sebe, ale nechte je nezarovnané.  
  
2.  V **sada nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládacího prvku.  
  
     Není přetáhněte ikonu do formuláře.  
  
3.  Přesunutí ukazatele myši blízko tří <xref:System.Windows.Forms.Button> ovládací prvky.  
  
     Ukazatel se změní na záměrný kříž s <xref:System.Windows.Forms.FlowLayoutPanel> řízení ikonu připojen.  
  
4.  Klikněte na tlačítko a podržte tlačítko myši.  
  
5.  Přetáhněte ukazatel myši k vykreslení obrys <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
6.  Kreslení obrys kolem tří <xref:System.Windows.Forms.Button> ovládací prvky.  
  
7.  Uvolnění tlačítka myši.  
  
     Tří <xref:System.Windows.Forms.Button> ovládací prvky jsou vloženy do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
