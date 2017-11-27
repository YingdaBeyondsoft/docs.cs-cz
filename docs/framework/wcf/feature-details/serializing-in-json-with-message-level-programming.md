---
title: "Serializace ve formátu Json s programováním na úrovni zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 33337f75032031ccfc81173f188f4ff7695ffd40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="4df62-102">Serializace ve formátu Json s programováním na úrovni zpráv</span><span class="sxs-lookup"><span data-stu-id="4df62-102">Serializing in Json with Message Level Programming</span></span>
<span data-ttu-id="4df62-103">WCF podporuje serializaci dat ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="4df62-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="4df62-104">Toto téma popisuje, jak říct WCF k serializaci vaší typy pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4df62-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="4df62-105">Zadanou zprávu programování</span><span class="sxs-lookup"><span data-stu-id="4df62-105">Typed Message Programming</span></span>  
 <span data-ttu-id="4df62-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Se používá při <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> se použije pro operaci služby.</span><span class="sxs-lookup"><span data-stu-id="4df62-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="4df62-107">Obě tyto atributy umožňují určit `RequestFormat` a `ResponseFormat`.</span><span class="sxs-lookup"><span data-stu-id="4df62-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="4df62-108">Chcete použít pro požadavky a odpovědi JSON nastavit obě tyto k `WebMessageFormat.Json`.</span><span class="sxs-lookup"><span data-stu-id="4df62-108">To use JSON for requests and responses set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="4df62-109">Chcete-li použít JSON je nutné použít <xref:System.ServiceModel.WebHttpBinding> který automaticky nakonfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="4df62-109">In order to use JSON you must use the <xref:System.ServiceModel.WebHttpBinding> which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="4df62-110">Další informace o serializaci WCF najdete v tématu: [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [serializace ve službě Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span><span class="sxs-lookup"><span data-stu-id="4df62-110">For more information about WCF serialization, see: [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Serialization in Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span></span> <span data-ttu-id="4df62-111">Další informace o formátu JSON a WCF najdete v části [Úvod do služby RESTfull s použitím technologie WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [povoleno vytváření JSON služby WCF v rozhraní .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), a [přehled REST ve službě WCF](http://msdn.microsoft.com/netframework/dd547388).</span><span class="sxs-lookup"><span data-stu-id="4df62-111">For more information about JSON and WCF see [An Introduction to RESTfull Services with WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Creating JSON-enabled WCF Services in .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), and [Overview of REST in WCF](http://msdn.microsoft.com/netframework/dd547388).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4df62-112">Použití JSON vyžaduje použití <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> který nepodporuje komunikaci protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4df62-112">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="4df62-113">Služby, které komunikují <xref:System.ServiceModel.WebHttpBinding> nepodporují zpřístupňuje metadata služby, takže nebudete moci používat funkce sady Visual Studio přidat odkaz na službu nebo nástroj příkazového řádku svcutil ke generování proxy serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="4df62-113">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="4df62-114">Další informace, jak můžete programově volat služby využívající <xref:System.ServiceModel.WebHttpBinding>, najdete v části [jak využívat služby REST s použitím technologie WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span><span class="sxs-lookup"><span data-stu-id="4df62-114">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="4df62-115">Programování bez typu zprávy</span><span class="sxs-lookup"><span data-stu-id="4df62-115">Untyped Message Programming</span></span>  
 <span data-ttu-id="4df62-116">Při práci s objekty bez typu zpráv přímo, musíte explicitně nastavit vlastnosti v netypové zpráva určená k serializaci jako JSON.</span><span class="sxs-lookup"><span data-stu-id="4df62-116">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="4df62-117">Následující fragment kódu ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="4df62-117">The following code snippet shows how to do this.</span></span>  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="4df62-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4df62-118">See Also</span></span>  
 [<span data-ttu-id="4df62-119">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="4df62-119">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="4df62-120">Samostatná serializace JSON</span><span class="sxs-lookup"><span data-stu-id="4df62-120">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="4df62-121">Serializace JSON</span><span class="sxs-lookup"><span data-stu-id="4df62-121">JSON Serialization</span></span>](../../../../docs/framework/wcf/samples/json-serialization.md)