---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 652cb551fb318d43d4284dbee48aeb994f056692
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746794"
---
# <a name="ltnamedpipetransportgt"></a>&lt;namedPipeTransport&gt;
Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenované kanály, když je zahrnutý do vlastní vazby.  
  
\<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<namePipeTransport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<namedPipeTransport channelInitializationTimeout="TimeSpan"   
                    connectionBufferSize="Integer"   
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
                    manualAddressing="Boolean"   
                    maxBufferPoolSize="Integer"  
                    maxBufferSize="Integer"  
                    maxOutputDelay="TimeSpan"  
                    maxPendingAccepts="Integer"   
                    maxPendingConnections="Integer"  
                    maxReceivedMessageSize="Integer"   
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">  
  <connectionPoolSettings groupName="String" 
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|ChannelInitializationTimeout|Získá nebo nastaví <xref:System.TimeSpan> který určuje maximální dobu, po kanál, který může být ve stavu inicializace uplynutí dojde k odpojení.|  
|ConnectionBufferSize|Získá nebo nastaví velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.|  
|hostNameComparisonMode|Získá nebo nastaví hodnotu, která určuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.|  
|manualAddressing|Získá nebo nastaví hodnotu, která určuje, zda je vyžadováno ruční adresování zprávy.|  
|maxBufferPoolSize|Získá nebo nastaví maximální velikost v bajtech všechny fondy vyrovnávací paměti používané přenosu.|  
|maxBufferSize|Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití. Pro proudu zpráv tato hodnota by měla být alespoň maximální možná velikost záhlaví zprávy, které jsou přečíst v režim s vyrovnávací pamětí.|  
|maxOutputDelay|Získá nebo nastaví maximální dobu, po kterou bloku zprávu nebo zprávu úplné může zůstat ve vyrovnávací paměti v paměti před odesláním interval.|  
|maxPendingAccepts|Získá nebo nastaví maximální počet kanálů služby může mít čekání na naslouchací proces pro zpracování příchozí připojení ke službě.|  
|maxPendingConnections|Získá nebo nastaví maximální počet připojení, které čekají na odeslání ve službě.|  
|MaxReceivedMessageSize|Získá nebo nastaví maximální povolenou velikost zprávy, v bajtech, které můžou přijímat.|  
|transferMode|Získá nebo nastaví hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.|  
|[\<connectionPoolSettings > z \<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
Tento přenos používá identifikátory URI ve tvaru "net.pipe://hostname/path". Ostatní součásti URI jsou volitelné.  
  
`namedPipeTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol pojmenovaných kanálů. Tento přenos slouží serveru na počítači Windows Communication Foundation (WCF), - na - WCF komunikace.  
  
## <a name="see-also"></a>Viz také  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
[Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)   
[Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
[Vazby](../../../../../docs/framework/wcf/bindings.md)   
[Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
[Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
[\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
