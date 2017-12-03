---
title: "Vlastní upgrady streamů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20b061418ee2dc6c3adcde5553d29e680d739582
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-stream-upgrades"></a><span data-ttu-id="d2d65-102">Vlastní upgrady streamů</span><span class="sxs-lookup"><span data-stu-id="d2d65-102">Custom Stream Upgrades</span></span>
<span data-ttu-id="d2d65-103">Datový proud orientované přenosy například TCP a pojmenované kanály pracovat nepřetržitý proud bajtů mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="d2d65-103">Stream-oriented transports such as TCP and Named Pipes operate on a continuous stream of bytes between the client and server.</span></span> <span data-ttu-id="d2d65-104">Tento datový proud je realizován pomocí <xref:System.IO.Stream> objektu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-104">This stream is realized by a  <xref:System.IO.Stream> object.</span></span> <span data-ttu-id="d2d65-105">V případě upgradu datového proudu klient chce, aby se k přidání volitelné protokol vrstvy kanálu zásobníku a požádá druhém konci komunikační kanál Uděláte to tak.</span><span class="sxs-lookup"><span data-stu-id="d2d65-105">In a stream upgrade, the client wants to add an optional protocol layer to the channel stack, and asks the other end of the communication channel to do so.</span></span> <span data-ttu-id="d2d65-106">Upgrade datového proudu se skládá v nahrazení původní <xref:System.IO.Stream> objekt s některého upgradovaný.</span><span class="sxs-lookup"><span data-stu-id="d2d65-106">The stream upgrade consists in replacing the original <xref:System.IO.Stream> object with an upgraded one.</span></span>  
  
 <span data-ttu-id="d2d65-107">Můžete například vytvořit kompresního streamu přímo na základě datového proudu přenosu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-107">For example, you can build a compression stream directly on top of the transport stream.</span></span> <span data-ttu-id="d2d65-108">V tomto případě původní přenos <xref:System.IO.Stream> se nahradí ten, který zabalí komprese <xref:System.IO.Stream> kolem původnímu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-108">In this case the original transport <xref:System.IO.Stream> is replaced with one that wraps the compression <xref:System.IO.Stream> around the original one.</span></span>  
  
 <span data-ttu-id="d2d65-109">Můžete použít více upgradů datového proudu, každý zabalení ten předchozí.</span><span class="sxs-lookup"><span data-stu-id="d2d65-109">You can apply multiple stream upgrades, each wrapping the preceding one.</span></span>  
  
## <a name="how-stream-upgrades-work"></a><span data-ttu-id="d2d65-110">Jak datového proudu upgraduje pracovní</span><span class="sxs-lookup"><span data-stu-id="d2d65-110">How Stream Upgrades Work</span></span>  
 <span data-ttu-id="d2d65-111">Existují čtyři součásti pro proces upgradu datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-111">There are four components to the stream upgrade process.</span></span>  
  
1.  <span data-ttu-id="d2d65-112">Upgrade datového proudu *iniciátor* zahájí proces: při spuštění ho můžete zahájit požadavek na druhém konci připojení k upgradu přenosové vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-112">An upgrade stream *Initiator* begins the process: at run-time it can initiate a request to the other end of its connection to upgrade the channel transport layer.</span></span>  
  
2.  <span data-ttu-id="d2d65-113">Upgrade datového proudu *dodavatelem* provede upgrade: při spuštění obdrží žádost o upgrade z jiné počítače a pokud je to možné, přijímá upgradu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-113">An upgrade stream *Acceptor* carries out the upgrade: at run-time it receives the upgrade request from the other machine, and if possible, accepts the upgrade.</span></span>  
  
3.  <span data-ttu-id="d2d65-114">Upgrade *zprostředkovatele* vytvoří *iniciátor* na straně klienta a *dodavatelem* na serveru.</span><span class="sxs-lookup"><span data-stu-id="d2d65-114">An upgrade *Provider* creates the *Initiator* on the client and the *Acceptor* on the server.</span></span>  
  
