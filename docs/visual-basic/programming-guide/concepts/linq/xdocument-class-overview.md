---
title: Přehled XDocument třídy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 98ab095d67add2375eaf912ade71114c022b2ebb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651181"
---
# <a name="xdocument-class-overview-visual-basic"></a>Přehled XDocument třídy (Visual Basic)
Toto téma představuje <xref:System.Xml.Linq.XDocument> třídy.  
  
## <a name="overview-of-the-xdocument-class"></a>Přehled třídy XDocument  
 <xref:System.Xml.Linq.XDocument> Třída obsahuje informace potřebné pro platný dokument XML. To zahrnuje deklarace XML, zpracování pokyny a komentáře.  
  
 Všimněte si, že budete muset vytvořit <xref:System.Xml.Linq.XDocument> objekty, pokud potřebujete konkrétní funkce poskytované službou <xref:System.Xml.Linq.XDocument> třídy. V mnoha případech může spolupracovat přímo s <xref:System.Xml.Linq.XElement>. Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.  
  
 <xref:System.Xml.Linq.XDocument> odvozená z <xref:System.Xml.Linq.XContainer>. Proto může obsahovat podřízené uzly. Ale <xref:System.Xml.Linq.XDocument> objekty může mít pouze jednu podřízenou <xref:System.Xml.Linq.XElement> uzlu. Tento údaj zohledňuje standardní XML, že v dokumentu XML může existovat jenom jeden kořenový element.  
  
## <a name="components-of-xdocument"></a>Součástí XDocument  
 <xref:System.Xml.Linq.XDocument> Může obsahovat následující prvky:  
  
-   Jeden <xref:System.Xml.Linq.XDeclaration> objektu. <xref:System.Xml.Linq.XDeclaration> Umožňuje určit příslušné části deklarace XML: verze XML, kódování dokumentu, a jestli je samostatné dokumentu XML.  
  
-   Jeden <xref:System.Xml.Linq.XElement> objektu. Toto je kořenový uzel dokumentu XML.  
  
-   Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objekty. Zpracování instrukcí komunikuje informace, které aplikace, která zpracovává soubor XML.  
  
-   Libovolný počet <xref:System.Xml.Linq.XComment> objekty. Komentáře bude na stejné úrovni pro kořenový element. <xref:System.Xml.Linq.XComment> Objektu nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML a začněte komentář.  
  
-   Jeden <xref:System.Xml.Linq.XDocumentType> pro DTD.  
  
 Při serializaci <xref:System.Xml.Linq.XDocument>i v případě `XDocument.Declaration` je `null`, výstup bude mít deklarace XML, pokud má zapisovač `Writer.Settings.OmitXmlDeclaration` nastavena na `false` (výchozí).  
  
 Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví na verzi "1.0" a kódování "znakové sady utf-8".  
  
## <a name="using-xelement-without-xdocument"></a>Pomocí XElement bez XDocument  
 Jak už jsme zmínili, <xref:System.Xml.Linq.XElement> třída je hlavní třídy ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní. V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu. Pomocí <xref:System.Xml.Linq.XElement> třídu, můžete vytvořit strom XML, do ní přidejte další XML stromy, upravit stromu XML a uložte ho.  
  
## <a name="using-xdocument"></a>Pomocí XDocument  
 K vytvoření <xref:System.Xml.Linq.XDocument>, použít funkční konstrukce, stejně jako můžete vytvořit <xref:System.Xml.Linq.XElement> objekty.  
  
 Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objektu a jeho přidružených obsažené objekty.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Při kontrole souboru test.xml, získáte tento výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to přehled programování v XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
