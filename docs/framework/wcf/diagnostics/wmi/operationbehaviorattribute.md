---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd01c5c4d37f5c0ec5673dc9aa4a47cb8affbc29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída OperationBehaviorAttribute nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída OperationBehaviorAttribute má následující vlastnosti:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Stav funkce automatického uvolnění pro parametry.  
  
### <a name="impersonation"></a>Zosobnění  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Informuje o úrovni zosobnění volající, který podporuje operaci.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode u atributu  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, kdy v průběhu k vyvolání operace recyklace objektu.  
  
### <a name="transactionautocomplete"></a>Vlastnost TransactionAutoComplete  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, zda automaticky potvrzení aktuální transakce, pokud dojde k žádné neošetřených výjimek.  
  
### <a name="transactionscoperequired"></a>Vlastností TransactionScopeRequired  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda operace vyžaduje transakci.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationBehaviorAttribute>