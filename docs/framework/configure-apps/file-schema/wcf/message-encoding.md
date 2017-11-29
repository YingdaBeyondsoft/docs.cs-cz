---
title: "Kódování zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec7a85e95de9608d7a7daff11d70c9da3ff82989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="message-encoding"></a><span data-ttu-id="4c4cc-102">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="4c4cc-102">Message Encoding</span></span>
<span data-ttu-id="4c4cc-103">Proces transformace sadu znaků Unicode do pořadí bajtů kódování je.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="4c4cc-104">Dekódování je zpětné proces.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-104">Decoding is the reverse process.</span></span> <span data-ttu-id="4c4cc-105">Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4c4cc-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4c4cc-106">`binaryMessageEncoding` Znak kódování a zpráva verze založené na binární soubor XML pro zprávy určuje konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="4c4cc-107">Kodér zprávy v binární kódování zpráv Windows Communication Foundation (WCF) v binárním v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="4c4cc-108">Když toto kódování výsledkem velmi rychlé přenos zpráv, interoperabilita založené na protokolu WS-* dojde ke ztrátě standardů.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
 <span data-ttu-id="4c4cc-109">`mtomMessageEncoding` Konfigurační oddíl Určuje kódování a zpráva verze znak použít pro zprávu pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4c4cc-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="4c4cc-110">(MTOM) je technologie efektivní přenosu zpráv binární data ve zprávách služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4c4cc-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="4c4cc-111">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="4c4cc-112">Kódování MTOM přenáší většina XML v textové podobě, ale optimalizuje velkých bloků binárních dat tím, že je jako přenosu-je, bez převodu na text.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="4c4cc-113">`textMessageEncoding` Konfigurační oddíl určuje kodér textu, používá k vytvoření textových zpráv v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="4c4cc-114">Zprávy vyprodukované tento kodér jsou vhodné pro WS-* na základě zprostředkovatel komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-114">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="4c4cc-115">Webová služba nebo klient webové služby lze obecně pochopit textovou XML.</span><span class="sxs-lookup"><span data-stu-id="4c4cc-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4c4cc-116">Přenos velkých bloků binárních dat jako text je však alespoň efektivní metodu pro kódování zpráv XML</span><span class="sxs-lookup"><span data-stu-id="4c4cc-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c4cc-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c4cc-117">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [<span data-ttu-id="4c4cc-118">Vazby</span><span class="sxs-lookup"><span data-stu-id="4c4cc-118">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4c4cc-119">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="4c4cc-119">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4c4cc-120">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4c4cc-120">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4c4cc-121">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4c4cc-121">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="4c4cc-122">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="4c4cc-122">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)