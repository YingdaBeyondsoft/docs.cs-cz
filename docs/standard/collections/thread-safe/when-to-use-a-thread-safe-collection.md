---
title: "Kdy použít kolekci s bezpečnými vlákny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bfb5ef2679c4e20e99a10dcf82a251673811b41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-a-thread-safe-collection"></a><span data-ttu-id="02fea-102">Kdy použít kolekci s bezpečnými vlákny</span><span class="sxs-lookup"><span data-stu-id="02fea-102">When to Use a Thread-Safe Collection</span></span>
<span data-ttu-id="02fea-103">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Zavádí pět nové typy kolekcí, které jsou speciálně určené pro podporu Vícevláknová přidávat a odebírat operace.</span><span class="sxs-lookup"><span data-stu-id="02fea-103">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] introduces five new collection types that are specially designed to support multi-threaded add and remove operations.</span></span> <span data-ttu-id="02fea-104">K dosažení vláken, použít tyto nové typy různé druhy efektivní zamykání a mechanismy zámku bez synchronizace.</span><span class="sxs-lookup"><span data-stu-id="02fea-104">To achieve thread-safety, these new types use various kinds of efficient locking and lock-free synchronization mechanisms.</span></span> <span data-ttu-id="02fea-105">Synchronizace přidá režie pro operaci.</span><span class="sxs-lookup"><span data-stu-id="02fea-105">Synchronization adds overhead to an operation.</span></span> <span data-ttu-id="02fea-106">Množství práce, závisí na typ synchronizace, která se používá, druh operace, které se provádí a dalších faktorů, jako je počet vláken, které se pokoušíte získat přístup ke kolekci současně.</span><span class="sxs-lookup"><span data-stu-id="02fea-106">The amount of overhead depends on the kind of synchronization that is used, the kind of operations that are performed, and other factors such as the number of threads that are trying to concurrently access the collection.</span></span>  
  
 <span data-ttu-id="02fea-107">V některých scénářích synchronizace režie je nepatrné a umožňuje Vícevláknová typ výrazně rychlejší a škálovat mnohem lepší, než ekvivalentní není bezpečná pro přístup z více vláken při ochraně externí zámek.</span><span class="sxs-lookup"><span data-stu-id="02fea-107">In some scenarios, synchronization overhead is negligible and enables the multi-threaded type to perform significantly faster and scale far better than its non-thread-safe equivalent when protected by an external lock.</span></span> <span data-ttu-id="02fea-108">V jiných scénářích může způsobit nároky na typ bezpečného přístupu k provedení a škálování o stejný nebo i pomaleji než verze externě uzamčen, není bezpečná pro přístup z více vláken typu.</span><span class="sxs-lookup"><span data-stu-id="02fea-108">In other scenarios, the overhead can cause the thread-safe type to perform and scale about the same or even more slowly than the externally-locked, non-thread-safe version of the type.</span></span>  
  
 <span data-ttu-id="02fea-109">Následující části obsahují obecné pokyny o tom, kdy použít kolekci s bezpečnými vlákny versus ekvivalentem není bezpečná pro přístup z více vláken, který má zadaný uživatelem zámek čtení a zápisu operace.</span><span class="sxs-lookup"><span data-stu-id="02fea-109">The following sections provide general guidance about when to use a thread-safe collection versus its non-thread-safe equivalent that has a user-provided lock around its read and write operations.</span></span> <span data-ttu-id="02fea-110">Protože výkon se může lišit v závislosti na mnoha faktorech, není konkrétní pokyny a není nutně platné za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="02fea-110">Because performance may vary depending on many factors, the guidance is not specific and is not necessarily valid in all circumstances.</span></span> <span data-ttu-id="02fea-111">Pokud výkon je velmi důležité, je nejlepší způsob, jak určit typů kolekce, které se mají použít k měření výkonu na základě reprezentativní konfiguraci počítače a zatížení.</span><span class="sxs-lookup"><span data-stu-id="02fea-111">If performance is very important, then the best way to determine which collection type to use is to measure performance based on representative computer configurations and loads.</span></span> <span data-ttu-id="02fea-112">Tento dokument používá následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="02fea-112">This document uses the following terms:</span></span>  
  
 <span data-ttu-id="02fea-113">*Scénář čistý producent – příjemce*</span><span class="sxs-lookup"><span data-stu-id="02fea-113">*Pure producer-consumer scenario*</span></span>  
 <span data-ttu-id="02fea-114">Jakékoli dané vlákno je buď přidáním nebo odebráním elementů, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="02fea-114">Any given thread is either adding or removing elements, but not both.</span></span>  
  
 <span data-ttu-id="02fea-115">*Scénář smíšený producent – příjemce*</span><span class="sxs-lookup"><span data-stu-id="02fea-115">*Mixed producer-consumer scenario*</span></span>  
 <span data-ttu-id="02fea-116">Jakékoli dané vlákno přidání i odebrání elementy.</span><span class="sxs-lookup"><span data-stu-id="02fea-116">Any given thread is both adding and removing elements.</span></span>  
  
 <span data-ttu-id="02fea-117">*Zrychlení*</span><span class="sxs-lookup"><span data-stu-id="02fea-117">*Speedup*</span></span>  
 <span data-ttu-id="02fea-118">Rychlejší algoritmické výkonu vzhledem k jinému typu stejný scénář.</span><span class="sxs-lookup"><span data-stu-id="02fea-118">Faster algorithmic performance relative to another type in the same scenario.</span></span>  
  
 <span data-ttu-id="02fea-119">*Škálovatelnost*</span><span class="sxs-lookup"><span data-stu-id="02fea-119">*Scalability*</span></span>  
 <span data-ttu-id="02fea-120">Zvýšení výkonu, který je přímo úměrná počtu jader v počítači.</span><span class="sxs-lookup"><span data-stu-id="02fea-120">The increase in performance that is proportional to the number of cores on the computer.</span></span> <span data-ttu-id="02fea-121">Algoritmus, který přizpůsobí provede osm jader na rychlejší než u dvě jádra.</span><span class="sxs-lookup"><span data-stu-id="02fea-121">An algorithm that scales performs faster on eight cores than it does on two cores.</span></span>  
  
