---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f286d0f64478bfc46ca207086e4a6b918ee47b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576087"
---
# <a name="xml-documents-and-data"></a>Dokumenty a data XML
Rozhraní .NET Framework poskytuje komplexní a integrované sadu tříd, které vám umožní snadno vytvářet aplikace podporující rozhraní XML. Třídy v následujících oborů názvů podporují analýzy a zápis dat XML v paměti, ověřování dat a transformace XSLT pro úpravy XML.  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 Úplný seznam najdete v tématu [obory názvů System.Xml](https://msdn.microsoft.com/library/gg145036.aspx) webovou stránku.  
  
 Třídy v tyto obory názvů podporují doporučení World Wide Web Consortium (W3C). Příklad:  
  
-   <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Třída implementuje [základní úroveň 1 W3C Model Document Object (DOM)](https://www.w3.org/TR/REC-DOM-Level-1/) a [DOM úroveň 2 jádra](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.  
  
-   <xref:System.Xml.XmlReader?displayProperty=nameWithType> a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> třídy podpory [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v kódu XML](https://www.w3.org/TR/REC-xml-names/) doporučení.  
  
-   Schémata v <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídy podpory [W3C XML schéma část 1: struktury](https://www.w3.org/TR/xmlschema-1/) a [XML schéma část 2: datové typy](https://www.w3.org/TR/xmlschema-2/) doporučení.  
  
-   Třídy v <xref:System.Xml.Xsl?displayProperty=nameWithType> transformace XSLT podporu obor názvů, které odpovídají [W3C XSLT 1.0](http://www.w3.org/TR/xslt) doporučení.  
  
 Třídy XML v rozhraní .NET Framework poskytovat i tyto výhody:  
  
-   **Produktivitu.** [Technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) usnadňuje program s XML a poskytuje možnosti dotazu, které je podobná SQL.  
  
-   **Rozšiřitelnost.** Třídy XML v rozhraní .NET Framework jsou extensible prostřednictvím abstraktní základní třídy a virtuální metody. Například můžete vytvořit třídu odvozenou z <xref:System.Xml.XmlUrlResolver> třídu, která ukládá stream mezipaměti na místní disk.  
  
-   **Modulární architektura.** Rozhraní .NET Framework poskytuje architekturu, ve kterém součásti můžete využít jednu na druhou a Streamovat data mezi komponentami. Například úložiště dat, například <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu, lze je transformovat s <xref:System.Xml.Xsl.XslCompiledTransform> třídy a výstup pak může být buď do jiného úložiště datového proudu či vrácena jako datový proud z webové služby.  
  
-   **Výkon.** Pro lepší výkon aplikace některé třídy XML v rozhraní .NET Framework podporují model na základě streamování s následujícími charakteristikami:  
  
    -   Minimální ukládání do mezipaměti pro dopředné, pull model analýzu (<xref:System.Xml.XmlReader>).  
  
    -   Dopředné ověření (<xref:System.Xml.XmlReader>).  
  
    -   Navigace styl kurzor, který minimalizuje vytvoření uzlu do jednoho virtuálního uzlu při současném poskytování náhodný přístup k dokumentu (<xref:System.Xml.XPath.XPathNavigator>).  
  
     Pro lepší výkon při každém zpracování XSLT je požadováno, můžete použít <xref:System.Xml.XPath.XPathDocument> třída, která je úložišti optimalizované, jen pro čtení pro dotazy jazyka XPath navržený tak, aby efektivně pracovat <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
-   **Integrace s ADO.NET.** Třídy XML a [ADO.NET](../../../../docs/framework/data/adonet/index.md) jsou pevně integrovány sdružujícího relačních dat a XML. <xref:System.Data.DataSet> Třída je mezipaměť v paměti se data načtená z databáze. <xref:System.Data.DataSet> Třída má možnost číst a zapisovat XML pomocí <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy zachována jeho vnitřní relační schéma struktura jako schémat XML (XSD) a odvodit strukturu schématu dokumentu XML.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Možnosti zpracování XML](../../../../docs/standard/data/xml/xml-processing-options.md)  
 Popisuje možnosti pro zpracování dat XML.  
  
 [Zpracování dat XML v paměti](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 Popisuje tři modely pro zpracování XML data v paměti. [Technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> – třída (podle W3C Document Object Model) a <xref:System.Xml.XPath.XPathDocument> třídu (založenou na datovém modelu XPath).  
  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 Popisuje způsob použití procesoru XSLT.  
  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Popisuje třídy používané pro vytváření a manipulace s schémat XML (XSD) tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídy se načíst a upravit schéma.  
  
 [Integrace XML s relačními daty a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 Popisuje, jak rozhraní .NET Framework umožňuje v reálném čase, synchronní přístup k hierarchické a relační reprezentace dat prostřednictvím <xref:System.Data.DataSet> objektu a <xref:System.Xml.XmlDataDocument> objektu.  
  
 [Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 Popisuje, jak <xref:System.Xml.XmlNamespaceManager> třída se používá k uložení a správě informace oboru názvů.  
  
 [Podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 Popisuje, jak mapování typů dat XML do CLR typy, jak převést datové typy XML a další funkce, typ podpory v <xref:System.Xml> třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 Poskytuje informace o tom, jak získat přístup k datům s použitím technologie ADO.NET.  
  
 [Zabezpečení](../../../../docs/standard/security/index.md)  
 Obsahuje přehled systému zabezpečení rozhraní .NET Framework.  
  