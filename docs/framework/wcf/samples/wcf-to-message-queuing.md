---
title: "Z WCF do Řízení front zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6800db4e5f8dc1a0d571be3eed556503b907e16e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="907ce-102">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="907ce-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="907ce-103">Tento příklad ukazuje, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace můžete odeslat zprávu do aplikace služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="907ce-103">This sample demonstrates how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="907ce-104">Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="907ce-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="907ce-105">Klienta a služby nemusíte používat ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="907ce-105">The service and client do not have to be running at the same time.</span></span>  
  
 <span data-ttu-id="907ce-106">Služba přijímá zprávy z fronty a zpracovává objednávky.</span><span class="sxs-lookup"><span data-stu-id="907ce-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="907ce-107">Služba vytvoří transakční fronty a nastaví obslužné rutiny zpráv přijata zpráva, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="907ce-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>  
  
```  
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="907ce-108">Při příjmu zprávy ve frontě obslužné rutiny zpráv `ProcessOrder` je volána.</span><span class="sxs-lookup"><span data-stu-id="907ce-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>  
  
```  
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```  
  
 <span data-ttu-id="907ce-109">Extrahuje služby `ProcessOrder` ze služby MSMQ tělo zprávy a zpracuje pořadí.</span><span class="sxs-lookup"><span data-stu-id="907ce-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>  
  
 <span data-ttu-id="907ce-110">Název fronty služby MSMQ je zadaný v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="907ce-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="907ce-111">Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="907ce-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>  
  
 <span data-ttu-id="907ce-112">Klient vytvoří nákupní objednávka a odešle nákupní objednávka v rámci oboru transakce, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="907ce-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>  
  
```  
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="907ce-113">Klient použije k odeslání zprávy služby MSMQ do fronty vlastní klienta v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="907ce-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="907ce-114">Vzhledem k tomu, že je aplikace, který obdrží a zpracuje zprávy aplikací služby MSMQ a ne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, neexistuje žádný kontrakt implicitní služby mezi těmito dvěma aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="907ce-114">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="907ce-115">Ano nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="907ce-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="907ce-116">Vlastní klienta je v podstatě stejný pro všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, které používají `MsmqIntegration` vazby k odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="907ce-116">The custom client is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="907ce-117">Na rozdíl od ostatních klientů nebude obsahovat celou řadu operací služby.</span><span class="sxs-lookup"><span data-stu-id="907ce-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="907ce-118">Je zpráva operaci odeslání jenom.</span><span class="sxs-lookup"><span data-stu-id="907ce-118">It is a submit message operation only.</span></span>  
  
```  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```  
  
 <span data-ttu-id="907ce-119">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="907ce-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="907ce-120">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="907ce-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="907ce-121">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="907ce-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="907ce-122">Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="907ce-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="907ce-123">Například můžete spustit klienta, vypněte ho a potom spuštění služby a je stále by přijímat jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="907ce-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="907ce-124">Tato ukázka vyžaduje instalaci služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="907ce-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="907ce-125">Najdete v pokynech k instalaci v [služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="907ce-125">See the installation instructions in [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="907ce-126">Instalační program, sestavení a spuštění vzorku</span><span class="sxs-lookup"><span data-stu-id="907ce-126">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="907ce-127">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="907ce-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="907ce-128">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="907ce-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="907ce-129">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="907ce-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="907ce-130">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="907ce-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="907ce-131">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="907ce-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="907ce-132">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="907ce-132">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="907ce-133">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="907ce-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="907ce-134">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="907ce-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="907ce-135">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="907ce-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="907ce-136">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="907ce-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="907ce-137">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="907ce-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="907ce-138">Spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="907ce-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="907ce-139">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="907ce-139">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="907ce-140">Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="907ce-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="907ce-141">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="907ce-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="907ce-142">V souboru Client.exe.config změnit adresa koncového bodu klienta k zadání názvu počítače služba místo ".".</span><span class="sxs-lookup"><span data-stu-id="907ce-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="907ce-143">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="907ce-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="907ce-144">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="907ce-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="907ce-145">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="907ce-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="907ce-146">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="907ce-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="907ce-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="907ce-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="907ce-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="907ce-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="907ce-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="907ce-149">See Also</span></span>  
 [<span data-ttu-id="907ce-150">Postupy: výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="907ce-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="907ce-151">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="907ce-151">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)