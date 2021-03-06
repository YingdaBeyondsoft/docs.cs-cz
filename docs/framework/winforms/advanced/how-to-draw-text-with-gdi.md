---
title: 'Postupy: Kreslení textu pomocí GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: e18ff96ea97eb636de8ab73aaa094c07b10fd456
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522912"
---
# <a name="how-to-draw-text-with-gdi"></a>Postupy: Kreslení textu pomocí GDI
S <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metoda v <xref:System.Windows.Forms.TextRenderer> třída, dostanete [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funkce pro kreslení textu na formulář nebo ovládací prvek. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] vykreslování textu obvykle nabízí lepší výkon a přesnější text měření než [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> třídy nejsou podporovány pro tisk. Při tisku, vždy nutné použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak kreslení textu na více řádků v obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metoda.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 K vykreslení textu pomocí <xref:System.Windows.Forms.TextRenderer> třídy, musíte <xref:System.Drawing.IDeviceContext>, například <xref:System.Drawing.Graphics> a <xref:System.Drawing.Font>, umístění k vykreslení a barvy, ve kterém mají být vykresleny textu. Volitelně můžete zadat text formátování s použitím <xref:System.Windows.Forms.TextFormatFlags> výčtu.  
  
 Další informace o získání <xref:System.Drawing.Graphics>, najdete v části [postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Další informace o vytváření <xref:System.Drawing.Font>, najdete v části [postupy: vytváření rodin písem a písem](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu kódu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
