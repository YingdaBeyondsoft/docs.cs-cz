---
title: 'Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 023973e7fa4ab1e8b802d8c7cd8abef8201ed720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532548"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře
*Přístupový klíč* je podrženého znaku v textu nabídky, položku nabídky nebo popisek ovládací prvek tlačítko. Umožňuje uživateli "tlačítko" stisknutím klávesy ALT v kombinaci s předdefinované přístupový klíč. Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Tisk" přidáte ampersand (&) před písmenem "P" způsobí písmenem "P" podtržení text tlačítka v době běhu. Uživatele můžete spustit příkaz přidružené tlačítko stisknutím ALT + P. Nemůže mít přístupový klíč pro ovládací prvek, který nemůže přijmout fokus.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Chcete-li vytvořit přístupový klíč pro ovládací prvek  
  
1.  V **vlastnosti** nastavte `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmeno, které bude přístupový klíč. Například pokud chcete nastavit písmenem "P" jako přístupový klíč, zadejte **& Tisk** v mřížce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Button>  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
