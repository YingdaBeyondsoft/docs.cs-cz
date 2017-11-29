---
title: "Postupy: publikování metadat služby promocí konfiguračního souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e94fe7135d51c4e1578ca69768b6d0ba2aa6ae6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="991ee-102">Postupy: publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="991ee-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="991ee-103">Toto je jedna z dva postupy: témata, která ukazují publikování metadat pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="991ee-103">This is one of two how-to topics that demonstrate publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="991ee-104">Existují dva způsoby, jak určit, jak by měla služba publikování metadat, použití konfiguračního souboru a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="991ee-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="991ee-105">Toto téma ukazuje, jak publikování metadat služby promocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="991ee-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="991ee-106">Toto téma ukazuje, jak publikování metadat nezabezpečená způsobem.</span><span class="sxs-lookup"><span data-stu-id="991ee-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="991ee-107">Jakýkoli klient může načíst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="991ee-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="991ee-108">Pokud budete potřebovat k službě pro publikování metadat zabezpečeným způsobem, najdete v části [vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="991ee-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="991ee-109">publikování metadat v kódu, najdete v části [postupy: publikování metadat služby pomocí kód](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="991ee-109"> publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="991ee-110">Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="991ee-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="991ee-111">Ujistěte se, zda je funkční kód, vytvoření základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="991ee-111">To be sure that the code is working, create a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="991ee-112">Pro jednoduchost základní služba s vlastním hostováním zajišťuje v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="991ee-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="991ee-113">Tato služba je samoobslužné hostované služby, která je nakonfigurována pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="991ee-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="991ee-114">Následující konfigurační soubor slouží jako výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="991ee-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="991ee-115">K publikování metadat služby WCF pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="991ee-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="991ee-116">V souboru App.config po zavření `</services>` elementu, vytvoření `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="991ee-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="991ee-117">V rámci `<behaviors>` elementu, přidejte `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="991ee-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="991ee-118">Přidat `<behavior>` elementu, který chcete `<serviceBehaviors>` elementu a zadat hodnotu pro `name` atribut `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="991ee-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="991ee-119">Přidat `<serviceMetadata>` elementu, který chcete `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="991ee-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="991ee-120">Nastavte `httpGetEnabled` atribut `true` a `policyVersion` atribut Policy15.</span><span class="sxs-lookup"><span data-stu-id="991ee-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="991ee-121">`httpGetEnabled`umožňuje službě reagovat na požadavky na metadata požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="991ee-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="991ee-122">`policyVersion`informuje službu tak, aby odpovídala WS-Policy 1.5 při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="991ee-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="991ee-123">Přidat `behaviorConfiguration` atribut `<service>` elementu a zadejte `name` atribut `<behavior>` element přidali v kroku 1, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="991ee-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6.  <span data-ttu-id="991ee-124">Přidejte jednu nebo více `<endpoint>` elementy se smlouvou hodnotu `IMetadataExchange`, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="991ee-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7.  <span data-ttu-id="991ee-125">Pro koncové body metadat přidali v předchozím kroku, nastavte `binding` atribut jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="991ee-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="991ee-126">`mexHttpBinding`pro publikaci HTTP.</span><span class="sxs-lookup"><span data-stu-id="991ee-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="991ee-127">`mexHttpsBinding`pro publikaci HTTPS.</span><span class="sxs-lookup"><span data-stu-id="991ee-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="991ee-128">`mexNamedPipeBinding`pro publikaci pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="991ee-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="991ee-129">`mexTcpBinding`pro publikaci TCP.</span><span class="sxs-lookup"><span data-stu-id="991ee-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="991ee-130">Pro koncové body metadat přidali v předchozím kroku nastavte adresu rovno:</span><span class="sxs-lookup"><span data-stu-id="991ee-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="991ee-131">Prázdný řetězec pro použití základní adresy hostitelskou aplikaci jako bod publikace, pokud základní adresa je stejný jako metadata vazby.</span><span class="sxs-lookup"><span data-stu-id="991ee-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="991ee-132">Relativní adresa, pokud má základní adresu hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="991ee-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="991ee-133">Absolutní adresu.</span><span class="sxs-lookup"><span data-stu-id="991ee-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="991ee-134">Sestavte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="991ee-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="991ee-135">Základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, jestli je zapnutá publikování metadat pomocí aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="991ee-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="991ee-136">Pokud není, zobrazí se zpráva v horní části výsledné stránky: "publikování metadat pro tato služba je aktuálně zakázaná."</span><span class="sxs-lookup"><span data-stu-id="991ee-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="991ee-137">Chcete-li použít výchozí koncové body</span><span class="sxs-lookup"><span data-stu-id="991ee-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="991ee-138">Ke konfiguraci metadata na službu, která používá výchozí koncové body, zadejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguraci souboru jako v předchozím příkladu, ale nezadávejte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="991ee-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="991ee-139">Konfigurační soubor by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="991ee-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="991ee-140">Protože služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> s `httpGetEnabled` nastavena na `true`, služba má povoleno publikování metadat a vzhledem k tomu, že byly přidané žádné koncové body, modul runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="991ee-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="991ee-141">výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="991ee-141"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="991ee-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="991ee-142">Example</span></span>  
 <span data-ttu-id="991ee-143">Následující příklad kódu ukazuje implementaci základního [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a konfigurační soubor, který publikuje metadata pro službu.</span><span class="sxs-lookup"><span data-stu-id="991ee-143">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="991ee-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="991ee-144">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="991ee-145">Postupy: hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="991ee-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="991ee-146">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="991ee-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="991ee-147">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="991ee-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="991ee-148">Pomocí metadat</span><span class="sxs-lookup"><span data-stu-id="991ee-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="991ee-149">Postupy: publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="991ee-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)