4.  <span data-ttu-id="d2d65-115">Upgrade datového proudu *vazby Element* se přidá do vazby na službu a klienta a vytvoří zprostředkovatele za běhu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-115">A stream upgrade *Binding Element* is added to the bindings on the service and the client, and creates the provider at runtime.</span></span>  
  
 <span data-ttu-id="d2d65-116">Všimněte si, že v případě více upgradů iniciátor a dodavatel zapouzdření stavu počítače k vynucení, který upgradu přechody jsou platné pro každé spuštění.</span><span class="sxs-lookup"><span data-stu-id="d2d65-116">Note that in the case of multiple upgrades, the Initiator and Acceptor encapsulate state machines to enforce which upgrade transitions are valid for each Initiation.</span></span>  
  
## <a name="how-to-implement-a-stream-upgrade"></a><span data-ttu-id="d2d65-117">Jak implementovat upgradu datového proudu</span><span class="sxs-lookup"><span data-stu-id="d2d65-117">How to Implement a Stream Upgrade</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="d2d65-118">poskytuje čtyři `abstract` třídy, které můžete implementovat:</span><span class="sxs-lookup"><span data-stu-id="d2d65-118"> provides four `abstract` classes that you can implement:</span></span>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 <span data-ttu-id="d2d65-119">Chcete-li implementovat vlastní datový proud upgrade, postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="d2d65-119">To implement a custom stream upgrade, do the following.</span></span> <span data-ttu-id="d2d65-120">Tento postup implementuje procesu upgradu minimální datový proud na počítačích, klient i server.</span><span class="sxs-lookup"><span data-stu-id="d2d65-120">This procedure implements a minimal stream upgrade process on both the client and server machines.</span></span>  
  
1.  <span data-ttu-id="d2d65-121">Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.</span><span class="sxs-lookup"><span data-stu-id="d2d65-121">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.</span></span>  
  
    1.  <span data-ttu-id="d2d65-122">Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> metoda provést v datovém proudu upgradovat a vrátíte se do upgradovaný datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-122">Override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> method to take in the stream to be upgraded, and return the upgraded stream.</span></span> <span data-ttu-id="d2d65-123">Tato metoda funguje synchronně; asynchronně zahájit upgrade podobá způsoby.</span><span class="sxs-lookup"><span data-stu-id="d2d65-123">This method works synchronously; there are analogous methods to initiate the upgrade asynchronously.</span></span>  
  
    2.  <span data-ttu-id="d2d65-124">Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metoda zkontrolujte další možnosti upgradu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-124">Override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> method to check for additional upgrades.</span></span>  
  
2.  <span data-ttu-id="d2d65-125">Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.</span><span class="sxs-lookup"><span data-stu-id="d2d65-125">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.</span></span>  
  
    1.  <span data-ttu-id="d2d65-126">Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> metoda provést v datovém proudu upgradovat a vrátíte se do upgradovaný datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-126">Override the <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> method to take in the stream to be upgraded, and return the upgraded stream.</span></span> <span data-ttu-id="d2d65-127">Tato metoda funguje synchronně; jsou obdobou metody tak, aby přijímal upgradu asynchronně.</span><span class="sxs-lookup"><span data-stu-id="d2d65-127">This method works synchronously; there are analogous methods to accept the upgrade asynchronously.</span></span>  
  
    2.  <span data-ttu-id="d2d65-128">Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metoda k určení, pokud je upgrade požadovaný nepodporuje tento upgrade dodavatel v tomto okamžiku v procesu upgradu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-128">Override the <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> method to determine if the upgrade requested is supported by this upgrade acceptor at this point in the upgrade process.</span></span>  
  
