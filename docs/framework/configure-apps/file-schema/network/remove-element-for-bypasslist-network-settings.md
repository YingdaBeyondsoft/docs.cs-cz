---
title: '&lt;Odebrat&gt; Element pro bypasslist – (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5c7918048743d53d8523ec399d1a11c67152a2bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742946"
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a>&lt;Odebrat&gt; Element pro bypasslist – (nastavení sítě)
Odebere seznam obcházení proxy adresy IP nebo název DNS.  
  
 \<Konfigurace >  
\<system.net>  
\<defaultProxy – >  
\<bypasslist – >  
\<Odebrat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`address`|Regulární výraz popisující IP adresu nebo název DNS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[bypasslist –](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.|  
  
## <a name="remarks"></a>Poznámky  
 `remove` Element odebere regulární výrazy, které popisují IP adresy nebo názvy serverů DNS ze seznamu adres, které Nepoužívat proxy server. Adresy byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.  
  
 Hodnota `address` atribut by měl mít regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.  
  
 Další informace o regulárních výrazech najdete v tématu. [Regulární výrazy rozhraní .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny předchozí definice pro doménu společnosti adventure-works.com a pak přidá do seznamu jednorázové přihlášení k doméně contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
