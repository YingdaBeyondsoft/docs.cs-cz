---
title: "Přehled vlastnosti AutoSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8216880ebdede03bbd01fe53b622c14ca8c514d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="autosize-property-overview"></a><span data-ttu-id="4bb96-102">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="4bb96-102">AutoSize Property Overview</span></span>
<span data-ttu-id="4bb96-103"><xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost umožňuje změnit jeho velikost, pokud je to nezbytné, aby bylo možné hodnotu zadanou pomocí ovládacího prvku <xref:System.Windows.Forms.Control.PreferredSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-103">The <xref:System.Windows.Forms.Control.AutoSize%2A> property enables a control to change its size, if necessary, to attain the value specified by the <xref:System.Windows.Forms.Control.PreferredSize%2A> property.</span></span> <span data-ttu-id="4bb96-104">Upravit chování nastavení velikosti pro konkrétní ovládací prvky podle nastavení `AutoSizeMode` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-104">You adjust the sizing behavior for specific controls by setting the `AutoSizeMode` property.</span></span>  
  
## <a name="autosize-behavior"></a><span data-ttu-id="4bb96-105">Chování AutoSize</span><span class="sxs-lookup"><span data-stu-id="4bb96-105">AutoSize Behavior</span></span>  
 <span data-ttu-id="4bb96-106">Pouze některé ovládací prvky podporují <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-106">Only some controls support the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="4bb96-107">Kromě toho některé ovládací prvky podporující <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost podporovat i `AutoSizeMode` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-107">In addition, some controls that support the <xref:System.Windows.Forms.Control.AutoSize%2A> property also support the `AutoSizeMode` property.</span></span>  
  
 <span data-ttu-id="4bb96-108"><xref:System.Windows.Forms.Control.AutoSize%2A> Vytváří poněkud různé chování v závislosti na určitý ovládací prvek typ a hodnotu vlastnosti `AutoSizeMode` vlastnost, pokud existuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-108">The <xref:System.Windows.Forms.Control.AutoSize%2A> property produces somewhat different behavior, depending on the specific control type and the value of the `AutoSizeMode` property, if the property exists.</span></span> <span data-ttu-id="4bb96-109">Následující tabulka popisuje chování, které jsou vždy hodnotu true a obsahuje stručný popis jednotlivých:</span><span class="sxs-lookup"><span data-stu-id="4bb96-109">The following table describes the behaviors that are always true and provides a brief description of each:</span></span>  
  
