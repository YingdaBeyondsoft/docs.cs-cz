---
title: ErrorProvider – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: 2272220917f2d5adf15f1ba84a5d4c3d0ec07165
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528883"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider – přehled komponenty (Windows Forms)
Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) komponenta se používá k ověření vstupu uživatele na formulář nebo ovládací prvek. Se obvykle používá ve spojení s ověřování uživatelského vstupu ve formuláři, nebo zobrazení chyb v rámci datové sady. Poskytovatele chyba je lepší alternativou než zobrazení chybové zprávy v okně se zprávou, protože po se zavře okno se zprávou, chybová zpráva již není viditelný. <xref:System.Windows.Forms.ErrorProvider> Součást zobrazuje ikonu chyby (![ErrorProvider ikonu](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) vedle relevantní ovládací prvek, například textové pole; když uživatel umístí ukazatel myši nad ikona chyby popisek zobrazí, řetězec chybové zprávy.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 <xref:System.Windows.Forms.ErrorProvider> Klíčové vlastnosti součásti jsou <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, a <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Při použití <xref:System.Windows.Forms.ErrorProvider> součásti s ovládací prvky vázané na data, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> vlastnost musí být nastavená na odpovídajícího kontejneru (obvykle formuláře Windows), v pořadí pro součást zobrazíte ikonu chyby na formuláři. Při přidání komponentu v návrháři <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> je nastavena na ve formuláři; Pokud chcete přidat ovládací prvek v kódu, ho musíte nastavit sami.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Vlastnost lze nastavit ikonu Vlastní chybové místo výchozího. Když <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> je vlastnost nastavena, <xref:System.Windows.Forms.ErrorProvider> součást může zobrazovat chybové zprávy pro datovou sadu. Metodě klíče <xref:System.Windows.Forms.ErrorProvider> součást je <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda, která určuje řetězec chybové zprávy a kde by se měla objevit ikonu chyby.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> Součást neposkytuje integrovanou podporu pro usnadnění přístupu klientů. Chcete-li aplikace dostupné při použití této součásti, je nutné zadat mechanismus další, přístupný zpětnou vazbu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ErrorProvider>  
 [Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [Postupy: Zobrazení ikon chyb pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
