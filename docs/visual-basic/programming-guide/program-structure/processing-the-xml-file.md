---
title: "Zpracování souboru XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d44f58951d99f1b4b551af75dc0a0e895e337e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="7c7f5-102">Zpracování souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c7f5-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="7c7f5-103">Kompilátor generuje řetězec ID pro každý konstrukce ve vašem kódu, který se označí ke generování dokumentace.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="7c7f5-104">(Informace o tom, jak označit kódu najdete v tématu [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) ID řetězec jednoznačně identifikuje konstruktu.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="7c7f5-105">Programy, které zpracovávají soubor XML můžete použít ID řetězec k identifikaci odpovídající [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] položky metadat/reflexe.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="7c7f5-106">Soubor XML není znázornění hierarchické kódu; je to plochý seznam s generovaného ID pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="7c7f5-107">Kompilátor dodržuje následující pravidla, když ji vygeneruje ID řetězce:</span><span class="sxs-lookup"><span data-stu-id="7c7f5-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="7c7f5-108">Bez mezer je umístěn v řetězci.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="7c7f5-109">První část řetězec ID identifikuje druh člen, které jsou označené pomocí jednoho znaku následovaným dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="7c7f5-110">Se používají následující typy členů.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="7c7f5-111">Znak</span><span class="sxs-lookup"><span data-stu-id="7c7f5-111">Character</span></span>|<span data-ttu-id="7c7f5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7c7f5-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="7c7f5-113">N</span><span class="sxs-lookup"><span data-stu-id="7c7f5-113">N</span></span>|<span data-ttu-id="7c7f5-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="7c7f5-114">namespace</span></span><br /><br /> <span data-ttu-id="7c7f5-115">Dokumentační komentáře nelze přidat do oboru názvů, ale můžete vytvořit CREF odkazy, pokud je podporována.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="7c7f5-116">T</span><span class="sxs-lookup"><span data-stu-id="7c7f5-116">T</span></span>|<span data-ttu-id="7c7f5-117">Typ: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`</span><span class="sxs-lookup"><span data-stu-id="7c7f5-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="7c7f5-118">F</span><span class="sxs-lookup"><span data-stu-id="7c7f5-118">F</span></span>|<span data-ttu-id="7c7f5-119">pole:`Dim`</span><span class="sxs-lookup"><span data-stu-id="7c7f5-119">field: `Dim`</span></span>|  
|<span data-ttu-id="7c7f5-120">P</span><span class="sxs-lookup"><span data-stu-id="7c7f5-120">P</span></span>|<span data-ttu-id="7c7f5-121">Vlastnost: `Property` (včetně výchozí vlastnosti)</span><span class="sxs-lookup"><span data-stu-id="7c7f5-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="7c7f5-122">M</span><span class="sxs-lookup"><span data-stu-id="7c7f5-122">M</span></span>|<span data-ttu-id="7c7f5-123">Metoda: `Sub`, `Function`, `Declare`,`Operator`</span><span class="sxs-lookup"><span data-stu-id="7c7f5-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="7c7f5-124">E</span><span class="sxs-lookup"><span data-stu-id="7c7f5-124">E</span></span>|<span data-ttu-id="7c7f5-125">události:`Event`</span><span class="sxs-lookup"><span data-stu-id="7c7f5-125">event: `Event`</span></span>|  
|<span data-ttu-id="7c7f5-126">!</span><span class="sxs-lookup"><span data-stu-id="7c7f5-126">!</span></span>|<span data-ttu-id="7c7f5-127">Řetězec chyby.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-127">error string</span></span><br /><br /> <span data-ttu-id="7c7f5-128">Zbývající řetězec poskytuje informace o této chybě.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="7c7f5-129">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru generuje informace o chybě pro odkazy, které nelze rozpoznat.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-129">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="7c7f5-130">Druhá část `String` je plně kvalifikovaný název položky začínající na kořen oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="7c7f5-131">Název položky, jeho nadřazených typů a obor názvů jsou odděleny tečkami.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="7c7f5-132">Pokud název samotné položky obsahuje období, se nahrazují křížku (#).</span><span class="sxs-lookup"><span data-stu-id="7c7f5-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="7c7f5-133">Předpokládá se, že žádná položka má znaménko čísla přímo v jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="7c7f5-134">Třeba plně kvalifikovaný název `String` konstruktor by `System.String.#ctor`.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="7c7f5-135">Pro vlastnosti a metody Pokud jsou argumenty pro metodu, seznam argumentů uzavřený v závorkách následuje.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="7c7f5-136">Pokud neexistují žádné argumenty, jsou k dispozici žádné závorek.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="7c7f5-137">Argumenty, které jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-137">The arguments are separated by commas.</span></span> <span data-ttu-id="7c7f5-138">Kódování každý argument přímo řídí, jak je zakódován do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] podpis.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c7f5-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c7f5-139">Example</span></span>  
 <span data-ttu-id="7c7f5-140">Následující kód ukazuje, jak ID řetězce pro třídu a její členy se generují.</span><span class="sxs-lookup"><span data-stu-id="7c7f5-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7c7f5-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c7f5-141">See Also</span></span>  
 [<span data-ttu-id="7c7f5-142">/ DOC</span><span class="sxs-lookup"><span data-stu-id="7c7f5-142">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="7c7f5-143">Postupy: vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="7c7f5-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)