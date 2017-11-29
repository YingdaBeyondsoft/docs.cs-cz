---
title: "Doporučené postupy spravovaného dělení na vlákna"
ms.custom: 
ms.date: 11/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="f7d06-102">Doporučené postupy spravovaného dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="f7d06-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="f7d06-103">Multithreading vyžaduje pečlivé programování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="f7d06-104">V případě většiny úkolů lze omezit složitost umístěním požadavků do fronty pro spuštění pomocí vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="f7d06-105">Toto téma řeší obtížnější situace, například koordinaci práce více vláken nebo zpracování vláken, která se blokují.</span><span class="sxs-lookup"><span data-stu-id="f7d06-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7d06-106">Od verze rozhraní .NET Framework 4, Task Parallel Library a PLINQ poskytují rozhraní API, která snižuje některé složitost a rizika vícevláknové programování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="f7d06-107">Další informace najdete v tématu [paralelní programování v rozhraní .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7d06-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="f7d06-108">Zablokování a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="f7d06-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="f7d06-109">Multithreading řeší problémy s propustností a rychlostí odezvy, ale zároveň přináší nové problémy: zablokování a konflikty časování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="f7d06-110">Zablokování</span><span class="sxs-lookup"><span data-stu-id="f7d06-110">Deadlocks</span></span>  
 <span data-ttu-id="f7d06-111">K zablokování dochází tehdy, pokud se každé ze dvou vláken pokusí uzamknout prostředek, který je již zamčený.</span><span class="sxs-lookup"><span data-stu-id="f7d06-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="f7d06-112">Ani jedno vlákno nemůže provádět žádný další krok.</span><span class="sxs-lookup"><span data-stu-id="f7d06-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="f7d06-113">Mnoho metod tříd modelu spravovaných vláken poskytuje časové limity, které usnadňují zjišťování případů zablokování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="f7d06-114">Například následující kód, pokusí se získat zámek na objekt s názvem `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="f7d06-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="f7d06-115">Pokud není v milisekundách 300, získat zámek <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="f7d06-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="f7d06-116">Konflikty časování</span><span class="sxs-lookup"><span data-stu-id="f7d06-116">Race Conditions</span></span>  
 <span data-ttu-id="f7d06-117">Konflikt časování je chyba, ke které dojde, pokud výstup programu závisí na tom, které ze dvou nebo více vláken dříve dosáhne určitého bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="f7d06-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="f7d06-118">Opakované spuštění programu vrací různé výsledky a nelze předpovědět výsledek jakéhokoli daného běhu.</span><span class="sxs-lookup"><span data-stu-id="f7d06-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="f7d06-119">Jednoduchým příkladem konfliktu časování je zvyšování pole.</span><span class="sxs-lookup"><span data-stu-id="f7d06-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="f7d06-120">Předpokládejme, že třída obsahuje soukromé **statické** pole (**sdílené** v jazyce Visual Basic), se zvýší pokaždé, když je vytvořena instance třídy, například pomocí kódu `objCt++;` (C#) nebo `objCt += 1` () Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f7d06-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="f7d06-121">Tato operace vyžaduje načtení hodnoty z kódu `objCt` do registru, navýšení hodnoty a její uložení v kódu `objCt`.</span><span class="sxs-lookup"><span data-stu-id="f7d06-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="f7d06-122">Ve vícevláknových aplikacích platí, že vlákno, které načetlo a zvýšilo hodnotu, může být přerušeno jiným vláknem, jež provede všechny tři kroky. Pokud první vlákno pokračuje v provádění a uloží svou hodnotu, přepíše kód `objCt`, aniž by zohlednilo, že hodnota se mezitím změnila.</span><span class="sxs-lookup"><span data-stu-id="f7d06-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="f7d06-123">Těmto konkrétním konfliktům časování se dá snadno vyhnout použitím metod třídy <xref:System.Threading.Interlocked>, jako například <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7d06-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7d06-124">Další metody pro synchronizaci dat mezi více vláken, najdete informace o [synchronizaci dat pro Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="f7d06-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="f7d06-125">Ke konfliktům časování může docházet také tehdy, pokud synchronizujete aktivity více vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="f7d06-126">Při každém zápisu řádku kódu je nutné zvážit, co může nastat, pokud by vlákno bylo před provedením daného řádku (nebo před provedením jakéhokoliv jednotlivého pokynu počítače, který řádek tvoří) přerušeno a jiné vlákno by jej nahradilo.</span><span class="sxs-lookup"><span data-stu-id="f7d06-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="f7d06-127">Počet procesorů</span><span class="sxs-lookup"><span data-stu-id="f7d06-127">Number of Processors</span></span>  
 <span data-ttu-id="f7d06-128">Většina počítačů dnes již obsahuje více procesorů (také nazývané jádra), dokonce i v malých zařízeních, jako jsou tablety a telefony.</span><span class="sxs-lookup"><span data-stu-id="f7d06-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="f7d06-129">Víte-li, že vyvíjíte software, který bude spouštěn také na jednoprocesorových počítačích, je zapotřebí si uvědomit, že multithreading řeší odlišné problémy pro jednoprocesorové a víceprocesorové počítače.</span><span class="sxs-lookup"><span data-stu-id="f7d06-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="f7d06-130">Počítače s více procesory</span><span class="sxs-lookup"><span data-stu-id="f7d06-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="f7d06-131">Multithreading poskytuje větší propustnost.</span><span class="sxs-lookup"><span data-stu-id="f7d06-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="f7d06-132">Deset procesorů může provést desetkrát více práce než jeden procesor, ale pouze pokud je práce rozdělena tak, aby všech deset procesorů mohlo pracovat současně. Vlákna poskytují snadný způsob rozdělení práce a využití tohoto vysokého výkonu.</span><span class="sxs-lookup"><span data-stu-id="f7d06-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="f7d06-133">Pokud používáte multithreading na počítači s více procesory:</span><span class="sxs-lookup"><span data-stu-id="f7d06-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="f7d06-134">Počet vláken, která mohou být prováděna současně, je omezen počtem procesorů.</span><span class="sxs-lookup"><span data-stu-id="f7d06-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="f7d06-135">Vlákno na pozadí se provádí pouze v případě, že počet vláken v popředí je menší než počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="f7d06-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="f7d06-136">Pokud voláte metodu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> na vlákno, pak dané vlákno může, ale nemusí, okamžitě spustit provádění, a to v závislosti na počtu procesorů a počtu vláken, která čekají na provedení.</span><span class="sxs-lookup"><span data-stu-id="f7d06-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="f7d06-137">Ke konfliktům časování nemusí dojít pouze v případě, že jsou vlákna neočekávaně přerušena, ale i v situaci, kdy jsou prováděna dvě vlákna na různých procesorech a soupeří o dosažení stejného bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="f7d06-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="f7d06-138">Počítače s jedním procesorem</span><span class="sxs-lookup"><span data-stu-id="f7d06-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="f7d06-139">Multithreading poskytuje větší rychlost odezvy na činnost uživatele a pro úkoly na pozadí využívá čas nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="f7d06-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="f7d06-140">Pokud používáte multithreading na počítači s jedním procesorem:</span><span class="sxs-lookup"><span data-stu-id="f7d06-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="f7d06-141">V jednom okamžiku se provádí pouze jedno vlákno.</span><span class="sxs-lookup"><span data-stu-id="f7d06-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="f7d06-142">Vlákno na pozadí se spustí pouze tehdy, pokud je nečinné hlavní uživatelské vlákno.</span><span class="sxs-lookup"><span data-stu-id="f7d06-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="f7d06-143">Vlákno na popředí, které se provádí nepřetržitě, ubírá vláknům na pozadí čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="f7d06-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="f7d06-144">Pokud voláte metodu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> na vlákno, pak se dané vlákno nespustí, dokud se provádí aktuální vlákno nebo dokud není přerušeno operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="f7d06-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="f7d06-145">Ke konfliktům časování obvykle dochází tehdy, pokud programátor nepředpokládal skutečnost, že vlákno může být přerušeno v nevhodnou chvíli, což někdy umožní jinému vláknu dosáhnout určitého bloku kódu jako první.</span><span class="sxs-lookup"><span data-stu-id="f7d06-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="f7d06-146">Statické členy a statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="f7d06-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="f7d06-147">Třída není inicializována až do té doby, dokud příslušný konstruktor třídy (konstruktor `static` v jazyce C#, konstruktor `Shared Sub New` v jazyce Visual Basic) nedokončí provádění.</span><span class="sxs-lookup"><span data-stu-id="f7d06-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="f7d06-148">Aby nedošlo ke spuštění kódu pro typ, který není inicializován, blokuje modul CLR všechna volání členů `static` dané třídy (`Shared` v jazyce Visual Basic) z jiných vláken až do dokončení konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="f7d06-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="f7d06-149">Pokud například konstruktor třídy začíná nové vlákno a procedura vlákna volá člen `static` dané třídy, je nové vlákno blokováno do doby, než je konstruktor třídy dokončen.</span><span class="sxs-lookup"><span data-stu-id="f7d06-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="f7d06-150">To platí pro jakýkoli typ, který může mít konstruktor `static`.</span><span class="sxs-lookup"><span data-stu-id="f7d06-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="f7d06-151">Obecná doporučení</span><span class="sxs-lookup"><span data-stu-id="f7d06-151">General Recommendations</span></span>  
 <span data-ttu-id="f7d06-152">Při používání více vláken zvažte následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="f7d06-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="f7d06-153">Pro ukončení ostatních vláken nepoužívejte vlákno <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7d06-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="f7d06-154">Volání metody **Abort** na jiné vlákno se podobají došlo k výjimce, že vlákno, aniž by věděly, co bod daném vláknu dosáhl v jeho zpracování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="f7d06-155">Pro synchronizaci činností více vláken nepoužívejte vlákna <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7d06-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="f7d06-156">Použijte vlákna <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="f7d06-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="f7d06-157">Řízení zpracovávání pracovních vláken neprovádějte z hlavního programu (například pomocí událostí).</span><span class="sxs-lookup"><span data-stu-id="f7d06-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="f7d06-158">Namísto toho je vhodné navrhnout program tak, aby pracovní vlákna byla zodpovědná za čekání, dokud není k dispozici činnost, kterou pak vykonají a oznámí ostatním částem programu, že byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="f7d06-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="f7d06-159">Pokud nejsou pracovní vlákna blokovací, zvažte používání vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="f7d06-160">Volání metody <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> je užitečné v situacích, kdy pracovní vlákna provádí blokování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="f7d06-161">Nepoužívejte typy jako objekty zámku.</span><span class="sxs-lookup"><span data-stu-id="f7d06-161">Don't use types as lock objects.</span></span> <span data-ttu-id="f7d06-162">To znamená, že byste neměli používat kódy, jako je `lock(typeof(X))` v jazyce C# nebo `SyncLock(GetType(X))` v jazyce Visual Basic, nebo používat kód <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> s objekty <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="f7d06-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="f7d06-163">Pro daný typ existuje pouze jedna instance <xref:System.Type?displayProperty=nameWithType> v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7d06-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="f7d06-164">V případě, že typ, pro který použijete zámek, je veřejný, může jej jiný kód uzamknout, což povede k zablokování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="f7d06-165">Další problémy najdete v tématu [spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="f7d06-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="f7d06-166">Při zamykání instancí, například `lock(this)` v jazyce C# nebo `SyncLock(Me)` v jazyce Visual Basic, buďte obezřetní.</span><span class="sxs-lookup"><span data-stu-id="f7d06-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="f7d06-167">Pokud jiný kód v aplikaci, který je vůči typu externí, převezme zámek objektu, může dojít k zablokování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="f7d06-168">Zajistěte, aby vlákno, které se zobrazilo v monitorovacím nástroji, jej opustilo vždy, i pokud dojde k výjimce během zobrazení vlákna v monitorovacím nástroji.</span><span class="sxs-lookup"><span data-stu-id="f7d06-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="f7d06-169">Jazyka C# [zámku](~/docs/csharp/language-reference/keywords/lock-statement.md) příkaz a Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) příkaz zadejte toto chování automaticky, nasazení **nakonec** bloku zajistit, aby <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> je volá se.</span><span class="sxs-lookup"><span data-stu-id="f7d06-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="f7d06-170">Pokud nelze zajistěte, aby **ukončení** bude volán, zvažte změnu návrhu používat **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="f7d06-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="f7d06-171">Objekt mutex je automaticky uvolněn, pokud se ukončí vlákno, které jej vlastní.</span><span class="sxs-lookup"><span data-stu-id="f7d06-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="f7d06-172">Pro úkoly, jež vyžadují různé prostředky, používejte více vláken a zamezte přiřazení většího počtu vláken jedinému prostředku.</span><span class="sxs-lookup"><span data-stu-id="f7d06-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="f7d06-173">Například všechny úkoly zahrnující vstup-výstup těží z toho, že mají vlastní vlákno, protože dané vlákno bude přerušováno během vstupně-výstupních operací, a tím umožní provedení jiných vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="f7d06-174">Uživatelský vstup je dalším prostředkem, který těží z vyhrazeného vlákna.</span><span class="sxs-lookup"><span data-stu-id="f7d06-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="f7d06-175">Úkol, který vyžaduje intenzivní výpočty, existuje na počítači s jedním procesorem spolu s uživatelským vstupem a s úkoly, jež se týkají vstupu-výstupu, ale úkoly s vícenásobnými intenzivními výpočty si vzájemně konkurují.</span><span class="sxs-lookup"><span data-stu-id="f7d06-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="f7d06-176">Pro jednoduché změny stavu je třeba zvážit použití metod třídy <xref:System.Threading.Interlocked> namísto používání příkazu `lock` (`SyncLock` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f7d06-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="f7d06-177">Příkaz `lock` je dobrý univerzální nástroj, avšak třída <xref:System.Threading.Interlocked> poskytuje lepší výkon aktualizací, které musí být atomické.</span><span class="sxs-lookup"><span data-stu-id="f7d06-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="f7d06-178">Pokud neexistují žádné kolize, provede interně jedinou předponu zámku.</span><span class="sxs-lookup"><span data-stu-id="f7d06-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="f7d06-179">V revizích kódu hledejte stejný kód, jaký je uveden v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="f7d06-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="f7d06-180">V prvním příkladu je zvýšena stavová proměnná:</span><span class="sxs-lookup"><span data-stu-id="f7d06-180">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="f7d06-181">Pokud použijete metodu <xref:System.Threading.Interlocked.Increment%2A> namísto příkazu `lock`, můžete zlepšit výkon, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="f7d06-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f7d06-182">V rozhraní .NET Framework verze 2.0 poskytuje metoda <xref:System.Threading.Interlocked.Add%2A> atomické aktualizace v přírůstcích větších než 1.</span><span class="sxs-lookup"><span data-stu-id="f7d06-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="f7d06-183">Ve druhém příkladu je proměnná referenčního typu aktualizována pouze tehdy, pokud má odkaz hodnotu null (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f7d06-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="f7d06-184">Výkon lze zvýšit pomocí metody <xref:System.Threading.Interlocked.CompareExchange%2A>, jak je zobrazeno dále:</span><span class="sxs-lookup"><span data-stu-id="f7d06-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f7d06-185">V rozhraní .NET Framework verze 2.0 má metoda <xref:System.Threading.Interlocked.CompareExchange%2A> obecné přetížení, které může být použito pro typově bezpečné nahrazení jakéhokoliv odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="f7d06-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="f7d06-186">Doporučení pro knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="f7d06-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="f7d06-187">Při navrhování knihoven tříd pro multithreading zvažte následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="f7d06-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="f7d06-188">Pokud je to možné, synchronizaci nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="f7d06-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="f7d06-189">To zejména platí pro velmi vytížený kód.</span><span class="sxs-lookup"><span data-stu-id="f7d06-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="f7d06-190">Algoritmus může být například upraven pro tolerování konfliktů časování spíše než pro jejich odstranění.</span><span class="sxs-lookup"><span data-stu-id="f7d06-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="f7d06-191">Zbytečná synchronizace snižuje výkon a vytvoří možnosti pro zablokování a konflikty časování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="f7d06-192">Zajistěte, aby data deklarovaná jako static (`Shared` v jazyce Visual Basic) byla ve výchozím nastavení bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="f7d06-193">Nenastavujte data instancí ve výchozím nastavení jako bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="f7d06-194">Přidávání zámků za účelem vytvoření kódu bezpečného pro přístup z více vláken snižuje výkon, zvyšuje kolize zámků a vytváří možnost zablokování.</span><span class="sxs-lookup"><span data-stu-id="f7d06-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="f7d06-195">V běžných modelech aplikací provádí uživatelský kód v každém okamžiku pouze jedno vlákno, což minimalizuje potřebu zabezpečení pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="f7d06-196">Z tohoto důvodu nejsou knihovny tříd rozhraní .NET Framework ve výchozím nastavení bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="f7d06-197">Nepoužívejte poskytování statických metod, které mění stav.</span><span class="sxs-lookup"><span data-stu-id="f7d06-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="f7d06-198">V případě běžných použití serverů je statický stav sdílen napříč požadavky, což znamená, že více vláken může současně spustit tento kód.</span><span class="sxs-lookup"><span data-stu-id="f7d06-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="f7d06-199">Tato skutečnost otevírá možnosti pro chyby spojené s používáním více vláken.</span><span class="sxs-lookup"><span data-stu-id="f7d06-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="f7d06-200">Zvažte používání návrhového vzoru, který zapouzdřuje data do instancí, jež nejsou sdíleny napříč požadavky.</span><span class="sxs-lookup"><span data-stu-id="f7d06-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="f7d06-201">Dále platí, že pokud jsou synchronizována statická data, volání mezi statickými metodami, které mění stav, může způsobit zablokování nebo redundantní synchronizaci, což nepříznivě ovlivňuje výkon.</span><span class="sxs-lookup"><span data-stu-id="f7d06-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d06-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7d06-202">See Also</span></span>  
 [<span data-ttu-id="f7d06-203">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="f7d06-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="f7d06-204">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="f7d06-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)