---
title: "Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
caps.latest.revision: "33"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cb8b47b147e3a7a3c615418e2c0987e4d6a20f4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a><span data-ttu-id="47b6b-102">Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b6b-102">Implementing the UI Automation Selection Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="47b6b-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="47b6b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="47b6b-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="47b6b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="47b6b-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="47b6b-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>, including information about events and properties.</span></span> <span data-ttu-id="47b6b-106">Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="47b6b-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="47b6b-107"><xref:System.Windows.Automation.SelectionPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které fungují jako kontejnery pro kolekci volitelný podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="47b6b-107">The <xref:System.Windows.Automation.SelectionPattern> control pattern is used to support controls that act as containers for a collection of selectable child items.</span></span> <span data-ttu-id="47b6b-108">Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span> <span data-ttu-id="47b6b-109">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="47b6b-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="47b6b-110">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="47b6b-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="47b6b-111">Při implementace vzoru ovládacích prvků výběr, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="47b6b-111">When implementing the Selection control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="47b6b-112">Určuje, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider> povolit jednoho nebo několika podřízenými vybrat položky.</span><span class="sxs-lookup"><span data-stu-id="47b6b-112">Controls that implement <xref:System.Windows.Automation.Provider.ISelectionProvider> allow either single or multiple child items to be selected.</span></span> <span data-ttu-id="47b6b-113">Pole se seznamem, zobrazení seznamu a stromové zobrazení podporovat více výběrů, že pole se seznamem, posuvník a skupina přepínacích tlačítek podpory jednoho výběru.</span><span class="sxs-lookup"><span data-stu-id="47b6b-113">For example, list box, list view, and tree view support multiple selections whereas combo box, slider, and radio button group support single selection.</span></span>  
  
-   <span data-ttu-id="47b6b-114">Ovládací prvky, které mají minimální, maximální a průběžné rozsah, například **svazku** posuvník, by měla implementovat <xref:System.Windows.Automation.Provider.IRangeValueProvider> místo <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-114">Controls that have a minimum, maximum, and continuous range, such as the **Volume** slider control, should implement <xref:System.Windows.Automation.Provider.IRangeValueProvider> instead of <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span>  
  
