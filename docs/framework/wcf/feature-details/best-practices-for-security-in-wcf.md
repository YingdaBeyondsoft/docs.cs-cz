---
title: Doporučené postupy pro zabezpečení ve WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2c1588fa48631aec4e185fd8362a02505aa15e58
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753458"
---
# <a name="best-practices-for-security-in-wcf"></a>Doporučené postupy pro zabezpečení ve WCF
Následující části uvádějí osvědčené postupy, které je třeba zvážit při vytváření zabezpečených aplikací pomocí služby Windows Communication Foundation (WCF). Další informace o zabezpečení najdete v tématu [aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), a [aspekty zabezpečení s metadaty](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identifikoval služby, provádění ověřování systému Windows s SPN  
 Služby lze identifikovat pomocí hlavních názvů uživatelů (UPN) nebo hlavní názvy služby (SPN). Služby spuštěné pod účty počítače, jako je síťová služba mít SPN identity odpovídající počítači, na kterém se používáte. Služby spuštěné pod uživatelské účty mají identitu UPN odpovídající uživatel, který se spouští jako, i když `setspn` nástroje lze přiřadit název SPN pro uživatelský účet. Konfigurace služby tak, aby ho bylo možné identifikovat pomocí hlavního názvu služby a konfiguraci klientů připojení ke službě, aby používali tuto SPN provádět určité útokům obtížnější. Tyto pokyny platí pro vazby vyjednání protokolu Kerberos nebo rozhraní SSPI.  Klienti musí určovat název SPN stále v případě, kdy SSPI spadne zpět na protokol NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Ověření identity služby v jazyce WSDL  
 WS-SecurityPolicy umožňuje službám publikovat informace o své vlastní identity v metadatech. Pokud načteny prostřednictvím `svcutil` nebo jiné metody, jako <xref:System.ServiceModel.Description.WsdlImporter>, tyto informace identity převádějí na vlastnosti identity adresy koncových bodů služby WCF. Klienti, které není ověřte, zda identita tyto služby jsou správné a platné efektivně obejít ověřování služby. Škodlivý služby může zneužít těchto klientů k provedení předávání přihlašovacích údajů a další útoky "man uprostřed" tak, že změníte identitu uplatňovat v jeho WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Použití X509 certifikátů místo protokolu NTLM  
 WCF nabízí dva mechanismy pro ověřování peer-to-peer: X509 certifikáty (používané rovnocenného kanálu) a ověřování systému Windows, kde vyjednávání SSPI snížení úrovně z protokolu Kerberos k ověřování NTLM.  Ověřování pomocí certifikátů pomocí velikosti klíče 1 024 bitů nebo víc je upřednostňovaný NTLM z několika důvodů:  
  
-   dostupnost vzájemné ověřování  
  
-   použití silnější kryptografické algoritmy a  
  
-   je větší obtížné využitím předávaných X509 přihlašovací údaje.  
   
## <a name="always-revert-after-impersonation"></a>Vždy vrátit po zosobnění  
 Pokud používáte rozhraní API umožňujících zosobnění klienta, ujistěte se, zda je vrátit zpět na původní identitu. Například při použití <xref:System.Security.Principal.WindowsIdentity> a <xref:System.Security.Principal.WindowsImpersonationContext>, pomocí jazyka C# `using` příkaz nebo Visual Basic`Using` příkaz, jak je znázorněno v následujícím kódu. <xref:System.Security.Principal.WindowsImpersonationContext> Třída implementuje <xref:System.IDisposable> rozhraní a proto common language runtime (CLR) automaticky vrátí původní identitu po kód zůstane `using` bloku.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Zosobnit pouze v případě potřeby  
 Pomocí <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metodu <xref:System.Security.Principal.WindowsIdentity> třídy, je možné použít zosobnění v velmi řízené oboru. Tím se liší od použití <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute>, což umožňuje zosobnění pro obor celou operaci. Pokud je to možné, řízení rozsahu zosobnění pomocí přesnější <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metoda.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Získat Metadata z důvěryhodných zdrojů  
 Ujistěte se, kterým důvěřujete zdroj metadata a ujistěte se, že nikdo neoprávněně metadata. Metadata načíst pomocí protokolu HTTP je odesláno jako nezašifrovaný text a může být úmyslně poškozena. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti, použijte adresu URL zadanou tvůrcem služby ke stahování dat pomocí protokolu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikování metadat pomocí zabezpečení  
 Chcete-li zabránit manipulaci s metadaty publikované služby, zabezpečený koncový bod metadat exchange s přenos nebo zabezpečení na úrovni zpráv. Další informace najdete v tématu [publikování kocových bodů metadat](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) a [postupy: publikování metadat služby pomocí kód](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Ujistěte se pomocí místního vystavitele  
 Pokud adresu vystavitele a vazby jsou zadané pro danou vazbu, místního vystavitele se nepoužije pro koncové body, které tuto vazbu používají. Klienti, kteří měli vždycky používat místního vystavitele zkontrolujte nepoužívají takovou vazbu nebo jejich Upravit vazby tak, že adresa Vystavitel je null.  
  
## <a name="saml-token-size-quotas"></a>Kvóty velikost tokenu SAML  
 Když tokeny zabezpečení kontrolní výrazy Markup Language (SAML) se serializují ve zprávách, buď při vydávání podle zabezpečení tokenu služby (STS), nebo když klienti k dispozici je ke službám v rámci ověřování, kvóta maximální velikosti zprávy musí být dostatečně k tomuto tokenu SAML a dalšími částmi zprávy dostačující. V případech, normální výchozích kvót velikost zprávy je dostatečné. Však v případech, kdy je SAML token velké vzhledem k tomu, že obsahuje stovky deklarace identity, kvóty by měl být skutečnost zohlednit zvýšením serializovaný token. Další informace o kvótách najdete v tématu [důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Nastavit SecurityBindingElement.IncludeTimestamp na hodnotu True u vlastních vazeb  
 Když vytvoříte vlastní vazby, je nutné nastavit <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> k `true`. Jinak, pokud <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> je nastaven na `false`, a klient používá asymetrické na základě klíčů token například X509 certifikát, nesmí být podepsané zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
