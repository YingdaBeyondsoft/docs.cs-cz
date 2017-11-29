---
title: "Průvodce programováním (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7ee6ac9d13d265442e6d5b9f02c6d5788e75c50f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="programming-guide-linq-to-xml-c"></a><span data-ttu-id="7427b-102">Průvodce programováním (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-102">Programming Guide (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7427b-103">Tato část obsahuje informace o programování s koncepční a postupy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7427b-103">This section provides conceptual and how-to information about programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
## <a name="who-should-read-this-documentation"></a><span data-ttu-id="7427b-104">Komu je tato dokumentace určen</span><span class="sxs-lookup"><span data-stu-id="7427b-104">Who Should Read This Documentation</span></span>  
 <span data-ttu-id="7427b-105">Tato dokumentace cílem vývojáře, kteří již pochopit C# a některé základní aspekty [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7427b-105">This documentation targets developers who already understand C# and some basic aspects of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="7427b-106">Cílem této dokumentace je aby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] snadno použitelný pro všechny typy vývojářů.</span><span class="sxs-lookup"><span data-stu-id="7427b-106">The goal of this documentation is to make [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] easy to use for all kinds of developers.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7427b-107">usnadňuje programování XML.</span><span class="sxs-lookup"><span data-stu-id="7427b-107"> makes XML programming easier.</span></span> <span data-ttu-id="7427b-108">Nemusíte být vývojář odborné ji použít.</span><span class="sxs-lookup"><span data-stu-id="7427b-108">You do not have to be an expert developer to use it.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7427b-109">založena na obecných tříd.</span><span class="sxs-lookup"><span data-stu-id="7427b-109"> relies heavily on generic classes.</span></span> <span data-ttu-id="7427b-110">Je proto velmi důležité, abyste rozuměli tomu použití obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="7427b-110">Therefore, is very important that you understand the use of generic classes.</span></span> <span data-ttu-id="7427b-111">Navíc je užitečné, pokud jste se seznámili s delegáti, které jsou deklarované jako parametrizované typy.</span><span class="sxs-lookup"><span data-stu-id="7427b-111">Further, it is helpful if you are familiar with delegates that are declared as parameterized types.</span></span> <span data-ttu-id="7427b-112">Pokud nejste obeznámeni s C# obecné třídy, přečtěte si téma [obecné třídy](../../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7427b-112">If you are not familiar with C# generic classes, see [Generic Classes](../../../../csharp/programming-guide/generics/generic-classes.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7427b-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7427b-113">In This Section</span></span>  
  
|<span data-ttu-id="7427b-114">Téma</span><span class="sxs-lookup"><span data-stu-id="7427b-114">Topic</span></span>|<span data-ttu-id="7427b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7427b-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7427b-116">Technologie LINQ to XML přehled programování (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-116">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|<span data-ttu-id="7427b-117">Obsahuje přehled [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] třídy a podrobné informace o tři nejdůležitější tříd: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, a <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="7427b-117">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, and detailed information about three of the most important classes: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, and <xref:System.Xml.Linq.XDocument>.</span></span>|  
|[<span data-ttu-id="7427b-118">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-118">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|<span data-ttu-id="7427b-119">Poskytuje informace o vytváření stromů XML koncepční a založený na úlohách.</span><span class="sxs-lookup"><span data-stu-id="7427b-119">Provides conceptual and task-based information about creating XML trees.</span></span> <span data-ttu-id="7427b-120">Stromy XML můžete vytvořit pomocí funkční konstrukce nebo analýzou textu XML z řetězce nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="7427b-120">You can create XML trees by using functional construction, or by parsing XML text from a string or a file.</span></span> <span data-ttu-id="7427b-121">Můžete použít také <xref:System.Xml.XmlReader> k naplnění strom XML.</span><span class="sxs-lookup"><span data-stu-id="7427b-121">You can also use an <xref:System.Xml.XmlReader> to populate an XML tree.</span></span>|  
|[<span data-ttu-id="7427b-122">Práce s obory názvů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-122">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|<span data-ttu-id="7427b-123">Poskytuje podrobné informace o vytváření stromů XML, které používají obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7427b-123">Provides detailed information about creating XML trees that use namespaces.</span></span>|  
|[<span data-ttu-id="7427b-124">Serializace XML stromů (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-124">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|<span data-ttu-id="7427b-125">Popisuje více přístupy k serializaci strom XML a poskytuje pokyny k jaký přístup k použití.</span><span class="sxs-lookup"><span data-stu-id="7427b-125">Describes multiple approaches to serializing an XML tree, and gives guidance on which approach to use.</span></span>|  
|[<span data-ttu-id="7427b-126">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-126">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|<span data-ttu-id="7427b-127">Uvádí a popisuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy metody, které je třeba porozumět před zápisem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="7427b-127">Enumerates and describes the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis methods, which you must understand before you can write [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>|  
|[<span data-ttu-id="7427b-128">Dotazování stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-128">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|<span data-ttu-id="7427b-129">Obsahuje běžné příklady dotazování stromy XML.</span><span class="sxs-lookup"><span data-stu-id="7427b-129">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="7427b-130">Úprava XML stromů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|<span data-ttu-id="7427b-131">Modelu DOM (Document Object), jako například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete upravit strom XML na místě.</span><span class="sxs-lookup"><span data-stu-id="7427b-131">Like the Document Object Model (DOM), [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enables you to modify an XML tree in place.</span></span>|  
|[<span data-ttu-id="7427b-132">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|<span data-ttu-id="7427b-133">Poskytuje informace o poznámky, události, streamování a další pokročilé scénáře.</span><span class="sxs-lookup"><span data-stu-id="7427b-133">Provides information about annotations, events, streaming, and other advanced scenarios.</span></span>|  
|[<span data-ttu-id="7427b-134">Technologie LINQ to XML zabezpečení (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-134">LINQ to XML Security (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|<span data-ttu-id="7427b-135">Popisuje problémy se zabezpečením přidružené technologie LINQ to XML a obsahuje některé pokyny pro minimalizaci ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7427b-135">Describes security issues associated with LINQ to XML and provides some guidance for mitigating security exposure.</span></span>|  
|[<span data-ttu-id="7427b-136">Dokumenty XML ukázkové (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7427b-136">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|<span data-ttu-id="7427b-137">Obsahuje ukázkové XML dokumenty, které jsou používány mnoho příklady v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="7427b-137">Contains the sample XML documents that are used by many examples in this documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7427b-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="7427b-138">See Also</span></span>  
 [<span data-ttu-id="7427b-139">Začínáme (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7427b-139">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [<span data-ttu-id="7427b-140">Technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7427b-140">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)