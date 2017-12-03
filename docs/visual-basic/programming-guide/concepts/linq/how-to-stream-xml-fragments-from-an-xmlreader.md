---
title: 'Postupy: Stream fragmenty XML z objekt XmlReader (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f18c922208fb52ffa775bd36e76c74f04d60f3b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="c4809-102">Postupy: Stream fragmenty XML z objekt XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4809-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="c4809-103">Až budete mít ke zpracování velkých souborů XML, nemusí být vhodný načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="c4809-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="c4809-104">Toto téma ukazuje, jak k vysílání datového proudu fragmenty pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c4809-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="c4809-105">Jedním z nejúčinnějších způsobů, jak používat <xref:System.Xml.XmlReader> číst <xref:System.Xml.Linq.XElement> objektů je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="c4809-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="c4809-106">Metodu osy, jako obvykle vrátí kolekci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c4809-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="c4809-107">V metodě vlastní osy, po vytvoření XML fragment voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda, vrátí kolekce používá `yield return`.</span><span class="sxs-lookup"><span data-stu-id="c4809-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="c4809-108">To poskytuje sémantiku odložené provedení metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="c4809-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="c4809-109">Když vytvoříte strom XML z <xref:System.Xml.XmlReader> objekt, <xref:System.Xml.XmlReader> musí být umístěn v elementu.</span><span class="sxs-lookup"><span data-stu-id="c4809-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="c4809-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nevrátí před přečtením značka ukončení elementu.</span><span class="sxs-lookup"><span data-stu-id="c4809-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="c4809-111">Pokud chcete vytvořit částečné stromové struktury, můžete vytvořit instanci <xref:System.Xml.XmlReader>, pozice čtenáře na uzlu, který chcete převést na <xref:System.Xml.Linq.XElement> stromu a pak vytvořte <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="c4809-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="c4809-112">Téma [postup: datový proud XML fragmenty se přístup k informacím o záhlaví (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad o tom, jak stream složitější dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c4809-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="c4809-113">Téma [postup: provedení vysílání datového proudu transformace z velké dokumentů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití technologie LINQ to XML k transformaci velmi velký dokumentů XML při zachování nároků paměti.</span><span class="sxs-lookup"><span data-stu-id="c4809-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4809-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4809-114">Example</span></span>  
 <span data-ttu-id="c4809-115">Tento příklad vytvoří vlastní osy metoda.</span><span class="sxs-lookup"><span data-stu-id="c4809-115">This example creates a custom axis method.</span></span> <span data-ttu-id="c4809-116">Se můžete dotazovat pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="c4809-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="c4809-117">Metodu vlastní osy `StreamRootChildDoc`, je metoda, která je určená speciálně pro čtení dokumentu, který má opakující se `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="c4809-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="c4809-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4809-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="c4809-119">V tomto příkladu jsou velmi malé zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="c4809-119">In this example, the source document is very small.</span></span> <span data-ttu-id="c4809-120">Ale i v případě, že bylo miliony `Child` elementy, v tomto příkladu by mít stále malou paměťovou zátěž.</span><span class="sxs-lookup"><span data-stu-id="c4809-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4809-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4809-121">See Also</span></span>  
 [<span data-ttu-id="c4809-122">Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4809-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [<span data-ttu-id="c4809-123">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4809-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)