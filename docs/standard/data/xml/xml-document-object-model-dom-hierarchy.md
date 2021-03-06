---
title: Hierarchie modelu (DOM) objekt dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5b4ca249928200ddfc9dcd133ac673261046fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570169"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchie modelu (DOM) objekt dokumentu XML
Následující obrázek znázorňuje hierarchie tříd pro XML modelu DOM (Document Object), s World Wide Web Consortium (W3C) název do závorek společně s název třídy, kde je relevantní.  
  
 ![XML Document Object Model &#40;DOM&#41; hierarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchii XML modelu DOM (Document Object)  
  
 Následující třídy nedědí z **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** třída se používá k vytvoření dokumentu XML. Další informace najdete v tématu [vytvoření dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** třída zpracovává neuspořádaný sada uzlů. Další informace najdete v tématu [Neseřazený uzlu načítání podle názvu nebo Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** třída zpracovává seřazený seznam uzlů. Další informace najdete v tématu [načtení uzlu seřazené podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** třída zpracovává obslužné rutiny událostí zaregistrované na **třídou XMLDocument nastavenou na**. Další informace najdete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** třída dědí z **XmlNode**. Jejím účelem je přepsat dvě metody z **XmlNode**: **PreviousSibling** a **NextSibling** metody. Tyto metody přepsaného pak zděděná a používá **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, a **XmlProcessingInstruction**, které jsou třídy, které nemají stejné úrovně předchozí a další.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
