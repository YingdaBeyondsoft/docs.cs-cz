---
title: SyncLock – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: cf2aad9ec2ba67200d175fbcddfcb49afeac6efc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604975"
---
# <a name="synclock-statement"></a>SyncLock – příkaz
Získá výhradní zámek pro příkaz blok před provedením bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Součásti  
 `lockobject`  
 Požadováno. Výraz, který se vyhodnotí jako odkaz na objekt.  
  
 `block`  
 Volitelné. Blok příkazů, které se mají spustit, když je získat zámek.  
  
 `End SyncLock`  
 Ukončí `SyncLock` bloku.  
  
## <a name="remarks"></a>Poznámky  
 `SyncLock` Příkaz zajistí, že více vláken nespouštějte příkaz bloku ve stejnou dobu. `SyncLock` každé vlákno zabrání zadávání bloku, dokud ho spustíte žádné jiné vlákno.  
  
 Nejběžnější použití `SyncLock` je ochrana dat před více než jedním vláknem aktualizované současně. Pokud příkazů, které manipulovat s daty, třeba přejít k dokončení bez přerušení, umístí je uvnitř `SyncLock` bloku.  
  
 Blok příkazu chráněn výhradní zámek se někdy nazývá *kritická sekce*.  
  
## <a name="rules"></a>Pravidla  
  
-   Vytvoření větve. Můžete nemůže provést větvení do `SyncLock` blokovat z mimo blok.  
  
-   Hodnota zámek objektu. Hodnota `lockobject` nemůže být `Nothing`. Než ho použijete, musíte vytvořit zámek objektu `SyncLock` příkaz.  
  
     Nelze změnit hodnotu `lockobject` při provádění `SyncLock` bloku. Tento mechanismus vyžaduje, že zůstanou nezměněny zámek objektu.  
  
-   Nelze použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor `SyncLock` bloku.  
  
## <a name="behavior"></a>Chování  
  
-   Mechanismus. Když se dosáhne vlákna `SyncLock` příkaz, vyhodnocuje `lockobject` výraz a pozastaví spuštění, dokud ho získá výhradní zámek na objekt vrácený výrazem. Když se dosáhne jiné vlákno `SyncLock` příkaz ji není získat zámek dokud provede první vlákno `End SyncLock` příkaz.  
  
-   Chráněná Data. Pokud `lockobject` je `Shared` proměnné, vlákno v žádné instanci třídy výhradní zámek brání v provádění `SyncLock` blokovat, když se spouští jiné vlákno. To chrání data, která je sdílena mezi všemi instancemi.  
  
     Pokud `lockobject` je proměnná instance (není `Shared`), zámek brání spuštěné v aktuální instanci ze provádění vlákna `SyncLock` bloku ve stejnou dobu jako jiné vlákno ve stejné instanci. To chrání data zachována jednotlivých instancí.  
  
-   Získání a verzi. A `SyncLock` bloku se chová stejně jako `Try...Finally` konstrukce, ve kterém `Try` bloku získá výhradní zámek na `lockobject` a `Finally` uvolněním bloku. Z toho důvodu `SyncLock` bloku zaručuje verze zámku, bez ohledu na to, jak byl ukončen blok. To platí i v případě neošetřené výjimce.  
  
-   Volá Framework. `SyncLock` Bloku operace čtení a uvolní výhradní zámek voláním `Enter` a `Exit` metody `Monitor` třídy v <xref:System.Threading> oboru názvů.  
  
## <a name="programming-practices"></a>Postupy programování  
 `lockobject` Výraz by měl být vždy vyhodnocen objekt, který patří výhradně na třídu. By měly deklarovat `Private` objektová proměnná k ochraně dat, které patří do aktuální instance nebo `Private Shared` objektová proměnná k ochraně dat, které jsou společné pro všechny instance.  
  
 Neměli byste používat `Me` data pro instanci objektu – klíčové slovo zajistit zámek. Pokud kód externí ke třídě obsahuje odkaz na instanci třídě, by mohl použít tento odkaz jako objekt zámku pro `SyncLock` bloku zcela liší od váš, ochrana dat na jiný. Tímto způsobem třídě a jiná třída může blokovat navzájem z provedením jejich nesouvisejícími `SyncLock` bloky. Vzhledem k tomu, že jakýkoli jiný kód v procesu pomocí stejné řetězce budou sdílet stejnou zámek může být problematické podobně uzamčení na řetězec.  
  
 Byste neměli používat `Me.GetType` metody můžete zajistit objekt zámku pro sdílená data. Důvodem je, že `GetType` vždy vrátí stejné `Type` objekt pro název dané třídy. Externí kód může volat `GetType` na vaší třídě a získat používáte stejný objekt zámku. To by způsobilo dvě třídy blokování jiných z jejich `SyncLock` bloky.  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv. Drží zprávy v matici a posledních použít element tohoto pole v proměnné. `addAnotherMessage` Postup zvýší posledním elementem a uloží novou zprávu. Tyto dvě operace jsou chráněny `SyncLock` a `End SyncLock` příkazy, protože po posledním elementem se zvýší, nové zprávy musí být uložen před posledním elementem můžete zvýšit znovu jiné vlákno.  
  
 Pokud `simpleMessageList` třída sdílet jeden seznam zpráv mezi všechny jeho instance, proměnné `messagesList` a `messagesLast` by být deklarována jako `Shared`. V tomto případě proměnnou `messagesLock` navíc by měl mít `Shared`, takže by jeden zámek objekt použitý objektem všechny instance.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Popis  
 Následující příklad používá vláken a `SyncLock`. Tak dlouho, dokud `SyncLock` příkaz, příkaz blok je důležitý oddíl a `balance` nikdy se změní na záporné číslo. Můžete Zakomentovat `SyncLock` a `End SyncLock` příkazy zobrazíte účinek vynechala `SyncLock` – klíčové slovo.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [Synchronizace vláken](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [Dělení na vlákna](../../programming-guide/concepts/threading/index.md)
