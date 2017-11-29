---
title: "x:Type – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: ed0372349a08687fd83b0fc989cc4cb88c29d96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="00096-102">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="00096-102">x:Type Markup Extension</span></span>
<span data-ttu-id="00096-103">Poskytuje modulu CLR <xref:System.Type> objekt, který je základní typ pro zadaný typ jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="00096-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="00096-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="00096-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="00096-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="00096-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="00096-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="00096-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="00096-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="00096-107">Optional.</span></span> <span data-ttu-id="00096-108">Předpona, která se mapuje jiné než výchozí oboru názvů jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="00096-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="00096-109">Zadání předpony není často nutné.</span><span class="sxs-lookup"><span data-stu-id="00096-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="00096-110">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="00096-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="00096-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="00096-111">Required.</span></span> <span data-ttu-id="00096-112">Název typu přeložit na aktuální výchozí XAML obor názvů; nebo zadané mapování předpony Pokud `prefix` pochází.</span><span class="sxs-lookup"><span data-stu-id="00096-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00096-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00096-113">Remarks</span></span>  
 <span data-ttu-id="00096-114">`x:Type` Podobné funkce, která se má – rozšíření značek `typeof()` operátor v [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] nebo `GetType` operátor v [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00096-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] or the `GetType` operator in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span></span>  
  
 <span data-ttu-id="00096-115">`x:Type` – Rozšíření značek poskytuje chování převod z řetězce pro vlastnosti, které typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="00096-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="00096-116">Vstup je typ jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="00096-116">The input is a XAML type.</span></span> <span data-ttu-id="00096-117">Vztah mezi vstupní typ jazyka XAML a výstup CLR <xref:System.Type> je, že výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupu <xref:System.Xaml.XamlType>, po vyhledávání nezbytné <xref:System.Xaml.XamlType> na základě kontextu schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver>service poskytuje kontext.</span><span class="sxs-lookup"><span data-stu-id="00096-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="00096-118">V rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.TypeExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="00096-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="00096-119">V implementacích konkrétní framework některé vlastnosti, které přebírají <xref:System.Type> jako hodnotu může přijmout název typu přímo (s řetězcovou hodnotou obsahující typ `Name`).</span><span class="sxs-lookup"><span data-stu-id="00096-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="00096-120">Implementace toto chování je však komplexní scénář.</span><span class="sxs-lookup"><span data-stu-id="00096-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="00096-121">Příklady najdete v části "Poznámky pro použití WPF", který následuje.</span><span class="sxs-lookup"><span data-stu-id="00096-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="00096-122">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="00096-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="00096-123">Token řetězec zadaný po `x:Type` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.TypeExtension.TypeName%2A> hodnotu základní <xref:System.Windows.Markup.TypeExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="00096-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="00096-124">V části výchozí kontext schématu XAML pro rozhraní .NET Framework XAML Services, která je založena na typy CLR, hodnota tohoto atributu je buď <xref:System.Reflection.MemberInfo.Name%2A> požadovaného typu, nebo který obsahuje <xref:System.Reflection.MemberInfo.Name%2A> sebou předponu pro obor názvů jiný než výchozí XAML mapování.</span><span class="sxs-lookup"><span data-stu-id="00096-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="00096-125">`x:Type` – Rozšíření značek mohou být používány syntaxe element objektu.</span><span class="sxs-lookup"><span data-stu-id="00096-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="00096-126">V takovém případě určující hodnotu <xref:System.Windows.Markup.TypeExtension.TypeName%2A> vlastnost je potřeba správně inicializovat rozšíření.</span><span class="sxs-lookup"><span data-stu-id="00096-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="00096-127">`x:Type` – Rozšíření značek lze také jako atribut podrobné; však není toto použití typické: `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="00096-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="00096-128">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="00096-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="00096-129">Výchozí Namespace XAML a mapování typu</span><span class="sxs-lookup"><span data-stu-id="00096-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="00096-130">Výchozí obor názvů jazyka XAML pro programování WPF obsahuje většinu typů XAML, které jsou potřeba pro typické scénáře XAML; Při odkazování na hodnoty typu XAML proto můžete vyhnout často předpony.</span><span class="sxs-lookup"><span data-stu-id="00096-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="00096-131">Možná budete muset namapovat předpony, pokud odkazujete typu z vlastního sestavení nebo pro typy, které existují v sestavení WPF, ale jsou od CLR oboru názvů, který nebyl namapovaný na výchozí obor názvů jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="00096-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="00096-132">Další informace o předpony, obory názvů jazyka XAML a obory názvů mapování CLR najdete v tématu [obory názvů jazyka XAML a mapování Namespace pro jazyk XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="00096-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="00096-133">Zadejte vlastnosti tento podporu Typename – jako – řetězec</span><span class="sxs-lookup"><span data-stu-id="00096-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="00096-134">WPF podporuje techniky, které umožňují určující hodnotu některých vlastností typu <xref:System.Type> bez nutnosti `x:Type` využití rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="00096-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="00096-135">Místo toho můžete zadat hodnotu jako řetězec, který názvy typu.</span><span class="sxs-lookup"><span data-stu-id="00096-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="00096-136">Příklady jsou <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> a <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="00096-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="00096-137">Podpora pro toto chování není k dispozici prostřednictvím převaděče typů nebo rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="00096-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="00096-138">Místo toho jedná o odložení chování implementuje pomocí <xref:System.Windows.FrameworkElementFactory>.</span><span class="sxs-lookup"><span data-stu-id="00096-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="00096-139">Program Silverlight podporuje podobné konvence.</span><span class="sxs-lookup"><span data-stu-id="00096-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="00096-140">Ve skutečnosti Silverlight aktuálně nepodporuje `{x:Type}` v jeho podporu jazyka XAML a nepřijímá `{x:Type}` použití mimo za určitých okolností, které jsou určeny pro podporu migrace WPF Silverlight XAML.</span><span class="sxs-lookup"><span data-stu-id="00096-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="00096-141">Proto je integrovaný do všech testování nativní vlastnost Silverlight chování typename jako řetězec kde <xref:System.Type> je hodnota.</span><span class="sxs-lookup"><span data-stu-id="00096-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="00096-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="00096-142">XAML 2009</span></span>  
 <span data-ttu-id="00096-143">XAML 2009 poskytuje další podporu pro obecné typy a mění chování funkce `x:TypeArguments` a `x:Type` pro tuto funkci podporují.</span><span class="sxs-lookup"><span data-stu-id="00096-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="00096-144">`x:TypeArguments`a element přidruženého objektu pro vytváření instancí obecný objekt může být u jiných elementů než kořenu.</span><span class="sxs-lookup"><span data-stu-id="00096-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="00096-145">Další informace najdete v části "XAML 2009" [x: TypeArguments – direktiva](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="00096-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="00096-146">XAML 2009 podporuje syntaxi pro určení omezení obecného typu v kódu.</span><span class="sxs-lookup"><span data-stu-id="00096-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="00096-147">To mohou být využívána `x:TypeArguments`, pomocí `x:Type`, nebo tyto dvě funkce v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="00096-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="00096-148">Implementace WPF XAML při zpracování jazyka XAML 2009, pro zatížení tato funkce také přidá do chování typu implicitní převod některé vlastnosti framework, které používají typ <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="00096-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="00096-149">V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009 ale jenom pro přijít XAML (XAML, který zkompiluje značek není).</span><span class="sxs-lookup"><span data-stu-id="00096-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="00096-150">Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.</span><span class="sxs-lookup"><span data-stu-id="00096-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00096-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="00096-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="00096-152">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="00096-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="00096-153">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="00096-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="00096-154">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="00096-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)