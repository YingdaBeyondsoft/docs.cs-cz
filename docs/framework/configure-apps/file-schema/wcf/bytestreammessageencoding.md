---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 3493588d4613131ad9526a8d26912ecdb601ea25
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753271"
---
# <a name="ltbytestreammessageencodinggt"></a>&lt;byteStreamMessageEncoding&gt;
Určuje zprávu, která kódování pomocí datového proudu bajtů, přičemž můžete určit kódování znaků.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<binaryMessageEncoding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|verze messageVersion|Určuje verzi protokolu SOAP zprávy odeslané pomocí vazby. Tuto vlastnost lze nastavit pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Kodér zpráv datového proudu bajtů nepodporuje žádné jiné verze zprávy.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [Kódování zpráv](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
