---
title: "Virtuální režim v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10c6afbcde22a82e6227ce1d95d57749bee1a88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d0a68-102">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d0a68-102">Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d0a68-103">Virtuální režim, můžete spravovat interakce mezi <xref:System.Windows.Forms.DataGridView> řízení a vlastní datové mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d0a68-103">With virtual mode, you can manage the interaction between the <xref:System.Windows.Forms.DataGridView> control and a custom data cache.</span></span> <span data-ttu-id="d0a68-104">Chcete-li implementovat virtuální režim, nastavte <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a zpracovat jeden nebo více událostí, které jsou popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d0a68-104">To implement virtual mode, set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and handle one or more of the events described in this topic.</span></span> <span data-ttu-id="d0a68-105">Obvykle bude zpracovávat alespoň `CellValueNeeded` událost, která umožňuje vzhledu ovládacího prvku hodnot v datové mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d0a68-105">You will typically handle at least the `CellValueNeeded` event, which enables the control look up values in the data cache.</span></span>  
  
## <a name="bound-mode-and-virtual-mode"></a><span data-ttu-id="d0a68-106">Vázané režim a virtuální režim</span><span class="sxs-lookup"><span data-stu-id="d0a68-106">Bound Mode and Virtual Mode</span></span>  
 <span data-ttu-id="d0a68-107">Virtuální režim je nutné pouze v případě potřeby k doplnění nebo nahrazení vázané režimu.</span><span class="sxs-lookup"><span data-stu-id="d0a68-107">Virtual mode is necessary only when you need to supplement or replace bound mode.</span></span> <span data-ttu-id="d0a68-108">V vázané režimu, můžete nastavit <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost a ovládací prvek automaticky načte data ze zadaného zdroje a odešle uživatel změní na jiné místo.</span><span class="sxs-lookup"><span data-stu-id="d0a68-108">In bound mode, you set the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property and the control automatically loads the data from the specified source and submits user changes back to it.</span></span> <span data-ttu-id="d0a68-109">Můžete řídit, které vázaných sloupců se zobrazují a zdroji dat, samotné obvykle zpracovává operace, jako je například řazení.</span><span class="sxs-lookup"><span data-stu-id="d0a68-109">You can control which of the bound columns are displayed, and the data source itself typically handles operations such as sorting.</span></span>  
  
## <a name="supplementing-bound-mode"></a><span data-ttu-id="d0a68-110">Dodávání vázané režimu</span><span class="sxs-lookup"><span data-stu-id="d0a68-110">Supplementing Bound Mode</span></span>  
 <span data-ttu-id="d0a68-111">Vázané režimu lze rozšířit pomocí zobrazení nevázaných sloupců společně s vázané sloupce.</span><span class="sxs-lookup"><span data-stu-id="d0a68-111">You can supplement bound mode by displaying unbound columns along with the bound columns.</span></span> <span data-ttu-id="d0a68-112">To se někdy označuje jako "smíšený režim" a jsou užitečné pro zobrazení akce, jako je počítaných hodnot nebo uživatelského rozhraní (UI) ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d0a68-112">This is sometimes called "mixed mode" and is useful for displaying things like calculated values or user-interface (UI) controls.</span></span>  
  
 <span data-ttu-id="d0a68-113">Protože nevázaných sloupců je mimo zdroj dat, jsou ignorovány ve zdroji dat operace řazení.</span><span class="sxs-lookup"><span data-stu-id="d0a68-113">Because unbound columns are outside the data source, they are ignored by the data source's sorting operations.</span></span> <span data-ttu-id="d0a68-114">Proto když povolíte řazení ve smíšeném režimu, musí spravovat nepřipojená data v místní mezipaměti a implementace virtuálního režimu umožníte <xref:System.Windows.Forms.DataGridView> řízení pracovat s ním.</span><span class="sxs-lookup"><span data-stu-id="d0a68-114">Therefore, when you enable sorting in mixed mode, you must manage the unbound data in a local cache and implement virtual mode to let the <xref:System.Windows.Forms.DataGridView> control interact with it.</span></span>  
  
 <span data-ttu-id="d0a68-115">Další informace o používání virtuálních režimu zachování hodnoty v nevázaných sloupců, podívejte se na příklady v <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> třídy referenční témata.</span><span class="sxs-lookup"><span data-stu-id="d0a68-115">For more information about using virtual mode to maintain the values in unbound columns, see the examples in the <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> property and <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> class reference topics.</span></span>  
  
