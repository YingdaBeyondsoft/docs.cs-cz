---
title: "Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením Windows Form pomocí metody ShowDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f01fc82be38f7c5acb02c28960785e97a782909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="dd8d4-102">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením Windows Form pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="dd8d4-102">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>
<span data-ttu-id="dd8d4-103">Modelu COM (Component Object) interoperabilita problémy můžete vyřešit zobrazení formuláře Windows v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve smyčce zpráv, která je vytvořena pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-103">You can resolve Component Object Model (COM) interoperability problems by displaying your Windows Form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which is created by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dd8d4-104">Chcete-li formuláře fungování z klientské aplikace modelu COM, musíte ji provést ve smyčce zpráv Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-104">To make a form work correctly from a COM client application, you must run it on a Windows Forms message loop.</span></span> <span data-ttu-id="dd8d4-105">K tomuto účelu použijte jednu z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="dd8d4-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="dd8d4-106">Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows;</span><span class="sxs-lookup"><span data-stu-id="dd8d4-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form;</span></span>  
  
-   <span data-ttu-id="dd8d4-107">Zobrazení jednotlivých formulářů Windows na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-107">Display each Windows Form on a separate thread.</span></span> <span data-ttu-id="dd8d4-108">Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span><span class="sxs-lookup"><span data-stu-id="dd8d4-108">For more information, see [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="dd8d4-109">Postup</span><span class="sxs-lookup"><span data-stu-id="dd8d4-109">Procedure</span></span>  
 <span data-ttu-id="dd8d4-110">Pomocí <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda může být nejjednodušší způsob, jak zobrazit formulář na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zpráva smyčky, protože všechny přístupů, vyžaduje minimálně kód pro implementaci.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-110">Using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method can be the easiest way to display a form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop because, of all the approaches, it requires the least code to implement.</span></span>  
  
 <span data-ttu-id="dd8d4-111"><xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Metoda pozastaví nespravovaná aplikace zpráva smyčky a zobrazí formulář jako dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-111">The <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method suspends the unmanaged application's message loop and displays the form as a dialog box.</span></span> <span data-ttu-id="dd8d4-112">Protože byla pozastavena hostitelskou aplikaci zpráva smyčky, <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda vytvoří novou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zpráva smyčky ke zpracování zpráv formuláře.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-112">Because the host application's message loop has been suspended, the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method creates a new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop to process the form's messages.</span></span>  
  
 <span data-ttu-id="dd8d4-113">Nevýhodou použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda je, že formulář otevřou jako modální dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-113">The disadvantage of using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method is that the form will be opened as a modal dialog box.</span></span> <span data-ttu-id="dd8d4-114">Toto chování bloků žádné uživatelské rozhraní (UI) v volající aplikace při otevřeném formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-114">This behavior blocks any user interface (UI) in the calling application while the Windows Form is open.</span></span> <span data-ttu-id="dd8d4-115">Při ukončení formuláře, uživatelem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] smyčky zavře a starší aplikace zpráva smyčky spustí znovu zpráv.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-115">When the user exits the form, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop closes and the earlier application's message loop starts running again.</span></span>  
  
 <span data-ttu-id="dd8d4-116">Můžete vytvořit knihovny tříd ve Windows Forms, který má metodu pro zobrazení formuláře a následně vytvořit knihovny tříd pro zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-116">You can create a class library in Windows Forms which has a method to show the form, and then build the class library for COM interop.</span></span> <span data-ttu-id="dd8d4-117">Tento soubor knihovny DLL z Visual Basic 6.0 nebo Microsoft Foundation třídy (MFC) můžete použít, a pomocí kteréhokoli z těchto prostředí můžete volat <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-117">You can use this DLL file from Visual Basic 6.0 or Microsoft Foundation Classes (MFC), and from either of these environments you can call the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the form.</span></span>  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="dd8d4-118">Pro podporu zprostředkovatele komunikace s objekty COM zobrazením windows form pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="dd8d4-118">To support COM interop by displaying a windows form with the ShowDialog method</span></span>  
  
-   <span data-ttu-id="dd8d4-119">Nahraďte všechna volání <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> metoda pomocí volání <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda v vaší [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] součásti.</span><span class="sxs-lookup"><span data-stu-id="dd8d4-119">Replace all calls to the <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> method with calls to the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method in your [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8d4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd8d4-120">See Also</span></span>  
 [<span data-ttu-id="dd8d4-121">Vystavení součástí .NET Framework do modelu COM</span><span class="sxs-lookup"><span data-stu-id="dd8d4-121">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="dd8d4-122">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="dd8d4-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [<span data-ttu-id="dd8d4-123">Windows Forms a nespravované aplikace</span><span class="sxs-lookup"><span data-stu-id="dd8d4-123">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)