---
title: "ListView – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bda009beb429345d05aeba4e04f2ce1f07e627da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="listview-control-overview-windows-forms"></a><span data-ttu-id="b5ab3-102">ListView – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b5ab3-102">ListView Control Overview (Windows Forms)</span></span>
<span data-ttu-id="b5ab3-103">Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek zobrazí seznam položky s ikonami.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-103">The Windows Forms <xref:System.Windows.Forms.ListView> control displays a list of items with icons.</span></span> <span data-ttu-id="b5ab3-104">Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je v pravém podokně Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span> <span data-ttu-id="b5ab3-105">Ovládací prvek má čtyři režimy zobrazení: LargeIcon, SmallIcon, seznamu a podrobností.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-105">The control has four view modes: LargeIcon, SmallIcon, List, and Details.</span></span>  
  
## <a name="what-you-can-do-with-the-listview-control"></a><span data-ttu-id="b5ab3-106">Co můžete dělat pomocí ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="b5ab3-106">What You Can Do with the ListView Control</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5ab3-107">Další zobrazení režimu, dlaždice, je dostupná pouze na systémy Windows XP a operační systém Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-107">An additional view mode, Tile, is only available on Windows XP and the Windows Server 2003 operating system.</span></span> <span data-ttu-id="b5ab3-108">Další informace najdete v tématu [postupy: povolení zobrazení Tile v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b5ab3-108">For more information, see [How to: Enable Tile View in a Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="b5ab3-109">Režim LargeIcon zobrazí ikony. velké ikony vedle textu položky; Pokud ovládací prvek je dostatečně velké na to, zobrazí položky ve více sloupců.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-109">The LargeIcon mode displays large icons next to the item text; the items appear in multiple columns if the control is large enough.</span></span> <span data-ttu-id="b5ab3-110">Režim SmallIcon je stejný, s tím rozdílem, že se zobrazí ikony. Malé ikony.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-110">The SmallIcon mode is the same except that it displays small icons.</span></span> <span data-ttu-id="b5ab3-111">Režim seznamu zobrazí ikony. Malé ikony, ale je vždy v jeden sloupec.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-111">The List mode displays small icons but is always in a single column.</span></span> <span data-ttu-id="b5ab3-112">Podrobnosti o režimu zobrazí položky v více sloupců.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-112">The Details mode displays items in multiple columns.</span></span> <span data-ttu-id="b5ab3-113">Podrobnosti najdete v tématu [postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b5ab3-113">For details, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span> <span data-ttu-id="b5ab3-114">Režim zobrazení je dáno <xref:System.Windows.Forms.ListView.View%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-114">The view mode is determined by the <xref:System.Windows.Forms.ListView.View%2A> property.</span></span> <span data-ttu-id="b5ab3-115">Všechny režimy zobrazení můžete zobrazit obrázky ze seznamů obrázků.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-115">All of the view modes can display images from image lists.</span></span> <span data-ttu-id="b5ab3-116">Podrobnosti najdete v tématu [postupy: zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b5ab3-116">For details, see [How to: Display Icons for the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="b5ab3-117">Následující tabulka uvádí některé <xref:System.Windows.Forms.ListView> členy a zobrazení jsou platné v.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-117">The following table lists some of the <xref:System.Windows.Forms.ListView> members and the views they are valid in.</span></span>  
  
