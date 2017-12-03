---
title: "Postupy: Určení modifikační klávesy, která byla stisknuta"
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
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fdc93063bbc8c9428f2f01c6cd5c0578e77ab01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="5d23c-102">Postupy: Určení modifikační klávesy, která byla stisknuta</span><span class="sxs-lookup"><span data-stu-id="5d23c-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="5d23c-103">Když vytvoříte aplikaci, která podporuje stisknutí kláves uživatele, můžete také monitorovat modifikační klávesy třeba klávesy SHIFT, ALT a CTRL.</span><span class="sxs-lookup"><span data-stu-id="5d23c-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="5d23c-104">Při stisknutí modifikační klávesy v kombinaci s jiných klíčů nebo kliknutími myši, vaše aplikace může reagovat správně.</span><span class="sxs-lookup"><span data-stu-id="5d23c-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="5d23c-105">Například pokud stisknutí písmeno S to může způsobit jednoduše "s" zobrazí na obrazovce, ale pokud stisknutí kláves CTRL + S, mohou být uloženy aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5d23c-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="5d23c-106">Pokud zpracováváte <xref:System.Windows.Forms.Control.KeyDown> událostí, <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> obdržel událost obslužné rutiny Určuje, které modifikační klávesy stisknutí.</span><span class="sxs-lookup"><span data-stu-id="5d23c-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="5d23c-107">Případně <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> Určuje znak, která byla stisknuta stejně jako jakýkoli modifikační klávesy v kombinaci s bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="5d23c-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="5d23c-108">Ale pokud jsou zpracování <xref:System.Windows.Forms.Control.KeyPress> událostí nebo myš událost, obslužné rutiny události neobdrží tyto informace.</span><span class="sxs-lookup"><span data-stu-id="5d23c-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="5d23c-109">V takovém případě musíte použít <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnost <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="5d23c-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="5d23c-110">V obou případech je třeba provést bitové operace AND příslušné <xref:System.Windows.Forms.Keys> hodnota a hodnota testování.</span><span class="sxs-lookup"><span data-stu-id="5d23c-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="5d23c-111"><xref:System.Windows.Forms.Keys> Výčtu nabízí variace každý modifikační klávesy, proto je důležité provést bitové hodnotě a s správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5d23c-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="5d23c-112">Například je reprezentována klávesu SHIFT <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> a <xref:System.Windows.Forms.Keys.LShiftKey> správnou hodnotu pro testovací SHIFT, jako je modifikační klávesy <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="5d23c-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="5d23c-113">Podobně testování pro řadič a ALT jako modifikátory můžete využít <xref:System.Windows.Forms.Keys.Control> a <xref:System.Windows.Forms.Keys.Alt> hodnoty v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5d23c-113">Similarly, to test for CTLR and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d23c-114">Programátory v jazyce Visual Basic je přístupný také informace o klíči prostřednictvím <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="5d23c-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="5d23c-115">K určení modifikační klávesy, která byla stisknuta</span><span class="sxs-lookup"><span data-stu-id="5d23c-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="5d23c-116">Použít bitové hodnotě `AND` operátor s <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnosti a hodnotu <xref:System.Windows.Forms.Keys> výčtu k určení, zda stisknutí konkrétní modifikační klávesy.</span><span class="sxs-lookup"><span data-stu-id="5d23c-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="5d23c-117">Následující příklad kódu ukazuje, jak určit, zda je v rámci stisknutí klávesy SHIFT <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5d23c-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5d23c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d23c-118">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [<span data-ttu-id="5d23c-119">Vstup z klávesnice ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="5d23c-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="5d23c-120">Postupy: určí, zda CapsLock – na v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d23c-120">How to: Determine If CapsLock is On in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/91e60f5c-dd61-4222-ba5f-39af803afd8c)