---
title: Použití vlastní vazby s kanálem klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 4ef85b4c52c1f27b333413e2b6178452142d313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498355"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Použití vlastní vazby s kanálem klienta zjišťování
Při použití vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, je nutné definovat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> vytvářející <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Vytváření DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zodpovídá za vytvoření <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance na vyžádání. K definování zjišťování zprostředkovatele koncových bodů, odvození třídy z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> a přepsat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metoda a vraťte se nový koncový bod zjišťování. Následující příklad ukazuje, jak vytvořit poskytovatele koncový bod zjišťování.  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel   
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 Jakmile definujete zprostředkovatele zjišťování koncových bodů, které můžete vytvořit vlastní vazby a přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, který odkazuje na zprostředkovatele zjišťování koncových bodů, jak je znázorněno v následujícím příkladu.  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Další informace o používání kanálem klienta zjišťování najdete v tématu [pomocí kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). Úplný příklad, naleznete v tématu [– ukázka prvky vazby zjišťování](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Ukázka elementu vazby zjišťování](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
