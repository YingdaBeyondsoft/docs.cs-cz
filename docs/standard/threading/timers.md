---
title: Časovače
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 478484651bf839f842148f0b4164c9387db3b98a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584954"
---
# <a name="timers"></a>Časovače
Časovače jsou zjednodušené objekty, které umožňují delegátu, aby byl zavolán v určený čas. Vlákno ve fondu vláken provádí operaci čekání.  
  
 Používání třídy <xref:System.Threading.Timer?displayProperty=nameWithType> je jednoduché. Vytváření **časovače**, předejte <xref:System.Threading.TimerCallback> delegátovi, aby se metoda zpětného volání, objekt reprezentující stav, který se předá zpětné volání, vyvolat počáteční čas a čas představující dobu mezi volání zpětného volání. Chcete-li zrušit čekající časovač, zavolejte **Timer.Dispose** funkce.  
  
> [!NOTE]
>  Existují dvě další třídy časovače. Třída <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> je ovládací prvek, který pracuje s vizuálními návrháři, a používá se v kontextu uživatelského rozhraní. Vyvolává události na vlákně uživatelského rozhraní. Třída <xref:System.Timers.Timer?displayProperty=nameWithType> je odvozena z třídy <xref:System.ComponentModel.Component>, takže ji lze použít s vizuálními návrháři, a také vyvolává události, avšak na vlákně <xref:System.Threading.ThreadPool>. Třída <xref:System.Threading.Timer?displayProperty=nameWithType> vytváří zpětná volání na vlákno <xref:System.Threading.ThreadPool> a nepoužívá model událostí. Poskytuje také stav objektu metodě zpětného volání, což jiné časovače neumožňují. Je to velmi jednoduché.  
  
 Následující příklad kódu spustí časovač, která se spouští za sekundu (1000 milisekund) a rysky každou sekundu se stisknutím **Enter** klíč. Proměnná obsahující odkaz na časovač je pole na úrovni třídy. Díky tomu nebude časovač uvolněn z paměti, pokud je stále spuštěn. Další informace o agresivním uvolňování paměti naleznete v tématu <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Timer>  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
