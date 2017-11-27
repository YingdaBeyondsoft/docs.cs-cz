---
title: "Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4a1fbe175abf07eaccfd177c6e32f5515e88c4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="8d28c-102">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d28c-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8d28c-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d28c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8d28c-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8d28c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8d28c-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableProvider>, včetně informací o události, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="8d28c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="8d28c-106">Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="8d28c-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="8d28c-107"><xref:System.Windows.Automation.TablePattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="8d28c-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="8d28c-108">Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ITableItemProvider> a být uspořádány do dvourozměrná logické systém souřadnic, který lze procházet podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="8d28c-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="8d28c-109">Tento vzor ovládacích prvků je podobná <xref:System.Windows.Automation.Provider.IGridProvider>, s rozdíl, že všechny řídí, implementace <xref:System.Windows.Automation.Provider.ITableProvider> musí také vystavit vztahu sloupec nebo řádek záhlaví pro každý podřízený element.</span><span class="sxs-lookup"><span data-stu-id="8d28c-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="8d28c-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8d28c-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8d28c-111">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="8d28c-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8d28c-112">Když implementace vzoru ovládacích prvků tabulka, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="8d28c-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="8d28c-113">Přístup k obsahu jednotlivých buněk je prostřednictvím dvourozměrná logické souřadnicový systém nebo pole poskytované požadované souběžné provádění <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="8d28c-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
-   <span data-ttu-id="8d28c-114">Záhlaví sloupce nebo řádku může být obsažený v rámci objektu tabulky nebo být samostatné záhlaví objekt, který je přidružený objekt tabulky.</span><span class="sxs-lookup"><span data-stu-id="8d28c-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
-   <span data-ttu-id="8d28c-115">Záhlaví řádků a sloupců může zahrnovat jak primární záhlaví a také všechny podpůrné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="8d28c-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d28c-116">Tento koncept se stane zřejmé ve [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] tabulky, kde má uživatelem definovaný sloupec "Jméno".</span><span class="sxs-lookup"><span data-stu-id="8d28c-116">This concept becomes evident in a [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="8d28c-117">Tento sloupec má teď dvě hlavičky – hlavička "Jméno" definované uživatelem a alfanumerické označení pro tento sloupec přiřazeno aplikací.</span><span class="sxs-lookup"><span data-stu-id="8d28c-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
-   <span data-ttu-id="8d28c-118">V tématu [implementace vzoru ovládacích prvků uživatelského rozhraní automatizace mřížka](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) pro funkci související mřížky.</span><span class="sxs-lookup"><span data-stu-id="8d28c-118">See [Implementing the UI Automation Grid Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="8d28c-119">![Tabulka s komplexními položkami záhlaví. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="8d28c-119">![Table with complex header items.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="8d28c-120">Příklad tabulky se záhlavími sloupců. komplexní</span><span class="sxs-lookup"><span data-stu-id="8d28c-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="8d28c-121">![Tabulka s nejednoznačný RowOrColumnMajor vlastností. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="8d28c-121">![Table with ambiguous RowOrColumnMajor property.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="8d28c-122">Příklad tabulky s vlastností nejednoznačný RowOrColumnMajor</span><span class="sxs-lookup"><span data-stu-id="8d28c-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="8d28c-123">Požadované členy pro ITableProvider</span><span class="sxs-lookup"><span data-stu-id="8d28c-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="8d28c-124">Následující vlastnosti a metody jsou požadovány pro rozhraní ITableProvider.</span><span class="sxs-lookup"><span data-stu-id="8d28c-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="8d28c-125">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="8d28c-125">Required members</span></span>|<span data-ttu-id="8d28c-126">Typ člena</span><span class="sxs-lookup"><span data-stu-id="8d28c-126">Member type</span></span>|<span data-ttu-id="8d28c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d28c-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="8d28c-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8d28c-128">Property</span></span>|<span data-ttu-id="8d28c-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d28c-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="8d28c-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="8d28c-130">Method</span></span>|<span data-ttu-id="8d28c-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d28c-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="8d28c-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="8d28c-132">Method</span></span>|<span data-ttu-id="8d28c-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d28c-133">None</span></span>|  
  
 <span data-ttu-id="8d28c-134">Tento vzor ovládacích prvků nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="8d28c-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8d28c-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="8d28c-135">Exceptions</span></span>  
 <span data-ttu-id="8d28c-136">Tento vzor ovládacích prvků nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="8d28c-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d28c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d28c-137">See Also</span></span>  
 [<span data-ttu-id="8d28c-138">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d28c-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8d28c-139">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d28c-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8d28c-140">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="8d28c-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8d28c-141">Implementace vzoru TableItem ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d28c-141">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="8d28c-142">Implementace vzoru ovládacích prvků uživatelského rozhraní automatizaci mřížky</span><span class="sxs-lookup"><span data-stu-id="8d28c-142">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="8d28c-143">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d28c-143">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8d28c-144">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d28c-144">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)