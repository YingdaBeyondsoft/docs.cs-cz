---
title: "Pomocí soket synchronního serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ce50fa5cf8664f93753312ee5f1db2b3058c3fd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="888d9-102">Pomocí soket synchronního serveru</span><span class="sxs-lookup"><span data-stu-id="888d9-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="888d9-103">Synchronní serveru sockets pozastavit provádění aplikace, dokud obdrží žádost o připojení soketu.</span><span class="sxs-lookup"><span data-stu-id="888d9-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="888d9-104">Sokety synchronní serveru nejsou vhodné pro aplikace, které hodně využívají sítě v jejich operaci, ale mohou být vhodný pro jednoduché síťových aplikací.</span><span class="sxs-lookup"><span data-stu-id="888d9-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="888d9-105">Po <xref:System.Net.Sockets.Socket> je nastaven tak, aby naslouchala na k koncový bod pomocí <xref:System.Net.Sockets.Socket.Bind%2A> a <xref:System.Net.Sockets.Socket.Listen%2A> metody, je připravena přijímat požadavky na příchozí připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="888d9-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="888d9-106">Aplikace je pozastaveno, dokud je přijal žádost o připojení při **přijmout** metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="888d9-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="888d9-107">Po přijetí požadavku na připojení **přijmout** vrátí novou **soketu** instance, který je přidružen připojujícího se klienta.</span><span class="sxs-lookup"><span data-stu-id="888d9-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="888d9-108">Následující příklad načte data z klienta, zobrazí v konzole a vrátí data zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="888d9-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="888d9-109">**Soketu** neurčuje libovolný protokol pro zasílání zpráv, takže řetězec "\<EOF >" označuje konec daty zprávy.</span><span class="sxs-lookup"><span data-stu-id="888d9-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="888d9-110">Předpokládá, že **soketu** s názvem `listener` byl inicializován a vázána na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="888d9-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="888d9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="888d9-111">See Also</span></span>  
 [<span data-ttu-id="888d9-112">Pomocí soketu asynchronní serveru</span><span class="sxs-lookup"><span data-stu-id="888d9-112">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="888d9-113">Příklad soketu synchronní serveru</span><span class="sxs-lookup"><span data-stu-id="888d9-113">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [<span data-ttu-id="888d9-114">Naslouchání s Sockets</span><span class="sxs-lookup"><span data-stu-id="888d9-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)