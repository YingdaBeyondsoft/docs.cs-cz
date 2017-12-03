---
title: "Informační sadu po schématu kompilace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77fe1790a4ff2f910a740e969e458549f1fd9642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="db5a8-102">Informační sadu po schématu kompilace</span><span class="sxs-lookup"><span data-stu-id="db5a8-102">Post-Schema Compilation Infoset</span></span>
<span data-ttu-id="db5a8-103">[Doporučení schématu XML World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?linkid=45242) popisuje sady informace (informační sadu), musí se zveřejnit pro ověření schématu před a po schématu kompilace.</span><span class="sxs-lookup"><span data-stu-id="db5a8-103">The [World Wide Web Consortium (W3C) XML Schema Recommendation](http://go.microsoft.com/fwlink/?linkid=45242) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="db5a8-104">Model objektu schématu XML (SOM) zobrazení tato ohrožení před a po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána.</span><span class="sxs-lookup"><span data-stu-id="db5a8-104">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="db5a8-105">Informační sadu ověření před schématu je vytvořené během úprav schématu.</span><span class="sxs-lookup"><span data-stu-id="db5a8-105">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="db5a8-106">Po vygenerování informační sadu kompilace po schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána při kompilaci schématu a je k dispozici jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="db5a8-106">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="db5a8-107">SOM je model objektu, který představuje ověřování schématu před a po schématu kompilace infosets; skládá se ze třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="db5a8-107">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="db5a8-108">Všechny číst a Zapisovat vlastnosti třídy v <xref:System.Xml.Schema> obor názvů patří do informační ověření před schématu sadu při všechny jen pro čtení vlastnosti třídy v <xref:System.Xml.Schema> obor názvů patří do informační sadu kompilace po schématu.</span><span class="sxs-lookup"><span data-stu-id="db5a8-108">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="db5a8-109">Výjimkou z tohoto pravidla jsou následující vlastnosti, které jsou informační sadu ověřování schématu před a po schématu kompilace informační sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="db5a8-109">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="db5a8-110">Třída</span><span class="sxs-lookup"><span data-stu-id="db5a8-110">Class</span></span>|<span data-ttu-id="db5a8-111">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="db5a8-111">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="db5a8-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="db5a8-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="db5a8-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="db5a8-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="db5a8-114">Například <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaComplexType> třídy oba mají `BlockResolved` a `FinalResolved` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="db5a8-114">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="db5a8-115">Tyto vlastnosti jsou používané pro udržení hodnoty `Block` a `Final` vlastnosti po schématu byl zkompilován a ověřit.</span><span class="sxs-lookup"><span data-stu-id="db5a8-115">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="db5a8-116">`BlockResolved`a `FinalResolved` jsou jen pro čtení vlastnosti, které jsou součástí informační sadu kompilace po schématu.</span><span class="sxs-lookup"><span data-stu-id="db5a8-116">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="db5a8-117">Následující příklad ukazuje <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> třídy sady po ověření schématu.</span><span class="sxs-lookup"><span data-stu-id="db5a8-117">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="db5a8-118">Před ověřování, obsahuje vlastnost `null` odkaz a <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je nastavena na název typu nejistá.</span><span class="sxs-lookup"><span data-stu-id="db5a8-118">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="db5a8-119">Po ověření <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je přeložit na platný typ, a objekt typu je k dispozici prostřednictvím <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="db5a8-119">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="db5a8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="db5a8-120">See Also</span></span>  
 [<span data-ttu-id="db5a8-121">Objektový Model schématu XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="db5a8-121">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)