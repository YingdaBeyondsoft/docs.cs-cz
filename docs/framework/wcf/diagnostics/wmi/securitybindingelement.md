---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ceb674ea7c20386acb821d3a41c1ad0c743a7607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487552"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída elementu SecurityBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída elementu SecurityBindingElement má následující vlastnosti:  
  
### <a name="defaultalgorithmsuite"></a>defaultAlgorithmSuite  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje algoritmy pro použití s vazby.  
  
### <a name="includetimestamp"></a>includeTimestamp  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda každá zpráva obsahuje časové razítko.  
  
### <a name="keyentropymode"></a>keyEntropyMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Zdroj šifry použitý k vytvoření klíče.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Datový typ: LocalServiceSecuritySettings  
  
 Přístup k typu: jen pro čtení  
  
 Vlastnosti konkrétní bezpečnostní vazby pro místní služby.  
  
### <a name="messagesecurityversion"></a>messageSecurityVersion  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Je verze použitá pro zabezpečení zpráv.  
  
### <a name="securityheaderlayout"></a>securityHeaderLayout  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
