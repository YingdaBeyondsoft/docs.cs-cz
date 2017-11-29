---
title: "Úrovně důvěryhodnosti zabezpečení v přístupu k prostředkům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4cefe74b745eb4a1c71124176985c548f9b1244
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-trust-levels-in-accessing-resources"></a><span data-ttu-id="e5e1b-102">Úrovně důvěryhodnosti zabezpečení v přístupu k prostředkům</span><span class="sxs-lookup"><span data-stu-id="e5e1b-102">Security Trust Levels in Accessing Resources</span></span>
<span data-ttu-id="e5e1b-103">Toto téma popisuje, jak je omezen přístup na studijních materiálech, které <xref:System.Transactions> zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-103">This topic discusses how access is restricted on the types of resources that <xref:System.Transactions> exposes.</span></span>  
  
 <span data-ttu-id="e5e1b-104">Existují tři hlavní úrovně důvěryhodnosti pro <xref:System.Transactions>.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-104">There are three main levels of trust for <xref:System.Transactions>.</span></span> <span data-ttu-id="e5e1b-105">Úrovně důvěryhodnosti jsou definovány v závislosti na studijních materiálech, které <xref:System.Transactions> zpřístupňuje a úroveň vztahu důvěryhodnosti, který je třeba získat přístup k těmto prostředkům.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-105">The trust levels are defined based on the types of resources that <xref:System.Transactions> exposes, and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="e5e1b-106">Materiály, <xref:System.Transactions> poskytuje přístup k jsou systémové paměti, sdílený proces wide materiály a široké systémových prostředků.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-106">The resources that <xref:System.Transactions> provides access to are system memory, shared process wide resources, and system wide resources.</span></span> <span data-ttu-id="e5e1b-107">Úrovně jsou:</span><span class="sxs-lookup"><span data-stu-id="e5e1b-107">The levels are:</span></span>  
  
-   <span data-ttu-id="e5e1b-108">**AllowPartiallyTrustedCallers** (APTCA) pro aplikace pomocí transakce v rámci domény jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-108">**AllowPartiallyTrustedCallers** (APTCA) for applications using transactions within a single application domain.</span></span>  
  
-   <span data-ttu-id="e5e1b-109">**DistributedTransactionPermission** (DTP) pro aplikace pomocí distribuovaných transakcí.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-109">**DistributedTransactionPermission** (DTP) for applications using distributed transactions.</span></span>  
  
-   <span data-ttu-id="e5e1b-110">Úplný vztah důvěryhodnosti pro trvalý zdroje, aplikace pro správu konfigurace a starší definiční aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-110">Full trust for durable resources, configuration management applications, and legacy interop applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5e1b-111">Neměli volat některý z rozhraní zařazení s zosobněným kontexty.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-111">You should not call any of the enlistment interfaces with impersonated contexts.</span></span>  
  
## <a name="trust-levels"></a><span data-ttu-id="e5e1b-112">Úrovně důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="e5e1b-112">Trust Levels</span></span>  
  
### <a name="aptca-partial-trust"></a><span data-ttu-id="e5e1b-113">APTCA (částečným vztahem důvěryhodnosti)</span><span class="sxs-lookup"><span data-stu-id="e5e1b-113">APTCA (Partial Trust)</span></span>  
 <span data-ttu-id="e5e1b-114"><xref:System.Transactions> Sestavení lze volat částečně důvěryhodným kódem, protože je označená s **AllowPartiallyTrustedCallers** atribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="e5e1b-114">The <xref:System.Transactions> assembly can be called by partially trusted code because it has been marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="e5e1b-115">Tento atribut v podstatě odebere implicitní <xref:System.Security.Permissions.SecurityAction.LinkDemand> pro **FullTrust** oprávnění, který je nastavena jinak automaticky umístí na jednotlivých metod veřejně dostupné v jednotlivých typů.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-115">This attribute essentially removes the implicit <xref:System.Security.Permissions.SecurityAction.LinkDemand> for the **FullTrust** permission set that is otherwise automatically placed on each publicly accessible method in each type.</span></span> <span data-ttu-id="e5e1b-116">Nicméně některé typy a členy stále vyžadují bezpečnějších oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-116">However, some types and members still require stronger permissions.</span></span>  
  
 <span data-ttu-id="e5e1b-117">Atribut APTCA umožňuje aplikacím používat transakcí v částečným vztahem důvěryhodnosti v rámci jediné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-117">The APTCA attribute enables applications to use transactions in partial trust within a single application domain.</span></span> <span data-ttu-id="e5e1b-118">To umožňuje-eskalován transakce a Nestálá zařazení, které lze použít pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-118">This enables non-escalated transactions and volatile enlistments that can be used for error handling.</span></span> <span data-ttu-id="e5e1b-119">Příkladem je tabulka transacted hash a aplikace, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-119">One example of this is a transacted hash table and an application that uses it.</span></span> <span data-ttu-id="e5e1b-120">Data lze přidat do a odebrán z tabulky hash v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-120">Data can be added to and removed from the hash table under a single transaction.</span></span> <span data-ttu-id="e5e1b-121">Pokud později transakce vrácena zpět, všechny změny provedené v tabulce hash v rámci dané transakce lze vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-121">If the transaction is later rolled back, all of the changes made to the hash table under that transaction can be undone.</span></span>  
  
