---
title: "Serializace v rozhraní .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c97dc9b98f90af31c86af5295a7a4ad9894b428
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serialization-in-net"></a><span data-ttu-id="d52ed-102">Serializace v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d52ed-102">Serialization in .NET</span></span>
<span data-ttu-id="d52ed-103">Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu.</span><span class="sxs-lookup"><span data-stu-id="d52ed-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="d52ed-104">Doplňkovým serializace je deserializace, která převádí na objekt datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d52ed-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="d52ed-105">Tyto procesy dohromady, povolit, aby snadno ukládat a přenesených údaje.</span><span class="sxs-lookup"><span data-stu-id="d52ed-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="d52ed-106">Služeb .NET features dvě technologie serializace:</span><span class="sxs-lookup"><span data-stu-id="d52ed-106">.NET features two serialization technologies:</span></span>  
  
-   <span data-ttu-id="d52ed-107">Binární serializace zachová věrnost typu, což je užitečné pro zachování stav objektu mezi různé volání aplikace.</span><span class="sxs-lookup"><span data-stu-id="d52ed-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="d52ed-108">Například můžete sdílet objekt mezi různými aplikacemi pomocí jeho serializace do schránky.</span><span class="sxs-lookup"><span data-stu-id="d52ed-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="d52ed-109">Může serializovat objekt do datového proudu, na disk do paměti, v síti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d52ed-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="d52ed-110">Vzdálená komunikace používá serializace k předání objekty "hodnotou" z jedné domény počítače nebo aplikace do jiného.</span><span class="sxs-lookup"><span data-stu-id="d52ed-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
-   <span data-ttu-id="d52ed-111">Serializace XML serializuje pouze veřejné vlastnosti a pole a nezachovává věrnost typu.</span><span class="sxs-lookup"><span data-stu-id="d52ed-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="d52ed-112">To je užitečné, pokud chcete zadat nebo spotřebovat data bez omezení aplikace, která používá data.</span><span class="sxs-lookup"><span data-stu-id="d52ed-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="d52ed-113">Protože kód XML je otevřený standard, je to atraktivní volba pro sdílení dat v rámci webu.</span><span class="sxs-lookup"><span data-stu-id="d52ed-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="d52ed-114">Protokol SOAP je rovněž otevřený standard, díky čemuž je atraktivní výběru.</span><span class="sxs-lookup"><span data-stu-id="d52ed-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d52ed-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d52ed-115">In This Section</span></span>  
[<span data-ttu-id="d52ed-116">Postupy: témata serializace</span><span class="sxs-lookup"><span data-stu-id="d52ed-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="d52ed-117">Obsahuje seznam odkazů na témata s postupy, které jsou obsažené v této části.</span><span class="sxs-lookup"><span data-stu-id="d52ed-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="d52ed-118">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="d52ed-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="d52ed-119">Popisuje binární serializace mechanismus, který je součástí common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d52ed-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="d52ed-120">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d52ed-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="d52ed-121">Popisuje mechanismus serializace XML a SOAP, která je součástí common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d52ed-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="d52ed-122">Serializace nástroje</span><span class="sxs-lookup"><span data-stu-id="d52ed-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="d52ed-123">Tyto nástroje pomáhají při vývoji serializace kódu.</span><span class="sxs-lookup"><span data-stu-id="d52ed-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="d52ed-124">Ukázky serializace</span><span class="sxs-lookup"><span data-stu-id="d52ed-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="d52ed-125">Ukázky ukazují, jak provést serializace.</span><span class="sxs-lookup"><span data-stu-id="d52ed-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="d52ed-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d52ed-126">Reference</span></span>
<span data-ttu-id="d52ed-127"><xref:System.Runtime.Serialization>Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="d52ed-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="d52ed-128">Obsahuje třídy, které lze použít k serializaci objektů do formátu dokumentů XML nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="d52ed-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>