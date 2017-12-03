---
title: "Řízení front zpráv do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc295eac67f521e255a27f069ca15cca94dbe768
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="c6057-102">Řízení front zpráv do WCF</span><span class="sxs-lookup"><span data-stu-id="c6057-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="c6057-103">Tento příklad ukazuje, jak můžete k aplikaci služby Řízení front zpráv (MSMQ) odešle zprávu služby MSMQ pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="c6057-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="c6057-104">Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="c6057-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="c6057-105">Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné služby, který je vhodný pro použití s front.</span><span class="sxs-lookup"><span data-stu-id="c6057-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="c6057-106">Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ kontrakty operaci.</span><span class="sxs-lookup"><span data-stu-id="c6057-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="c6057-107">Proto může být pouze jeden kontrakt operaci.</span><span class="sxs-lookup"><span data-stu-id="c6057-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="c6057-108">Pokud chcete definovat více než jeden kontrakt operace služby, aplikace musí poskytovat informace o tom, které záhlaví zprávy služby MSMQ (například popisek nebo correlationID) slouží k rozhodnout, které operace kontrakt k odeslání.</span><span class="sxs-lookup"><span data-stu-id="c6057-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="c6057-109">Tento postup je znázorněn v [vlastní Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="c6057-109">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="c6057-110">Zprávy služby MSMQ neobsahuje informace o tom, které hlavičky jsou namapované na různé parametry operace kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c6057-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="c6057-111">Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), která obsahuje základní zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6057-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="c6057-112">Typ "T" v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) třída reprezentuje data, která je serializován do textu zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6057-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="c6057-113">V této ukázce `PurchaseOrder` typ serializován do textu zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6057-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="c6057-114">Následující vzorový kód ukazuje kontrakt služby pořadí zpracování služby.</span><span class="sxs-lookup"><span data-stu-id="c6057-114">The following sample code shows the service contract of the order processing service.</span></span>  
  
```  
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 <span data-ttu-id="c6057-115">Služba je sám sebou hostované.</span><span class="sxs-lookup"><span data-stu-id="c6057-115">The service is self hosted.</span></span> <span data-ttu-id="c6057-116">Při použití služby MSMQ, používá fronty musí být vytvořeny předem.</span><span class="sxs-lookup"><span data-stu-id="c6057-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="c6057-117">Tento krok můžete provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="c6057-117">This can be done manually or through code.</span></span> <span data-ttu-id="c6057-118">V této ukázce služba zkontroluje existenci fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="c6057-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="c6057-119">Název fronty je číst z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c6057-119">The queue name is read from the configuration file.</span></span>  
  
```  
public static void Main()  
{  
    // Get the MSMQ queue name from the application settings in   
    // configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
    // Create the MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
    …  
}  
```  
  
 <span data-ttu-id="c6057-120">Služba vytvoří a otevře <xref:System.ServiceModel.ServiceHost> pro `OrderProcessorService`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c6057-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>  
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```  
  
 <span data-ttu-id="c6057-121">Název fronty služby MSMQ je zadaný v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c6057-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6057-122">Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="c6057-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="c6057-123">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje schématu msmq.formatname a používá localhost pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="c6057-123">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="c6057-124">Adresu fronty pro každý název formátu MSMQ adresování pokyny následuje msmq.formatname schéma.</span><span class="sxs-lookup"><span data-stu-id="c6057-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="c6057-125">Klientská aplikace je aplikace služby MSMQ, která používá <xref:System.Messaging.MessageQueue.Send%2A> metoda odeslání odolné a transakční zprávy do fronty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c6057-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>  
  
```  
//Connect to the queue.  
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);  
  
// Create the purchase order.  
PurchaseOrder po = new PurchaseOrder();  
po.CustomerId = "somecustomer.com";  
po.PONumber = Guid.NewGuid().ToString();  
  
PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
lineItem1.ProductId = "Blue Widget";  
lineItem1.Quantity = 54;  
lineItem1.UnitCost = 29.99F;  
  
PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
lineItem2.ProductId = "Red Widget";  
lineItem2.Quantity = 890;  
lineItem2.UnitCost = 45.89F;  
  
po.orderLineItems = new PurchaseOrderLineItem[2];  
po.orderLineItems[0] = lineItem1;  
po.orderLineItems[1] = lineItem2;  
  
// Submit the purchase order.  
Message msg = new Message();  
msg.Body = po;  
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
  
    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
    // Complete the transaction.  
    scope.Complete();  
  
}  
Console.WriteLine("Placed the order:{0}", po);  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="c6057-126">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="c6057-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c6057-127">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="c6057-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c6057-128">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="c6057-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="c6057-129">Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="c6057-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="c6057-130">Například můžete spustit klienta, vypněte ho a potom spuštění služby a je stále by přijímat jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="c6057-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="c6057-131">Instalační program, sestavení a spuštění vzorku</span><span class="sxs-lookup"><span data-stu-id="c6057-131">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6057-132">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6057-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c6057-133">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="c6057-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c6057-134">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="c6057-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c6057-135">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6057-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c6057-136">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="c6057-136">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="c6057-137">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6057-137">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="c6057-138">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="c6057-138">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="c6057-139">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="c6057-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="c6057-140">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="c6057-140">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="c6057-141">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="c6057-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="c6057-142">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6057-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c6057-143">Spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6057-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c6057-144">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="c6057-144">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="c6057-145">Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="c6057-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="c6057-146">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="c6057-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="c6057-147">V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba místo ".".</span><span class="sxs-lookup"><span data-stu-id="c6057-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="c6057-148">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="c6057-148">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="c6057-149">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="c6057-149">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6057-150">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c6057-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c6057-151">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6057-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6057-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c6057-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6057-153">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6057-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="c6057-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6057-154">See Also</span></span>  
 [<span data-ttu-id="c6057-155">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="c6057-155">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="c6057-156">Postupy: výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="c6057-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="c6057-157">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="c6057-157">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)