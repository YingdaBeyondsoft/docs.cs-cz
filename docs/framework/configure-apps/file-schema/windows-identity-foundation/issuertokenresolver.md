---
title: '&lt;issuerTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02e2beb285cb0c4d88f98c3155ab5a3ff5e31e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="762a5-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="762a5-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="762a5-103">Zaregistruje překladač vystavitele tokenu, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="762a5-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="762a5-104">Překladač vystavitele tokenu se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="762a5-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="762a5-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="762a5-105">\<system.identityModel></span></span>  
<span data-ttu-id="762a5-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="762a5-106">\<identityConfiguration></span></span>  
<span data-ttu-id="762a5-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="762a5-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="762a5-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="762a5-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="762a5-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="762a5-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="762a5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="762a5-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="762a5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="762a5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="762a5-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="762a5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="762a5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="762a5-113">Attributes</span></span>  
  
|<span data-ttu-id="762a5-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="762a5-114">Attribute</span></span>|<span data-ttu-id="762a5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="762a5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="762a5-116">– typ</span><span class="sxs-lookup"><span data-stu-id="762a5-116">type</span></span>|<span data-ttu-id="762a5-117">Určuje typ tokenu překladače vystavitele.</span><span class="sxs-lookup"><span data-stu-id="762a5-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="762a5-118">Musí být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy nebo typu, která je odvozena z <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="762a5-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="762a5-119">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="762a5-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="762a5-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="762a5-120">Child Elements</span></span>  
 <span data-ttu-id="762a5-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="762a5-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="762a5-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="762a5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="762a5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="762a5-123">Element</span></span>|<span data-ttu-id="762a5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="762a5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="762a5-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="762a5-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="762a5-126">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="762a5-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="762a5-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="762a5-127">Remarks</span></span>  
 <span data-ttu-id="762a5-128">Překladač vystavitele tokenu se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="762a5-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="762a5-129">Slouží k načtení kryptografických materiál, který se používá k ověření podpisu.</span><span class="sxs-lookup"><span data-stu-id="762a5-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="762a5-130">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="762a5-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="762a5-131">Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> nebo vlastního typu, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="762a5-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="762a5-132">Některé tokenu obslužné rutiny umožňují určit nastavení vystavitele tokenu překladače v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="762a5-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="762a5-133">Nastavení na jednotlivých tokenu obslužné rutiny potlačit platformám zadaným v kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="762a5-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="762a5-134">Určení `<issuerTokenResolver>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="762a5-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="762a5-135">Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="762a5-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="762a5-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="762a5-136">Example</span></span>  
 <span data-ttu-id="762a5-137">Následující kód XML zobrazí konfiguraci pro token překladač vystavitele, založený na vlastní třídu, která je odvozena z <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="762a5-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="762a5-138">Překladač tokenu udržuje slovník párů klíč cílové skupiny, který je inicializován ze element vlastní konfigurace (`<AddAudienceKeyPair>`) pro třídu definovaný.</span><span class="sxs-lookup"><span data-stu-id="762a5-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="762a5-139">Třída přepsání <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metoda ke zpracování tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="762a5-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="762a5-140">Přepsání je znázorněno v následujícím příkladu; metody, který volá však nejsou zobrazeny jako stručný výtah.</span><span class="sxs-lookup"><span data-stu-id="762a5-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="762a5-141">Úplný příklad najdete v tématu `CustomToken` ukázka.</span><span class="sxs-lookup"><span data-stu-id="762a5-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="762a5-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="762a5-142">Example</span></span>  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="762a5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="762a5-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>