## <a name="concurrentqueuet-vs-queuet"></a><span data-ttu-id="02fea-122">ConcurrentQueue(T) vs. Queue(T)</span><span class="sxs-lookup"><span data-stu-id="02fea-122">ConcurrentQueue(T) vs. Queue(T)</span></span>  
 <span data-ttu-id="02fea-123">V čistě producent – příjemce scénářích, kde je doba zpracování pro každý prvek velmi malé (pár pokynů), pak <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> může nabídnout menší výkony oproti <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> má externí zámek.</span><span class="sxs-lookup"><span data-stu-id="02fea-123">In pure producer-consumer scenarios, where the processing time for each element is very small (a few instructions), then <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> can offer modest performance benefits over a <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> that has an external lock.</span></span> <span data-ttu-id="02fea-124">V tomto scénáři <xref:System.Collections.Concurrent.ConcurrentQueue%601> poskytuje nejlepší výkon, když je služba Řízení front jedním vláknem a jedním vláknem vyřazuje z fronty.</span><span class="sxs-lookup"><span data-stu-id="02fea-124">In this scenario, <xref:System.Collections.Concurrent.ConcurrentQueue%601> performs best when one dedicated thread is queuing and one dedicated thread is de-queuing.</span></span> <span data-ttu-id="02fea-125">Pokud toto pravidlo, pak nevynutíte <xref:System.Collections.Generic.Queue%601> může provádět i mírně rychlejší než <xref:System.Collections.Concurrent.ConcurrentQueue%601> na počítačích, které mají víc jader.</span><span class="sxs-lookup"><span data-stu-id="02fea-125">If you do not enforce this rule, then <xref:System.Collections.Generic.Queue%601> might even perform slightly faster than <xref:System.Collections.Concurrent.ConcurrentQueue%601> on computers that have multiple cores.</span></span>  
  
 <span data-ttu-id="02fea-126">Pokud doba zpracování je přibližně 500 FLOPS (operací s pohyblivou čárkou) nebo další, pak pravidlo dvou vláken nevztahuje na <xref:System.Collections.Concurrent.ConcurrentQueue%601>, který pak má velmi dobré škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="02fea-126">When processing time is around 500 FLOPS (floating point operations) or more, then the two-thread rule does not apply to <xref:System.Collections.Concurrent.ConcurrentQueue%601>, which then has very good scalability.</span></span> <span data-ttu-id="02fea-127"><xref:System.Collections.Generic.Queue%601>nejsou adekvátní i v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="02fea-127"><xref:System.Collections.Generic.Queue%601> does not scale well in this scenario.</span></span>  
  
 <span data-ttu-id="02fea-128">Ve smíšených producent – příjemce scénářích, kdy je velmi malý, bude čas zpracování <xref:System.Collections.Generic.Queue%601> má externí zámek škáluje líp, než <xref:System.Collections.Concurrent.ConcurrentQueue%601> nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="02fea-128">In mixed producer-consumer scenarios, when the processing time is very small, a <xref:System.Collections.Generic.Queue%601> that has an external lock scales better than <xref:System.Collections.Concurrent.ConcurrentQueue%601> does.</span></span> <span data-ttu-id="02fea-129">Ale pokud je doba zpracování přibližně 500 FLOPS nebo více, pak se <xref:System.Collections.Concurrent.ConcurrentQueue%601> poskytuje lepší škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="02fea-129">However, when processing time is around 500 FLOPS or more, then the <xref:System.Collections.Concurrent.ConcurrentQueue%601> scales better.</span></span>  
  
