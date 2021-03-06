---
title: '&lt;Přidat&gt; Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743820"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;Přidat&gt; Element pro &lt;namedCaches&gt;
Přidá `namedCache` položku s `namedCaches` kolekci pro mezipaměť.  
  
 \<system.runtime.caching>  
\<memoryCache >  
\<namedCaches >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolená velikost (v megabajtech), instanci <xref:System.Runtime.Caching.MemoryCache> můžete dosáhnout. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky Automatická změna velikosti třídy se používají ve výchozím nastavení.|  
|`Name`|Název mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalovaném počítači, která mohou být spotřebovávána mezipaměti. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky Automatická změna velikosti třídy se používají ve výchozím nastavení.|  
|`PollingInterval`|Hodnota, která určuje časový interval, po jejímž uplynutí implementace mezipaměti porovná aktuální zatížení paměti do paměti absolutní a na základě procenta omezení, které jsou nastavené pro instanci mezipaměti. Tato hodnota je uvedeno ve formátu hh: mm".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 `None`  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.|  
  
## <a name="remarks"></a>Poznámky  
 `add` Element přidá položku do `namedCaches` kolekci pro mezipaměť. Můžete použít [vymazat](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element před použitím `add` elementu, který chcete být jisti, že neexistují žádné další s názvem mezipaměti v kolekci. Tento element lze použít v souboru machine.config a v souboru Web.config.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku na `namedCaches` kolekci pro mezipaměť.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<namedCaches > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
