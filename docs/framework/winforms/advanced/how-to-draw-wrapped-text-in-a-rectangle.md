---
title: 'Postupy: Kreslení zalomeného textu do obdélníku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524970"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>Postupy: Kreslení zalomeného textu do obdélníku
Zalamování textu můžete kreslení v obdélníku pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížený metodu <xref:System.Drawing.Graphics> třídu, která přebírá <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.RectangleF> parametr. Budete taky používat <xref:System.Drawing.Brush> a <xref:System.Drawing.Font>.  
  
 Zalamování textu můžete také kreslení v obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížený metodu <xref:System.Windows.Forms.TextRenderer> , která má <xref:System.Drawing.Rectangle> a <xref:System.Windows.Forms.TextFormatFlags> parametr. Budete taky používat <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.  
  
 Následující obrázek ukazuje výstup textu vykresluje v obdélníku, při použití <xref:System.Drawing.Graphics.DrawString%2A> metoda.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Kreslení zalomeného textu do obdélníku pomocí GDI +  
  
1.  Použití <xref:System.Drawing.Graphics.DrawString%2A> metodu, předávání text, který má, přetížených <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> a <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Kreslení zalomeného textu do obdélníku pomocí GDI  
  
1.  Použití <xref:System.Windows.Forms.TextFormatFlags> hodnota výčtu Určuje text by měl být uzavřen s <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metodu, předávání text, který má, přetížených <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> a <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyžadovat v předchozích příkladech:  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Kreslení textu pomocí GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Postupy: Vytváření rodin písem a písem](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Postupy: Kreslení textu v určeném umístění](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
