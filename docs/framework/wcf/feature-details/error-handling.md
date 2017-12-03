---
title: "Zpracování chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215fb30772e4f1b25e20303b3f83d6fe0c00ebae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling"></a><span data-ttu-id="9df3c-102">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="9df3c-102">Error handling</span></span>
## <a name="error-handling-in-windows-communication-foundation"></a><span data-ttu-id="9df3c-103">Chyba při zpracování ve Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9df3c-103">Error Handling in Windows Communication Foundation</span></span>  
 <span data-ttu-id="9df3c-104">Když služba dojde neočekávané výjimce nebo chyba, návrh řešení zpracování výjimek s několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="9df3c-104">When a service encounters an unexpected exception or error, there are multiple ways to design an exception-handling solution.</span></span> <span data-ttu-id="9df3c-105">Pokud není žádná jedním "Opravit" nebo "nejlépe praxi" zpracování chyb řešení, existuje více cest platný pro jednu vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="9df3c-105">While there is no single "correct" or "best practice" error-handling solution, there are multiple valid paths for one to consider.</span></span> <span data-ttu-id="9df3c-106">Za normálních okolností se doporučuje, že jeden implementovat hybridní řešení, které se kombinuje několik přístupů ze seznamu níže, v závislosti na složitosti implementace WCF, typ a frekvenci výjimky, zpracovaná oproti neošetřené povaha výjimky a všechny související trasování, protokolování nebo požadavky zásad.</span><span class="sxs-lookup"><span data-stu-id="9df3c-106">It is normally recommended that one implement a hybrid solution that combines multiple approaches from the list below, depending on the complexity of the WCF implementation, the type and frequency of the exceptions, the handled vs. unhandled nature of the exceptions, and any associated tracing, logging, or policy requirements.</span></span>  
  
 <span data-ttu-id="9df3c-107">Tato řešení jsou vysvětleny hlubšímu ve zbývající části této části.</span><span class="sxs-lookup"><span data-stu-id="9df3c-107">These solutions are explained more deeply in the rest of this section.</span></span>  
  
