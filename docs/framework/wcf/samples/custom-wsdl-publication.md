---
title: "Vlastní publikování WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e390bf728cde703a967fcea954583f6e5f84002
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="85b75-102">Vlastní publikování WSDL</span><span class="sxs-lookup"><span data-stu-id="85b75-102">Custom WSDL Publication</span></span>
<span data-ttu-id="85b75-103">Tento příklad znázorňuje postup:</span><span class="sxs-lookup"><span data-stu-id="85b75-103">This sample demonstrates how to:</span></span>  
  
-   <span data-ttu-id="85b75-104">Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na vlastní <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atribut, který chcete exportovat vlastnosti atribut jako WSDL poznámky.</span><span class="sxs-lookup"><span data-stu-id="85b75-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
-   <span data-ttu-id="85b75-105">Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> Import vlastního WSDL poznámky.</span><span class="sxs-lookup"><span data-stu-id="85b75-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
-   <span data-ttu-id="85b75-106">Implementace <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> na vlastní smlouvy chování a vlastní operace chování, v uvedeném pořadí, zápis importované poznámky jako komentáře v modelu CodeDom pro importované kontrakt a operace.</span><span class="sxs-lookup"><span data-stu-id="85b75-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
-   <span data-ttu-id="85b75-107">Použití <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> ke stažení WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> import schématu WSDL pomocí vlastní – Importér WSDL a <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> ke generování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kód klienta s poznámkami WSDL jako / / / a ''' komentáře v jazyce C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="85b75-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85b75-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="85b75-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="85b75-109">Služba</span><span class="sxs-lookup"><span data-stu-id="85b75-109">Service</span></span>  
 <span data-ttu-id="85b75-110">Služby v této ukázce je označené dvěma vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="85b75-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="85b75-111">První, `WsdlDocumentationAttribute`, přijme řetězec v konstruktoru a dají se použít k poskytování rozhraní kontraktu nebo operaci s řetězec, který popisuje jeho použití.</span><span class="sxs-lookup"><span data-stu-id="85b75-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="85b75-112">Druhá s názvem `WsdlParamOrReturnDocumentationAttribute`, můžete použít k vrácení hodnoty nebo parametry, které popisují tyto hodnoty v operaci.</span><span class="sxs-lookup"><span data-stu-id="85b75-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="85b75-113">Následující příklad ukazuje kontraktu služby `ICalculator`, které jsou popsány pomocí těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="85b75-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 <span data-ttu-id="85b75-114">`WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior>, takže instance atributy jsou přidány do odpovídajících <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Description.OperationDescription> při otevření službu.</span><span class="sxs-lookup"><span data-stu-id="85b75-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="85b75-115">Atribut také implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="85b75-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="85b75-116">Když <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> je volána, <xref:System.ServiceModel.Description.WsdlExporter> používané pro export metadat a <xref:System.ServiceModel.Description.WsdlContractConversionContext> obsahující popis služby předávání objektů v jako parametry umožňující úpravy exportovaný metadat.</span><span class="sxs-lookup"><span data-stu-id="85b75-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="85b75-117">V této ukázce, v závislosti na tom, jestli má objekt context exportu <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Description.OperationDescription>, komentář se extrahuje z atributu pomocí vlastnosti text a je přidán do elementu WSDL poznámky, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="85b75-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (contractDescription != null)  
    {  
        // Inside this block it is the contract-level comment attribute.  
        // This.Text returns the string for the contract attribute.  
        // Set the doc element; if this isn't done first, there is no XmlElement in the   
        // DocumentElement property.  
        context.WsdlPortType.Documentation = string.Empty;  
        // Contract comments.  
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
        XmlElement summaryElement = owner.CreateElement("summary");  
        summaryElement.InnerText = this.Text;  
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
    }  
    else  
    {  
        Operation operation = context.GetOperation(operationDescription);  
        if (operation != null)  
        {  
            // We are dealing strictly with the operation here.  
            // This.Text returns the string for the operation-level attributes.  
            // Set the doc element; if this isn't done first, there is no XmlElement in the   
            // DocumentElement property.  
            operation.Documentation = String.Empty;  
  
            // Operation C# triple comments.  
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;  
            XmlElement newSummaryElement = owner.CreateElement("summary");  
            newSummaryElement.InnerText = this.Text;  
            operation.DocumentationElement.AppendChild(newSummaryElement);  
```  
  
 <span data-ttu-id="85b75-118">Pokud je v průběhu operace exportu příklad používá reflexe získat žádné `WsdlParamOrReturnDocumentationAttribute` hodnoty pro parametry a návratové hodnoty a přidá je do elementů poznámky WSDL pro tuto operaci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="85b75-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```  
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 <span data-ttu-id="85b75-119">Ukázka pak publikuje metadata standardní způsobem, pomocí následujícího konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="85b75-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a><span data-ttu-id="85b75-120">Svcutil klienta</span><span class="sxs-lookup"><span data-stu-id="85b75-120">Svcutil client</span></span>  
 <span data-ttu-id="85b75-121">Tato ukázka nepoužívá Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="85b75-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="85b75-122">Kontrakt je zadaný v generatedClient.cs nelze vyvolat soubor, který po ukázku ukazuje vlastní importu WSDL a generování kódu, službu.</span><span class="sxs-lookup"><span data-stu-id="85b75-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="85b75-123">Pokud chcete použít následující vlastní – Importér WSDL pro tento příklad, můžete spustit Svcutil.exe a zadejte `/svcutilConfig` možnost poskytnutí cestu k souboru konfigurace klienta použít v této ukázce, která odkazuje `WsdlDocumentation.dll` knihovny.</span><span class="sxs-lookup"><span data-stu-id="85b75-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="85b75-124">Načíst `WsdlDocumentationImporter`, ale musí být schopný pro vyhledání a načtení Svuctil.exe `WsdlDocumentation.dll` knihovny, tzn. buď ji je zaregistrován v globální mezipaměti sestavení, v cestě, nebo je ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="85b75-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="85b75-125">Základní příklad, jako je tato, je nejjednodušší cesta ke kopírování Svcutil.exe a konfigurační soubor klienta do stejného adresáře jako `WsdlDocumentation.dll` a spusťte jej z ní.</span><span class="sxs-lookup"><span data-stu-id="85b75-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="85b75-126">Program pro import vlastního WSDL</span><span class="sxs-lookup"><span data-stu-id="85b75-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="85b75-127">Vlastní <xref:System.ServiceModel.Description.IWsdlImportExtension> objekt `WsdlDocumentationImporter` také implementuje <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior> přidat do třídy importované ServiceEndpoints a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> má být volána k úpravě generování kódu při kontrakt nebo operace Probíhá vytváření kódu.</span><span class="sxs-lookup"><span data-stu-id="85b75-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="85b75-128">V první <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metoda, ukázku Určuje, zda WSDL poznámky na úrovni kontrakt nebo operace a přidá sám sebe jako chování v příslušné oboru, a jeho konstruktoru předá text importované poznámky.</span><span class="sxs-lookup"><span data-stu-id="85b75-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```  
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="85b75-129">Poté, když se vygeneruje kód, systém vyvolá <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metody, předávání informací odpovídající kontext.</span><span class="sxs-lookup"><span data-stu-id="85b75-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="85b75-130">Ukázka formáty vlastní poznámky WSDL a vloží je do modelu CodeDom jako komentáře.</span><span class="sxs-lookup"><span data-stu-id="85b75-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```  
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a><span data-ttu-id="85b75-131">Klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="85b75-131">The Client Application</span></span>  
 <span data-ttu-id="85b75-132">Klientská aplikace načte vlastní – Importér WSDL zadáním v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="85b75-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 <span data-ttu-id="85b75-133">Jakmile byl zadán vlastní – Importér, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] systém metadat načte vlastní – Importér do jakéhokoli <xref:System.ServiceModel.Description.WsdlImporter> vytvořený pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="85b75-133">Once the custom importer has been specified, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="85b75-134">Této ukázce se používá <xref:System.ServiceModel.Description.MetadataExchangeClient> stáhnout metadata, <xref:System.ServiceModel.Description.WsdlImporter> správně nakonfigurovaná tak, aby import metadat pomocí vlastní – Importér ukázka vytvoří, a <xref:System.ServiceModel.Description.ServiceContractGenerator> zkompilovat upravené kontrakt informace do obou jazyka Visual Basic C# kódu a klienta, můžete použít v sadě Visual Studio pro podporu technologie Intellisense nebo zkompilovat do dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="85b75-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```  
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="85b75-135">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="85b75-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="85b75-136">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="85b75-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="85b75-137">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="85b75-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="85b75-138">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="85b75-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85b75-139">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="85b75-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="85b75-140">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="85b75-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="85b75-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="85b75-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="85b75-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="85b75-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a><span data-ttu-id="85b75-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="85b75-143">See Also</span></span>