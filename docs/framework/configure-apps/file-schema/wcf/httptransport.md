---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 77400348e9adc31d8121fc75f46d75d757af270f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362870"
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
Určuje přenosového protokolu HTTP pro přenos protokolu SOAP zprávy pro vlastní vazby.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<httpTransport>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
    realm="String"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
        useDefaultWebProxy="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků. Výchozí hodnota je `false`.<br /><br /> Tento atribut můžete použít při používání ASMX webové služby, které používají soubory cookie. Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.|  
|AuthenticationScheme|Určuje protokol, používá k ověření klientských požadavků zpracovávaných naslouchací proces protokolu HTTP. Platné hodnoty patří:<br /><br /> -Digest: Určuje ověřování hodnotou hash.<br />-Vyjednávání: Vyjedná s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokolu Kerberos, použije se; jinak se používá protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování NTLM.<br />– Základní: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Tento atribut lze nastavit pouze jednou.|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy. Výchozí hodnota je `false`.<br /><br /> Místní adresa je ten, který je v místní síti LAN nebo intranet.<br /><br /> Windows Communication Foundation (WCF) vždy ignoruje proxy server, pokud začíná adresu služby http://localhost.<br /><br /> Pokud chcete klientům jít přes proxy server při posuzování ke službám ve stejném počítači, se musí používat název hostitele místo localhost.|  
|hostnameComparisonMode|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Platné hodnoty jsou,<br /><br /> -StrongWildcard: ("+") odpovídá všechny možné názvy hostitelů v rámci zadané schéma, port a relativní identifikátor URI.<br />-Přesnou: žádné zástupné znaky<br />-WeakWildcard: ("*") shoduje s názvem všechny možné hostitele zadané schéma, port a relativní UIR, která nejsou explicitně shoduje nebo přes mechanismus silné zástupný znak v kontextu.<br /><br /> Výchozí hodnota je StrongWildcard. Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`.|  
|KeepAliveEnabled|Logická hodnota, která určuje, jestli má být trvalé připojení k internetového zdroji.|  
|maxBufferSize|Kladné celé číslo, které určuje maximální velikost vyrovnávací paměti. Výchozí hodnota je 524288|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|ProxyAuthenticationScheme|Určuje protokol použitý pro ověřování proxy serveru HTTP zpracovává požadavky klienta. Platné hodnoty patří:<br /><br /> -None: Neprobíhá žádné ověřování.<br />-Digest: Určuje ověřování hodnotou hash.<br />-Vyjednávání: Vyjedná s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokolu Kerberos, použije se; jinak se používá protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování NTLM.<br />– Základní: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br />-IntegratedWindowsAuthentication: Určuje ověřování systému Windows.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>.|  
|sféry|Řetězec, který určuje sféry, použijte na proxy serveru. Výchozí hodnota je prázdný řetězec.<br /><br /> Servery používají sfér k oddílu chráněným prostředkům. Každý oddíl může mít svou vlastní databázi schéma nebo autorizace ověřování. Sfér se používají pouze pro základní a ověřování algoritmem digest. Jakmile klient úspěšně ověří, je platný pro všechny prostředky v dané sféry ověřování. Podrobný popis sfér, najdete v dokumentu RFC 2617 na http://www.ietf.org.|  
|transferMode|Určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi. Platné hodnoty patří:<br /><br /> -Uložená do vyrovnávací paměti: Zprávy požadavku a odpovědi jsou uložená do vyrovnávací paměti.<br />-Streamování: Streamovaných zprávy požadavku a odpovědi.<br />-StreamedRequest: Zprávu požadavku je streamování a zprávu odpovědi do vyrovnávací paměti.<br />-StreamedResponse: Zprávu požadavku do vyrovnávací paměti a je streamování zprávu odpovědi.<br /><br /> Výchozí hodnota je uložená do vyrovnávací paměti. Tento atribut je typu <xref:System.ServiceModel.TransferMode> .|  
|UnsafeConnectionNtlmAuthentication|Logická hodnota, která určuje, zda je na serveru povoleno Unsafe sdílení připojení. Výchozí hodnota je `false`. Pokud je povoleno, ověřování protokolem NTLM se provádí jednou v každé připojení TCP.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli jsou nastavení proxy serveru celého systému použít místo nastavení specifická pro uživatele. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `httpTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol HTTP. HTTP je primární přenosu použitý pro zajištění spolupráce. Tento přenos je podporována pomocí Windows Communication Foundation (WCF) a zajišťuje interakci s Další zásobníky služby WCF Web.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
