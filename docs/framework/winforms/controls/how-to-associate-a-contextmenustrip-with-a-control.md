---
title: 'Postupy: Přidružení prvku ContextMenuStrip k ovládacímu prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 4014324d83e4de634ff7b42204d50fa11dff7ea3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526407"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Postupy: Přidružení prvku ContextMenuStrip k ovládacímu prvku
Po vytvoření ovládacích prvků a místní nabídky, použijte následující postupy k zobrazení dané místní nabídky po kliknutí pravým tlačítkem ovládací prvek. Tyto postupy přidružit <xref:System.Windows.Forms.ContextMenuStrip> s formuláři Windows a <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Chcete-li přidružení prvku ContextMenuStrip k formuláři Windows  
  
1.  Nastavte <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost na název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Chcete-li přidružení prvku ContextMenuStrip k ovládacího prvku ToolStrip  
  
1.  Nastavte ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost na název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří formuláře Windows a <xref:System.Windows.Forms.ToolStrip>a přidruží jiné <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku pomocí každého z nich.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Postupy: Přidání položek nabídky do ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [Ovládací prvek ContextMenuStrip](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
