---
title: "Pomocí zabezpečené sokety vrstvy"
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
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b4cdc21b9ecfdb1bb37f26f82200b211967043c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="54834-102">Pomocí zabezpečené sokety vrstvy</span><span class="sxs-lookup"><span data-stu-id="54834-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="54834-103"><xref:System.Net> Třídy použít Secure Sockets Layer (SSL) k šifrování připojení několik síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="54834-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="54834-104">Pro připojení protokolu http <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používat protokol SSL pro komunikaci s weboví hostitelé, které podporují protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="54834-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="54834-105">Rozhodnutí ohledně používání protokolu SSL je provedené <xref:System.Net.WebRequest> třídy, na základě v identifikátoru URI je zadána.</span><span class="sxs-lookup"><span data-stu-id="54834-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="54834-106">Pokud identifikátor URI začíná řetězcem "https:", se používá protokol SSL; Pokud identifikátor URI začíná řetězcem "http:", je použít nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="54834-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="54834-107">Chcete-li používat protokol SSL pomocí protokolu FTP (File Transfer), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> vlastnost na hodnotu true před voláním <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="54834-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="54834-108">Podobně, chcete-li používat protokol SSL s transportní protokol SMTP (Simple Mail), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> vlastnost na hodnotu true před odesláním e-mailu.</span><span class="sxs-lookup"><span data-stu-id="54834-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the e-mail.</span></span>  
  
 <span data-ttu-id="54834-109"><xref:System.Net.Security.SslStream> Třída poskytuje abstrakci se na základě datového proudu pro protokol SSL a nabízí mnoho způsobů, jak nakonfigurovat metody handshake SSL.</span><span class="sxs-lookup"><span data-stu-id="54834-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54834-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="54834-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="54834-111">Kód</span><span class="sxs-lookup"><span data-stu-id="54834-111">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54834-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="54834-112">Compiling the Code</span></span>  
 <span data-ttu-id="54834-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="54834-113">This example requires:</span></span>  
  
-   <span data-ttu-id="54834-114">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="54834-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54834-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="54834-115">See Also</span></span>  
 [<span data-ttu-id="54834-116">Zabezpečení v síťové programování</span><span class="sxs-lookup"><span data-stu-id="54834-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [<span data-ttu-id="54834-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54834-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="54834-118">Výběr certifikátu a ověření</span><span class="sxs-lookup"><span data-stu-id="54834-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)