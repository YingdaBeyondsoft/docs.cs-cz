---
title: 'Postupy: publikování metadat služby promocí konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 94013c69bec0ea37c9260567437aeada3ebe2ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495691"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Postupy: publikování metadat služby promocí konfiguračního souboru
Toto je jedna z dva postupy: témata, která ukazují publikování metadat služby Windows Communication Foundation (WCF). Existují dva způsoby, jak určit, jak by měla služba publikování metadat, použití konfiguračního souboru a pomocí kódu. Toto téma ukazuje, jak publikování metadat služby promocí konfiguračního souboru.  
  
> [!CAUTION]
>  Toto téma ukazuje, jak publikování metadat nezabezpečená způsobem. Jakýkoli klient může načíst metadata ze služby. Pokud budete potřebovat k službě pro publikování metadat zabezpečeným způsobem, najdete v části [vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v kódu najdete v tématu [postupy: publikování metadat služby pomocí kód](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu. Ujistěte se, zda je funkční kód, vytvoření základní služby WCF. Pro jednoduchost základní služba s vlastním hostováním zajišťuje v následujícím kódu.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 Tato služba je samoobslužné hostované služby, která je nakonfigurována pomocí konfiguračního souboru. Následující konfigurační soubor slouží jako výchozí bod.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>K publikování metadat služby WCF pomocí konfiguračního souboru aplikace  
  
1.  V souboru App.config po zavření `</services>` elementu, vytvoření `<behaviors>` elementu.  
  
  
  
2.  V rámci `<behaviors>` elementu, přidejte `<serviceBehaviors>` elementu.  
  
  
  
3.  Přidat `<behavior>` elementu, který chcete `<serviceBehaviors>` elementu a zadat hodnotu pro `name` atribut `<behavior>` elementu.  
  
  
  
4.  Přidat `<serviceMetadata>` elementu, který chcete `<behavior>` elementu. Nastavte `httpGetEnabled` atribut `true` a `policyVersion` atribut Policy15. `httpGetEnabled` umožňuje službě reagovat na požadavky na metadata požadavek HTTP GET. `policyVersion` informuje službu tak, aby odpovídala WS-Policy 1.5 při generování metadat.  
  
  
  
5.  Přidat `behaviorConfiguration` atribut `<service>` elementu a zadejte `name` atribut `<behavior>` element přidali v kroku 1, jak je znázorněno v následujícím příkladu kódu.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6.  Přidejte jednu nebo více `<endpoint>` elementy se smlouvou hodnotu `IMetadataExchange`, jak je znázorněno v následujícím příkladu kódu.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7.  Pro koncové body metadat přidali v předchozím kroku, nastavte `binding` atribut jednu z následujících:  
  
    -   `mexHttpBinding` pro publikaci HTTP.  
  
    -   `mexHttpsBinding` pro publikaci HTTPS.  
  
    -   `mexNamedPipeBinding` pro publikaci pojmenovaný kanál.  
  
    -   `mexTcpBinding` pro publikaci TCP.  
  
8.  Pro koncové body metadat přidali v předchozím kroku nastavte adresu rovno:  
  
    -   Prázdný řetězec pro použití základní adresy hostitelskou aplikaci jako bod publikace, pokud základní adresa je stejný jako metadata vazby.  
  
    -   Relativní adresa, pokud má základní adresu hostitelskou aplikaci.  
  
    -   Absolutní adresu.  
  
9. Sestavte a spusťte konzolovou aplikaci.  
  
10. Použijte Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, jestli je zapnutá publikování metadat. Pokud není, zobrazí se zpráva v horní části výsledné stránky: "publikování metadat pro tato služba je aktuálně zakázaná."  
  
### <a name="to-use-default-endpoints"></a>Chcete-li použít výchozí koncové body  
  
1.  Ke konfiguraci metadata na službu, která používá výchozí koncové body, zadejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguraci souboru jako v předchozím příkladu, ale nezadávejte žádné koncové body. Konfigurační soubor by měl vypadat takto.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Protože služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> s `httpGetEnabled` nastavena na `true`, služba má povoleno publikování metadat a vzhledem k tomu, že byly přidané žádné koncové body, modul runtime přidá výchozí koncové body. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci základní služby WCF a konfigurační soubor, který publikuje metadata pro službu.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Vlastní hostování](../../../../docs/framework/wcf/samples/self-host.md)  
 [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
