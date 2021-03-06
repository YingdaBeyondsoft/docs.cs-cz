---
title: 'Postupy: Převod obrázku BPM na obrázek PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: fd890c4f17b9759d37d7625526366034c664a71a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520783"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Postupy: Převod obrázku BPM na obrázek PNG
Často budete chtít převést z jedné bitové kopie souboru formátu do druhého. Můžete provést tento převod snadno voláním <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy a určení <xref:System.Drawing.Imaging.ImageFormat> pro formát souboru požadovanou image.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte obrázku Bpm na obrázek z typu a uloží obrázek ve formátu PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace Windows Forms.  
  
-   Odkaz na `System.Drawing.Imaging` oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Použití kodérů a dekodérů ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [Typy rastrových obrázků](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
