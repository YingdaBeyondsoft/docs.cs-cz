---
title: Přehled modelu webového programování HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 2c3498857c7c0e69c3678ba03f94c14f9b6d8e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507110"
---
# <a name="wcf-web-http-programming-model-overview"></a>Přehled modelu webového programování HTTP služby WCF
Programovací model Windows Communication Foundation (WCF) WEB HTTP poskytuje základní prvky potřebné k vytvoření webové služby HTTP s použitím technologie WCF. Služby WCF WEB HTTP jsou navržené tak, ke kterým přistupují širokou škálu možných klientů, včetně webových prohlížečů a mají následující jedinečné požadavky:  
  
-   **Identifikátory URI a zpracování URI** identifikátory URI hrají ústřední roli v návrhu webové služby HTTP. WCF WEB HTTP, používá model programování <xref:System.UriTemplate> a <xref:System.UriTemplateTable> třídy nabízí možnosti zpracování identifikátor URI.  
  
-   **Podpora pro operace GET a POST** webové služby HTTP Ujistěte se, použijte příkaz GET pro načtení dat, kromě různé vyvolání příkazy pro úpravu dat a vzdálené volání. WCF WEB HTTP, používá model programování <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> přidružit operací služby GET a další příkazy HTTP jako PUT, POST a odstraňovat.  
  
