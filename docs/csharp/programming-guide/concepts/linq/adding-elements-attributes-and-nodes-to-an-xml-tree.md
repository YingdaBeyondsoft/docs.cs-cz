---
title: "Přidání prvky, atributy a uzly na strom XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbe7d00dc1a0b0ad5dcc7cbbedb1f2886f6ff2de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="6a95c-102">Přidání prvky, atributy a uzly na strom XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6a95c-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="6a95c-103">Obsah (elementy, atributy, komentáře, pokyny pro zpracování, text a CDATA) můžete přidat na stávající strom XML.</span><span class="sxs-lookup"><span data-stu-id="6a95c-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="6a95c-104">Metody pro přidávání obsahu</span><span class="sxs-lookup"><span data-stu-id="6a95c-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="6a95c-105">Následující metody přidat podřízené obsah tak, aby <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="6a95c-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="6a95c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a95c-106">Method</span></span>|<span data-ttu-id="6a95c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6a95c-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="6a95c-108">Přidá obsah na konci obsahu z podřízené <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="6a95c-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="6a95c-109">Přidá obsah na začátku podřízené obsah <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="6a95c-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="6a95c-110">Následující metody přidat jako uzly na stejné úrovni jako obsah <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="6a95c-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="6a95c-111">Nejběžnější uzel, do níž přidáváte obsah na stejné úrovni jako je <xref:System.Xml.Linq.XElement>, i když na stejné úrovni jako platný obsah na jiné typy uzlů můžete přidat například <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="6a95c-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="6a95c-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a95c-112">Method</span></span>|<span data-ttu-id="6a95c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6a95c-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="6a95c-114">Přidá obsah po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="6a95c-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="6a95c-115">Přidá obsahu před <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="6a95c-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a95c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a95c-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6a95c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6a95c-117">Description</span></span>  
 <span data-ttu-id="6a95c-118">Následující příklad vytvoří dvě stromy XML a pak upravením mezi stromy.</span><span class="sxs-lookup"><span data-stu-id="6a95c-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6a95c-119">Kód</span><span class="sxs-lookup"><span data-stu-id="6a95c-119">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="6a95c-120">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6a95c-120">Comments</span></span>  
 <span data-ttu-id="6a95c-121">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6a95c-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a95c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a95c-122">See Also</span></span>  
 [<span data-ttu-id="6a95c-123">Úprava XML stromů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6a95c-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)