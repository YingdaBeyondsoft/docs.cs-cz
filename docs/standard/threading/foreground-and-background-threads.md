---
title: Vlákna v popředí a v pozadí
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 476dc75a569224db405eb7498ecb35eb6bda24d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí
Spravované vlákno je vlákna na pozadí nebo vlákna popředí. Vlákna na pozadí jsou stejné jako vlákna na popředí s jednou výjimkou: vlákna na pozadí nezachovat spravovaného spouštění prostředí spuštěna. Jakmile v spravovaného procesu (kde soubor .exe je spravované sestavení) byly zastaveny všechny vlákna na popředí, systém zastaví všechny vlákna na pozadí a ukončí.  
  
> [!NOTE]
>  Když se modul runtime zastaví vlákna na pozadí, protože proces se vypíná, nedojde k výjimce v vlákno. Ale když vláken byla zastavena, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolní doménu aplikace, <xref:System.Threading.ThreadAbortException> je vyvolána v popředí ani pozadí vláken.  
  
 Použití <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti k určení, zda je vlákna na pozadí nebo vlákna popředí nebo změnit jeho stav. Vlákno můžete změnit tak, aby vlákna na pozadí kdykoli znovu nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true`.  
  
> [!IMPORTANT]
>  Stav popředí nebo pozadí vlákno nemá vliv na výsledek k neošetřené výjimce v vlákno. V rozhraní .NET Framework verze 2.0 k neošetřené výjimce v popředí nebo pozadí vláken výsledkem ukončení aplikace. V tématu [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Vláken, které patří do spravovaný fond vláken (to znamená, jehož vláken <xref:System.Threading.Thread.IsThreadPoolThread%2A> vlastnost je `true`) jsou vlákna na pozadí. Všechna vlákna, zadejte spravovaného prostředí pro spouštění z nespravovaného kódu jsou označeny jako vlákna na pozadí. Všechna vlákna vygenerovaných vytvoření a spuštění nové <xref:System.Threading.Thread> objektu se ve výchozím nastavení vlákna na popředí.  
  
 Používáte-li vlákna monitorování aktivity, jako je připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true` tak, aby vlákno nezabrání váš proces se ukončuje.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
