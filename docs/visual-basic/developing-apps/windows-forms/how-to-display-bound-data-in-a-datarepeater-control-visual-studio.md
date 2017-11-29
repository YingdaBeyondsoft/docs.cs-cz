---
title: "Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770003c8879661bfc1ce683f5b6ed84483cf47ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="b10b3-102">Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b10b3-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="b10b3-103">Nejběžnější použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zobrazení vázaných dat z databáze nebo jiného zdroje dat je řízení.</span><span class="sxs-lookup"><span data-stu-id="b10b3-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="b10b3-104">Kromě vázané ovládací prvky, můžete přidat další ovládací prvky, jako je například statické štítek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b10b3-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="b10b3-105">Další informace najdete v tématu [postupy: zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b10b3-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="b10b3-106">Můžete také navázat ke zdroji dat za běhu nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` a přiřazení zdroje dat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b10b3-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="b10b3-107">V takovém případě bude muset spravovat všechny interakce se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="b10b3-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="b10b3-108">Další informace najdete v tématu [virtuální režim ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b10b3-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="b10b3-109">Chcete-li vytvořit DataRepeater vázané na data</span><span class="sxs-lookup"><span data-stu-id="b10b3-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="b10b3-110">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b10b3-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="b10b3-111">Přetáhněte obslužné rutiny pro změnu velikosti a pozice na velikost a umístění ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b10b3-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="b10b3-112">Všimněte si, že ovládací prvek má dvě obdélníková oblasti.</span><span class="sxs-lookup"><span data-stu-id="b10b3-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="b10b3-113">Horní oblast je *šablony položky*; ovládací prvky přidat do šablony budou opakovat v jednotlivé položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku za běhu.</span><span class="sxs-lookup"><span data-stu-id="b10b3-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="b10b3-114">Dolní oblast je *zobrazení*, kde se zobrazí položky.</span><span class="sxs-lookup"><span data-stu-id="b10b3-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="b10b3-115">Můžete také upravit velikost a umístění ovládacího prvku nebo šablony položky změnou **velikost** a **pozice** vlastnosti v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b10b3-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="b10b3-116">Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.</span><span class="sxs-lookup"><span data-stu-id="b10b3-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b10b3-117">Pokud **zdroje dat** přidejte do něj zdroj dat, je prázdný.</span><span class="sxs-lookup"><span data-stu-id="b10b3-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="b10b3-118">Další informace najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="b10b3-118">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="b10b3-119">V **zdroje dat** okně vyberte uzel pro tabulku, která obsahuje data, která chcete vytvořit vazbu na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="b10b3-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="b10b3-120">Změňte typ tabulky na `Details` kliknutím `Details` v rozevíracím seznamu na uzlu tabulky.</span><span class="sxs-lookup"><span data-stu-id="b10b3-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="b10b3-121">Vyberte uzel tabulky a přetáhněte ji na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b10b3-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="b10b3-122">Můžete určit, které typy ovládacích prvků se zobrazují pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="b10b3-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="b10b3-123">Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span><span class="sxs-lookup"><span data-stu-id="b10b3-123">For more information, see [Set the control to be created when dragging from the Data Sources window](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10b3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b10b3-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="b10b3-125">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b10b3-125">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b10b3-126">Postupy: zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b10b3-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b10b3-127">Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b10b3-127">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="b10b3-128">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b10b3-128">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b10b3-129">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b10b3-129">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)