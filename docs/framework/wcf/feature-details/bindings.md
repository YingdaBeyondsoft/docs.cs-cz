---
title: Vazby WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 373f7feb64d69373630c942750f264d559643a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489661"
---
# <a name="windows-communcation-foundation-bindings"></a>Vazby WCF
Windows Communication Foundation (WCF) odděluje postup zápisu softwaru pro aplikaci z jak komunikuje s jiným softwarem. Vazby slouží k určení přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou. WCF používá vazby k vygenerování základní síťové vyjádření koncového bodu, takže většina podrobnosti vazba musí schválit strany, které komunikují. Nejjednodušší způsob, jak dosáhnout je pro klientům služby používat stejnou vazbu, která koncový bod služby používá. Další informace o tom, jak to udělat najdete v tématu [pomocí vazby na klienty a konfiguraci služby Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Vazba se skládá z kolekce elementů vazby. Každý prvek popisuje určitý aspekt jak koncový bod komunikuje s klienty. Vazba musí obsahovat alespoň jeden element vazby přenosu, alespoň jeden kódování zpráv prvku vazby (což element vazby přenosu může zajistit ve výchozím nastavení) a libovolný počet dalších protokol prvky vazeb. Proces, který sestaví runtime mimo tento popis umožňuje každého prvku vazby přispívání kód pro tento modul runtime.  
  
 WCF poskytuje vazby, které obsahují běžné možnosti elementů vazby. Ty mohou být použity ve výchozím nastavení, nebo můžete upravit tyto výchozí hodnoty podle požadavků uživatelů. Tyto vazby poskytované systémem mít vlastnosti, které umožňují přímou kontrolu nad prvky vazby a jejich nastavení. Můžete také snadno pracovat souběžného s více verzemi vazby tím, že každou verzi vazby svůj vlastní název. Podrobnosti najdete v tématu [Configuring System-Provided vazby](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Pokud potřebujete kolekce elementů vazby není poskytovaný jednu z těchto vazeb poskytovaných systémem můžete vytvořit vlastní vazby, která se skládá z kolekce elementů požadované vazby. Tyto vlastních vazeb se dají snadno vytvářet a provádět nevyžadují novou třídu, ale není zadejte vlastnosti pro řízení prvky vazby nebo jejich nastavení. Můžete používat prvky vazby a změnit jejich nastavení prostřednictvím kolekce, která obsahuje je. Podrobnosti najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Konfigurace vazeb poskytovaných systémem](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Popisuje, jak používat a upravovat vazby, které WCF poskytuje pro podporu běžné scénáře.  
  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Popisuje, jak definovat Windows Communication Foundation (WCF) vazeb pro služby a klienti imperativní v kódu a deklarativně pomocí konfigurace.  
  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Popisuje, co <xref:System.ServiceModel.Channels.CustomBinding> je a pokud se používá.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)
