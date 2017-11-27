---
title: "Postupy: Přidání příkazů trasování do kódu aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5dd46da24c379a7900dff0dc482577195f5f4c23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="a0003-102">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="a0003-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="a0003-103">Metody nejčastěji používají pro trasování jsou metody pro zápis výstupu do naslouchací procesy: **zápisu**, **writeif –**, **WriteLine**, **writelineif –**, **Assert**, a **nezdaří**.</span><span class="sxs-lookup"><span data-stu-id="a0003-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="a0003-104">Tyto metody lze rozdělit do dvou kategorií: **zápisu**, **WriteLine**, a **nezdaří** všechny bezpodmínečně, emitování výstup zatímco **writeif –**, **Writelineif –**, a **Assert** testů podmínce logické a zápisu nebo Nezapisovat závislosti na hodnotě podmínky.</span><span class="sxs-lookup"><span data-stu-id="a0003-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="a0003-105">**Writeif –** a **writelineif –** emitování výstupu, pokud je podmínka vyhodnocena `true`, a **Assert** vysílá výstupu, pokud je podmínka vyhodnocena `false`.</span><span class="sxs-lookup"><span data-stu-id="a0003-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="a0003-106">Při navrhování vaší trasování a ladění strategie, musí si myslíte o tom, jak chcete výstup k vypadat.</span><span class="sxs-lookup"><span data-stu-id="a0003-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="a0003-107">Více **zápisu** příkazy, naplní se nesouvisejícími informace vytvoří protokolu, které je obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="a0003-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="a0003-108">Na druhé straně pomocí **WriteLine** uvést související příkazy samostatné řádky může být obtížné rozlišit, jaké informace patří společně.</span><span class="sxs-lookup"><span data-stu-id="a0003-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="a0003-109">Obecně použít více **zápisu** příkazy, pokud chcete kombinovat informace z více zdrojů k vytvoření jedné informativní zprávy a použít **WriteLine** příkaz, pokud chcete vytvořit jeden, dokončení zpráva.</span><span class="sxs-lookup"><span data-stu-id="a0003-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="a0003-110">K zápisu dokončení řádku</span><span class="sxs-lookup"><span data-stu-id="a0003-110">To write a complete line</span></span>  
  
1.  <span data-ttu-id="a0003-111">Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a0003-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="a0003-112">Návrat je připojen na konec zprávy, tato metoda vrátí hodnotu, tak, aby na další zprávu vrácený **zápisu**, **writeif –**, **WriteLine**, nebo  **Writelineif –** zahájíte na následující řádek:</span><span class="sxs-lookup"><span data-stu-id="a0003-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="a0003-113">K zápisu částečné řádku</span><span class="sxs-lookup"><span data-stu-id="a0003-113">To write a partial line</span></span>  
  
1.  <span data-ttu-id="a0003-114">Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a0003-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="a0003-115">Na další zprávu put **zápisu**, **writeif –**, **WriteLine**, nebo **writelineif –** zahájíte na stejném řádku jako zprávu, která umístí **zápisu** nebo **writeif –** příkaz:</span><span class="sxs-lookup"><span data-stu-id="a0003-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="a0003-116">Chcete-li ověřit to existují před i po provedení metody</span><span class="sxs-lookup"><span data-stu-id="a0003-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1.  <span data-ttu-id="a0003-117">Volání <xref:System.Diagnostics.Trace.Assert%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a0003-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a0003-118">Můžete použít **Assert** s trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="a0003-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="a0003-119">Tento příklad výstupu pro všechny naslouchací proces v zásobníku volání **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="a0003-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="a0003-120">Další informace najdete v tématu [kontrolní výrazy ve spravovaného kódu](/visualstudio/debugger/assertions-in-managed-code) a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0003-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0003-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0003-121">See Also</span></span>  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a0003-122">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="a0003-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="a0003-123">Postupy: vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="a0003-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="a0003-124">Trasování – přepínače</span><span class="sxs-lookup"><span data-stu-id="a0003-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="a0003-125">Trasování – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="a0003-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)