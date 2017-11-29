---
title: "RichTextBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4278f569a789ca6e8466e0b8e71557446b63955e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="richtextbox-control-overview-windows-forms"></a><span data-ttu-id="dafd5-102">RichTextBox – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="dafd5-102">RichTextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="dafd5-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> řízení se používá k zobrazení, zadávání a manipulace s nimi formátování textu.</span><span class="sxs-lookup"><span data-stu-id="dafd5-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="dafd5-104"><xref:System.Windows.Forms.RichTextBox> Ovládací prvek provádí všechno, co <xref:System.Windows.Forms.TextBox> ovládací prvek provádí, ale můžete také zobrazit písma, barvy a odkazy; zatížení text a vložené obrázky ze souboru; a najít zadané znaky.</span><span class="sxs-lookup"><span data-stu-id="dafd5-104">The <xref:System.Windows.Forms.RichTextBox> control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; and find specified characters.</span></span> <span data-ttu-id="dafd5-105"><xref:System.Windows.Forms.RichTextBox> Řízení se obvykle používá k poskytování manipulaci s textem a zobrazení funkce podobná zpracování textu aplikace, jako je například Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="dafd5-105">The <xref:System.Windows.Forms.RichTextBox> control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="dafd5-106">Jako <xref:System.Windows.Forms.TextBox> ovládací prvek, <xref:System.Windows.Forms.RichTextBox> ovládací prvek může zobrazovat posuvníky; ale na rozdíl od <xref:System.Windows.Forms.TextBox> řízení, jeho výchozí nastavení je pro zobrazení vodorovného a svislého posuvníky podle potřeby a má scrollbar další nastavení.</span><span class="sxs-lookup"><span data-stu-id="dafd5-106">Like the <xref:System.Windows.Forms.TextBox> control, the <xref:System.Windows.Forms.RichTextBox> control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, its default setting is to display both horizontal and vertical scrollbars as needed, and it has additional scrollbar settings.</span></span>  
  
## <a name="working-with-the-richtextbox-control"></a><span data-ttu-id="dafd5-107">Práce s ovládacím prvkem RichTextBox</span><span class="sxs-lookup"><span data-stu-id="dafd5-107">Working with the RichTextBox Control</span></span>  
 <span data-ttu-id="dafd5-108">Stejně jako u <xref:System.Windows.Forms.TextBox> ovládací prvek, text zobrazený nastaven <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dafd5-108">As with the <xref:System.Windows.Forms.TextBox> control, the text displayed is set by the <xref:System.Windows.Forms.RichTextBox.Text%2A> property.</span></span> <span data-ttu-id="dafd5-109"><xref:System.Windows.Forms.RichTextBox> Řízení má mnoho vlastností k formátování textu.</span><span class="sxs-lookup"><span data-stu-id="dafd5-109">The <xref:System.Windows.Forms.RichTextBox> control has numerous properties to format text.</span></span> <span data-ttu-id="dafd5-110">Podrobnosti o těchto vlastnostech najdete v tématu [postupy: nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) a [postupy: nastavení odsazení, Hanging odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox ](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md).</span><span class="sxs-lookup"><span data-stu-id="dafd5-110">For details on these properties, see [How to: Set Font Attributes for the Windows Forms RichTextBox Control](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) and [How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md).</span></span> <span data-ttu-id="dafd5-111">K práci se soubory, <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> a <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody můžete zobrazit a zápis víc formáty souborů, včetně prostý text, prostý text v kódu Unicode a RTF (RICH Text Format).</span><span class="sxs-lookup"><span data-stu-id="dafd5-111">To manipulate files, the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> and <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> methods can display and write multiple file formats including plain text, Unicode plain text, and Rich Text Format (RTF).</span></span> <span data-ttu-id="dafd5-112">Formáty možné souborů jsou uvedeny v <xref:System.Windows.Forms.RichTextBoxStreamType>.</span><span class="sxs-lookup"><span data-stu-id="dafd5-112">The possible file formats are listed in <xref:System.Windows.Forms.RichTextBoxStreamType>.</span></span> <span data-ttu-id="dafd5-113">Můžete použít <xref:System.Windows.Forms.RichTextBox.Find%2A> metody k vyhledání řetězců textu nebo konkrétní znaků.</span><span class="sxs-lookup"><span data-stu-id="dafd5-113">You can use the <xref:System.Windows.Forms.RichTextBox.Find%2A> method to find strings of text or specific characters.</span></span>  
  
 <span data-ttu-id="dafd5-114">Můžete také použít <xref:System.Windows.Forms.RichTextBox> řízení pro odkazy ve stylu webového nastavením <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> vlastnost `true` a psaní kódu pro zpracování <xref:System.Windows.Forms.RichTextBox.LinkClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="dafd5-114">You can also use a <xref:System.Windows.Forms.RichTextBox> control for Web-style links by setting the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property to `true` and writing code to handle the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event.</span></span> <span data-ttu-id="dafd5-115">Další informace najdete v tématu [postupy: zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md).</span><span class="sxs-lookup"><span data-stu-id="dafd5-115">For more information, see [How to: Display Web-Style Links with the Windows Forms RichTextBox Control](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md).</span></span> <span data-ttu-id="dafd5-116">Uživatele můžete zabránit manipulaci s některé nebo všechny textu v ovládacím prvku nastavením <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="dafd5-116">You can prevent the user from manipulating some or all of the text in the control by setting the <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="dafd5-117">Můžete vrátit zpět a vrátit většinu operací upravit v <xref:System.Windows.Forms.RichTextBox> řízení voláním <xref:System.Windows.Forms.TextBoxBase.Undo%2A> a <xref:System.Windows.Forms.RichTextBox.Redo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dafd5-117">You can undo and redo most edit operations in a <xref:System.Windows.Forms.RichTextBox> control by calling the <xref:System.Windows.Forms.TextBoxBase.Undo%2A> and <xref:System.Windows.Forms.RichTextBox.Redo%2A> methods.</span></span> <span data-ttu-id="dafd5-118"><xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Metoda umožňuje určit, zda uživatel zrušila poslední operace můžete provádět znovu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dafd5-118">The <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> method enables you to determine whether the last operation the user has undone can be reapplied to the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafd5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="dafd5-119">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="dafd5-120">RichTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="dafd5-120">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="dafd5-121">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="dafd5-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)