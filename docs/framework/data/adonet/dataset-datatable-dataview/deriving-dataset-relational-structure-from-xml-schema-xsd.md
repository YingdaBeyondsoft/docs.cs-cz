---
title: Odvozování relační strukturu datové sady z schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 7599577c4e0f485e336e7f79a6c3bd17f0f0c316
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759605"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Odvozování relační strukturu datové sady z schématu XML (XSD)
Tato část obsahuje přehled o relační schéma `DataSet` je sestaven z dokument schématu XML definition language (XSD) schématu. Obecně platí, pro každou `complexType` podřízený prvek elementu schématu tabulky se generuje ve `DataSet`. Struktura tabulky je určen podle definice komplexního typu. Tabulky se vytváří v `DataSet` nejvyšší úrovně elementy ve schématu. Však tabulku je vytvořen pouze pro nejvyšší úroveň `complexType` element při `complexType` element vnořen uvnitř jiné `complexType` případ vnořený elementu, ve kterém `complexType` element je namapovaný na `DataTable` v rámci `DataSet`.  
  
 Další informace o XSD, najdete v části schématu XML World Wide Web Consortium (W3C) 0: Úvod do doporučení, část 1 schématu XML: struktury doporučení a XML schéma část 2: datové typy doporučení, nacházející se v [ http://www.w3.org/ ](http://www.w3.org/TR/).  
  
 Následující příklad ukazuje schématu XML kde `customers` je podřízený element `MyDataSet` element, který je **datovou sadu** elementu.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 V předchozím příkladu element `customers` je element komplexního typu. Proto je analýze definice komplexního typu, a proces mapování vytvoří v následující tabulce.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Datový typ jednotlivých sloupců v tabulce je odvozený od typu schématu XML odpovídající element nebo atribut.  
  
> [!NOTE]
>  Pokud element `customers` , jako je jednoduchý datový typ schématu XML **celé číslo**, je vygenerována žádná tabulka. Tabulky se vytváří jenom pro nejvyšší úrovně prvky, které jsou komplexní typy.  
  
 V následující schématu XML **schématu** element má dva podřízené elementy, `InStateCustomers` a `OutOfStateCustomers`.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Jak `InStateCustomers` a `OutOfStateCustomers` podřízené elementy jsou komplexní typ elementy (`customerType`). Proto proces mapování generuje následující dva identické tabulky v `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje elementy schématu XML použitý k vytvoření jedinečné a cizí klíče omezení `DataSet`.  
  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje elementy schématu XML použitý k vytvoření relace mezi sloupci tabulky v `DataSet`.  
  
 [Omezení schématu XML a relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Popisuje, jak vztahy jsou implicitně vytvořen při použití schématu XML elementů vytvořte omezení v `DataSet`.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak načíst a zachování relační struktura a data v `DataSet` jako XML data.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
