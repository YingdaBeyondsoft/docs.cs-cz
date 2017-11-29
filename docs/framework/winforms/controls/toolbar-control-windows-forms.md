---
title: "ToolBar – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18fc87d4ebccd101bec47abd39805746d0b9ef81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="7804f-102">ToolBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7804f-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="7804f-103"><xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce `ToolBar` řízení; však `ToolBar` řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="7804f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7804f-104">Windows Forms `ToolBar` řízení se používá ve formulářích jako ovládací prvek panel, který zobrazí řádek rozevíracích nabídek a rastrové tlačítka, který aktivovat příkazy.</span><span class="sxs-lookup"><span data-stu-id="7804f-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="7804f-105">Kliknutím na tlačítko panelu nástrojů je proto ekvivalentem možnosti vybrání příkazu nabídky.</span><span class="sxs-lookup"><span data-stu-id="7804f-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="7804f-106">Tlačítka lze nastavit zobrazit, a chovat jako tlačítek, rozevíracích nabídek nebo oddělovače.</span><span class="sxs-lookup"><span data-stu-id="7804f-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="7804f-107">Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v nabídce struktura aplikace, poskytující rychlý přístup aplikaci nejčastěji používaných funkcí a příkazy.</span><span class="sxs-lookup"><span data-stu-id="7804f-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7804f-108">`ToolBar` Ovládacího prvku <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> vlastnost přijímá instanci <xref:System.Windows.Forms.ContextMenu> třída jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="7804f-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="7804f-109">Pečlivě zvažte, předáte při implementaci této řazení tlačítka na panely nástrojů v aplikaci jako vlastnost bude přijímat všechny objektu, který dědí z odkazu <xref:System.Windows.Forms.Menu> třídy.</span><span class="sxs-lookup"><span data-stu-id="7804f-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7804f-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7804f-110">In This Section</span></span>  
 [<span data-ttu-id="7804f-111">Přehled ovládacího prvku panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="7804f-111">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="7804f-112">Představuje obecné koncepty `ToolBar` řízení, které je možné vytvořit vlastní panely nástrojů, které vaši uživatelé můžete pracovat.</span><span class="sxs-lookup"><span data-stu-id="7804f-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="7804f-113">Postupy: přidávání tlačítek do ovládacího prvku panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="7804f-113">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="7804f-114">Popisuje postup přidání tlačítek `ToolBar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7804f-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="7804f-115">Postupy: definování ikony pro tlačítko panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="7804f-115">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="7804f-116">Popisuje, jak zobrazit ikony v rámci `ToolBar` ovládacího prvku tlačítka.</span><span class="sxs-lookup"><span data-stu-id="7804f-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="7804f-117">Postupy: spouštění událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="7804f-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="7804f-118">Poskytuje pokyny na psaní kódu interpretovat, které tlačítko uživatel klikne v `ToolBar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7804f-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="7804f-119">Viz také [postupy: definování ikony pro panelu nástrojů tlačítko pomocí návrháře](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [postupy: přidání tlačítek na panelu nástrojů ovládacího prvku pomocí návrháře](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7804f-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [How to: Add Buttons to a ToolBar Control Using the Designer](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7804f-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7804f-120">Reference</span></span>  
 <span data-ttu-id="7804f-121"><xref:System.Windows.Forms.ToolBar>– Třída</span><span class="sxs-lookup"><span data-stu-id="7804f-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="7804f-122">Poskytuje referenční informace o třídě a její členy.</span><span class="sxs-lookup"><span data-stu-id="7804f-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7804f-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7804f-123">Related Sections</span></span>  
 [<span data-ttu-id="7804f-124">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="7804f-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7804f-125">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="7804f-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="7804f-126">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7804f-126">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 <span data-ttu-id="7804f-127">Popisuje panely nástrojů, které může být hostitelem nabídek, ovládacích prvků a uživatelské ovládací prvky v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7804f-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>