3.  <span data-ttu-id="d2d65-129">Vytvořte třídu implementuje <xref:System.ServiceModel.Channels.StreamUpgradeProvider>.</span><span class="sxs-lookup"><span data-stu-id="d2d65-129">Create a class the implements <xref:System.ServiceModel.Channels.StreamUpgradeProvider>.</span></span> <span data-ttu-id="d2d65-130">Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> a <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> metody vrátit instance dodavatel a iniciátor definovaný v kroku 2 a 1.</span><span class="sxs-lookup"><span data-stu-id="d2d65-130">Override the <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> and the <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> methods to return instances of the acceptor and initiator defined in steps 2 and 1.</span></span>  
  
4.  <span data-ttu-id="d2d65-131">Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d2d65-131">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.</span></span>  
  
    1.  <span data-ttu-id="d2d65-132">Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> metody na straně klienta a <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> metoda ve službě.</span><span class="sxs-lookup"><span data-stu-id="d2d65-132">Override the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> method on the client and the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> method on the service.</span></span>  
  
    2.  <span data-ttu-id="d2d65-133">Přepsání <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> metody na straně klienta a <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> metoda na službu, kterou chcete přidat upgradu vazby elementu, který chcete <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2d65-133">Override the <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> method on the client and the <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> method on the service to add the upgrade Binding Element to <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.</span></span>  
  
5.  <span data-ttu-id="d2d65-134">Přidáte nový element upgradu vazby datového proudu do vazby u serverových a klientských počítačů.</span><span class="sxs-lookup"><span data-stu-id="d2d65-134">Add the new stream upgrade binding element to bindings on the server and client machines.</span></span>  
  
## <a name="security-upgrades"></a><span data-ttu-id="d2d65-135">Upgrady zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d2d65-135">Security Upgrades</span></span>  
 <span data-ttu-id="d2d65-136">Přidání upgrade zabezpečení je specializovanou verzi procesu upgradu obecné datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-136">Adding a security upgrade is a specialized version of the general stream upgrade process.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d2d65-137">již poskytuje dva elementy vazby pro upgrade zabezpečení datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-137"> already provides two binding elements for upgrading stream security.</span></span> <span data-ttu-id="d2d65-138">Konfigurace zabezpečení na úrovni přenosu je zapouzdřené pomocí <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> a <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> které mohou být konfigurovány a přidat do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d2d65-138">The configuration of transport-level security is encapsulated by the <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> and the <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> which can be configured and added to a custom binding.</span></span> <span data-ttu-id="d2d65-139">Tyto prvky vazeb rozšířit <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> třídu, která vytvoří datový proud klientských a serverových upgradu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d2d65-139">These binding elements extend the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> class that builds the client and server stream upgrade providers.</span></span> <span data-ttu-id="d2d65-140">Tyto prvky vazeb mají metody, které vytvoření datového proudu specializované zabezpečení třídy upgradu zprostředkovatele, které nejsou `public`, takže pro tyto dva případy všechny musíte udělat je přidat do vazby prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d2d65-140">These binding elements have methods that create the specialized security stream upgrade provider classes, which are not `public`, so for these two cases all you need to do is to add the binding element to the binding.</span></span>  
  
 <span data-ttu-id="d2d65-141">Pro scénáře zabezpečení nejsou splněny ve výše uvedené prvky dvě vazby, tři související se zabezpečením `abstract` třídy jsou odvozené z výše uvedených iniciátor, dodavatel a zprostředkovatele základních tříd:</span><span class="sxs-lookup"><span data-stu-id="d2d65-141">For security scenarios not met by the above two binding elements, three security-related `abstract` classes are derived from the above initiator, acceptor and provider base classes:</span></span>  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 <span data-ttu-id="d2d65-142">Proces implementace upgrade datového proudu zabezpečení je stejná jako předtím, s tím rozdílem, že by odvozena z těchto tří tříd.</span><span class="sxs-lookup"><span data-stu-id="d2d65-142">The process of implementing a security stream upgrade is the same as before, with the difference that you would derive from these three classes.</span></span> <span data-ttu-id="d2d65-143">Přepsání dalších vlastností v těchto tříd zadat informace o zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d2d65-143">Override the additional properties in these classes to supply security information to the runtime.</span></span>  
  
