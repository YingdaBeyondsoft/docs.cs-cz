---
title: "Postupy: Změna zpoždění součásti Windows Forms ToolTip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48bb8c08fa02a54f9bfd3febbe99f683fd68d7f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="93c48-102">Postupy: Změna zpoždění součásti Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="93c48-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="93c48-103">Existuje více hodnot zpoždění, které se dají nastavit pro Windows Forms <xref:System.Windows.Forms.ToolTip> součásti.</span><span class="sxs-lookup"><span data-stu-id="93c48-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="93c48-104">Jednotka měření pro tyto vlastnosti je milisekundách.</span><span class="sxs-lookup"><span data-stu-id="93c48-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="93c48-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Vlastnost určuje, jak dlouho musí odkazovat uživatele na související ovládací prvek pro text popisu tlačítka se objeví.</span><span class="sxs-lookup"><span data-stu-id="93c48-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="93c48-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Vlastnost nastaví počet milisekund, po je potřebná pro následné řetězce popisu tlačítka se objeví při pohybu myší z jednoho popisku přidruženého ovládacího prvku do jiného.</span><span class="sxs-lookup"><span data-stu-id="93c48-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="93c48-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Vlastnost určuje dobu, se zobrazí řetězec popisku.</span><span class="sxs-lookup"><span data-stu-id="93c48-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="93c48-108">Tyto hodnoty lze nastavit samostatně, nebo nastavením hodnoty <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost; ostatní vlastnosti jsou nastavené na hodnotu přiřazenou základě zpoždění <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="93c48-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="93c48-109">Například, když <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> je nastavená na hodnotu N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> je nastaven na N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> je nastaven na hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> rozdělený podle pět (nebo N/5), a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> nastavena na hodnotu, která je pětkrát hodnota <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost (nebo 5N).</span><span class="sxs-lookup"><span data-stu-id="93c48-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="93c48-110">Chcete-li nastavit zpoždění</span><span class="sxs-lookup"><span data-stu-id="93c48-110">To set the delay</span></span>  
  
1.  <span data-ttu-id="93c48-111">Jak je znázorněno v tomto příkladu, nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93c48-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="93c48-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="93c48-112">See Also</span></span>  
 [<span data-ttu-id="93c48-113">ToolTip – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="93c48-113">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="93c48-114">Postupy: nastavení ToolTips pro ovládací prvky na formuláři Windows v době návrhu</span><span class="sxs-lookup"><span data-stu-id="93c48-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="93c48-115">ToolTip – komponenta</span><span class="sxs-lookup"><span data-stu-id="93c48-115">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)