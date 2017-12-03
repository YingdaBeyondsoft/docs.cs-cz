---
title: "Webové a soketu oprávnění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 102d7d92384d77b5fbb56cd8c3eb859ec64bcca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="74ac2-102">Webové a soketu oprávnění</span><span class="sxs-lookup"><span data-stu-id="74ac2-102">Web and Socket Permissions</span></span>
<span data-ttu-id="74ac2-103">Zabezpečení Internetu pro aplikace pomocí <xref:System.Net> obor názvů poskytuje <xref:System.Net.WebPermission> a <xref:System.Net.SocketPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="74ac2-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="74ac2-104">**Oprávnění WebPermission** třída ovládací prvky aplikace k data žádosti z identifikátoru URI nebo identifikátor URI sloužit k Internetu.</span><span class="sxs-lookup"><span data-stu-id="74ac2-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="74ac2-105">**SocketPermission** třídy ovládacích prvků aplikace je správné použití <xref:System.Net.Sockets.Socket> tak, aby přijímal data na místních portů nebo se obrátit na vzdálených zařízení pomocí přenosového protokolu na jinou adresu, na základě na hostiteli, číslo portu, a protokol pro přenos soketu.</span><span class="sxs-lookup"><span data-stu-id="74ac2-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="74ac2-106">Které oprávnění třídy použijete, závisí na typu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="74ac2-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="74ac2-107">Aplikace, které používají <xref:System.Net.WebRequest> a jeho následníky by měl používat **oprávnění WebPermission** třídy ke správě oprávnění.</span><span class="sxs-lookup"><span data-stu-id="74ac2-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="74ac2-108">Aplikace, které používají přístup na úrovni soketu měli používat **SocketPermission** třídy ke správě oprávnění.</span><span class="sxs-lookup"><span data-stu-id="74ac2-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="74ac2-109">**Oprávnění WebPermission** a **SocketPermission** definovat dvě oprávnění: přijměte a připojení.</span><span class="sxs-lookup"><span data-stu-id="74ac2-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="74ac2-110">Přijměte uděluje právo k zodpovězení příchozího spojení ze strany jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="74ac2-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="74ac2-111">Připojení aplikace uděluje práva k navázání připojení k jiné straně.</span><span class="sxs-lookup"><span data-stu-id="74ac2-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="74ac2-112">Pro **SocketPermission** instance, přijímat znamená, že aplikace může přijmout příchozí spojení na místní přenosu adresu; připojení znamená, že aplikace může připojit k adrese některé přenosu vzdálené (nebo místní).</span><span class="sxs-lookup"><span data-stu-id="74ac2-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="74ac2-113">Pro **oprávnění WebPermission** instance, přijímat znamená, že aplikace můžete exportovat identifikátor URI řízené **oprávnění WebPermission** World; připojení znamená, že aplikace může použít tento identifikátor URI (ať už jde Vzdálení nebo místní).</span><span class="sxs-lookup"><span data-stu-id="74ac2-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ac2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="74ac2-114">See Also</span></span>  
 [<span data-ttu-id="74ac2-115">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="74ac2-115">Security</span></span>](../../../docs/standard/security/index.md)  
 [<span data-ttu-id="74ac2-116">Zabezpečení v síťové programování</span><span class="sxs-lookup"><span data-stu-id="74ac2-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)