|<span data-ttu-id="b5ab3-118">Člen ListView</span><span class="sxs-lookup"><span data-stu-id="b5ab3-118">ListView member</span></span>|<span data-ttu-id="b5ab3-119">Zobrazit</span><span class="sxs-lookup"><span data-stu-id="b5ab3-119">View</span></span>|  
|---------------------|----------|  
|<span data-ttu-id="b5ab3-120"><xref:System.Windows.Forms.ListView.Alignment%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5ab3-120"><xref:System.Windows.Forms.ListView.Alignment%2A> property</span></span>|<span data-ttu-id="b5ab3-121"><xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.LargeIcon></span><span class="sxs-lookup"><span data-stu-id="b5ab3-121"><xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon></span></span>|  
|<span data-ttu-id="b5ab3-122"><xref:System.Windows.Forms.ListView.AutoArrange%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5ab3-122"><xref:System.Windows.Forms.ListView.AutoArrange%2A> property</span></span>|<span data-ttu-id="b5ab3-123"><xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.LargeIcon></span><span class="sxs-lookup"><span data-stu-id="b5ab3-123"><xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon></span></span>|  
|<span data-ttu-id="b5ab3-124"><xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="b5ab3-124"><xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> method</span></span>|<xref:System.Windows.Forms.View.Details>|  
|<span data-ttu-id="b5ab3-125"><xref:System.Windows.Forms.ListView.Columns%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5ab3-125"><xref:System.Windows.Forms.ListView.Columns%2A> property</span></span>|<span data-ttu-id="b5ab3-126"><xref:System.Windows.Forms.View.Details>nebo<xref:System.Windows.Forms.View.Tile></span><span class="sxs-lookup"><span data-stu-id="b5ab3-126"><xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.Tile></span></span>|  
|<span data-ttu-id="b5ab3-127"><xref:System.Windows.Forms.ListView.DrawSubItem>události</span><span class="sxs-lookup"><span data-stu-id="b5ab3-127"><xref:System.Windows.Forms.ListView.DrawSubItem> event</span></span>|<xref:System.Windows.Forms.View.Details>|  
|<span data-ttu-id="b5ab3-128"><xref:System.Windows.Forms.ListView.FindItemWithText%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="b5ab3-128"><xref:System.Windows.Forms.ListView.FindItemWithText%2A> method</span></span>|<span data-ttu-id="b5ab3-129"><xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, nebo<xref:System.Windows.Forms.View.Tile></span><span class="sxs-lookup"><span data-stu-id="b5ab3-129"><xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, or <xref:System.Windows.Forms.View.Tile></span></span>|  
|<span data-ttu-id="b5ab3-130"><xref:System.Windows.Forms.ListView.FindNearestItem%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="b5ab3-130"><xref:System.Windows.Forms.ListView.FindNearestItem%2A> method</span></span>|<span data-ttu-id="b5ab3-131"><xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.LargeIcon></span><span class="sxs-lookup"><span data-stu-id="b5ab3-131"><xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon></span></span>|  
|<span data-ttu-id="b5ab3-132"><xref:System.Windows.Forms.ListView.GetItemAt%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="b5ab3-132"><xref:System.Windows.Forms.ListView.GetItemAt%2A> method</span></span>|<span data-ttu-id="b5ab3-133"><xref:System.Windows.Forms.View.Details>nebo<xref:System.Windows.Forms.View.Tile></span><span class="sxs-lookup"><span data-stu-id="b5ab3-133"><xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.Tile></span></span>|  
|<span data-ttu-id="b5ab3-134"><xref:System.Windows.Forms.ListView.Groups%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5ab3-134"><xref:System.Windows.Forms.ListView.Groups%2A> property</span></span>|<span data-ttu-id="b5ab3-135">Všechna zobrazení s výjimkou<xref:System.Windows.Forms.View.List></span><span class="sxs-lookup"><span data-stu-id="b5ab3-135">All views except <xref:System.Windows.Forms.View.List></span></span>|  
|<span data-ttu-id="b5ab3-136"><xref:System.Windows.Forms.ListView.HeaderStyle%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5ab3-136"><xref:System.Windows.Forms.ListView.HeaderStyle%2A> property</span></span>|<span data-ttu-id="b5ab3-137"><xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-137"><xref:System.Windows.Forms.View.Details>.</span></span>|  
|<span data-ttu-id="b5ab3-138"><xref:System.Windows.Forms.ListView.InsertionMark%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5ab3-138"><xref:System.Windows.Forms.ListView.InsertionMark%2A> property</span></span>|<span data-ttu-id="b5ab3-139"><xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, nebo<xref:System.Windows.Forms.View.Tile></span><span class="sxs-lookup"><span data-stu-id="b5ab3-139"><xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, or <xref:System.Windows.Forms.View.Tile></span></span>|  
  
 <span data-ttu-id="b5ab3-140">Klíčové vlastnosti <xref:System.Windows.Forms.ListView> ovládací prvek je <xref:System.Windows.Forms.ListView.Items%2A>, který obsahuje položky zobrazené ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-140">The key property of the <xref:System.Windows.Forms.ListView> control is <xref:System.Windows.Forms.ListView.Items%2A>, which contains the items displayed by the control.</span></span> <span data-ttu-id="b5ab3-141"><xref:System.Windows.Forms.ListView.SelectedItems%2A> Vlastnost obsahuje kolekce položek v ovládacím prvku aktuálně vybranou.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-141">The <xref:System.Windows.Forms.ListView.SelectedItems%2A> property contains a collection of the items currently selected in the control.</span></span> <span data-ttu-id="b5ab3-142">Uživatel může vybrat více položek, například přetáhnout několik položek najednou do jiného ovládacího prvku, pokud <xref:System.Windows.Forms.ListView.MultiSelect%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-142">The user can select multiple items, for example to drag and drop several items at a time to another control, if the <xref:System.Windows.Forms.ListView.MultiSelect%2A> property is set to `true`.</span></span> <span data-ttu-id="b5ab3-143"><xref:System.Windows.Forms.ListView> Řízení zobrazíte zaškrtnutí políček vedle položky, když <xref:System.Windows.Forms.ListView.CheckBoxes%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-143">The <xref:System.Windows.Forms.ListView> control can display check boxes next to the items, if the <xref:System.Windows.Forms.ListView.CheckBoxes%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="b5ab3-144"><xref:System.Windows.Forms.ListView.Activation%2A> Vlastnost určuje, jaký typ akce uživatel musí přijmout aktivovat položku v seznamu: možnosti <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, a <xref:System.Windows.Forms.ItemActivation.TwoClick>.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-144">The <xref:System.Windows.Forms.ListView.Activation%2A> property determines what type of action the user must take to activate an item in the list: the options are <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, and <xref:System.Windows.Forms.ItemActivation.TwoClick>.</span></span> <span data-ttu-id="b5ab3-145"><xref:System.Windows.Forms.ItemActivation.OneClick>Aktivace vyžaduje jedním kliknutím aktivujte položky.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-145"><xref:System.Windows.Forms.ItemActivation.OneClick> activation requires a single click to activate the item.</span></span> <span data-ttu-id="b5ab3-146"><xref:System.Windows.Forms.ItemActivation.TwoClick>Aktivace vyžaduje, aby uživatel k dvakrát klikněte na panel aktivace položky; jedním kliknutím změní barvu textu položky.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-146"><xref:System.Windows.Forms.ItemActivation.TwoClick> activation requires the user to double-click to activate the item; a single click changes the color of the item text.</span></span> <span data-ttu-id="b5ab3-147"><xref:System.Windows.Forms.ItemActivation.Standard>Aktivace vyžaduje, aby uživatel k dvakrát klikněte na položku aktivovat, ale položka nezmění vzhled.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-147"><xref:System.Windows.Forms.ItemActivation.Standard> activation requires the user to double-click to activate an item, but the item does not change appearance.</span></span>  
  
 <span data-ttu-id="b5ab3-148"><xref:System.Windows.Forms.ListView> Řízení také podporuje vizuální styly a další funkce, které jsou k dispozici na platformě Windows XP, včetně seskupení, zobrazení tile a značky pro vložení.</span><span class="sxs-lookup"><span data-stu-id="b5ab3-148">The <xref:System.Windows.Forms.ListView> control also supports the visual styles and other features available on the Windows XP platform, including grouping, tile view, and insertion marks.</span></span> <span data-ttu-id="b5ab3-149">Další informace najdete v tématu [funkce systému Windows XP a Windows Forms – ovládací prvky](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).</span><span class="sxs-lookup"><span data-stu-id="b5ab3-149">For more information, see [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ab3-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5ab3-150">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 [<span data-ttu-id="b5ab3-151">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5ab3-151">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="b5ab3-152">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5ab3-152">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-153">Postupy: přidávání sloupců do ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5ab3-153">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-154">Postupy: zobrazení ikon pro Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5ab3-154">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-155">Postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5ab3-155">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-156">Postupy: vyberte položku v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="b5ab3-156">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-157">Postupy: seskupení položek v systému Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5ab3-157">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-158">Postupy: zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="b5ab3-158">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [<span data-ttu-id="b5ab3-159">Postupy: přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="b5ab3-159">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [<span data-ttu-id="b5ab3-160">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b5ab3-160">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="b5ab3-161">Postupy: vytváření více podokny uživatelského rozhraní s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5ab3-161">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)