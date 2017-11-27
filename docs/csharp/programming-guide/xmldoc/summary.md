---
title: "&lt;Souhrn&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a8aa1f8a07019ff6ccefe90f03b217067ae22c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="603bf-102">&lt;Souhrn&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="603bf-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="603bf-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="603bf-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="603bf-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="603bf-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="603bf-105">Souhrn objektu.</span><span class="sxs-lookup"><span data-stu-id="603bf-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="603bf-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="603bf-106">Remarks</span></span>  
 <span data-ttu-id="603bf-107">\<Souhrnné > značka slouží k popisu typu nebo typ člena.</span><span class="sxs-lookup"><span data-stu-id="603bf-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="603bf-108">Použití [ \<Poznámky >](../../../csharp/programming-guide/xmldoc/remarks.md) přidat další informace o popis typu.</span><span class="sxs-lookup"><span data-stu-id="603bf-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="603bf-109">Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) k povolení nástrojů, dokumentace, jako [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření interní hypertextové odkazy na stránky dokumentace pro elementy kódu.</span><span class="sxs-lookup"><span data-stu-id="603bf-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="603bf-110">Text pro \<souhrnné > značky je jediný zdroj informací o typu v IntelliSense a se také zobrazí v okně prohlížeče objektů.</span><span class="sxs-lookup"><span data-stu-id="603bf-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="603bf-111">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="603bf-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="603bf-112">K vytvoření konečné dokumentaci založenou na soubor generované kompilátorem, můžete vytvořit vlastní nástroj nebo pomocí nástroje, jako například [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="603bf-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="603bf-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="603bf-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 <span data-ttu-id="603bf-114">Předchozí příklad vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="603bf-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="603bf-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="603bf-115">Example</span></span>  
 <span data-ttu-id="603bf-116">Následující příklad ukazuje, jak provádět `cref` odkaz na obecného typu.</span><span class="sxs-lookup"><span data-stu-id="603bf-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 <span data-ttu-id="603bf-117">Předchozí příklad vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="603bf-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="603bf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="603bf-118">See Also</span></span>  
 [<span data-ttu-id="603bf-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="603bf-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="603bf-120">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="603bf-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)