---
title: 119 - WorkflowInstanceUpdatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b838f764b1f86b0477dc797620dca5f99bb13d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="119---workflowinstanceupdatedrecord"></a><span data-ttu-id="8722b-102">119 - WorkflowInstanceUpdatedRecord</span><span class="sxs-lookup"><span data-stu-id="8722b-102">119 - WorkflowInstanceUpdatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="8722b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8722b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8722b-104">ID</span><span class="sxs-lookup"><span data-stu-id="8722b-104">ID</span></span>|<span data-ttu-id="8722b-105">119</span><span class="sxs-lookup"><span data-stu-id="8722b-105">119</span></span>|  
|<span data-ttu-id="8722b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8722b-106">Keywords</span></span>|<span data-ttu-id="8722b-107">HealthMonitoring WFTracking</span><span class="sxs-lookup"><span data-stu-id="8722b-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="8722b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8722b-108">Level</span></span>|<span data-ttu-id="8722b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="8722b-109">Information</span></span>|  
|<span data-ttu-id="8722b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8722b-110">Channel</span></span>|<span data-ttu-id="8722b-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="8722b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8722b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8722b-112">Description</span></span>  
 <span data-ttu-id="8722b-113">Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když je aktualizována instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8722b-113">This event is emitted by the ETW tracking participant when a workflow instance is updated.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8722b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8722b-114">Message</span></span>  
 <span data-ttu-id="8722b-115">TrackRecord = WorkflowInstanceUpdatedRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stav = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, poznámky = %8, ProfileName = %9</span><span class="sxs-lookup"><span data-stu-id="8722b-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9</span></span>  
  
## <a name="details"></a><span data-ttu-id="8722b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8722b-116">Details</span></span>  
  
|<span data-ttu-id="8722b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8722b-117">Data Item Name</span></span>|<span data-ttu-id="8722b-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8722b-118">Data Item Type</span></span>|<span data-ttu-id="8722b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8722b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8722b-120">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="8722b-120">InstanceId</span></span>|<span data-ttu-id="8722b-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="8722b-121">xs:GUID</span></span>|<span data-ttu-id="8722b-122">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8722b-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="8722b-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="8722b-123">RecordNumber</span></span>|<span data-ttu-id="8722b-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="8722b-124">xs:long</span></span>|<span data-ttu-id="8722b-125">Pořadové číslo emitovaného záznamu</span><span class="sxs-lookup"><span data-stu-id="8722b-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="8722b-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="8722b-126">EventTime</span></span>|<span data-ttu-id="8722b-127">xs</span><span class="sxs-lookup"><span data-stu-id="8722b-127">xs:dateTime</span></span>|<span data-ttu-id="8722b-128">Čas v UTC při byl vygenerované události</span><span class="sxs-lookup"><span data-stu-id="8722b-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="8722b-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="8722b-129">ActivityDefinitionId</span></span>|<span data-ttu-id="8722b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-130">xs:string</span></span>|<span data-ttu-id="8722b-131">Název kořenové aktivity v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="8722b-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="8722b-132">Stav</span><span class="sxs-lookup"><span data-stu-id="8722b-132">State</span></span>|<span data-ttu-id="8722b-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-133">xs:string</span></span>|<span data-ttu-id="8722b-134">Aktuální stav pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8722b-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="8722b-135">OriginalDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8722b-135">OriginalDefinitionIdentity</span></span>|<span data-ttu-id="8722b-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-136">xs:string</span></span>|<span data-ttu-id="8722b-137">Původní id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8722b-137">The original workflow definition id</span></span>|  
|<span data-ttu-id="8722b-138">UpdatedDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8722b-138">UpdatedDefinitionIdentity</span></span>|<span data-ttu-id="8722b-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-139">xs:string</span></span>|<span data-ttu-id="8722b-140">Id definice aktualizované pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8722b-140">The updated workflow definition id</span></span>|  
|<span data-ttu-id="8722b-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8722b-141">Annotations</span></span>|<span data-ttu-id="8722b-142">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-142">xs:string</span></span>|<span data-ttu-id="8722b-143">Poznámky, které byly přidány k této události.</span><span class="sxs-lookup"><span data-stu-id="8722b-143">The annotations that were added to this event.</span></span> <span data-ttu-id="8722b-144">Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="8722b-144">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="8722b-145">Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >.</span><span class="sxs-lookup"><span data-stu-id="8722b-145">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="8722b-146">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="8722b-146">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="8722b-147">Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="8722b-147">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="8722b-148">ProfileName</span><span class="sxs-lookup"><span data-stu-id="8722b-148">ProfileName</span></span>|<span data-ttu-id="8722b-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-149">xs:string</span></span>|<span data-ttu-id="8722b-150">Název nebo sledování profil, který způsobil v tomto případě se vygenerované</span><span class="sxs-lookup"><span data-stu-id="8722b-150">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="8722b-151">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8722b-151">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="8722b-152">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-152">xs:string</span></span>|<span data-ttu-id="8722b-153">Id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8722b-153">The workflow definition id</span></span>|  
|<span data-ttu-id="8722b-154">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8722b-154">AppDomain</span></span>|<span data-ttu-id="8722b-155">xs:String</span><span class="sxs-lookup"><span data-stu-id="8722b-155">xs:string</span></span>|<span data-ttu-id="8722b-156">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8722b-156">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|