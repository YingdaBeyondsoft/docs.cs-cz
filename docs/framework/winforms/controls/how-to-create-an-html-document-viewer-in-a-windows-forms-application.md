---
title: "Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows"
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
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e06fbfde68c0d02a94f8c7e4657e2907cd3fa7eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="889ee-102">Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="889ee-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="889ee-103">Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazit a tisk dokumentů HTML bez zadání všechny funkce prohlížeči Internet.</span><span class="sxs-lookup"><span data-stu-id="889ee-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="889ee-104">To je užitečné, pokud chcete využít výhod možnosti formátování HTML, ale nechcete, aby vaši uživatelé načíst libovolné webové stránky, které mohou obsahovat nedůvěryhodné ovládací prvky webového nebo potenciálně škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="889ee-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="889ee-105">Můžete chtít omezit schopnosti produktu <xref:System.Windows.Forms.WebBrowser> řídit tímto způsobem, například můžete použít jako prohlížeč formátu HTML e-mailu nebo k poskytnutí nápovědy ve formátu HTML v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="889ee-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML e-mail viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="889ee-106">K vytvoření prohlížeče dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="889ee-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="889ee-107">Nastavit <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost, která má `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek v otevírání souborů, které jsou umístěny na ho.</span><span class="sxs-lookup"><span data-stu-id="889ee-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="889ee-108">Nastavte <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnost do umístění souboru počáteční k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="889ee-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="889ee-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="889ee-109">Compiling the Code</span></span>  
 <span data-ttu-id="889ee-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="889ee-110">This example requires:</span></span>  
  
-   <span data-ttu-id="889ee-111">A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="889ee-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="889ee-112">Odkazuje na `System` a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="889ee-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889ee-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="889ee-113">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [<span data-ttu-id="889ee-114">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="889ee-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="889ee-115">WebBrowser – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="889ee-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [<span data-ttu-id="889ee-116">Postupy: přechod na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="889ee-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [<span data-ttu-id="889ee-117">Postupy: tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="889ee-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)