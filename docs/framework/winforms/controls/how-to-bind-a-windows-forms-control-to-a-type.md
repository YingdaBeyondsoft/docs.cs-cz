---
title: 'Postupy: Vázání ovládacího prvku Windows Forms k typu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 1130eba7b92ecb5adeba2df9601a31637823754e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530091"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Postupy: Vázání ovládacího prvku Windows Forms k typu
Při vytváření ovládacích prvků, které pracují s daty, někdy zjistíte, je potřeba vytvořit vazbu ovládacího prvku do typu, nikoli objekt. Tato situace nastane zejména v době návrhu, když data nemusí být k dispozici, ale vaše ovládací prvky vázané na data pořád potřebovat k zobrazení informací z veřejné rozhraní typu. Například může vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řízení k objektu vystavené webové služby a chcete <xref:System.Windows.Forms.DataGridView> ovládací prvek pro názvy vlastního typu označení její sloupce v době návrhu se členem.  
  
 Můžete snadno vytvořit vazbu ovládacího prvku s typem s <xref:System.Windows.Forms.BindingSource> součásti.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku do vlastního typu pomocí <xref:System.Windows.Forms.BindingSource> součásti. Když spustíte v příkladu, můžete si všimnout <xref:System.Windows.Forms.DataGridView> má označené sloupce, které odpovídají vlastnosti `Customer` objektu, než je ovládací prvek naplněný daty. V příkladu má tlačítko Přidat zákazníka k přidání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Po kliknutí na tlačítko Nový `Customer` objekt přidán do <xref:System.Windows.Forms.BindingSource>. Ve scénáři reálného může volání webové služby nebo jiného zdroje dat získat data.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)