### <a name="the-microsoft-enterprise-library"></a><span data-ttu-id="9df3c-108">Knihovna Microsoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="9df3c-108">The Microsoft Enterprise Library</span></span>  
 <span data-ttu-id="9df3c-109">Microsoft Enterprise knihovny výjimka zpracování aplikace bloku pomáhá implementovat obecné vzory návrhu a vytvořit konzistentní strategie pro zpracování výjimek, které se vyskytují ve všech architektury vrstev podniková aplikace.</span><span class="sxs-lookup"><span data-stu-id="9df3c-109">The Microsoft Enterprise Library Exception Handling Application Block helps implement common design patterns and create a consistent strategy for processing exceptions that occur in all architectural layers of an enterprise application.</span></span> <span data-ttu-id="9df3c-110">Je navržen pro podporu kód typické obsažené v příkazech catch v součásti aplikace.</span><span class="sxs-lookup"><span data-stu-id="9df3c-110">It is designed to support the typical code contained in catch statements in application components.</span></span> <span data-ttu-id="9df3c-111">Místo opakující se tento kód (například kód, který zaznamenává informace o výjimce) ve stejné catch – bloky v celé aplikaci, bloku aplikace zpracování výjimky umožňuje vývojářům zapouzdření této logiky jako obslužné rutiny výjimek opakovaně použitelné.</span><span class="sxs-lookup"><span data-stu-id="9df3c-111">Instead of repeating this code (such as code that logs exception information) in identical catch blocks throughout an application, the Exception Handling Application Block allows developers to encapsulate this logic as reusable exception handlers.</span></span>  
  
 <span data-ttu-id="9df3c-112">Tato knihovna obsahuje out-of-the-box obslužná rutina výjimky kontrakt chyb.</span><span class="sxs-lookup"><span data-stu-id="9df3c-112">This Library includes out-of-the-box a Fault Contract Exception Handler.</span></span> <span data-ttu-id="9df3c-113">Tato obslužná rutina výjimky je určen k použití v hranice služby Windows® Communication Foundation (WCF) a vygeneruje nové smlouvy chyby z výjimku.</span><span class="sxs-lookup"><span data-stu-id="9df3c-113">This exception handler is designed for use at Windows® Communication Foundation (WCF) service boundaries, and generates a new Fault Contract from the exception.</span></span>  
  
 <span data-ttu-id="9df3c-114">Zaměřte se na začlenit běžně používané osvědčené postupy a zadejte běžný postup pro zpracování v celé vaší aplikaci výjimek aplikace bloky.</span><span class="sxs-lookup"><span data-stu-id="9df3c-114">Application blocks aim to incorporate commonly used best practices and provide a common approach for exception handling throughout your application.</span></span> <span data-ttu-id="9df3c-115">Na druhé straně obslužné rutiny vlastní chyby a selhání kontrakty vyvinuté v vlastního může být taky hodně užitečný.</span><span class="sxs-lookup"><span data-stu-id="9df3c-115">On the other hand, custom error handlers and fault contracts developed on one’s own can also be very useful.</span></span> <span data-ttu-id="9df3c-116">Vlastní chyba obslužné rutiny pro instanci nabízejí vynikající možnost automaticky podporovat všechny výjimky FaultExceptions a také pro přidání možností protokolování do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="9df3c-116">For instance, custom error handlers provide an excellent opportunity to automatically promote all exceptions to FaultExceptions and also to add logging capabilities to your application.</span></span>  
  
 <span data-ttu-id="9df3c-117">Další informace najdete v tématu [knihovna Microsoft Enterprise](http://msdn.microsoft.com/library/ff632023.aspx).</span><span class="sxs-lookup"><span data-stu-id="9df3c-117">For more information, please see [Microsoft Enterprise Library](http://msdn.microsoft.com/library/ff632023.aspx).</span></span>  
  
### <a name="dealing-with-expected-exceptions"></a><span data-ttu-id="9df3c-118">Práci s očekávané výjimky</span><span class="sxs-lookup"><span data-stu-id="9df3c-118">Dealing with Expected Exceptions</span></span>  
 <span data-ttu-id="9df3c-119">Správné během akce je catch očekávané výjimky v každé operace nebo bod relevantní rozšiřitelnosti, rozhodněte, zda lze obnovit z a vrátí správné vlastní chyby v FaultException\<T ></span><span class="sxs-lookup"><span data-stu-id="9df3c-119">The proper course of action is to catch expected exceptions in every operation or relevant extensibility point, decide whether they can be recovered from, and return the proper custom fault in a FaultException\<T></span></span>  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a><span data-ttu-id="9df3c-120">Práci s neočekávané výjimky pomocí IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="9df3c-120">Dealing with Unexpected Exceptions using an IErrorHandler</span></span>  
 <span data-ttu-id="9df3c-121">Jak nakládat s neočekávané výjimky, je "připojit" IErrorHandler během doporučené akce.</span><span class="sxs-lookup"><span data-stu-id="9df3c-121">To deal with unexpected exceptions, the recommended course of action is to "hook" an IErrorHandler.</span></span> <span data-ttu-id="9df3c-122">Chyba obslužné rutiny pouze zachytávat výjimky na úrovni modulu runtime WCF (layer "model služby"), není ve vrstvě kanálu.</span><span class="sxs-lookup"><span data-stu-id="9df3c-122">Error handlers only catch exceptions at the WCF runtime level (the "service model" layer), not at the channel layer.</span></span> <span data-ttu-id="9df3c-123">Vytvořte vlastní kanál, nedoporučuje se ve většině scénářů je jediný způsob, jak připojit IErrorHandler na úrovni kanálu.</span><span class="sxs-lookup"><span data-stu-id="9df3c-123">The only way to hook an IErrorHandler at the channel level is to create a custom channel, which is not recommended in most scenarios.</span></span>  
  
 <span data-ttu-id="9df3c-124">"Neočekávanou výjimku" je obecně výjimku nezotavitelné ani zpracování výjimky; je, místo toho výjimku neočekávané uživatele.</span><span class="sxs-lookup"><span data-stu-id="9df3c-124">An "unexpected exception" is generally neither an irrecoverable exception nor a processing exception; it is, instead, an unexpected user exception.</span></span> <span data-ttu-id="9df3c-125">Výjimku nezotavitelné (například k výjimce z důvodu nedostatku paměti) – jeden obecně provádí [obslužná rutina výjimky modelu služby](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) automaticky – nelze obecně zpracovat řádně a z důvodu pouze pro zpracování takové výjimky může být vůbec proveďte další protokolování nebo pro návrat do klienta standardní výjimka.</span><span class="sxs-lookup"><span data-stu-id="9df3c-125">An irrecoverable exception (such as an out-of-memory exception) – one generally handled by the [Service Model Exception Handler](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) automatically – cannot generally be handled gracefully, and the only reason to handle such an exception at all may be do additional logging or to return a standard exception to the client.</span></span> <span data-ttu-id="9df3c-126">Došlo k výjimce zpracování ve zpracování zprávy – například v serializaci, kodér nebo formátování úroveň – obecně nelze zpracovat jako IErrorHandler, protože je obecně buď příliš brzké, nebo příliš pozdní pro obslužnou rutinu chyby zasáhnout podle čas, kdy dojde k tyto výjimky.</span><span class="sxs-lookup"><span data-stu-id="9df3c-126">A processing exception occurs in the processing of the message – for example, at the serialization, encoder, or formatter level – generally cannot be handled at an IErrorHandler, because it is generally either too early or too late for the error handler to intervene by the time these exceptions occur.</span></span> <span data-ttu-id="9df3c-127">Podobně nelze zpracovat výjimky přenosu IErrorHandler.</span><span class="sxs-lookup"><span data-stu-id="9df3c-127">Similarly, transport exceptions cannot be handled at an IErrorHandler.</span></span>  
  
 <span data-ttu-id="9df3c-128">S IErrorHandler můžete řídit explicitně chování vaší aplikace, pokud je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9df3c-128">With an IErrorHandler, you can explicitly control the behavior of your application when an exception is thrown.</span></span> <span data-ttu-id="9df3c-129">Můžete:</span><span class="sxs-lookup"><span data-stu-id="9df3c-129">You may:</span></span>  
  
1.  <span data-ttu-id="9df3c-130">Rozhodněte, zda se má odeslat klientovi chybu</span><span class="sxs-lookup"><span data-stu-id="9df3c-130">Decide whether or not to send a fault to the client</span></span>  
  
2.  <span data-ttu-id="9df3c-131">Nahraďte výjimku chybu</span><span class="sxs-lookup"><span data-stu-id="9df3c-131">Replace an exception with a fault</span></span>  
  
3.  <span data-ttu-id="9df3c-132">Nahraďte chybu jiné chyby</span><span class="sxs-lookup"><span data-stu-id="9df3c-132">Replace a fault with another fault</span></span>  
  
4.  <span data-ttu-id="9df3c-133">Provedení protokolování nebo trasování</span><span class="sxs-lookup"><span data-stu-id="9df3c-133">Perform logging or tracing</span></span>  
  
5.  <span data-ttu-id="9df3c-134">Provedení dalších vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="9df3c-134">Perform other custom activities</span></span>  
  
 <span data-ttu-id="9df3c-135">Obslužná rutina vlastní chybové jeden můžete nainstalovat jeho přidáním do vlastnost ErrorHandlers dispečerů kanál pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="9df3c-135">One can install a custom error handler by adding it to the ErrorHandlers property of the channel dispatchers for your service.</span></span>  <span data-ttu-id="9df3c-136">Je možné, že více než jeden obslužnou rutinu chyby a stejně jako v pořadí, ve kterém budou přidány do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="9df3c-136">It is possible to have more than one error handler and they are called in the order they are added to this collection.</span></span>  
  
 <span data-ttu-id="9df3c-137">IErrorHandler.ProvideFault řídí selhání zprávu, která je odeslána do klienta.</span><span class="sxs-lookup"><span data-stu-id="9df3c-137">IErrorHandler.ProvideFault controls the fault message that is sent to the client.</span></span> <span data-ttu-id="9df3c-138">Tato metoda je volána bez ohledu na typ výjimky vyvolané operace ve službě.</span><span class="sxs-lookup"><span data-stu-id="9df3c-138">This method is called regardless of the type of the exception thrown by an operation in your service.</span></span> <span data-ttu-id="9df3c-139">Pokud žádná operace se zde provádí, WCF předpokládá jeho výchozí chování a bude pokračovat, jako kdyby nebyla žádná vlastní chybě obslužné rutiny na místě.</span><span class="sxs-lookup"><span data-stu-id="9df3c-139">If no operation is performed here, WCF assumes its default behaviour and continues as if there were no custom error handlers in place.</span></span>  
  
 <span data-ttu-id="9df3c-140">Jednou z oblastí, můžete případně použít tuto metodu je, když chcete vytvořit centrální místo pro výjimky převádění chyb před jejich odesláním do klienta (zajistit, aby instance není vyřazen a kanál není přesunut do stavu chybný).</span><span class="sxs-lookup"><span data-stu-id="9df3c-140">One area that you could perhaps use this approach is when you want to create a central place for converting exceptions to faults before they are sent to the client (ensuring that the instance is not disposed and the channel is not moved to the Faulted state).</span></span>  
  
 <span data-ttu-id="9df3c-141">Metoda IErrorHandler.HandleError se obvykle používá k implementaci chyba související chování, například protokolování, systémová oznámení, vypínání aplikace atd. IErrorHandler.HandleError lze volat na více místech uvnitř služby a v závislosti na tom, kde je vyvolána chyba, metoda HandleError může nebo nemusí být volána ve stejném vlákně, v jako operaci; v tomto ohledu jsou vytvářeny žádné záruky.</span><span class="sxs-lookup"><span data-stu-id="9df3c-141">The IErrorHandler.HandleError method is usually used to implement error-related behaviors such as error logging, system notifications, shutting down the application, etc. IErrorHandler.HandleError can be called at multiple places inside the service, and depending on where the error is thrown, the HandleError method may or may not be called by the same thread as the operation; no guarantees are made in this regard.</span></span>  
  
### <a name="dealing-with-exceptions-outside-wcf"></a><span data-ttu-id="9df3c-142">Práci s výjimkami mimo WCF</span><span class="sxs-lookup"><span data-stu-id="9df3c-142">Dealing with Exceptions outside WCF</span></span>  
 <span data-ttu-id="9df3c-143">Často, může dojít v kontextu aplikace WCF výjimek konfigurace, výjimky řetězec připojení databáze a další podobné výjimky, ale jsou sami nejsou výjimky způsobené modelu služby nebo samotnou webovou službu.</span><span class="sxs-lookup"><span data-stu-id="9df3c-143">Often, configuration exceptions, database connection string exceptions, and other similar exceptions may occur within the context of a WCF application, but are themselves are not exceptions caused by the service model or the web service itself.</span></span> <span data-ttu-id="9df3c-144">Tyto výjimky jsou "Regulérní" výjimky externí k webové službě a měla by ji zpracovat, stejně jako ostatní externí výjimky v prostředí jsou zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="9df3c-144">These exceptions are "regular" exceptions external to the web service, and should be handled just as other external exceptions in the environment are to be handled.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="9df3c-145">Trasování výjimky</span><span class="sxs-lookup"><span data-stu-id="9df3c-145">Tracing exceptions</span></span>  
 <span data-ttu-id="9df3c-146">Trasování je pouze "pokrývající vše" místem, kde jeden může potenciálně sledovat všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="9df3c-146">Tracing is the only "catch-all" place where one can potentially see all exceptions.</span></span> <span data-ttu-id="9df3c-147">Další informace o trasování a protokolování výjimky najdete v části protokolování a trasování.</span><span class="sxs-lookup"><span data-stu-id="9df3c-147">For more information on tracing and logging exceptions, see Tracing and Logging.</span></span>  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a><span data-ttu-id="9df3c-148">Chyby šablony URI při používání WebGetAttribute a WebInvokeAttribute</span><span class="sxs-lookup"><span data-stu-id="9df3c-148">URI template errors when using WebGetAttribute and WebInvokeAttribute</span></span>  
 <span data-ttu-id="9df3c-149">Atributy WebGet a WebInvoke umožňují zadejte identifikátor URI šablonu, která mapuje součástí adresu požadavek na operaci parametry.</span><span class="sxs-lookup"><span data-stu-id="9df3c-149">The WebGet and WebInvoke attributes allow you to specify a URI template that maps components of the request address to operation parameters.</span></span> <span data-ttu-id="9df3c-150">Například šablony URI "počasí / {stavu} / {města}" mapuje adresu požadavku do literálu tokeny, parametr s názvem stavu a parametr s názvem města.</span><span class="sxs-lookup"><span data-stu-id="9df3c-150">For example, the URI template "weather/{state}/{city}" maps the request address into literal tokens, a parameter named state, and a parameter named city.</span></span> <span data-ttu-id="9df3c-151">Tyto parametry mohou navázat poté podle názvu na některé formální parametry operace.</span><span class="sxs-lookup"><span data-stu-id="9df3c-151">These parameters might then be bound by name to some of the formal parameters of the operation.</span></span>  
  
 <span data-ttu-id="9df3c-152">Parametry šablony se zobrazí ve formě řetězce v rámci identifikátoru URI při formální parametry typu kontraktu, může být typy jiné než řetězec.</span><span class="sxs-lookup"><span data-stu-id="9df3c-152">The template parameters appear in the form of strings within the URI while the formal parameters of a typed contract might be of non-string types.</span></span> <span data-ttu-id="9df3c-153">Převodu z je proto potřeba předtím, než může vyvolat operace.</span><span class="sxs-lookup"><span data-stu-id="9df3c-153">Therefore, a conversion needs to take place before the operation can be invoked.</span></span> <span data-ttu-id="9df3c-154">A [tabulku převod formátů](http://msdn.microsoft.com/library/bb412172.aspx) je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9df3c-154">A [table of conversion formats](http://msdn.microsoft.com/library/bb412172.aspx) is available.</span></span>  
  
 <span data-ttu-id="9df3c-155">Ale pokud převod selže, pak neexistuje žádný způsob, jak v operaci vědět, že něco nepovede.</span><span class="sxs-lookup"><span data-stu-id="9df3c-155">However, if the conversion fails, then there's no way to let the operation know that something has gone wrong.</span></span> <span data-ttu-id="9df3c-156">Převod typu místo toho zobrazí ve formě selhání odesílání.</span><span class="sxs-lookup"><span data-stu-id="9df3c-156">The type conversion instead surfaces in the form of a dispatch failure.</span></span>  
  
 <span data-ttu-id="9df3c-157">Odesílání chybu v převodu typů může být stejný jako u mnoha jiných typů chyb odesílání prověřovány nainstalováním obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="9df3c-157">A type conversion dispatch failure can be inspected the same as with many other types of dispatch failures by installing an error handler.</span></span> <span data-ttu-id="9df3c-158">Zpracování výjimek úrovně služeb se nazývá bod rozšiřitelnosti IErrorHandler.</span><span class="sxs-lookup"><span data-stu-id="9df3c-158">The IErrorHandler extensibility point is called to handle service-level exceptions.</span></span> <span data-ttu-id="9df3c-159">Z tohoto místa odpověď k odeslání zpět do volající – jako a proveďte vlastní úlohu a vytváření sestav – je možné zvolit.</span><span class="sxs-lookup"><span data-stu-id="9df3c-159">From there, the response to be sent back to the caller – as well as perform any custom tasks and reporting – may be chosen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df3c-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="9df3c-160">See Also</span></span>  
 [<span data-ttu-id="9df3c-161">Zpracování chyb základní WCF</span><span class="sxs-lookup"><span data-stu-id="9df3c-161">Basic WCF Error Handling</span></span>](http://msdn.microsoft.com/library/gg281715.aspx)