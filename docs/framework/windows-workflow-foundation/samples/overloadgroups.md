---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f644f09af3ce9e191dc6c5680472de4ef5ab727d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="overloadgroups"></a><span data-ttu-id="41a9f-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="41a9f-102">OverloadGroups</span></span>
<span data-ttu-id="41a9f-103">Tato ukázka se skládá z aktivity (`CreateLocation`), která má dva zajímavé vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="41a9f-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="41a9f-104">Je to některé požadováno, argumentů a ty, které jsou některé volitelné.</span><span class="sxs-lookup"><span data-stu-id="41a9f-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="41a9f-105">Umožňuje uživateli rozhodnout pro poskytnutí jednou ze dvou různých sad argumentů.</span><span class="sxs-lookup"><span data-stu-id="41a9f-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="41a9f-106">Tyto chování se dá udělat pomocí tyto dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="41a9f-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="41a9f-107">`[isRequired]`ověří, že vlastnost konkrétní aktivity je přiřadit, a pokud ne, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="41a9f-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="41a9f-108">`[OverloadGroup]`tak, aby uživatel aktivity můžete zvolit použití jedné množiny nebo jiné umístí společně sadu argumentů.</span><span class="sxs-lookup"><span data-stu-id="41a9f-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="41a9f-109">Uživatel nemůže použít argumenty z různých skupin přetížení ve stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="41a9f-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="41a9f-110">Po nastavení jiné pracovní postupy, volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> která vrací <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="41a9f-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="41a9f-111">Tisk <xref:System.Activities.Validation.Constraint> objekty do konzoly.</span><span class="sxs-lookup"><span data-stu-id="41a9f-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41a9f-112">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="41a9f-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="41a9f-113">Otevřete **OverloadGroups.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41a9f-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="41a9f-114">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="41a9f-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="41a9f-115">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="41a9f-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41a9f-116">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="41a9f-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="41a9f-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="41a9f-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41a9f-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="41a9f-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`