## <a name="replacing-bound-mode"></a><span data-ttu-id="d0a68-116">Nahrazení vázané režimu</span><span class="sxs-lookup"><span data-stu-id="d0a68-116">Replacing Bound Mode</span></span>  
 <span data-ttu-id="d0a68-117">Pokud vázané režim nesplňuje vašim požadavkům na výkon, můžete spravovat všechna vaše data v vlastní mezipaměti prostřednictvím obslužné rutiny událostí Virtuální režim.</span><span class="sxs-lookup"><span data-stu-id="d0a68-117">If bound mode does not meet your performance needs, you can manage all your data in a custom cache through virtual-mode event handlers.</span></span> <span data-ttu-id="d0a68-118">Můžete například použít virtuální režim k implementaci dat za běhu načítání mechanismus, který načte jenom tolik dat z databáze síťových, jako je nezbytné k zajištění optimálního výkonu.</span><span class="sxs-lookup"><span data-stu-id="d0a68-118">For example, you can use virtual mode to implement a just-in-time data loading mechanism that retrieves only as much data from a networked database as is necessary for optimal performance.</span></span> <span data-ttu-id="d0a68-119">Tento scénář je zvláště užitečná při práci s velkými objemy dat přes pomalé připojení k síti nebo se klientské počítače, které mají omezené množství paměti RAM nebo úložný prostor.</span><span class="sxs-lookup"><span data-stu-id="d0a68-119">This scenario is particularly useful when working with large amounts of data over a slow network connection or with client machines that have a limited amount of RAM or storage space.</span></span>  
  
 <span data-ttu-id="d0a68-120">Další informace o používání virtuální režim ve scénáři za běhu, najdete v části [implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="d0a68-120">For more information about using virtual mode in a just-in-time scenario, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="virtual-mode-events"></a><span data-ttu-id="d0a68-121">Virtuální režim události</span><span class="sxs-lookup"><span data-stu-id="d0a68-121">Virtual-Mode Events</span></span>  
 <span data-ttu-id="d0a68-122">Pokud vaše data jsou jen pro čtení, `CellValueNeeded` události může být pouze událost, budete muset zpracovat.</span><span class="sxs-lookup"><span data-stu-id="d0a68-122">If your data is read-only, the `CellValueNeeded` event may be the only event you will need to handle.</span></span> <span data-ttu-id="d0a68-123">Další virtuální režim události umožňují povolit určitých funkcí jako uživatelské úpravy, řádek přidání a odstranění a transakce na úrovni řádků.</span><span class="sxs-lookup"><span data-stu-id="d0a68-123">Additional virtual-mode events let you enable specific functionality like user edits, row addition and deletion, and row-level transactions.</span></span>  
  
 <span data-ttu-id="d0a68-124">Některé standardní <xref:System.Windows.Forms.DataGridView> události (například události, které dojít, když uživatelé přidat nebo odstranit řádky nebo pokud buňka hodnoty jsou úpravy, analyzovat, ověřit nebo naformátovaný) jsou užitečné v virtuální režim také.</span><span class="sxs-lookup"><span data-stu-id="d0a68-124">Some standard <xref:System.Windows.Forms.DataGridView> events (such as events that occur when users add or delete rows, or when cell values are edited, parsed, validated, or formatted) are useful in virtual mode, as well.</span></span> <span data-ttu-id="d0a68-125">Můžete také zpracovat události, které umožňují udržovat hodnoty, které obvykle nejsou uložené v vázaný datový zdroj, například buňky text popisku, buňky a text chyby řádek, buňky a řádek místní nabídky dat a dat výšku řádku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-125">You can also handle events that let you maintain values not typically stored in a bound data source, such as cell ToolTip text, cell and row error text, cell and row shortcut menu data, and row height data.</span></span>  
  
 <span data-ttu-id="d0a68-126">Další informace o implementace virtuálního režimu ke správě pro čtení a zápis dat v rozsahu, potvrdit nízkoúrovňové najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0a68-126">For more information about implementing virtual mode to manage read/write data with a row-level commit scope, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="d0a68-127">Příklad, který implementuje virtuálního režimu s obor potvrzení úrovni buněk, naleznete v části <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost referenční téma.</span><span class="sxs-lookup"><span data-stu-id="d0a68-127">For an example that implements virtual mode with a cell-level commit scope, see the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property reference topic.</span></span>  
  
 <span data-ttu-id="d0a68-128">Proběhne pouze když <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="d0a68-128">The following events occur only when the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property is set to `true`.</span></span>  
  
|<span data-ttu-id="d0a68-129">Událost</span><span class="sxs-lookup"><span data-stu-id="d0a68-129">Event</span></span>|<span data-ttu-id="d0a68-130">Popis</span><span class="sxs-lookup"><span data-stu-id="d0a68-130">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|<span data-ttu-id="d0a68-131">Používá k načtení hodnoty buňky z mezipaměť dat pro zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-131">Used by the control to retrieve a cell value from the data cache for display.</span></span> <span data-ttu-id="d0a68-132">K této události dochází pouze pro buněk v nevázaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="d0a68-132">This event occurs only for cells in unbound columns.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|<span data-ttu-id="d0a68-133">Potvrzení uživatelský vstup pro buňku mezipaměť dat používá ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-133">Used by the control to commit user input for a cell to the data cache.</span></span> <span data-ttu-id="d0a68-134">K této události dochází pouze pro buněk v nevázaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="d0a68-134">This event occurs only for cells in unbound columns.</span></span><br /><br /> <span data-ttu-id="d0a68-135">Volání <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metoda při změně hodnotu uloženou v mezipaměti mimo <xref:System.Windows.Forms.DataGridView.CellValuePushed> obslužné rutiny události, ujistěte se, že je aktuální hodnota nezobrazí v ovládacím prvku a použít všechny režimy Automatická změna velikosti aktuálně v platnost.</span><span class="sxs-lookup"><span data-stu-id="d0a68-135">Call the <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> method when changing a cached value outside of a <xref:System.Windows.Forms.DataGridView.CellValuePushed> event handler to ensure that the current value is displayed in the control and to apply any automatic sizing modes currently in effect.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|<span data-ttu-id="d0a68-136">Pomocí ovládacího prvku je třeba nový řádek v datové mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d0a68-136">Used by the control to indicate the need for a new row in the data cache.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|<span data-ttu-id="d0a68-137">Ovládací prvek používá k určení, zda má řádek všechny nepotvrzené změny.</span><span class="sxs-lookup"><span data-stu-id="d0a68-137">Used by the control to determine whether a row has any uncommitted changes.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|<span data-ttu-id="d0a68-138">Používá k označení, že řádek by měl vrátit se do své mezipaměti hodnoty ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-138">Used by the control to indicate that a row should revert to its cached values.</span></span>|  
  
 <span data-ttu-id="d0a68-139">Tyto události jsou užitečné v virtuální režim, ale je možné bez ohledu na to <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d0a68-139">The following events are useful in virtual mode, but can be used regardless of the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property setting.</span></span>  
  
|<span data-ttu-id="d0a68-140">Události</span><span class="sxs-lookup"><span data-stu-id="d0a68-140">Events</span></span>|<span data-ttu-id="d0a68-141">Popis</span><span class="sxs-lookup"><span data-stu-id="d0a68-141">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|<span data-ttu-id="d0a68-142">Používá ovládacího prvku označíte, když jsou odstraněných řádků nebo přidané, když necháte aktualizovat mezipaměť dat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="d0a68-142">Used by the control to indicate when rows are deleted or added, letting you update the data cache accordingly.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|<span data-ttu-id="d0a68-143">Používá k zobrazení a k analýze a ověření vstupu uživatele do formátu hodnot v buňkách ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-143">Used by the control to format cell values for display and to parse and validate user input.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|<span data-ttu-id="d0a68-144">Ovládací prvek používají k načítání text popisu tlačítka buňky při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`.</span><span class="sxs-lookup"><span data-stu-id="d0a68-144">Used by the control to retrieve cell ToolTip text when the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property is set or the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property is `true`.</span></span><br /><br /> <span data-ttu-id="d0a68-145">Popisy tlačítek buněk se zobrazí pouze tehdy, když <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> hodnota vlastnosti je `true`.</span><span class="sxs-lookup"><span data-stu-id="d0a68-145">Cell ToolTips are displayed only when the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property value is `true`.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|<span data-ttu-id="d0a68-146">Ovládací prvek používají k načítání buňku nebo řádek text chyby při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`.</span><span class="sxs-lookup"><span data-stu-id="d0a68-146">Used by the control to retrieve cell or row error text when the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property is set or the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property is `true`.</span></span><br /><br /> <span data-ttu-id="d0a68-147">Volání <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> metoda nebo <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> metoda při změně buňku nebo řádek text chyby zajistit, že je aktuální hodnota zobrazena v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-147">Call the <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> method or the <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> method when you change the cell or row error text to ensure that the current value is displayed in the control.</span></span><br /><br /> <span data-ttu-id="d0a68-148">Buňky a řádek glyfů chyba se zobrazí při <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> a <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> jsou hodnoty vlastností `true`.</span><span class="sxs-lookup"><span data-stu-id="d0a68-148">Cell and row error glyphs are displayed when the <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> and <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> property values are `true`.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|<span data-ttu-id="d0a68-149">Ovládací prvek používají k načítání buňku nebo řádek <xref:System.Windows.Forms.ContextMenuStrip> při ovládacího prvku <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`.</span><span class="sxs-lookup"><span data-stu-id="d0a68-149">Used by the control to retrieve a cell or row <xref:System.Windows.Forms.ContextMenuStrip> when the control <xref:System.Windows.Forms.DataGridView.DataSource%2A> property is set or the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property is `true`.</span></span>|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|<span data-ttu-id="d0a68-150">Ovládací prvek používá k načtení nebo ukládání informací výšky řádku v datové mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d0a68-150">Used by the control to retrieve or store row height information in the data cache.</span></span> <span data-ttu-id="d0a68-151">Volání <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> metoda při změně informace uložené v mezipaměti řádek výška mimo <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> obslužné rutiny události pro zajištění, že aktuální hodnota se používá v zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0a68-151">Call the <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> method when changing the cached row height information outside of a <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> event handler to ensure that the current value is used in the display of the control.</span></span>|  
  
## <a name="best-practices-in-virtual-mode"></a><span data-ttu-id="d0a68-152">Osvědčené postupy v virtuální režim</span><span class="sxs-lookup"><span data-stu-id="d0a68-152">Best Practices in Virtual Mode</span></span>  
 <span data-ttu-id="d0a68-153">Pokud jsou implementace virtuálního režimu, aby bylo možné efektivně pracovat s velkými objemy dat, budete také chtít Ujistěte se, že pracujete efektivně <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d0a68-153">If you are implementing virtual mode in order to work efficiently with large amounts of data, you will also want to ensure that you are working efficiently with the <xref:System.Windows.Forms.DataGridView> control itself.</span></span> <span data-ttu-id="d0a68-154">Další informace o efektivní využití styly buňky, automatická změna velikosti, výběr a sdílení řádků najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0a68-154">For more information about the efficient use of cell styles, automatic sizing, selections, and row sharing, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a68-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0a68-155">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [<span data-ttu-id="d0a68-156">Ladění výkonu v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d0a68-156">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d0a68-157">Osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d0a68-157">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d0a68-158">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d0a68-158">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [<span data-ttu-id="d0a68-159">Implementace virtuálního režimu s načítáním v ovládacím prvku Windows Forms DataGridView dat za běhu</span><span class="sxs-lookup"><span data-stu-id="d0a68-159">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)