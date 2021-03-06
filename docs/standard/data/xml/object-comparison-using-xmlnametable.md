---
title: Objekt porovnání pomocí XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09f717cb4c09c1e35b9472b7b549f1d3edf0dd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569275"
---
# <a name="object-comparison-using-xmlnametable"></a>Objekt porovnání pomocí XmlNameTable
**XmlDocuments**, při vytváření, máte název tabulky vytvořené speciálně pro tento dokument. Pokud načten do dokumentu nebo se vytvářejí nové elementy nebo atributy, názvy elementu a atributu jsou vloženy do **XmlNameTable**. Můžete taky vytvořit **třídou XMLDocument nastavenou na** použití stávající **tabulky názvů** z jiného dokumentu. Když **XmlDocuments** jsou vytvořeny pomocí konstruktor, který přebírá **XmlNameTable** parametr dokument má přístup k uzlu názvy, obory názvů a předpony, které jsou již uloženy v  **XmlNameTable**. Bez ohledu na to, jak načíst název tabulky s názvy, jakmile se názvy jsou uložené v tabulce, názvy lze porovnat rychle pomocí objektu porovnání místo porovnání řetězců. Řetězce lze také přidat název tabulky pomocí <xref:System.Xml.NameTable.Add%2A>. Následující příklad kódu ukazuje název tabulky vytváří a řetězec **MyString** přidávané do tabulky. Potom **třídou XMLDocument nastavenou na** je vytvořený pomocí této tabulky a názvy elementu a atributu v **Myfile.xml** jsou přidány do existující název tabulky.  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 Následující příklad kódu ukazuje vytvoření dokumentu, dva nové prvky, který se přidává do dokumentu, který je také přidá do dokumentu název tabulky a porovnání objektu na názvy.  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 Výše uvedené scénáře předávají mezi dva dokumenty název tabulky je typické, když stejného typu dokumentu, jsou zpracovávány opakovaně, jako jsou dokumenty pořadí v lokalitě elektronické obchodování, která vyhovují schématu XML definition language (XSD) schéma nebo dokument typ definice (DTD) a stejné řetězce se opakují. Pomocí stejné název tabulky dává zlepšení výkonu, jako stejným názvem elementu dochází v více dokumentů.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
