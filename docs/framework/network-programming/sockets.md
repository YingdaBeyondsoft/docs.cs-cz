---
title: Sokety
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b234846e63eab59602069aa72125df116e30375d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398284"
---
# <a name="sockets"></a>Sokety
<xref:System.Net.Sockets> Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets. Všechny ostatní-přístup k síti třídy v <xref:System.Net> obor názvů jsou postavená na tuto implementaci soketů.  
  
 Rozhraní .NET Framework <xref:System.Net.Sockets.Socket> třída je verzi služby soketu poskytovaný rozhraním Winsock32 API spravovaného kódu. Ve většině případů **soketu** metody třídy jednoduše zařazování dat do jejich nativní protějšky Win32 a zpracovat všechny kontroly potřeby zabezpečení.  
  
 **Soketu** třída podporuje dva základní režimy synchronní a asynchronní. V synchronním režimu, zavolá na funkce, které provádějí síťových operací (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A>) počkejte na dokončení operace před vrácením volací program ovládacího prvku. Tyto volání v asynchronním režimu, vrátí okamžitě.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření soketu](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