-   **Více formátů data** stylu Web services zpracovat mnoho typů dat kromě protokolu SOAP zprávy. WCF WEB HTTP, používá model programování <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> pro podporu mnoha různých datových formátů včetně dokumentů XML, JSON datový objekt a proudy binární obsah, jako jsou bitové kopie, video soubory nebo prostý text.  
  
 Programovací model WCF WEB HTTP rozšiřuje rozsah WCF tak, aby pokrýval scénáře webové stylu, které zahrnují HTTP webové služby, služby AJAX a JSON a informační kanály syndikace (ATOM/RSS). Další informace o službách AJAX a JSON najdete v tématu [integrace jazyka AJAX a podpora formátu JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Další informace o syndikace najdete v tématu [syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Neexistují žádná další omezení na typy dat, která lze vrátit ze HTTP webové služby. Jakýkoli serializovatelný typ mohou být vráceny z operace HTTP webové služby. Webový prohlížeč, který je omezení toho, jaká data typy lze zadat v adrese URL vyvolejte, protože mohou být operace HTTP webové služby. Další informace o jaké typy jsou podporovány ve výchozím nastavení najdete v článku **UriTemplate parametrů řetězce dotazu a adresy URL** části níže. Výchozí chování lze změnit tím, že poskytuje vlastní T:System.ServiceModel.Dispatcher.QueryStringConverter implementace, která určuje, jak převést parametry zadané v adrese URL skutečný parametr typu. Další informace najdete v tématu <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Služby, které jsou napsané pomocí programovacího modelu WCF WEB HTTP nepoužívejte protokolu SOAP zprávy. Protože protokolu SOAP se nepoužívá, nelze použít funkce zabezpečení poskytované službou WCF. Můžete ale použít zabezpečení na základě přenosu hostováním služby prostřednictvím protokolu HTTPS. Další informace o zabezpečení WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Instalace rozšíření WebDAV pro službu IIS může způsobit vrátí chybu HTTP 405 jako protokol WebDAV rozšíření pokusí zpracovat všechny požadavky PUT HTTP webové služby. Chcete-li vyřešit tento problém můžete odinstalovat rozšíření WebDAV nebo zakázat rozšíření WebDAV pro svůj web. Další informace najdete v tématu [služby IIS a protokolu WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Identifikátor URI zpracování s UriTemplate a UriTemplateTable  
 Identifikátor URI šablony poskytují efektivní syntaxe pro vyjádření velkých sad strukturálně podobné identifikátory URI. Například následující šablony vyjadřoval sadu všechny tři segment URI, které začínají řetězcem "a" a "c" bez ohledu na hodnotu zprostředkující segmentu na konci: / {segmentovat} /c  
  
 Tato šablona popisuje identifikátory URI jako následující:  
  
-   a/x/c  
  
-   / y/c  
  
-   a/z/c  
  
-   a tak dále.  
  
 V této šabloně zápis složené závorky ("{segment}") označuje segment proměnné místo je Literálová hodnota.  
  
 Rozhraní .NET framework poskytuje rozhraní API pro práci se šablonami URI volá <xref:System.UriTemplate>. `UriTemplates` povolit, můžete provést následující akce:  
  
-   Můžete volání jednoho z `Bind` metody s sadu parametrů k vytvoření *plně uzavřený URI* odpovídající šablonu. To znamená, že všechny proměnné v rámci šablony URI jsou nahrazeny skutečnými hodnotami.  
  
-   Můžete volat `Match`() s kandidátem identifikátor URI, který používá šablonu k rozdělit kandidátem URI do jeho prvku části a vrátí slovník, který obsahuje různé části identifikátor URI s názvem bez přípony podle proměnné v šabloně.  
  
-   `Bind`() a `Match`() jsou inverses, takže můžete volat `Match`( `Bind`(x)) a vraťte se stejné prostředí, které jste začali s.  
  
 Existují mnohokrát (hlavně na serveru, kde odeslání požadavek na operaci služby podle identifikátoru URI je nutné) Chcete-li ke sledování sadu <xref:System.UriTemplate> objekty v datová struktura, která můžete nezávisle se vztahují na všechny uzavřeného šablony. <xref:System.UriTemplateTable> představuje sadu šablony URI a vybere nejlepší shodu určitou sadu šablon a kandidátem identifikátor URI. Abyste mohli používat, kdykoli je to nutné, to není přidružený žádné konkrétní sadu síťových protokolů (součást WCF).  
  
 Model služby WCF využívá <xref:System.UriTemplate> a <xref:System.UriTemplateTable> přidružit sadu identifikátory URI popsaného operací služby <xref:System.UriTemplate>. Operace služby je přidružen <xref:System.UriTemplate>, buď pomocí <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute>. Další informace o <xref:System.UriTemplate> a <xref:System.UriTemplateTable>, najdete v části [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet a WebInvoke atributy  
 Ujistěte se, služby WCF WEB HTTP použití příkazů načtení (třeba HTTP GET) kromě různé vyvolání operace (například HTTP POST, PUT a DELETE). Programovací model WCF WEB HTTP umožňuje vývojářům služby ovládacího prvku na obou šablonu identifikátoru URI a akci spojenou s jejich operací služby pomocí <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> povolit vám umožňují řídit, jak jednotlivé operace váže k identifikátory URI a metody HTTP přidružený tyto identifikátory URI. Například přidání <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> v následujícím kódu.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 Předchozí kód můžete provádět následující požadavky HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Výchozí hodnota je POST, ale můžete ji použít pro jiné příkazy příliš.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Služby WCF, která používá programovací model WCF WEB HTTP ucelenou ukázku najdete v sekci [postupy: vytvoření základní služby WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parametrů řetězce dotazu UriTemplate a adresy URL  
 Styl webové služby lze volat z webového prohlížeče zadáním adresy URL, která souvisí s operaci služby. Tyto operace služby může trvat parametrů řetězce dotazu, které je třeba zadat ve formátu řetězce v rámci adresy URL. Následující tabulka uvádí typy, které lze předat v rámci adresy URL a formát použitý.  
  
|Typ|Formát|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (exponentu zápis se nevyžaduje)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (exponentu zápis se nevyžaduje)|  
|<xref:System.Char>|Libovolný znak|  
|<xref:System.Decimal>|Všechny decimal ve standardním zápisu (žádné exponent)|  
|<xref:System.Boolean>|PRAVDA nebo NEPRAVDA (případ malých a velkých písmen)|  
|<xref:System.String>|Libovolný řetězec (hodnotu null. řetězec se nepodporuje a žádné uvozovací znaky se provádí)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/RRRR HH: MM: [AM&AMP;#124;PM]<br /><br /> Měsíc dne roku.<br /><br /> Den měsíce roku hh: mm: [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Kde DD = dny, HH = hodiny, MM minuty, SS = = sekund|  
|<xref:System.Guid>|Identifikátor GUID, například:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/RRRR HH: MM: MM: SS<br /><br /> Kde DD = dny, HH = hodiny, MM minuty, SS = = sekund|  
|Výčty|Hodnota výčtu například určující výčtu, jak je znázorněno v následujícím kódu.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Některá z hodnot výčtu jednotlivých (nebo jejich příslušné hodnoty celé číslo) může být určen v řetězci dotazu.|  
|Typy, které mají `TypeConverterAttribute` typ, můžete převést do a z řetězcová reprezentace.|Závisí na převaděč typů.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formáty a programovací Model WCF WEB HTTP  
 Programovací model WCF WEB HTTP obsahuje nové funkce pro práci s mnoha různých datových formátů. Ve vrstvě vazbu <xref:System.ServiceModel.WebHttpBinding> lze číst a zapisovat následující různé druhy dat:  
  
-   XML  
  
-   FORMÁT JSON  
  
-   Neprůhledné binární datové proudy  
  
 To znamená programovací model WCF WEB HTTP dokáže zpracovat libovolný typ dat, ale můžete být programové ošetření <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] poskytuje podporu pro data JSON (AJAX) a také informační kanály syndikace (včetně ATOM a RSS). Další informace o těchto funkcích najdete v tématu [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) a [integrace jazyka AJAX a podpora formátu JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Programovací Model WCF WEB HTTP a zabezpečení  
 Protože programovací model WCF WEB HTTP nepodporuje WS-* protokoly, jediný způsob, jak zabezpečit webové služby WCF HTTP je službu vystavit přes HTTPS pomocí protokolu SSL. Další informace o nastavení protokolu SSL s [!INCLUDE[iisver](../../../../includes/iisver-md.md)], najdete v části [implementaci protokolu SSL ve službě IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Řešení potíží s WCF WEB HTTP, programovací Model  
 Při volání metody WCF WEB HTTP services pomocí <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> k vytvoření kanálu, <xref:System.ServiceModel.Description.WebHttpBehavior> používá <xref:System.ServiceModel.EndpointAddress> nastavit i když soubor konfigurace jiné <xref:System.ServiceModel.EndpointAddress> je předán <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Viz také  
 [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