## <a name="concurrentstack-vs-stack"></a><span data-ttu-id="02fea-130">ConcurrentStack vs. Rámec</span><span class="sxs-lookup"><span data-stu-id="02fea-130">ConcurrentStack vs. Stack</span></span>  
 <span data-ttu-id="02fea-131">V čistě producent – příjemce scénáře, kdy je čas zpracování velmi malý, pak <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> má externí zámek provede pravděpodobně o totožný s jedním vláknem vyhrazeným operace vložení a jeden vyhrazený vláknem.</span><span class="sxs-lookup"><span data-stu-id="02fea-131">In pure producer-consumer scenarios, when processing time is very small, then <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> and <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> that has an external lock will probably perform about the same with one dedicated pushing thread and one dedicated popping thread.</span></span> <span data-ttu-id="02fea-132">Ale, jako je počet vláken zvyšuje oba typy zpomalit kvůli rostoucím sporům, a <xref:System.Collections.Generic.Stack%601> by mohl poskytovat lepší, než <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="02fea-132">However, as the number of threads increases, both types slow down because of increased contention, and <xref:System.Collections.Generic.Stack%601> might perform better than <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span> <span data-ttu-id="02fea-133">Pokud je doba zpracování přibližně 500 FLOPS nebo více, pak oba typy škálování v o stejný kurz.</span><span class="sxs-lookup"><span data-stu-id="02fea-133">When processing time is around 500 FLOPS or more, then both types scale at about the same rate.</span></span>  
  
 <span data-ttu-id="02fea-134">Ve smíšených producent – příjemce scénářích, <xref:System.Collections.Concurrent.ConcurrentStack%601> je rychlejší pro malé a velké zatížení.</span><span class="sxs-lookup"><span data-stu-id="02fea-134">In mixed producer-consumer scenarios, <xref:System.Collections.Concurrent.ConcurrentStack%601> is faster for both small and large workloads.</span></span>  
  
 <span data-ttu-id="02fea-135">Použití <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> a <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> může výrazně zrychlit čas přístupu.</span><span class="sxs-lookup"><span data-stu-id="02fea-135">The use of the <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> and <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> may greatly speed up access times.</span></span>  
  
