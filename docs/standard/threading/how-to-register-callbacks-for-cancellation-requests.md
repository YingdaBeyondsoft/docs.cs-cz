---
title: 'Postupy: Registrace zpětných volání pro požadavky zrušení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8df4c73af81580d1b242ce0ede8f8bcb4cad4fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583289"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Postupy: Registrace zpětných volání pro požadavky zrušení
Následující příklad ukazuje, jak zaregistrovat delegáta, který bude vyvolán při <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost bude PRAVDA z důvodu volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> na objektu, který vytvořen token. Tento postup použijte pro zrušení asynchronních operací, které nativně nepodporují rozhraní jednotná zrušení a odblokování metody, které může být čekání na dokončení asynchronní operace.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech. Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> metoda je registrován jako metoda má být volána, pokud se požaduje zrušení prostřednictvím token zrušení.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Pokud po registraci zpětného volání již požadavek zrušení, zpětné volání stále záruku, že má být volána. V tomto konkrétním případě <xref:System.Net.WebClient.CancelAsync%2A> metoda se nic nestane. Pokud žádná asynchronní operace probíhá, takže je bezpečně volat metodu.  
  
## <a name="see-also"></a>Viz také  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