|<span data-ttu-id="4bb96-110">Chování vždy hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="4bb96-110">Always true behavior</span></span>|<span data-ttu-id="4bb96-111">Popis</span><span class="sxs-lookup"><span data-stu-id="4bb96-111">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="4bb96-112">Automatická změna velikosti je běhové funkce.</span><span class="sxs-lookup"><span data-stu-id="4bb96-112">Automatic sizing is a run-time feature.</span></span>|<span data-ttu-id="4bb96-113">To znamená, že se nikdy zvětšování nebo zmenšuje ovládacího prvku a pak nemá žádný efekt Další.</span><span class="sxs-lookup"><span data-stu-id="4bb96-113">This means it never grows or shrinks a control and then has no further effect.</span></span>|  
|<span data-ttu-id="4bb96-114">Pokud se ovládací prvek změní velikost, hodnota jeho <xref:System.Windows.Forms.Control.Location%2A> vlastnost vždy zůstává konstantní.</span><span class="sxs-lookup"><span data-stu-id="4bb96-114">If a control changes size, the value of its <xref:System.Windows.Forms.Control.Location%2A> property always remains constant.</span></span>|<span data-ttu-id="4bb96-115">Pokud obsah ovládacího prvku způsobit, že ho růst, ovládacího prvku zvětšování směrem doprava a směrem dolů.</span><span class="sxs-lookup"><span data-stu-id="4bb96-115">When a control's contents cause it to grow, the control grows toward the right and downward.</span></span> <span data-ttu-id="4bb96-116">Ovládací prvky nejsou růst vlevo.</span><span class="sxs-lookup"><span data-stu-id="4bb96-116">Controls do not grow to the left.</span></span>|  
|<span data-ttu-id="4bb96-117"><xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti jsou přijmout, kdy <xref:System.Windows.Forms.Control.AutoSize%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="4bb96-117">The <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> properties are honored when <xref:System.Windows.Forms.Control.AutoSize%2A> is `true`.</span></span>|<span data-ttu-id="4bb96-118">Hodnota ovládacího prvku <xref:System.Windows.Forms.Control.Location%2A> vlastnost se upraví na správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4bb96-118">The value of the control's <xref:System.Windows.Forms.Control.Location%2A> property is adjusted to the correct value.</span></span><br /><br /> <span data-ttu-id="4bb96-119">**Poznámka:** <xref:System.Windows.Forms.Label> řízení je výjimka, která má toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="4bb96-119">**Note** The <xref:System.Windows.Forms.Label> control is the exception to this rule.</span></span> <span data-ttu-id="4bb96-120">Pokud nastavíte hodnotu ukotveného <xref:System.Windows.Forms.Label> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`, <xref:System.Windows.Forms.Label> nebude roztažení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4bb96-120">When you set the value of a docked <xref:System.Windows.Forms.Label> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`, the <xref:System.Windows.Forms.Label> control will not stretch.</span></span>|  
|<span data-ttu-id="4bb96-121">Ovládací prvek <xref:System.Windows.Forms.Control.MaximumSize%2A> a <xref:System.Windows.Forms.Control.MinimumSize%2A> vlastnosti se vždy dodržují bez ohledu na hodnotu z její <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-121">A control's <xref:System.Windows.Forms.Control.MaximumSize%2A> and <xref:System.Windows.Forms.Control.MinimumSize%2A> properties are always honored, regardless of the value of its <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span>|<span data-ttu-id="4bb96-122"><xref:System.Windows.Forms.Control.MaximumSize%2A> a <xref:System.Windows.Forms.Control.MinimumSize%2A> vlastnosti nemá vliv <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-122">The <xref:System.Windows.Forms.Control.MaximumSize%2A> and <xref:System.Windows.Forms.Control.MinimumSize%2A> properties are not affected by the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span>|  
|<span data-ttu-id="4bb96-123">Není k dispozici minimální velikost ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4bb96-123">There is no minimum size set by default.</span></span>|<span data-ttu-id="4bb96-124">To znamená, že pokud ovládacího prvku je nastavený na zmenšit pod <xref:System.Windows.Forms.Control.AutoSize%2A> a nemá žádný obsah, hodnotu jeho <xref:System.Windows.Forms.Control.Size%2A> vlastnost je 0,0.</span><span class="sxs-lookup"><span data-stu-id="4bb96-124">This means that if a control is set to shrink under <xref:System.Windows.Forms.Control.AutoSize%2A> and it has no contents, the value of its <xref:System.Windows.Forms.Control.Size%2A> property is 0,0.</span></span> <span data-ttu-id="4bb96-125">V takovém případě zmenší vlastního ovládacího prvku do bodu, a nebude snadno viditelná.</span><span class="sxs-lookup"><span data-stu-id="4bb96-125">In this case, your control will shrink to a point, and it will not be readily visible.</span></span>|  
|<span data-ttu-id="4bb96-126">Pokud ovládací prvek neimplementuje <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda vrátí poslední hodnotu přiřazenou <xref:System.Windows.Forms.Control.Size%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-126">If a control does not implement the <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method, the <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method returns last value assigned to the <xref:System.Windows.Forms.Control.Size%2A> property.</span></span>|<span data-ttu-id="4bb96-127">To znamená, že nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> k `true` nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="4bb96-127">This means that setting <xref:System.Windows.Forms.Control.AutoSize%2A> to `true` will have no effect.</span></span>|  
|<span data-ttu-id="4bb96-128">V ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> zmenší, aby se vešla do buňky do buňky vždy jeho <xref:System.Windows.Forms.Control.MinimumSize%2A> je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="4bb96-128">A control in a <xref:System.Windows.Forms.TableLayoutPanel> cell always shrinks to fit in the cell until its <xref:System.Windows.Forms.Control.MinimumSize%2A> is reached.</span></span>|<span data-ttu-id="4bb96-129">Tato velikost je vynucená jako maximální velikost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-129">This size is enforced as a maximum size.</span></span> <span data-ttu-id="4bb96-130">To tak není při buňky je součástí <xref:System.Windows.Forms.SizeType.AutoSize> sloupce či řádku.</span><span class="sxs-lookup"><span data-stu-id="4bb96-130">This is not the case when the cell is part of an <xref:System.Windows.Forms.SizeType.AutoSize> row or column.</span></span>|  
  
## <a name="autosizemode-property"></a><span data-ttu-id="4bb96-131">AutoSizeMode – vlastnost</span><span class="sxs-lookup"><span data-stu-id="4bb96-131">AutoSizeMode Property</span></span>  
 <span data-ttu-id="4bb96-132">`AutoSizeMode` Vlastnost poskytuje jemně odstupňovanou kontrolu nad výchozí <xref:System.Windows.Forms.Control.AutoSize%2A> chování.</span><span class="sxs-lookup"><span data-stu-id="4bb96-132">The `AutoSizeMode` property provides more fine-grained control over the default <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span> <span data-ttu-id="4bb96-133">`AutoSizeMode` Vlastnost určuje, jak ovládacího prvku velikostí sám sebe na jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="4bb96-133">The `AutoSizeMode` property specifies how a control sizes itself to its content.</span></span> <span data-ttu-id="4bb96-134">Obsah, například může být text pro <xref:System.Windows.Forms.Button> podřízených ovládacích prvků pro kontejner nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4bb96-134">The content, for example, could be the text for a <xref:System.Windows.Forms.Button> control or the child controls for a container.</span></span>  
  
 <span data-ttu-id="4bb96-135">Následující tabulce je zobrazena <xref:System.Windows.Forms.AutoSizeMode> nastavení a popis chování elicits jednotlivých nastavení.</span><span class="sxs-lookup"><span data-stu-id="4bb96-135">The following table shows the <xref:System.Windows.Forms.AutoSizeMode> settings and a description of the behavior each setting elicits.</span></span>  
  
|<span data-ttu-id="4bb96-136">AutoSizeMode nastavení</span><span class="sxs-lookup"><span data-stu-id="4bb96-136">AutoSizeMode setting</span></span>|<span data-ttu-id="4bb96-137">Chování</span><span class="sxs-lookup"><span data-stu-id="4bb96-137">Behavior</span></span>|  
|--------------------------|--------------|  
|<span data-ttu-id="4bb96-138">GrowAndShrink</span><span class="sxs-lookup"><span data-stu-id="4bb96-138">GrowAndShrink</span></span>|<span data-ttu-id="4bb96-139">Ovládací prvek zvětšováním nebo zmenšováním zahrnuje její obsah.</span><span class="sxs-lookup"><span data-stu-id="4bb96-139">The control grows or shrinks to encompass its contents.</span></span><br /><br /> <span data-ttu-id="4bb96-140"><xref:System.Windows.Forms.Control.MinimumSize%2A> a <xref:System.Windows.Forms.Control.MaximumSize%2A> hodnoty jsou ignorovány, ale aktuální hodnota <xref:System.Windows.Forms.Control.Size%2A> vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="4bb96-140">The <xref:System.Windows.Forms.Control.MinimumSize%2A> and <xref:System.Windows.Forms.Control.MaximumSize%2A> values are honored, but the current value of the <xref:System.Windows.Forms.Control.Size%2A> property is ignored.</span></span><br /><br /> <span data-ttu-id="4bb96-141">Toto je stejné chování jako ovládacích prvků pomocí <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a ne `AutoSizeMode` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-141">This is the same behavior as controls with the <xref:System.Windows.Forms.Control.AutoSize%2A> property and no `AutoSizeMode` property.</span></span>|  
|<span data-ttu-id="4bb96-142">GrowOnly</span><span class="sxs-lookup"><span data-stu-id="4bb96-142">GrowOnly</span></span>|<span data-ttu-id="4bb96-143">Ovládací prvek zvětšování co nejvíce potřeba zahrnovat její obsah, ale nebude menší než hodnota zadaná podle zmenšit jeho <xref:System.Windows.Forms.Control.Size%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-143">The control grows as much as necessary to encompass its contents, but it will not shrink smaller than the value specified by its <xref:System.Windows.Forms.Control.Size%2A> property.</span></span><br /><br /> <span data-ttu-id="4bb96-144">Toto je výchozí hodnota pro `AutoSizeMode`.</span><span class="sxs-lookup"><span data-stu-id="4bb96-144">This is the default value for `AutoSizeMode`.</span></span>|  
  
## <a name="controls-that-support-the-autosize-property"></a><span data-ttu-id="4bb96-145">Ovládací prvky, které podporují s vlastností AutoSize</span><span class="sxs-lookup"><span data-stu-id="4bb96-145">Controls That Support the AutoSize Property</span></span>  
 <span data-ttu-id="4bb96-146">Následující tabulka uvádí prvky, které podporují <xref:System.Windows.Forms.Control.AutoSize%2A> a `AutoSizeMode` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4bb96-146">The following table lists the controls that support the <xref:System.Windows.Forms.Control.AutoSize%2A> and `AutoSizeMode` properties.</span></span>  
  
|<span data-ttu-id="4bb96-147">Podpora AutoSize</span><span class="sxs-lookup"><span data-stu-id="4bb96-147">AutoSize support</span></span>|<span data-ttu-id="4bb96-148">– Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4bb96-148">Control type</span></span>|  
|----------------------|------------------|  
|<span data-ttu-id="4bb96-149">-   <xref:System.Windows.Forms.Control.AutoSize%2A>vlastnost podporována.</span><span class="sxs-lookup"><span data-stu-id="4bb96-149">-   <xref:System.Windows.Forms.Control.AutoSize%2A> property supported.</span></span><br /><span data-ttu-id="4bb96-150">-Již `AutoSizeMode` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-150">-   No `AutoSizeMode` property.</span></span>|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <span data-ttu-id="4bb96-151"><xref:System.Windows.Forms.MaskedTextBox>(<xref:System.Windows.Forms.TextBox> základní)</span><span class="sxs-lookup"><span data-stu-id="4bb96-151"><xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> base)</span></span><br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|<span data-ttu-id="4bb96-152">-   <xref:System.Windows.Forms.Control.AutoSize%2A>vlastnost podporována.</span><span class="sxs-lookup"><span data-stu-id="4bb96-152">-   <xref:System.Windows.Forms.Control.AutoSize%2A> property supported.</span></span><br /><span data-ttu-id="4bb96-153">-   `AutoSizeMode`vlastnost podporována.</span><span class="sxs-lookup"><span data-stu-id="4bb96-153">-   `AutoSizeMode` property supported.</span></span>|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|<span data-ttu-id="4bb96-154">-Již <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-154">-   No <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span>|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a><span data-ttu-id="4bb96-155">AutoSize v prostředí návrhu</span><span class="sxs-lookup"><span data-stu-id="4bb96-155">AutoSize in the Design Environment</span></span>  
 <span data-ttu-id="4bb96-156">Následující tabulka popisuje chování nastavení velikosti ovládacího prvku v době návrhu na základě hodnoty z jeho <xref:System.Windows.Forms.Control.AutoSize%2A> a `AutoSizeMode` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4bb96-156">The following table describes the sizing behavior of a control at design time, based on the value of its <xref:System.Windows.Forms.Control.AutoSize%2A> and `AutoSizeMode` properties.</span></span>  
  
 <span data-ttu-id="4bb96-157">Přepsání <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> vlastnosti k určení, zda daný ovládací prvek je ve stavu s možností změny velikosti uživatele.</span><span class="sxs-lookup"><span data-stu-id="4bb96-157">Override the <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> property to determine whether a given control is in a user-resizable state.</span></span> <span data-ttu-id="4bb96-158">V následující tabulce, "nelze" znamená <xref:System.Windows.Forms.Design.SelectionRules.Moveable> pouze "můžete" znamená <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> a <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.</span><span class="sxs-lookup"><span data-stu-id="4bb96-158">In the following table, "cannot" means <xref:System.Windows.Forms.Design.SelectionRules.Moveable> only, "can" means <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> and <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.</span></span>  
  
|<span data-ttu-id="4bb96-159">Nastavení AutoSize</span><span class="sxs-lookup"><span data-stu-id="4bb96-159">AutoSize settings</span></span>|<span data-ttu-id="4bb96-160">Nastavení velikosti návrhu gesto</span><span class="sxs-lookup"><span data-stu-id="4bb96-160">Design-time sizing gesture</span></span>|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br /><span data-ttu-id="4bb96-161">-Již `AutoSizeMode` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bb96-161">-   No `AutoSizeMode` property.</span></span>|<span data-ttu-id="4bb96-162">Uživatel nemůže změnit velikost ovládacího prvku v době návrhu, s výjimkou následující prvky:</span><span class="sxs-lookup"><span data-stu-id="4bb96-162">The user cannot resize the control at design time, except for the following controls:</span></span><br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|<span data-ttu-id="4bb96-163">Uživatel nemůže změnit velikost ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4bb96-163">The user cannot resize the control at design time.</span></span>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|<span data-ttu-id="4bb96-164">Uživatel může změnit velikost ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4bb96-164">The user can resize the control at design time.</span></span> <span data-ttu-id="4bb96-165">Když <xref:System.Windows.Forms.Control.Size%2A> vlastnost nastavena, uživatel pouze zvýšit velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4bb96-165">When the <xref:System.Windows.Forms.Control.Size%2A> property is set, the user can only increase the size of the control.</span></span>|  
|<span data-ttu-id="4bb96-166">-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, nebo <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost skryt.</span><span class="sxs-lookup"><span data-stu-id="4bb96-166">-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, or <xref:System.Windows.Forms.Control.AutoSize%2A> property is hidden.</span></span>|<span data-ttu-id="4bb96-167">Uživatel může změnit velikost ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4bb96-167">User can resize the control at design time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4bb96-168">Maximalizovat produktivitu, stínů Návrhář formulářů Windows <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost <xref:System.Windows.Forms.Form> třídy.</span><span class="sxs-lookup"><span data-stu-id="4bb96-168">To maximize productivity, the Windows Forms Designer shadows the <xref:System.Windows.Forms.Control.AutoSize%2A> property for the <xref:System.Windows.Forms.Form> class.</span></span> <span data-ttu-id="4bb96-169">V době návrhu, bude formulář chovat jako když <xref:System.Windows.Forms.Control.AutoSize%2A> je nastavena na `false`, bez ohledu na to jeho skutečného nastavení.</span><span class="sxs-lookup"><span data-stu-id="4bb96-169">At design time, the form behaves as though the <xref:System.Windows.Forms.Control.AutoSize%2A> property is set to `false`, regardless of its actual setting.</span></span> <span data-ttu-id="4bb96-170">V době běhu žádné speciální ubytovací přišla a <xref:System.Windows.Forms.Control.AutoSize%2A> použití vlastnosti je uvedené nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="4bb96-170">At runtime, no special accommodation is made, and the <xref:System.Windows.Forms.Control.AutoSize%2A> property is applied as specified by the property setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb96-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bb96-171">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.PreferredSize%2A>  
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>