## <a name="concurrentdictionary-vs-dictionary"></a><span data-ttu-id="02fea-136">ConcurrentDictionary vs. Slovník</span><span class="sxs-lookup"><span data-stu-id="02fea-136">ConcurrentDictionary vs. Dictionary</span></span>  
 <span data-ttu-id="02fea-137">Obecně platí, používat <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> v žádném scénáři, kde jsou přidat a aktualizovat klíče nebo hodnoty z více vláken současně.</span><span class="sxs-lookup"><span data-stu-id="02fea-137">In general, use a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> in any scenario where you are adding and updating keys or values concurrently from multiple threads.</span></span> <span data-ttu-id="02fea-138">Ve scénářích, které obsahují časté aktualizace a relativně malý počet čtení <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně nabízí mírné výhody.</span><span class="sxs-lookup"><span data-stu-id="02fea-138">In scenarios that involve frequent updates and relatively few reads, the <xref:System.Collections.Concurrent.ConcurrentDictionary%602> generally offers modest benefits.</span></span> <span data-ttu-id="02fea-139">Ve scénářích, které obsahují mnoho čtení a mnoho aktualizací <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně je výrazně rychlejší v počítačích, které mají libovolný počet jader.</span><span class="sxs-lookup"><span data-stu-id="02fea-139">In scenarios that involve many reads and many updates, the <xref:System.Collections.Concurrent.ConcurrentDictionary%602> generally is significantly faster on computers that have any number of cores.</span></span>  
  
 <span data-ttu-id="02fea-140">Ve scénářích, které obsahují časté aktualizace, můžete zvýšit stupeň souběžnosti v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a pak měřit zda výkon zvýšil na počítačích, které mají více jader.</span><span class="sxs-lookup"><span data-stu-id="02fea-140">In scenarios that involve frequent updates, you can increase the degree of concurrency in the <xref:System.Collections.Concurrent.ConcurrentDictionary%602> and then measure to see whether performance increases on computers that have more cores.</span></span> <span data-ttu-id="02fea-141">Pokud změníte úroveň souběžnosti, vyhněte se co nejvíce globální operace.</span><span class="sxs-lookup"><span data-stu-id="02fea-141">If you change the concurrency level, avoid global operations as much as possible.</span></span>  
  
 <span data-ttu-id="02fea-142">Při čtení pouze klíče nebo hodnoty, <xref:System.Collections.Generic.Dictionary%602> je rychlejší, protože pokud slovníku není upravován žádné podprocesy není nutná žádná synchronizace.</span><span class="sxs-lookup"><span data-stu-id="02fea-142">If you are only reading key or values, the <xref:System.Collections.Generic.Dictionary%602> is faster because no synchronization is required if the dictionary is not being modified by any threads.</span></span>  
  
## <a name="concurrentbag"></a><span data-ttu-id="02fea-143">ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="02fea-143">ConcurrentBag</span></span>  
 <span data-ttu-id="02fea-144">Ve scénářích čistý producent – příjemce <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> budou pravděpodobně fungovat pomaleji než jiné typy souběžných kolekcí.</span><span class="sxs-lookup"><span data-stu-id="02fea-144">In pure producer-consumer scenarios, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> will probably perform more slowly than the other concurrent collection types.</span></span>  
  
 <span data-ttu-id="02fea-145">Ve smíšených producent – příjemce scénářích, <xref:System.Collections.Concurrent.ConcurrentBag%601> je obvykle mnohem rychlejší a větší škálovatelnost než žádným jiným typem souběžných kolekce pro malé i velké zatížení.</span><span class="sxs-lookup"><span data-stu-id="02fea-145">In mixed producer-consumer scenarios, <xref:System.Collections.Concurrent.ConcurrentBag%601> is generally much faster and more scalable than any other concurrent collection type for both large and small workloads.</span></span>  
  
## <a name="blockingcollection"></a><span data-ttu-id="02fea-146">BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="02fea-146">BlockingCollection</span></span>  
 <span data-ttu-id="02fea-147">Když jsou povinné, sémantika ohraničování a blokování <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> bude pravděpodobně rychlejší než jakákoli vlastní implementace.</span><span class="sxs-lookup"><span data-stu-id="02fea-147">When bounding and blocking semantics are required, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> will probably perform faster than any custom implementation.</span></span> <span data-ttu-id="02fea-148">Podporuje také bohaté zrušení, výčet a výjimek.</span><span class="sxs-lookup"><span data-stu-id="02fea-148">It also supports rich cancellation, enumeration, and exception handling.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02fea-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="02fea-149">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="02fea-150">Kolekce bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="02fea-150">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)  
 [<span data-ttu-id="02fea-151">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="02fea-151">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)