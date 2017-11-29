---
title: "+ (Zřetězení řetězců) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 60661a592e23e230c32b1fd7093f5dfd8e6ed87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="7b095-102">+ (Zřetězení) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="7b095-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="7b095-103">Zřetězí dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="7b095-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b095-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b095-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b095-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7b095-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7b095-106">Jakýkoli platný výraz EDM. Datové typy řetězec.</span><span class="sxs-lookup"><span data-stu-id="7b095-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="7b095-107">Oba výrazy musí být stejného typu dat, nebo jeden výraz musí být schopen implicitně převést na datový typ druhého výrazu.</span><span class="sxs-lookup"><span data-stu-id="7b095-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7b095-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="7b095-108">Result Types</span></span>  
 <span data-ttu-id="7b095-109">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="7b095-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="7b095-110">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7b095-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b095-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b095-111">Example</span></span>  
 <span data-ttu-id="7b095-112">Následující dotaz Entity SQL používá + operátor a zřetězí dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="7b095-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="7b095-113">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7b095-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7b095-114">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="7b095-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7b095-115">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7b095-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="7b095-116">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="7b095-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="7b095-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b095-117">See Also</span></span>  
 [<span data-ttu-id="7b095-118">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="7b095-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="7b095-119">Typy konceptuálního modelu (CSDL)</span><span class="sxs-lookup"><span data-stu-id="7b095-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)