---
title: "Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91b611af6c8de5c2bc0119838eb12950d3207177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="65898-102">Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF</span><span class="sxs-lookup"><span data-stu-id="65898-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="65898-103">Toto téma popisuje postupy k migraci základní služby prvku ASP.NET AJAX ekvivalentní podporou AJAXU [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="65898-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="65898-104">Ukazuje, jak vytvořit funkčně srovnatelný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] verzi služby prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="65898-104">It shows how to create a functionally equivalent [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="65898-105">Tyto dvě služby je pak možné použít vedle sebe, nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby lze použít k nahrazení služba ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="65898-105">The two services can then be used side by side, or the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be used to replace the ASP.NET AJAX service.</span></span>  
  
 <span data-ttu-id="65898-106">Migrace na existující službu prvku ASP.NET AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba AJAX nabízí následující výhody:</span><span class="sxs-lookup"><span data-stu-id="65898-106">Migrating an existing ASP.NET AJAX service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="65898-107">Vaše služba AJAX můžou zpřístupnit jako SOAP služby s minimálními další konfigurace.</span><span class="sxs-lookup"><span data-stu-id="65898-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>  
  
-   <span data-ttu-id="65898-108">Můžete využívat výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce, jako je trasování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="65898-108">You can benefit from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features such as tracing, and so on.</span></span>  
  
 <span data-ttu-id="65898-109">V následujících postupech se předpokládá, že používáte [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65898-109">The following procedures assume that you are using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
 <span data-ttu-id="65898-110">Kód, který vyplývá z postupů uvedených v tomto tématu najdete v příkladu postupy.</span><span class="sxs-lookup"><span data-stu-id="65898-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="65898-111">vystavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přes koncový bod povolený AJAX, podívejte [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="65898-111"> exposing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="65898-112">Vytvoření a testování aplikace ASP.NET – webové služby</span><span class="sxs-lookup"><span data-stu-id="65898-112">To create and test the ASP.NET Web service application</span></span>  
  
1.  <span data-ttu-id="65898-113">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65898-113">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="65898-114">Z **soubor** nabídce vyberte možnost **nový**, pak **projektu**, pak **webové**a potom vyberte **aplikaci webové služby ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="65898-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>  
  
3.  <span data-ttu-id="65898-115">Název projektu `ASPHello` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="65898-115">Name the project `ASPHello` and click **OK**.</span></span>  
  
4.  <span data-ttu-id="65898-116">Zrušením komentáře u řádku v souboru Service1.asmx.cs, který obsahuje `System.Web.Script.Services.ScriptService]` povolit AJAX pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="65898-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>  
  
5.  <span data-ttu-id="65898-117">Z **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="65898-117">From the **Build** menu, select **Build Solution**.</span></span>  
  
6.  <span data-ttu-id="65898-118">Z **ladění** nabídce vyberte možnost **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="65898-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
7.  <span data-ttu-id="65898-119">Na webové stránce generované, vyberte `HelloWorld` operaci.</span><span class="sxs-lookup"><span data-stu-id="65898-119">On the Web page generated, select the `HelloWorld` operation.</span></span>  
  
8.  <span data-ttu-id="65898-120">Klikněte **Invoke** tlačítko `HelloWorld` zkušební stránku.</span><span class="sxs-lookup"><span data-stu-id="65898-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="65898-121">Měli byste obdržet následující odpověď XML.</span><span class="sxs-lookup"><span data-stu-id="65898-121">You should receive the following XML response.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. <span data-ttu-id="65898-122">Tato odezva potvrdí, že teď máte funkční služba ASP.NET AJAX a, zejména v případě, že služba nyní vystavila koncový bod v Service1.asmx/HelloWorld, která reaguje na HTTP POST požadavky a vrátí XML.</span><span class="sxs-lookup"><span data-stu-id="65898-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>  
  
     <span data-ttu-id="65898-123">Teď jste se převést tuto službu používat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba AJAX.</span><span class="sxs-lookup"><span data-stu-id="65898-123">Now you are ready to convert this service to use a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service.</span></span>  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="65898-124">Chcete-li vytvořit ekvivalentní aplikace služby WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="65898-124">To create an equivalent WCF AJAX service application</span></span>  
  
1.  <span data-ttu-id="65898-125">Klikněte pravým tlačítkem myši **ASPHello** projektu a vyberte **přidat**, pak **nová položka**a potom **podporou AJAXU služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="65898-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="65898-126">Název služby `WCFHello` a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="65898-126">Name the service `WCFHello` and click **Add**.</span></span>  
  
3.  <span data-ttu-id="65898-127">Otevřete soubor WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="65898-127">Open the WCFHello.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="65898-128">Z Service1.asmx.cs, zkopírujte následující implementace `HelloWorld` operaci.</span><span class="sxs-lookup"><span data-stu-id="65898-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  <span data-ttu-id="65898-129">Vložte zkopírovaný provádění `HelloWorld` operace do souboru WCFHello.svc.cs místo následující kód.</span><span class="sxs-lookup"><span data-stu-id="65898-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  <span data-ttu-id="65898-130">Zadejte `Namespace` atribut pro <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="65898-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  <span data-ttu-id="65898-131">Přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> k `HelloWorld` operace a sadu <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost vrátit <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="65898-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="65898-132">Všimněte si, že, není-li nastavit, výchozí hodnota je návratový typ <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="65898-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  <span data-ttu-id="65898-133">Z **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="65898-133">From the **Build** menu, select **Build Solution**.</span></span>  
  
9. <span data-ttu-id="65898-134">Otevřete soubor WCFHello.svc a z **ladění** nabídce vyberte možnost **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="65898-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
10. <span data-ttu-id="65898-135">Služba teď zpřístupní koncový bod v `WCFHello.svc/HelloWorld`, která reaguje na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="65898-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="65898-136">Požadavky HTTP POST nelze testovat z prohlížeče, ale koncový bod vrátí následující XML XML.</span><span class="sxs-lookup"><span data-stu-id="65898-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. <span data-ttu-id="65898-137">`WCFHello.svc/HelloWorld` a `Service1.aspx/HelloWorld` koncové body jsou funkčně rovnocenné.</span><span class="sxs-lookup"><span data-stu-id="65898-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65898-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="65898-138">Example</span></span>  
 <span data-ttu-id="65898-139">Kód, který vyplývá z postupů uvedených v tomto tématu najdete v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="65898-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>  
  
```  
//This is the ASP.NET code in the Service1.asmx.cs file.  
  
using System;  
using System.Collections;  
using System.ComponentModel;  
using System.Data;  
using System.Linq;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Linq;  
using System.Web.Script.Services;  
  
namespace ASPHello  
{  
    /// <summary>  
    /// Summary description for Service1.  
    /// </summary>  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    [ToolboxItem(false)]  
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.   
    [System.Web.Script.Services.ScriptService]  
    public class Service1 : System.Web.Services.WebService  
    {  
  
        [WebMethod]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
    }  
}   
  
//This is the WCF code in the WCFHello.svc.cs file.  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace ASPHello  
{  
    [ServiceContract(Namespace = "WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class WCFHello  
    {  
        // Add [WebInvoke] attribute to use HTTP GET.  
        [OperationContract]  
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
  
        // Add more operations here and mark them with [OperationContract].  
    }  
}  
```  
  
 <span data-ttu-id="65898-140"><xref:System.Xml.XmlDocument> Typ není podporován <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože není serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="65898-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="65898-141">Můžete použít buď <xref:System.Xml.Linq.XDocument> zadejte nebo serializovat <xref:System.Xml.XmlDocument.DocumentElement%2A> místo.</span><span class="sxs-lookup"><span data-stu-id="65898-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>  
  
 <span data-ttu-id="65898-142">Pokud ASMX webové služby se provádí upgrade a migrace souběžného k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, vyhněte se dva typy mapování se stejným názvem v klientovi.</span><span class="sxs-lookup"><span data-stu-id="65898-142">If ASMX Web services are being upgraded and migrated side-by-side to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="65898-143">Tím dojde k výjimce v serializátorů Pokud stejný typ se používá v <xref:System.Web.Services.WebMethodAttribute> a <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="65898-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>  
  
-   <span data-ttu-id="65898-144">Pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nejprve přidání služby, vyvolání metody webové služby ASMX způsobí, že výjimka v <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definici stylu pořadí v proxy serveru má přednost před.</span><span class="sxs-lookup"><span data-stu-id="65898-144">If [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] style definition of the order in the proxy takes precedence.</span></span>  
  
-   <span data-ttu-id="65898-145">Pokud nejprve přidáte ASMX webové služby, volání metody na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba způsobuje výjimka v <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> definici stylu webové služby v pořadí proxy serveru má přednost před.</span><span class="sxs-lookup"><span data-stu-id="65898-145">If ASMX Web Service is added first, invoking method on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>  
  
 <span data-ttu-id="65898-146">Existují významné rozdíly v chování mezi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a prvku ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="65898-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="65898-147">Například <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> představuje slovník jako pole dvojic klíč/hodnota, zatímco prvku ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> představuje slovník jako skutečných objektů JSON.</span><span class="sxs-lookup"><span data-stu-id="65898-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="65898-148">Tak, aby následující slovníku v prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="65898-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 <span data-ttu-id="65898-149">Tohoto slovníku je reprezentována v objekty JSON, jak je znázorněno v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="65898-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>  
  
-   <span data-ttu-id="65898-150">[{"Klíč": "1", "Value": 1}, {"Klíč": "Dva", "Value": 2}] pomocí<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="65898-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>  
  
-   <span data-ttu-id="65898-151">{"1": 1, "dva": 2} pomocí prvku ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="65898-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>  
  
 <span data-ttu-id="65898-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Účinnější v tom smyslu, že je můžete zpracovat slovník kde klíče typem není řetězec, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> nelze.</span><span class="sxs-lookup"><span data-stu-id="65898-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="65898-153">Ale k tomu je JSON popisný.</span><span class="sxs-lookup"><span data-stu-id="65898-153">But the latter is more JSON-friendly.</span></span>  
  
 <span data-ttu-id="65898-154">Významné rozdíly mezi tyto serializátorů jsou shrnuty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="65898-154">The significant differences between these serializers are summarized in the following table.</span></span>  
  
|<span data-ttu-id="65898-155">Kategorie rozdílů</span><span class="sxs-lookup"><span data-stu-id="65898-155">Category of Differences</span></span>|<span data-ttu-id="65898-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="65898-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="65898-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="65898-157">ASP.NET AJAX JavaScriptSerializer</span></span>|  
|-----------------------------|--------------------------------|---------------------------------------|  
|<span data-ttu-id="65898-158">Při deserializaci prázdný vyrovnávací paměti (nové byte[0]) do <xref:System.Object> (nebo <xref:System.Uri>, nebo některé jiné třídy).</span><span class="sxs-lookup"><span data-stu-id="65898-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="65898-159">Serializationexception –</span><span class="sxs-lookup"><span data-stu-id="65898-159">SerializationException</span></span>|<span data-ttu-id="65898-160">null</span><span class="sxs-lookup"><span data-stu-id="65898-160">null</span></span>|  
|<span data-ttu-id="65898-161">Serializace<xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="65898-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="65898-162">{} (nebo {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="65898-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="65898-163">Null</span><span class="sxs-lookup"><span data-stu-id="65898-163">Null</span></span>|  
|<span data-ttu-id="65898-164">Serializace soukromých členů typů [Serializable].</span><span class="sxs-lookup"><span data-stu-id="65898-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="65898-165">serializovat</span><span class="sxs-lookup"><span data-stu-id="65898-165">serialized</span></span>|<span data-ttu-id="65898-166">nelze serializovat.</span><span class="sxs-lookup"><span data-stu-id="65898-166">not serialized</span></span>|  
|<span data-ttu-id="65898-167">Serializace veřejné vlastnosti <xref:System.Runtime.Serialization.ISerializable> typy.</span><span class="sxs-lookup"><span data-stu-id="65898-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="65898-168">nelze serializovat.</span><span class="sxs-lookup"><span data-stu-id="65898-168">not serialized</span></span>|<span data-ttu-id="65898-169">serializovat</span><span class="sxs-lookup"><span data-stu-id="65898-169">serialized</span></span>|  
|<span data-ttu-id="65898-170">"Rozšíření" JSON</span><span class="sxs-lookup"><span data-stu-id="65898-170">"Extensions" of JSON</span></span>|<span data-ttu-id="65898-171">Dodržuje specifikaci JSON, která vyžaduje uvozovky na člen názvy objektů ({"a": "hello"}).</span><span class="sxs-lookup"><span data-stu-id="65898-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="65898-172">Podporuje názvy členové objektu bez uvozovek ({a: "text hello"}).</span><span class="sxs-lookup"><span data-stu-id="65898-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|  
|<span data-ttu-id="65898-173"><xref:System.DateTime>Koordinovaný světový čas (UTC)</span><span class="sxs-lookup"><span data-stu-id="65898-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="65898-174">Formát není podporován "\\/Date(123456789U)\\/" nebo "\\/Date\\(\d+ (P &#124; (\\+\\-[\d\{4\]}))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="65898-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="65898-175">Podporuje formát "\\/Date(123456789U)\\/" a "\\/Date\\(\d+ (P &#124; (\\+\\-[\d\{4\]}))?\\) \\ \\nebo) "jako hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="65898-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|  
|<span data-ttu-id="65898-176">Reprezentace slovníků</span><span class="sxs-lookup"><span data-stu-id="65898-176">Representation of dictionaries</span></span>|<span data-ttu-id="65898-177">Pole KeyValuePair\<tisíc, V >, zpracovává typy klíčů, které nejsou typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="65898-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="65898-178">Jako skutečných objektů JSON -, ale pouze klíče typy obslužných rutin, které jsou řetězce.</span><span class="sxs-lookup"><span data-stu-id="65898-178">As actual JSON objects - but only handles key types that are strings.</span></span>|  
|<span data-ttu-id="65898-179">Uvozený znaků</span><span class="sxs-lookup"><span data-stu-id="65898-179">Escaped characters</span></span>|<span data-ttu-id="65898-180">Vždy s escape dopředné lomítko (/); nikdy umožňuje zrušení uvozený neplatné znaky JSON, jako je například "\n".</span><span class="sxs-lookup"><span data-stu-id="65898-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="65898-181">Pomocí escape dopředné lomítko (/) pro hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="65898-181">With an escape forward slash (/) for DateTime values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65898-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="65898-182">See Also</span></span>  
 [<span data-ttu-id="65898-183">Postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="65898-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)