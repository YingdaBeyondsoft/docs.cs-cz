---
title: Používání vazeb NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: a753cca008c7eb9b500afa7f3f3b55b5410522a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498866"
---
# <a name="using-the-nethttpbinding"></a>Používání vazeb NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding> používá binární kódování ve výchozím nastavení je vazbu pro využívání služeb HTTP nebo protokolu WebSocket. <xref:System.ServiceModel.NetHttpBinding> rozpozná, jestli se používá s kontraktu požadavku a odpovědi nebo duplexního kontraktu a změnit své chování tak, aby odpovídaly – použije HTTP pro kontraktů požadavek odpověď a WebSockets pro duplexní kontrakty. Toto chování lze přepsat pomocí <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` nastavení:  
  
1.  Vždy - vynutí objekty WebSockets použije i pro kontraktů požadavek odpověď.  
  
2.  Nikdy – to zabraňuje objekty WebSockets. Pokus o použití duplexního kontraktu s tímto nastavením bude mít za následek výjimku.  
  
3.  WhenDuplex - Toto je výchozí hodnota a chová, jak je popsáno výše.  
  
 <xref:System.ServiceModel.NetHttpBinding> podporuje spolehlivé relace v HTTP režimu i režimu protokolu WebSocket. V protokolu WebSocket relace režimu jsou poskytovány přenosu.  
  
> [!WARNING]
>  Při použití <xref:System.ServiceModel.NetHttpBinding> a TransferMode vazby nastavena na TransferMode.Streamed, velké datové proudy může způsobit zablokování a bude časový limit volání. Chcete vyřešit tento problém odesílat menší zprávy nebo použít třídy TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurace služby pro použití NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> Může být nakonfigurované stejně jako jakákoli jiná vazba. Následující fragment kódu konfigurace znázorňuje, jak nakonfigurovat služby WCF s <xref:System.ServiceModel.NetHttpBinding>.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 Následující fragment kódu ukazuje, jak přidat <xref:System.ServiceModel.NetHttpBinding> v kódu.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace vazeb pro služby](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