## <a name="multiple-upgrades"></a><span data-ttu-id="d2d65-144">Více upgradů</span><span class="sxs-lookup"><span data-stu-id="d2d65-144">Multiple Upgrades</span></span>  
 <span data-ttu-id="d2d65-145">Vytvořit další upgradu požadavky, opakujte výše postup: vytvoření další rozšíření <xref:System.ServiceModel.Channels.StreamUpgradeProvider> a elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="d2d65-145">To create additional upgrade requests repeat the above process: create additional extensions of <xref:System.ServiceModel.Channels.StreamUpgradeProvider> and binding elements.</span></span> <span data-ttu-id="d2d65-146">Prvky vazby přidáte vazbu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-146">Add the binding elements to the binding.</span></span> <span data-ttu-id="d2d65-147">Prvky další vazby jsou zpracovávány postupně, počínaje první vazba prvek přidán do vazby.</span><span class="sxs-lookup"><span data-stu-id="d2d65-147">The additional binding elements are processed sequentially, starting with the first binding element added to the binding.</span></span> <span data-ttu-id="d2d65-148">V <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> a <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> každý poskytovatel upgradu můžete určit, jak se sám vrstvy na všechny existující upgrade vazby parametrů.</span><span class="sxs-lookup"><span data-stu-id="d2d65-148">In <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> and <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> each upgrade provider can determine how to layer itself on any pre-existing upgrade binding parameters.</span></span> <span data-ttu-id="d2d65-149">Potom by mělo nahradit existující upgradu vazba parametru s nový parametr složené upgradu vazbu.</span><span class="sxs-lookup"><span data-stu-id="d2d65-149">It should then replace the existing upgrade binding parameter with a new composite upgrade binding parameter.</span></span>  
  
 <span data-ttu-id="d2d65-150">Alternativně jednoho poskytovatele upgradu může podporovat více upgradů.</span><span class="sxs-lookup"><span data-stu-id="d2d65-150">Alternatively, one upgrade provider can support multiple upgrades.</span></span> <span data-ttu-id="d2d65-151">Například můžete chtít implementovat vlastní datový proud upgradu zprostředkovatele, který podporuje zabezpečení a komprese.</span><span class="sxs-lookup"><span data-stu-id="d2d65-151">For example, you might want to implement a custom stream upgrade provider that supports both security and compression.</span></span> <span data-ttu-id="d2d65-152">Proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d2d65-152">Do the following steps:</span></span>  
  
1.  <span data-ttu-id="d2d65-153">Podtřída <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> zapisovat zprostředkovatele třídu, která vytvoří iniciátor a příjemce.</span><span class="sxs-lookup"><span data-stu-id="d2d65-153">Subclass <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> to write the provider class that creates the Initiator and Acceptor.</span></span>  
  
2.  <span data-ttu-id="d2d65-154">Podtřída <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> a zkontrolujte, zda přepsat <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metoda vrátí typy obsahu pro kompresního streamu a zabezpečený datový proud v pořadí.</span><span class="sxs-lookup"><span data-stu-id="d2d65-154">Subclass the <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> making sure to override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> method to return the content types for the compression stream and the secure stream in order.</span></span>  
  
3.  <span data-ttu-id="d2d65-155">Podtřída <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> , rozumí vlastní typy obsahu v jeho <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d2d65-155">Subclass the <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> that understands the custom content types in its <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> method.</span></span>  
  
4.  <span data-ttu-id="d2d65-156">Datový proud se upgraduje po každé volání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> a <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2d65-156">The stream will be upgraded after each call to <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> and <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d65-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2d65-157">See Also</span></span>  
 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>