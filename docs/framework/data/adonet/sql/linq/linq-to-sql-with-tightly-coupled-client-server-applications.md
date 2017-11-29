---
title: "Technologie LINQ to SQL s aplikacemi úzce párované Klient Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3879d8eeec498f2855ee2b540f77570ee91109f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a><span data-ttu-id="47cc7-102">Technologie LINQ to SQL s aplikacemi úzce párované Klient Server</span><span class="sxs-lookup"><span data-stu-id="47cc7-102">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="47cc7-103">můžete používat ve střední vrstvě pro úzce párované inteligentní klienty na prezentační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="47cc7-103"> can be used on the middle tier with tightly-coupled Smart Clients on the presentation layer.</span></span> <span data-ttu-id="47cc7-104">Ve scénářích, které se týkají přístupu k datům jen pro čtení, žádné kontroly optimistickou metodu souběžného nebo optimistickou metodu souběžného časová razítka není mnohem složitější než v případě jiných vzdálené.</span><span class="sxs-lookup"><span data-stu-id="47cc7-104">In scenarios that involve read-only data access, no optimistic concurrency checks, or optimistic concurrency with timestamps, there is not much more complexity than with non-remote scenarios.</span></span> <span data-ttu-id="47cc7-105">Ale když databáze vyžaduje optimistickou metodu souběžného kontroluje s původní hodnoty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] neposkytuje úroveň podpory pro odezvy dat, které můžete najít v datových sadách.</span><span class="sxs-lookup"><span data-stu-id="47cc7-105">However, when a database requires optimistic concurrency checks with original values, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not provide the level of support for round-tripping of data that you find in DataSets.</span></span> <span data-ttu-id="47cc7-106">Ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] střední vrstvy můžou vyměňovat data s klienty na jakékoli platformě.</span><span class="sxs-lookup"><span data-stu-id="47cc7-106">However, a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] middle tier can exchange data with clients on any platform.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="47cc7-107">v [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] poskytuje žádnou infrastrukturu pro sledování stavu entity po mít byl serializován do klienta.</span><span class="sxs-lookup"><span data-stu-id="47cc7-107"> in [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] provides no infrastructure for tracking entity state after they have been serialized to a client.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="47cc7-108">Umožňuje kde interakce mezi data a prezentační vrstvy jsou malé a relativně atomic architektury orientované na služby, ale neprovádí žádné odezvy původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="47cc7-108"> enables service-oriented architectures where interactions between the data and presentation layers are small and relatively atomic, but does not perform any round-tripping of original values.</span></span> <span data-ttu-id="47cc7-109">Proto pokud budete chtít použít úzce párované inteligentní klienta s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]a databáze používá optimistickou metodu souběžného s původní hodnoty, je nutné implementovat vlastní mechanismus pro komunikaci mezi prezentační vrstvou a střední změny úroveň.</span><span class="sxs-lookup"><span data-stu-id="47cc7-109">Therefore, if you want to use a tightly-coupled Smart Client with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and a database uses optimistic concurrency with original values, you will have to implement your own mechanism for communicating changes between the presentation tier and middle tier.</span></span> <span data-ttu-id="47cc7-110">Je až návrháři se rozhodnout, zda má smysl udělat tento bit další práci za výhody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje ve střední vrstvě.</span><span class="sxs-lookup"><span data-stu-id="47cc7-110">It is up to the system designer to decide whether it makes sense to do this bit of extra work in exchange for the benefits that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides on the middle tier.</span></span> <span data-ttu-id="47cc7-111">Na druhé straně Pokud databáze obsahuje časová razítka, nejsou pro vlastní logiky sledování změn není nutné.</span><span class="sxs-lookup"><span data-stu-id="47cc7-111">On the other hand, if the database has timestamps, then there is no need for custom change-tracking logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cc7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="47cc7-112">See Also</span></span>  
 [<span data-ttu-id="47cc7-113">N-vrstvá a vzdálené aplikace s dotazy LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="47cc7-113">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [<span data-ttu-id="47cc7-114">Technologie LINQ to SQL N-vrstvá s webovými službami</span><span class="sxs-lookup"><span data-stu-id="47cc7-114">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [<span data-ttu-id="47cc7-115">Práce s datových sad ve víceúrovňových aplikacích</span><span class="sxs-lookup"><span data-stu-id="47cc7-115">Work with datasets in n-tier applications</span></span>](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)