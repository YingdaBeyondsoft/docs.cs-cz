---
title: Hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 02d77b851dcd35108668ee6a42022e9721b84bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491323"
---
# <a name="hosting-workflow-services"></a>Hostování služeb pracovních postupů
Musí být hostované služby pracovního postupu pro něj reagovat na příchozí zprávy. Služby pracovních postupů pomocí infrastruktury přenosu zpráv WCF a jsou proto hostované podobným způsobem. Jako služby WCF může být hostovaný pracovní postup služby ve spravované aplikaci, v rámci Internetové informační služby (IIS), nebo v rámci procesu aktivace služby WAS (Windows). Kromě toho může být hostovaný pracovní postup služby v systému Windows Server App Fabric. Další informace o systému Windows Server App Fabric najdete v části [dokumentaci systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037), [funkce hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494), a [AppFabric hostování koncepty](http://go.microsoft.com/fwlink/?LinkId=196495). Další informace o různých způsobech hostitele WCF služeb najdete v tématu [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci  
 K hostování služby pracovního postupu ve spravované aplikaci, použijte <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Konstruktor vám umožňuje určit instanci typu singleton pracovního postupu služby, definice pracovního postupu služby nebo aktivitu, která používá pracovní postup aktivity zasílání zpráv. Volání metody <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> způsobí, že službu, kterou chcete zahájit naslouchání pro příchozí zprávy.  
  
## <a name="hosting-under-iis-or-was"></a>Hostování v rámci služby IIS nebo WAS  
 Hostování služby pracovního procesu v rámci služby IIS nebo WAS zahrnuje vytvoření virtuálního adresáře a umístění souborů do virtuálního adresáře, který definovat službu a její chování. Při hostování služby pracovního postupu v rámci služby IIS nebo WAS dispozici je několik možností:  
  
-   Umístěte soubor .xamlx, které definuje služby pracovního postupu v Internetové informační služby byl virtuální adresář společně s souboru Web.config, která určuje chování služby, koncových bodů a další konfigurace – elementy.  
  
-   Umístěte soubor .xamlx, které definuje služby pracovního postupu v Internetové informační služby byl virtuální adresář. Soubor .xamlx určuje koncové body vystavit. Koncové body jsou určené v `WorkflowService.Endpoints` element, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
      <WorkflowService.Endpoints>  
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">  
          <Endpoint.Binding>  
            <BasicHttpBinding />  
          </Endpoint.Binding>  
        </Endpoint>  
      </WorkflowService.Endpoints>  
    <!-- ... -->  
    </WorkflowService>  
    ```  
  
    > [!NOTE]
    >  Chování nelze zadat v souboru .xamlx, je nutné použít soubor Web.config, pokud je třeba zadat nastavení chování.  
  
-   Umístěte soubor .xamlx, které definuje služby pracovního postupu v Internetové informační služby byl virtuální adresář. Kromě toho můžete umístíte soubor .svc ve virtuálním adresáři. Soubor .svc umožňuje zadat vlastní vytváření hostitele webové služby, použít vlastní chování nebo zavést konfiguraci z vlastního umístění.  
  
-   Umístěte sestavení do služby IIS nebo byl virtuálního adresáře, který obsahuje aktivitu, která používá WCF aktivity zasílání zpráv.  
  
 Musí obsahovat .xamlx soubor, který definuje služby pracovního postupu <`Service`> kořenový element nebo kořenový element, který obsahuje jakéhokoli typu odvozeného z <xref:System.Workflow.ComponentModel.Activity>. Při použití [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] .xamlx soubor se vytvoří šablonu aktivity. Když je vytvořena pomocí šablony služeb WCF pracovního postupu .xamlx souboru.  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hostování služeb pracovních postupů v systému Windows Server App Fabric  
 Hostování služby pracovního postupu v části Windows Server App Fabric se provádí stejným způsobem jako hostování v rámci služby IIS / byla. Jediným rozdílem je fakt, že je nainstalovaný Windows Server App Fabric. Windows Server App Fabric poskytuje nástroje, které jsou přidány do Správce Internetové informační služby, jakož i rutiny prostředí PowerShell. Tyto nástroje zjednodušit nasazování, správě a sledování pracovní postup služby a služby WCF. . Další informace o systému Windows Server App Fabric najdete v části [Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>Odkazování na vlastní aktivity  
 Odkazy na vlastní aktivity musí být přidán do <`Assemblies`> tématu v části <`System.Web.Compilation`> tak, aby jsou načtena do domény aplikace a je možné najít typy deserializátor XAML. Tato nastavení můžete provést na úrovni aplikace nebo v kořenovém souboru Web.config, chcete-li nastavení použít na všechny aplikace na počítači.  
  
## <a name="deployment"></a>Nasazení  
 Nástroje pro nasazení webu byla vytvořena v zájmu snazší úlohy nasazení. Tento nástroj umožňuje migrovat aplikací mezi službami IIS 6.0 a IIS 7.0, synchronizace serverové farmy a balíčků, archivování a nasazování webových aplikací. Další informace najdete v tématu [nástroj pro nasazení MS](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>Viz také  
 [Interní informace o hostiteli služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [Konfigurace třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
