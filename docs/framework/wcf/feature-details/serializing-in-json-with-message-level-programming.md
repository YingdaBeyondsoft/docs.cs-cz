---
title: Serializace ve formátu Json s programováním na úrovni zpráv
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: a2568c30d34e39aaf1708a9fb3e186f86b17f5b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498144"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializace ve formátu Json s programováním na úrovni zpráv
WCF podporuje serializaci dat ve formátu JSON. Toto téma popisuje, jak říct WCF k serializaci vaší typy pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Zadanou zprávu programování  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Se používá při <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> se použije pro operaci služby. Obě tyto atributy umožňují určit `RequestFormat` a `ResponseFormat`. Chcete použít pro požadavky a odpovědi JSON nastavit obě tyto k `WebMessageFormat.Json`.  Chcete-li použít JSON je nutné použít <xref:System.ServiceModel.WebHttpBinding> který automaticky nakonfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>. Další informace o serializaci WCF najdete v tématu: [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [serializace ve službě Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx). Další informace o formátu JSON a WCF najdete v části [Úvod do služby RESTfull s použitím technologie WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [povoleno vytváření JSON služby WCF v rozhraní .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), a [přehled REST ve službě WCF](http://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  Použití JSON vyžaduje použití <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> který nepodporuje komunikaci protokolu SOAP. Služby, které komunikují <xref:System.ServiceModel.WebHttpBinding> nepodporují zpřístupňuje metadata služby, takže nebudete moci používat funkce sady Visual Studio přidat odkaz na službu nebo nástroj příkazového řádku svcutil ke generování proxy serveru klienta. Další informace, jak můžete programově volat služby využívající <xref:System.ServiceModel.WebHttpBinding>, najdete v části [jak využívat služby REST s použitím technologie WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Programování bez typu zprávy  
 Při práci s objekty bez typu zpráv přímo, musíte explicitně nastavit vlastnosti v netypové zpráva určená k serializaci jako JSON. Následující fragment kódu ukazuje, jak to udělat.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Viz také  
 [Integrace jazyka AJAX a podpora JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