### <a name="distributedtransactionpermission-dtp"></a><span data-ttu-id="e5e1b-122">DistributedTransactionPermission (DTP)</span><span class="sxs-lookup"><span data-stu-id="e5e1b-122">DistributedTransactionPermission (DTP)</span></span>  
 <span data-ttu-id="e5e1b-123">Když <xref:System.Transactions> transakce je eskalován jej lze spravovat pomocí nástroje MSDTC, <xref:System.Transactions> požadavky <xref:System.Transactions.DistributedTransactionPermission> (DTP) k vytvoření distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-123">When a <xref:System.Transactions> transaction is escalated to be managed by MSDTC, <xref:System.Transactions> demands the <xref:System.Transactions.DistributedTransactionPermission> (DTP) to create the distributed transaction.</span></span> <span data-ttu-id="e5e1b-124">To znamená, že kód, který způsobí, že transakce se eskalován (například prostřednictvím serializace nebo další trvalé zařazení) by bylo nutné mít udělena DTP.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-124">This means that the code that causes the transaction to be escalated (such as through serialization or additional durable enlistments) would need to be granted DTP.</span></span> <span data-ttu-id="e5e1b-125">Kód, který původně vytvořil <xref:System.Transactions> transakce nutně nemusí mít toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-125">The code that originally created the <xref:System.Transactions> transaction does not necessarily need to possess this permission.</span></span>  
  
### <a name="fulltrust-link-demands"></a><span data-ttu-id="e5e1b-126">Požadavky na propojení FullTrust</span><span class="sxs-lookup"><span data-stu-id="e5e1b-126">FullTrust Link Demands</span></span>  
 <span data-ttu-id="e5e1b-127">Tuto úroveň oprávnění je určena k omezení aplikace, které jsou zápisu do trvalý prostředků.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-127">This permission level is intended to restrict applications that are writing to durable resources.</span></span> <span data-ttu-id="e5e1b-128">Po selhání aplikace musí být možné obnovit pomocí Správce transakcí k určení konečný výsledek transakce, tak, aby jej můžete aktualizovat trvalá data.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-128">Upon failure, the application needs to be able to recover with the transaction manager to determine the final outcome of the transaction, so that it can update permanent data.</span></span> <span data-ttu-id="e5e1b-129">Tento typ aplikace, se nazývá trvalý zdroj správce.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-129">This type of application is known as a durable source manager.</span></span> <span data-ttu-id="e5e1b-130">Klasické příkladem tento typ aplikace je SQL.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-130">A classic example of this type of application is SQL.</span></span>  
  
 <span data-ttu-id="e5e1b-131">Chcete-li povolit obnovení, tento typ aplikace má možnost trvale spotřebovávat systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-131">To enable recovery, this type of application has the ability to permanently consume system resources.</span></span> <span data-ttu-id="e5e1b-132">Toto je vzhledem k tomu, že správce obnovitelných transakcí musí mějte na paměti, transakcí, které mají potvrzeny, dokud můžete ověřit, že všechny správce trvalý prostředků, které se účastní transakce přijali výsledek.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-132">This is because the recoverable transaction manager must remember transactions that have committed until it can confirm that all durable resource managers that are participating in the transaction have received the outcome.</span></span> <span data-ttu-id="e5e1b-133">Proto tento typ aplikace vyžaduje plnou důvěryhodnost a by neměl být spuštěn, není-li poskytovaná úroveň vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-133">Therefore, this type of application requires full trust and should not be run unless that level of trust has been granted.</span></span>  
  
 <span data-ttu-id="e5e1b-134">Další informace o zařazení odolné a obnovení najdete v tématu [uvedení prostředky jako účastníky v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) a [provádění obnovení](../../../../docs/framework/data/transactions/performing-recovery.md) témata.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-134">For more information on durable enlistments and recovery, see the [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) and [Performing Recovery](../../../../docs/framework/data/transactions/performing-recovery.md) topics.</span></span>  
  
 <span data-ttu-id="e5e1b-135">Aplikace, které provádějí starší verze definiční pracovat s modelu COM + jsou také nutné mít plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-135">Applications that perform legacy interop work with COM+ are also required to have full trust.</span></span>  
  
 <span data-ttu-id="e5e1b-136">Tady je seznam typů a členy, kteří nejsou volatelné částečně důvěryhodného kódu, protože jsou označených pomocí **FullTrust** atribut deklarativní zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="e5e1b-136">The following is a list of types and members that are not callable by partially trusted code because they are decorated with the **FullTrust** declarative security attribute:</span></span>  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
-   <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
-   <xref:System.Transactions.TransactionInterop>  
  
-   <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
-   <xref:System.Transactions.HostCurrentTransactionCallback>  
  
-   <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
-   <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
-   <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 <span data-ttu-id="e5e1b-137">Pouze pro bezprostředního volajícího je potřeba mít **FullTrust** nastavit oprávnění používat výše uvedených typů nebo metody.</span><span class="sxs-lookup"><span data-stu-id="e5e1b-137">Only the immediate caller is required to possess the **FullTrust** permission set to use the above types or methods.</span></span>