-   <span data-ttu-id="47b6b-115">Jedním výběrem ovládacích prvků, které spravují podřízených ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, například **rozlišení obrazovky** jezdec v **vlastností zobrazení** dialogové okno nebo **barev Výběr** ovládacího prvku pro výběr z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (zobrazený dole), by měla implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider>; jejich podřízené by měla implementovat obě <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-115">Single-selection controls that manage child controls that implement <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, such as the **Screen Resolution** slider in the **Display Properties** dialog box or the **Color Picker** selection control from [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (illustrated below), should implement <xref:System.Windows.Automation.Provider.ISelectionProvider>; their children should implement both <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span>  
  
 <span data-ttu-id="47b6b-116">![Výběr barvy s žlutý zvýrazněná. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="47b6b-116">![Color picker with yellow highlighted.](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="47b6b-117">Příklad mapování řetězec vzorníku barev</span><span class="sxs-lookup"><span data-stu-id="47b6b-117">Example of Color Swatch String Mapping</span></span>  
  
-   <span data-ttu-id="47b6b-118">Nabídky nepodporují <xref:System.Windows.Automation.SelectionPattern>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-118">Menus do not support <xref:System.Windows.Automation.SelectionPattern>.</span></span> <span data-ttu-id="47b6b-119">Pokud pracujete s položky nabídky, které zahrnují grafika a text (například **podokno náhledu** položky v **zobrazení** nabídky v [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) a muset nesou stavu, měli byste implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-119">If you are working with menu items that include both graphics and text (such as the **Preview Pane** items in the **View** menu in [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) and need to convey state, you should implement <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a><span data-ttu-id="47b6b-120">Požadované členy pro ISelectionProvider</span><span class="sxs-lookup"><span data-stu-id="47b6b-120">Required Members for ISelectionProvider</span></span>  
 <span data-ttu-id="47b6b-121">Následující vlastnosti, metod a události jsou vyžadovány pro <xref:System.Windows.Automation.Provider.ISelectionProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47b6b-121">The following properties, methods, and events are required for the <xref:System.Windows.Automation.Provider.ISelectionProvider> interface.</span></span>  
  
|<span data-ttu-id="47b6b-122">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="47b6b-122">Required members</span></span>|<span data-ttu-id="47b6b-123">Typ</span><span class="sxs-lookup"><span data-stu-id="47b6b-123">Type</span></span>|<span data-ttu-id="47b6b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47b6b-124">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|<span data-ttu-id="47b6b-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="47b6b-125">Property</span></span>|<span data-ttu-id="47b6b-126">Musí podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-126">Should support property changed events using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> and <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|<span data-ttu-id="47b6b-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="47b6b-127">Property</span></span>|<span data-ttu-id="47b6b-128">Musí podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="47b6b-128">Should support property changed events using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> and <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|<span data-ttu-id="47b6b-129">Metoda</span><span class="sxs-lookup"><span data-stu-id="47b6b-129">Method</span></span>|<span data-ttu-id="47b6b-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="47b6b-130">None</span></span>|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|<span data-ttu-id="47b6b-131">Událost</span><span class="sxs-lookup"><span data-stu-id="47b6b-131">Event</span></span>|<span data-ttu-id="47b6b-132">Vyvolá, když výběr v kontejneru došlo ke změně výrazně a vyžaduje odesílání další přidávání a odebírání událostí, než <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> umožňuje konstanta.</span><span class="sxs-lookup"><span data-stu-id="47b6b-132">Raised when a selection in a container has changed significantly and requires sending more addition and removal events than the <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> constant permits.</span></span>|  
  
 <span data-ttu-id="47b6b-133"><xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> a <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> vlastnosti mohou být dynamické.</span><span class="sxs-lookup"><span data-stu-id="47b6b-133">The <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> and <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> properties can be dynamic.</span></span> <span data-ttu-id="47b6b-134">Počáteční stav ovládacího prvku nemusí mít například všechny položky vybrané ve výchozím nastavení, která znamená, že <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="47b6b-134">For example, the initial state of a control might not have any items selected by default, indicating that <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> is `false`.</span></span> <span data-ttu-id="47b6b-135">Ale po výběru položky se ovládací prvek musí mít vždy alespoň jedna položka vybrána.</span><span class="sxs-lookup"><span data-stu-id="47b6b-135">However, after an item is selected, the control must always have at least one item selected.</span></span> <span data-ttu-id="47b6b-136">Podobně ve výjimečných případech může povolit ovládacího prvku více položek v inicializace zaškrtnuta, ale následně povolit pouze jeden výběr má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="47b6b-136">Similarly, in rare cases, a control might allow multiple items to be selected on initialization, but subsequently allow only single selections to be made.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="47b6b-137">Výjimky</span><span class="sxs-lookup"><span data-stu-id="47b6b-137">Exceptions</span></span>  
 <span data-ttu-id="47b6b-138">Zprostředkovatelé musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="47b6b-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="47b6b-139">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="47b6b-139">Exception Type</span></span>|<span data-ttu-id="47b6b-140">Podmínka</span><span class="sxs-lookup"><span data-stu-id="47b6b-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<span data-ttu-id="47b6b-141">Pokud ovládací prvek není povolena.</span><span class="sxs-lookup"><span data-stu-id="47b6b-141">If the control is not enabled.</span></span>|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="47b6b-142">Pokud je skrytý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="47b6b-142">If the control is hidden.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47b6b-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="47b6b-143">See Also</span></span>  
 [<span data-ttu-id="47b6b-144">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b6b-144">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="47b6b-145">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b6b-145">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="47b6b-146">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="47b6b-146">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="47b6b-147">Implementace vzoru SelectionItem ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b6b-147">Implementing the UI Automation SelectionItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)  
 [<span data-ttu-id="47b6b-148">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b6b-148">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="47b6b-149">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b6b-149">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)