---
title: 'Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f83e260e41acd7c8fff03cf7df0832bab229911
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568495"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection
Tento příklad ukazuje, jak k přidání a odebrání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> blokování a neblokující způsobem. Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601>, najdete v části [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Příklad toho, jak vytvořit výčet <xref:System.Collections.Concurrent.BlockingCollection%601> dokud je prázdný, a budou přidány žádné další prvky, najdete v části [postupy: použití příkazu ForEach k odebrání položek v kolekci BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Příklad  
 Tento první příklad ukazuje, jak přidat a převzít položky tak, aby operace zablokuje, pokud kolekce je buď dočasně prázdný (když se vezme) nebo na maximální kapacity (při přidávání), nebo pokud dojde k uplynutí zadaného časového limitu. Všimněte si, že blokování na maximální kapacitě je povoleno pouze pokud BlockingCollection byl vytvořen s maximální kapacita určená v konstruktoru.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Příklad  
 Tento druhý příklad ukazuje, jak přidat a převzít položky tak, aby operace se nebude blokovat. Pokud je k dispozici žádné položky, bylo dosaženo maximální kapacity u ohraničené kolekce nebo uplynutí časového limitu, pak se <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace vrací hodnotu false. To umožňuje vláknu provádět některé další užitečné činnosti na chvíli a opakujte akci později buď načíst nové položky, nebo zkuste přidat stejnou položku, kterou nebylo možné přidat dříve. Program také ukazuje, jak implementovat zrušení při přístupu k <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
