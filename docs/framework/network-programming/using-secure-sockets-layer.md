---
title: Pomocí zabezpečené sokety vrstvy
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2baedaa445f81e3e204f7414c5142232755581ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396243"
---
# <a name="using-secure-sockets-layer"></a>Pomocí zabezpečené sokety vrstvy
<xref:System.Net> Třídy použít Secure Sockets Layer (SSL) k šifrování připojení několik síťových protokolů.  
  
 Pro připojení protokolu http <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používat protokol SSL pro komunikaci s weboví hostitelé, které podporují protokol SSL. Rozhodnutí ohledně používání protokolu SSL je provedené <xref:System.Net.WebRequest> třídy, na základě v identifikátoru URI je zadána. Pokud identifikátor URI začíná řetězcem "https:", se používá protokol SSL; Pokud identifikátor URI začíná řetězcem "http:", je použít nešifrované připojení.  
  
 Chcete-li používat protokol SSL pomocí protokolu FTP (File Transfer), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> vlastnost na hodnotu true před voláním <xref:System.Net.FtpWebRequest.GetResponse>. Podobně, chcete-li používat protokol SSL s transportní protokol SMTP (Simple Mail), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> vlastnost na hodnotu true před odesláním e-mailu.  
  
 <xref:System.Net.Security.SslStream> Třída poskytuje abstrakci se na základě datového proudu pro protokol SSL a nabízí mnoho způsobů, jak nakonfigurovat metody handshake SSL.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazuje na **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Výběr a ověření certifikátu](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
