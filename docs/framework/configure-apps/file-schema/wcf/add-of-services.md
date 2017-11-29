---
title: "&lt;add&gt; – &lt;services&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60a717513689aeba1bfbd6229d4eef28024df8c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="7c64f-102">&lt;add&gt; – &lt;services&gt;</span><span class="sxs-lookup"><span data-stu-id="7c64f-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="7c64f-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování založené na pracovním postupu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="7c64f-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="7c64f-104">Tento element je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="7c64f-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="7c64f-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7c64f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7c64f-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7c64f-106">\<behaviors></span></span>  
<span data-ttu-id="7c64f-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7c64f-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="7c64f-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7c64f-108">\<behavior></span></span>  
<span data-ttu-id="7c64f-109">\<služby ></span><span class="sxs-lookup"><span data-stu-id="7c64f-109">\<services></span></span>  
<span data-ttu-id="7c64f-110">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="7c64f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c64f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c64f-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c64f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c64f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7c64f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c64f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c64f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c64f-114">Attributes</span></span>  
  
|<span data-ttu-id="7c64f-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="7c64f-115">Attribute</span></span>|<span data-ttu-id="7c64f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7c64f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c64f-117">– typ</span><span class="sxs-lookup"><span data-stu-id="7c64f-117">type</span></span>|<span data-ttu-id="7c64f-118">Řetězec, který určuje název sestavení kvalifikovaný typ služby k inicializovat.</span><span class="sxs-lookup"><span data-stu-id="7c64f-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="7c64f-119">Zadaná služba musí následovat určitá pravidla o signatur jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="7c64f-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="7c64f-120">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="7c64f-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c64f-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c64f-121">Child Elements</span></span>  
 <span data-ttu-id="7c64f-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="7c64f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c64f-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c64f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7c64f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c64f-124">Element</span></span>|<span data-ttu-id="7c64f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7c64f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c64f-126">\<služby ></span><span class="sxs-lookup"><span data-stu-id="7c64f-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="7c64f-127">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul.</span><span class="sxs-lookup"><span data-stu-id="7c64f-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="7c64f-128">Elementy jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="7c64f-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="7c64f-129">Služby uvedené v kolekci se inicializovat modul runtime pracovního postupu a přidat do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7c64f-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="7c64f-130">Proto služby uvedené v kolekci musí následovat určitá pravidla o signatur jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="7c64f-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="7c64f-131">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="7c64f-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c64f-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c64f-132">Remarks</span></span>  
 <span data-ttu-id="7c64f-133">Zadaná služba v tomto elementu se inicializovat modul runtime pracovního postupu a přidat do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7c64f-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="7c64f-134">Zadaná služba proto musí následovat určitá pravidla o signatur jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="7c64f-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="7c64f-135">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="7c64f-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c64f-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c64f-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c64f-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c64f-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="7c64f-138">Konfigurační soubory pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7c64f-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)