---
title: "Postupy: Tisk ve Windows Forms pomocí náhledu tisku"
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
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ed914ebd868390233cead97de5d326eb77e390
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="c7bca-102">Postupy: Tisk ve Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="c7bca-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="c7bca-103">Je velmi běžné ve Windows Forms programování nabízet náhledu tisku kromě tisk služby.</span><span class="sxs-lookup"><span data-stu-id="c7bca-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="c7bca-104">Snadný způsob, jak do aplikace přidat náhledu tisku služby je použití <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek v kombinaci s <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiku zpracování událostí pro tisk souboru.</span><span class="sxs-lookup"><span data-stu-id="c7bca-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="c7bca-105">Zobrazte náhled textový dokument s printpreviewdialog – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c7bca-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1.  <span data-ttu-id="c7bca-106">Přidat <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>a dva řetězce do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="c7bca-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  <span data-ttu-id="c7bca-107">Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost k tomuto dokumentu chcete vytisknout a otevírat a číst obsah dokumentu na řetězec, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="c7bca-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="c7bca-108">Stejně jako pro tisk dokumentu v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru vypočítat řádků na stránce a vykreslit obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c7bca-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="c7bca-109">Po každé stránce vykreslením, zkontrolujte, zda se jedná o poslední stránku a nastavit <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c7bca-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="c7bca-110"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Událost se vyvolá, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="c7bca-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="c7bca-111">Po dokončení vykreslování dokumentu resetovat řetězec, který má být vykreslen.</span><span class="sxs-lookup"><span data-stu-id="c7bca-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="c7bca-112">Ujistěte se také, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost souvisí s příslušnou metodu zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="c7bca-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7bca-113">Možná jste již dokončili kroky 2 a 3 Pokud jste implementovali tisk ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c7bca-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="c7bca-114">V následujícím příkladu kódu obslužné rutiny události se používá k vytištění souboru "testPage.txt" ve stejném písmo použité ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c7bca-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="c7bca-115">Nastavte <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> řídit k <xref:System.Drawing.Printing.PrintDocument> součásti na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c7bca-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  <span data-ttu-id="c7bca-116">Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7bca-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="c7bca-117">By obvykle volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metodu události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c7bca-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="c7bca-118">Volání metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolá <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí a vykreslí výstup k <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7bca-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="c7bca-119">Když uživatel klikne na ikonu tisku v dialogovém okně <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se vyvolá, odesílá výstup na tiskárnu místo dialogové okno náhledu.</span><span class="sxs-lookup"><span data-stu-id="c7bca-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="c7bca-120">Z tohoto důvodu řetězec se resetuje na konci procesu vykreslování v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="c7bca-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="c7bca-121">Následující příklad kódu ukazuje <xref:System.Windows.Forms.Control.Click> metodu události pro tlačítko ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c7bca-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="c7bca-122">Tato metoda zpracování událostí volá metody pro čtení dokumentu a zobrazit dialogové okno náhledu tisku.</span><span class="sxs-lookup"><span data-stu-id="c7bca-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="c7bca-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7bca-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7bca-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c7bca-124">Compiling the Code</span></span>  
 <span data-ttu-id="c7bca-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c7bca-125">This example requires:</span></span>  
  
-   <span data-ttu-id="c7bca-126">Odkazy na systém, System.Windows.Forms, System.Drawing sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7bca-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="c7bca-127">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c7bca-127">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c7bca-128">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="c7bca-128">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="c7bca-129">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c7bca-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7bca-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7bca-130">See Also</span></span>  
 [<span data-ttu-id="c7bca-131">Postupy: Tisk vícestránkového textového souboru v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7bca-131">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="c7bca-132">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7bca-132">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="c7bca-133">Bezpečnější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7bca-133">More Secure Printing in Windows Forms</span></span>](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)