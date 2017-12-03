---
title: "DomainUpDown – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="0891b-102">DomainUpDown – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0891b-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="0891b-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek je v podstatě kombinací textového pole a pár tlačítka pro přesun nahoru nebo dolů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0891b-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="0891b-104">Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu voleb.</span><span class="sxs-lookup"><span data-stu-id="0891b-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="0891b-105">Uživatele můžete vybrat řetězec, klikněte na tlačítka pro přesouvání v seznamu nahoru a dolů, stisknutím klávesy se šipkami nahoru a dolů nebo zadáním řetězec, který odpovídá položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0891b-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="0891b-106">Je možné použití tohoto ovládacího prvku pro výběr položek z abecedně seřazený seznam názvů.</span><span class="sxs-lookup"><span data-stu-id="0891b-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0891b-107">Seřadit seznamu, nastavte <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="0891b-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="0891b-108">Funkce tohoto ovládacího prvku je velmi podobný pole se seznamem nebo pole se seznamem, ale zabírají velmi málo místa.</span><span class="sxs-lookup"><span data-stu-id="0891b-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="0891b-109">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0891b-109">Key Properties</span></span>  
 <span data-ttu-id="0891b-110">Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="0891b-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="0891b-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž hodnoty text se zobrazí v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0891b-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="0891b-112">Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastaven na `false`, ovládacího prvku automaticky dokončení text, že uživatel nezadá a odpovídá hodnotě v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0891b-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="0891b-113">Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastaven na `true`, posouvání za poslední položky se dostanete na první položku v seznamu a naopak.</span><span class="sxs-lookup"><span data-stu-id="0891b-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="0891b-114">Klíče metody ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="0891b-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="0891b-115">Tento ovládací prvek zobrazí pouze textové řetězce.</span><span class="sxs-lookup"><span data-stu-id="0891b-115">This control displays only text strings.</span></span> <span data-ttu-id="0891b-116">Pokud chcete ovládacího prvku, který zobrazí číselné hodnoty, použijte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0891b-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="0891b-117">Další informace najdete v tématu [– Přehled ovládacího prvku NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0891b-117">For more information, see [NumericUpDown Control Overview](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0891b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0891b-118">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 [<span data-ttu-id="0891b-119">DomainUpDown – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="0891b-119">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)