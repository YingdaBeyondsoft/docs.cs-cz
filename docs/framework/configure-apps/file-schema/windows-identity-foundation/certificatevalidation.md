---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af4dc459da49b46d70276d3f4bcd5f94d2a91ffe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756056"
---
# <a name="ltcertificatevalidationgt"></a>&lt;certificateValidation&gt;
Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů. Tato nastavení jsou přepsat, pokud obslužná rutina specifická nakonfigurovaný s vlastním validátoru.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<certificateValidation >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnotu, která určuje režim ověřování pro certifikát X.509. Výchozí hodnota je "PeerOrChainTrust". Chcete-li zadat vlastní validátor, nastavte tento atribut na hodnotu "Vlastní" a zadejte validátor pomocí [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element. Volitelné.|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnotu, která určuje režim odvolaných certifikátů pro certifikát X.509. Výchozí hodnota je "Online". Volitelné.|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje úložišti certifikátů X.509. Výchozí hodnota je "LocalMachine". Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|Určuje vlastní typ pro ověření certifikátu. Tento typ se používá pouze v případě `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element je nastaven na hodnotu "Vlastní".|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identity úrovně služeb.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.|  
  
## <a name="remarks"></a>Poznámky  
 A `<certificateValidation>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu. Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě. Některé tokenu obslužné rutiny umožňují určit nastavení ověření certifikátu v konfiguraci. Nastavení na jednotlivých tokenu obslužné rutiny přepsat tyto zadané na úrovni služby i na kolekci obslužná rutina tokenu zabezpečení.  
  
## <a name="example"></a>Příklad  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
