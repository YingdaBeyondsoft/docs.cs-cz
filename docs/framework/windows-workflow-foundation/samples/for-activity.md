---
title: Aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c8567eb848fbb7b5f6c68f52f1be78750a002411
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="for-activity"></a><span data-ttu-id="f80e3-102">Aktivity</span><span class="sxs-lookup"><span data-stu-id="f80e3-102">For Activity</span></span>
<span data-ttu-id="f80e3-103">Ukázka For ukazuje, jak vytvářet vlastní aktivity, která dědí z <xref:System.Activities.NativeActivity>a použít ho v pracovní postup provést v reálném světě příkladu.</span><span class="sxs-lookup"><span data-stu-id="f80e3-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="f80e3-104">Vlastní aktivity obsažené v této ukázkové funkce jako jazyka C# `for` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f80e3-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="f80e3-105">T</span><span class="sxs-lookup"><span data-stu-id="f80e3-105">T</span></span>  
  
 <span data-ttu-id="f80e3-106">`For` Vlastní aktivita má vlastností s názvem `InitAction`, `IterationAction`, `Condition`, a `Body` , odpovídají inicializace příkaz, příkaz iterativní, pokračování podmínku a textu v uvedeném pořadí – příkaz najít v standardní jazyka C# `For` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f80e3-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="f80e3-107">Následující tabulka popisuje soubory klíčů ve vzorku.</span><span class="sxs-lookup"><span data-stu-id="f80e3-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="f80e3-108">Soubor</span><span class="sxs-lookup"><span data-stu-id="f80e3-108">File</span></span>|<span data-ttu-id="f80e3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f80e3-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="f80e3-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="f80e3-110">For.cs</span></span>|<span data-ttu-id="f80e3-111">Definice pro třídy `For` vlastní aktivitu, která rozšiřuje <xref:System.Activities.NativeActivity> třída poskytuje funkce jazyka C# `For` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f80e3-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="f80e3-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="f80e3-112">Program.cs</span></span>|<span data-ttu-id="f80e3-113">Klientská aplikace, která provádí základní iterativní práci na kolekci pomocí vlastní `For` aktivity.</span><span class="sxs-lookup"><span data-stu-id="f80e3-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f80e3-114">Při použití `For` vlastní aktivitu, ujistěte se, že `Condition` je nastavena; jinak může dojít k nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="f80e3-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f80e3-115">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="f80e3-115">Demonstrates</span></span>  
 <span data-ttu-id="f80e3-116">Vytvořit vlastní aktivitu, která dědí z <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="f80e3-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="f80e3-117">Diskusní</span><span class="sxs-lookup"><span data-stu-id="f80e3-117">Discussion</span></span>  
 <span data-ttu-id="f80e3-118">Následující tabulka popisuje vlastnosti aktivity obsažené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="f80e3-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="f80e3-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="f80e3-119">InitAction</span></span>  
 <span data-ttu-id="f80e3-120">Inicializace – příkaz</span><span class="sxs-lookup"><span data-stu-id="f80e3-120">Initialization statement</span></span>  
  
 <span data-ttu-id="f80e3-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="f80e3-121">IterationAction</span></span>  
 <span data-ttu-id="f80e3-122">Iterační – příkaz</span><span class="sxs-lookup"><span data-stu-id="f80e3-122">Iterative statement</span></span>  
  
 <span data-ttu-id="f80e3-123">Podmínka</span><span class="sxs-lookup"><span data-stu-id="f80e3-123">Condition</span></span>  
 <span data-ttu-id="f80e3-124">Pokračování – příkaz</span><span class="sxs-lookup"><span data-stu-id="f80e3-124">Continuation statement</span></span>  
  
 <span data-ttu-id="f80e3-125">Text</span><span class="sxs-lookup"><span data-stu-id="f80e3-125">Body</span></span>  
 <span data-ttu-id="f80e3-126">Text – příkaz</span><span class="sxs-lookup"><span data-stu-id="f80e3-126">Body statement</span></span>  
  
 <span data-ttu-id="f80e3-127">Aktivity dědí z <xref:System.Activities.NativeActivity> k získání přístupu k funkcím runtime například plánování další aktivity byste měli spustit, pomocí jedné z `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="f80e3-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f80e3-128">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="f80e3-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="f80e3-129">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení For.sln.</span><span class="sxs-lookup"><span data-stu-id="f80e3-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f80e3-130">Sestavte řešení, stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f80e3-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f80e3-131">Stisknutím klávesy F5 spusťte tohoto řešení.</span><span class="sxs-lookup"><span data-stu-id="f80e3-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f80e3-132">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f80e3-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f80e3-133">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f80e3-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f80e3-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f80e3-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f80e3-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f80e3-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`  
  
## <a name="see-also"></a><span data-ttu-id="f80e3-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f80e3-136">See Also</span></span>