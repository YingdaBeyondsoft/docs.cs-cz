---
title: "Přenos WS s pověřením zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 517bf7684f6219248ade1f2c8e88879e94b2f1c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="0e8f1-102">Přenos WS s pověřením zpráv</span><span class="sxs-lookup"><span data-stu-id="0e8f1-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="0e8f1-103">Tento příklad znázorňuje použití přenosu zabezpečení SSL v kombinaci s pověření klienta provádí ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="0e8f1-104">V tomto příkladu `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="0e8f1-105">Ve výchozím nastavení `wsHttpBinding` vazby poskytuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="0e8f1-106">Když nakonfigurován pro zabezpečení přenosu, vazba podporuje komunikaci přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="0e8f1-107">HTTPS poskytuje utajení a integrity ochrany pro zprávy, které jsou odeslány prostřednictvím sítě.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="0e8f1-108">Je ale omezený na přenos HTTPS podporuje sadu ověřovací mechanismy, které lze použít k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0e8f1-109">nabízí `TransportWithMessageCredential` režim zabezpečení, která je určená k překonání tohoto omezení.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-109"> offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="0e8f1-110">Pokud je nakonfigurovaná tento režim zabezpečení, zabezpečení přenosu se používá k zajištění důvěrnosti a integrity pro přenášená zprávy a provádět ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="0e8f1-111">Ověření klienta se však provádí umístěním pověření klienta přímo ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="0e8f1-112">To umožňuje použít libovolný typ přihlašovacích údajů, který podporuje režim zabezpečení zprávy pro ověřování klientů a zachovat přitom výkon výhodou režim zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="0e8f1-113">V této ukázce `UserName` typ přihlašovacích údajů se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="0e8f1-114">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0e8f1-115">`wsHttpBinding` Vazba je zadán a nakonfigurované v konfiguračních souborech aplikace pro klient a služba.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e8f1-116">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0e8f1-117">Program kód v ukázce je téměř shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="0e8f1-118">Jeden další operace poskytované kontrakt služby - `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="0e8f1-119">Tato operace vrátí název identitu volajícího volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-119">This operation returns the name of the caller's identity to the caller.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```  
  
 <span data-ttu-id="0e8f1-120">Musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikátem webového serveru před vytváření a spouštění vzorku.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="0e8f1-121">Definice služby endpoint a definice vazby v konfiguraci souboru povolit nastavení `TransportWithMessageCredential` režim zabezpečení, jak je znázorněno v následující ukázka konfigurace pro klienta.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0e8f1-122">Zadaná adresa používá schéma https://.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="0e8f1-123">Konfigurace vazeb nastaví režim zabezpečení `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="0e8f1-124">Stejný režim zabezpečení je třeba zadat v souboru Web.config dané služby.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="0e8f1-125">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, zobrazí se výstraha zabezpečení při pokusu o přístup protokolu https: adresa, jako je například https://localhost/servicemodelsamples/service.svc z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="0e8f1-126">Chcete-li povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pro práci s testovací certifikát na místě, některé další kód byl přidán do klienta pro potlačení výstrahy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-126">To allow the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="0e8f1-127">Tento kód a doprovodné třídy, je potřeba, není při použití provozní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 <span data-ttu-id="0e8f1-128">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0e8f1-129">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="0e8f1-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0e8f1-130">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="0e8f1-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0e8f1-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e8f1-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0e8f1-132">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="0e8f1-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3.  <span data-ttu-id="0e8f1-133">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e8f1-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="0e8f1-134">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e8f1-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8f1-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e8f1-135">See Also</span></span>