---
title: "Postupy: Přidání zpracování třídy pro směrovanou událost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abbbdce0ca12c4d8bdd12f616bf49c3d6f66f441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="35af8-102">Postupy: Přidání zpracování třídy pro směrovanou událost</span><span class="sxs-lookup"><span data-stu-id="35af8-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="35af8-103">Směrované události mohou být zpracovány, obslužné rutiny třídy nebo instance obslužné rutiny v každém uzlu dané trasy.</span><span class="sxs-lookup"><span data-stu-id="35af8-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="35af8-104">Obslužné rutiny třídy jsou vyvolány nejprve a lze implementace třídy potlačit události z instance zpracování nebo zavést další události konkrétní chování na události, které jsou vlastněny základní třídy.</span><span class="sxs-lookup"><span data-stu-id="35af8-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="35af8-105">Tento příklad ukazuje dva úzce související techniky pro implementaci třídy obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="35af8-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35af8-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="35af8-106">Example</span></span>  
 <span data-ttu-id="35af8-107">Tento příklad používá vlastní třídu na základě <xref:System.Windows.Controls.Canvas> panelu.</span><span class="sxs-lookup"><span data-stu-id="35af8-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="35af8-108">Základním předpokladem aplikace je, že vlastní třídu zavádí chování na její podřízené elementy, včetně zachycení, které klikne na možnost žádné levým tlačítkem myši a označování, které je zpracovat, než bude volána třída podřízeného prvku nebo všechny instance obslužné rutiny na něm.</span><span class="sxs-lookup"><span data-stu-id="35af8-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="35af8-109"><xref:System.Windows.UIElement> Třída zpřístupní virtuální metodu, která umožňuje třída zpracování na <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> událostí, jednoduše přepsáním události.</span><span class="sxs-lookup"><span data-stu-id="35af8-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="35af8-110">Toto je nejjednodušší způsob, jak implementovat třídu zpracování, pokud virtuální metoda je k dispozici někde v hierarchii vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="35af8-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="35af8-111">Následující kód ukazuje <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementace v "MyEditContainer" odvozený z <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="35af8-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="35af8-112">Implementace označí událost jako zpracována v argumenty, pak přidá určitý kód umožnit source element základní viditelné změny.</span><span class="sxs-lookup"><span data-stu-id="35af8-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="35af8-113">Žádné virtuální je k dispozici na základní třídy, nebo pro tuto konkrétní metodu, třídu zpracování mohou být přidány přímo pomocí metoda nástroj <xref:System.Windows.EventManager> třídy <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="35af8-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="35af8-114">Tato metoda by měla být volána pouze v rámci statických inicializaci třídy, které přidáváte třída zpracování.</span><span class="sxs-lookup"><span data-stu-id="35af8-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="35af8-115">Tento příklad přidá jinou obslužnou rutinu pro <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , a v takovém případě registrované třídy je třída, která vlastní.</span><span class="sxs-lookup"><span data-stu-id="35af8-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="35af8-116">Naproti tomu při použití virtuals, registrované třídy je ve skutečnosti <xref:System.Windows.UIElement> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="35af8-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="35af8-117">V případech, kde základní třídy a podtřídy registrovat třídu zpracování jsou vyvolány nejprve podtřídami obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="35af8-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="35af8-118">Chování v aplikaci bude, že nejprve by tato obslužná rutina zobrazit její okno se zprávou a potom by visual změnu v hodnotě obslužná rutina virtuální metoda zobrazí.</span><span class="sxs-lookup"><span data-stu-id="35af8-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="35af8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="35af8-119">See Also</span></span>  
 <xref:System.Windows.EventManager>  
 [<span data-ttu-id="35af8-120">Označení směrované události, protože zpracována a třídy zpracování</span><span class="sxs-lookup"><span data-stu-id="35af8-120">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="35af8-121">Popisovač směrované události</span><span class="sxs-lookup"><span data-stu-id="35af8-121">Handle a Routed Event</span></span>](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [<span data-ttu-id="35af8-122">Přehled směrované události</span><span class="sxs-lookup"><span data-stu-id="35af8-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)