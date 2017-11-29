---
title: "Jazykové funkce jazyka XAML 2009"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 6299a29cb79650eb59df3f198c3ea3fcd49d0076
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-2009-language-features"></a><span data-ttu-id="1188d-102">Jazykové funkce jazyka XAML 2009</span><span class="sxs-lookup"><span data-stu-id="1188d-102">XAML 2009 Language Features</span></span>
<span data-ttu-id="1188d-103">XAML 2009 je sdružená termín pro nové funkce jazyka XAML, které rozšiřují existující specifikace jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="1188d-103">XAML 2009 is the shorthand term for new XAML language features that extend the existing XAML language specification.</span></span> <span data-ttu-id="1188d-104">XAML 2009 zavádí několik nových direktivách a konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1188d-104">XAML 2009 introduces several new directives and constructs.</span></span> <span data-ttu-id="1188d-105">Patří mezi ně[x: Arguments – direktiva](../../../docs/framework/xaml-services/x-arguments-directive.md); [x: factorymethod – direktiva](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x: Reference – rozšíření značek](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x: TypeArguments – direktiva ](../../../docs/framework/xaml-services/x-typearguments-directive.md); a vestavěné typy pro běžné primitiv jazyka (například `x:Char`).</span><span class="sxs-lookup"><span data-stu-id="1188d-105">These include the[x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md); the [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md); the [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md); the [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md); and built-in types for common language primitives (for example `x:Char`).</span></span>  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a><span data-ttu-id="1188d-106">Podpora jazyka XAML 2009 v WPF a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1188d-106">XAML 2009 Support in WPF and Visual Studio</span></span>  
 <span data-ttu-id="1188d-107">V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009, ale jenom pro jazyk XAML, který není WPF zkompilovat kód.</span><span class="sxs-lookup"><span data-stu-id="1188d-107">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="1188d-108">Zkompilovaný kód XAML a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.</span><span class="sxs-lookup"><span data-stu-id="1188d-108">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>  
  
 <span data-ttu-id="1188d-109">Nezapomeňte, že existující techniky pro načítání přijít XAML v grafickém subsystému WPF také mít možné zabezpečení a přístup omezení pro typy CLR a systém typů více omezující než zkompilovat kód XAML.</span><span class="sxs-lookup"><span data-stu-id="1188d-109">Note that existing techniques for loading loose XAML in WPF also have possible security and access restrictions to CLR types and the type system that are more restrictive than for markup-compiled XAML.</span></span> <span data-ttu-id="1188d-110">Další informace najdete v tématu [zabezpečení (WPF)](../../../docs/framework/wpf/security-wpf.md) nebo [strategie zabezpečení WPF - platformy zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="1188d-110">For more information, see [Security (WPF)](../../../docs/framework/wpf/security-wpf.md) or [WPF Security Strategy - Platform Security](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
 <span data-ttu-id="1188d-111">Také zavádí další funkce, upravte předchozí 2006 XAML XAML 2009 konstrukce nebo který měnit základní značek formuláře.</span><span class="sxs-lookup"><span data-stu-id="1188d-111">XAML 2009 also introduces additional features that either modify the previous XAML 2006 constructs or that modify the basic markup forms.</span></span>  
  
### <a name="xkey-as-an-object-element"></a><span data-ttu-id="1188d-112">x: Key jako Element objektu</span><span class="sxs-lookup"><span data-stu-id="1188d-112">x:Key as an Object Element</span></span>  
 <span data-ttu-id="1188d-113">Může podporovat XAML 2009 `x:Key` jako objekt (na vlastnost element, který má hodnotu elementu objektu); však XAML 2006 podporuje jenom `x:Key` jako atribut.</span><span class="sxs-lookup"><span data-stu-id="1188d-113">XAML 2009 can support `x:Key` as an object (a property element that has object element value); however, XAML 2006 only supported `x:Key` as an attribute.</span></span> <span data-ttu-id="1188d-114">Najdete v části "XAML 2009" [x: Key – direktiva](../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="1188d-114">See the "XAML 2009" section of [x:Key Directive](../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
### <a name="xmlns-on-property-elements"></a><span data-ttu-id="1188d-115">atribut xmlns u vlastností elementů</span><span class="sxs-lookup"><span data-stu-id="1188d-115">xmlns on Property Elements</span></span>  
 <span data-ttu-id="1188d-116">XAML 2009 může podporovat definice oboru názvů (xmlns) XAML na elementy vlastnost; XAML 2006 však podporuje pouze xmlns definice na elementy objektu.</span><span class="sxs-lookup"><span data-stu-id="1188d-116">XAML 2009 can support XAML namespace (xmlns) definitions on property elements; however, XAML 2006 only supports xmlns definitions on object elements.</span></span>  
  
### <a name="event-attributes"></a><span data-ttu-id="1188d-117">Atributy událostí</span><span class="sxs-lookup"><span data-stu-id="1188d-117">Event Attributes</span></span>  
 <span data-ttu-id="1188d-118">Pro atributy, které jsou zajišťované události XAML 2006 předpokládá, že kompilace kódu se tak zapojí a odesílá události, které kompilace kódu.</span><span class="sxs-lookup"><span data-stu-id="1188d-118">For attributes that are backed by events, XAML 2006 presumes that markup compilation is involved and submits the events to markup compilation.</span></span> <span data-ttu-id="1188d-119">XAML 2009 podporuje značku formuláře, který vypadá takto: rozšíření značek, které odkládat údaje spojení události do doby běhu analýzy a načítání XAML.</span><span class="sxs-lookup"><span data-stu-id="1188d-119">XAML 2009 supports a markup form that resembles a markup extension, which defers the event wiring until run-time parsing and loading of the XAML.</span></span> <span data-ttu-id="1188d-120">Však aplikace WPF a scénáře XAML pro uživatelské rozhraní WPF obecně nepoužívejte tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="1188d-120">However, WPF applications and XAML scenarios for WPF UI generally do not use this capability.</span></span> <span data-ttu-id="1188d-121">WPF a jeho implementace XAML 2006 používá kombinaci spojení obslužné rutiny události pro směrované události definované na <xref:System.Windows.UIElement> úroveň a jeho značek kompilátoru krok pro většinu jeho atribut zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="1188d-121">WPF and its XAML 2006 implementation uses the combination of event handler wiring for routed events defined at the <xref:System.Windows.UIElement> level and its markup compiler step for much of its event attribute processing.</span></span> <span data-ttu-id="1188d-122">Kompilátor značek také upraví žádné atributy událostí najít v jazyce XAML, kde akce sestavení deklarovat, že se používá kompilátoru značek.</span><span class="sxs-lookup"><span data-stu-id="1188d-122">The markup compiler also preprocesses any event attributes found in XAML where the build actions declare that the markup compiler is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1188d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1188d-123">See Also</span></span>  
 [<span data-ttu-id="1188d-124">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1188d-124">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)