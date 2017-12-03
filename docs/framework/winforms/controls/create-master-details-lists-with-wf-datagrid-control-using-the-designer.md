---
title: "Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 66de6fb17e3ee5b916c4bb20dfa0799758375406
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a><span data-ttu-id="857d7-102">Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="857d7-102">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="857d7-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="857d7-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="857d7-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="857d7-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="857d7-105">Pokud vaše <xref:System.Data.DataSet> obsahuje řadu související tabulky, můžete použít dva <xref:System.Windows.Forms.DataGrid> ovládacích prvků pro zobrazení dat ve formátu seznam podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="857d7-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master-detail format.</span></span> <span data-ttu-id="857d7-106">Jeden <xref:System.Windows.Forms.DataGrid> je určen jako hlavní mřížky, a druhý je určený jako podrobnosti mřížky.</span><span class="sxs-lookup"><span data-stu-id="857d7-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="857d7-107">Když vyberete položku v seznamu hlavní, všech souvisejících podřízených položek se zobrazí v seznamu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="857d7-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="857d7-108">Například pokud vaše <xref:System.Data.DataSet> obsahuje tabulku zákazníků a související tabulky objednávky, zadali byste tabulku zákazníků jako hlavní mřížky a tabulky objednávky být podrobnosti mřížky.</span><span class="sxs-lookup"><span data-stu-id="857d7-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="857d7-109">Pokud zákazník je vybraná z hlavní mřížky, všechny objednávky přidružené tohoto zákazníka v tabulce objednávky bude zobrazen v mřížce podrobností.</span><span class="sxs-lookup"><span data-stu-id="857d7-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
 <span data-ttu-id="857d7-110">Následující postup vyžaduje **aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="857d7-110">The following procedure requires a **Windows Application** project.</span></span> <span data-ttu-id="857d7-111">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="857d7-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="857d7-112">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="857d7-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="857d7-113">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="857d7-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="857d7-114">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="857d7-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a><span data-ttu-id="857d7-115">Můžete vytvořit seznam hlavních podrobných v Návrháři</span><span class="sxs-lookup"><span data-stu-id="857d7-115">To create a master-details list in the designer</span></span>  
  
1.  <span data-ttu-id="857d7-116">Přidejte dva <xref:System.Windows.Forms.DataGrid> ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="857d7-116">Add two <xref:System.Windows.Forms.DataGrid> controls to the form.</span></span> <span data-ttu-id="857d7-117">Další informace najdete v tématu [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="857d7-117">For more information, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="857d7-118">V [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> ovládací prvek není součástí **sada nástrojů** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="857d7-118">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="857d7-119">Další informace najdete v tématu [postupy: Přidání položky do sady nástrojů](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span><span class="sxs-lookup"><span data-stu-id="857d7-119">For more information, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="857d7-120">Následující postup se nejsou použitelné [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], které používá **zdroje dat** okna pro vázání dat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="857d7-120">The following steps are not applicable to [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], which uses the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="857d7-121">Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) a [postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).</span><span class="sxs-lookup"><span data-stu-id="857d7-121">For more information, see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) and [How to: Display Related Data in a Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).</span></span>  
  
2.  <span data-ttu-id="857d7-122">Přetáhněte dvou nebo více tabulek z **Průzkumníka serveru** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="857d7-122">Drag two or more tables from **Server Explorer** to the form.</span></span>  
  
3.  <span data-ttu-id="857d7-123">Z **Data** nabídce vyberte možnost **generovat datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="857d7-123">From the **Data** menu, select **Generate DataSet**.</span></span>  
  
4.  <span data-ttu-id="857d7-124">Nastavte relace mezi tabulkami pomocí návrháře XML.</span><span class="sxs-lookup"><span data-stu-id="857d7-124">Set the relationships between the tables using the XML Designer.</span></span> <span data-ttu-id="857d7-125">Podrobnosti najdete v tématu "postup: vytvoření na více vztahy v datových sadách a schématech XML" na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="857d7-125">For details, see "How to: Create One-to-Many Relationships in XML Schemas and Datasets" on MSDN.</span></span>  
  
5.  <span data-ttu-id="857d7-126">Uložit vztahy výběrem **Uložit vše** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="857d7-126">Save the relationships by selecting **Save All** from the **File** menu.</span></span>  
  
6.  <span data-ttu-id="857d7-127">Konfigurace <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete určit hlavní mřížky, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="857d7-127">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the master grid, as follows:</span></span>  
  
    1.  <span data-ttu-id="857d7-128">Vyberte <xref:System.Data.DataSet> v rozevíracím seznamu v <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="857d7-128">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>  
  
    2.  <span data-ttu-id="857d7-129">Vyberte v rozevíracím seznamu v hlavní tabulku (například "zákazníci") <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="857d7-129">Select the master table (for example, "Customers") from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span>  
  
7.  <span data-ttu-id="857d7-130">Konfigurace <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete určit podrobnosti mřížky, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="857d7-130">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the details grid, as follows:</span></span>  
  
    1.  <span data-ttu-id="857d7-131">Vyberte <xref:System.Data.DataSet> v rozevíracím seznamu v <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="857d7-131">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>  
  
    2.  <span data-ttu-id="857d7-132">Vyberte vztah mezi tabulkami v rozevíracím seznamu v seznamu a podrobností (například "Customers.CustOrd") <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="857d7-132">Select the relationship (for example, "Customers.CustOrd") between the master and detail tables from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span> <span data-ttu-id="857d7-133">Chcete-li zobrazit relace, rozbalte uzel kliknutím na znaménko plus (**+**) znaménkem hlavní tabulku v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="857d7-133">In order to see the relationship, expand the node by clicking on the plus (**+**) sign next to the master table in the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857d7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="857d7-134">See Also</span></span>  
 [<span data-ttu-id="857d7-135">DataGrid – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="857d7-135">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="857d7-136">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="857d7-136">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="857d7-137">Postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="857d7-137">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [<span data-ttu-id="857d7-138">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="857d7-138">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)