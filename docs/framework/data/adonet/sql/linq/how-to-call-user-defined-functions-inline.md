---
title: 'Postupy: volání vnořené funkce definované uživatelem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 39eeab06952e1d8a1128580a2be79ed4711d58d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359397"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Postupy: volání vnořené funkce definované uživatelem
I když bude možné volat vložené uživatelem definované funkce, funkce, které jsou zahrnuty v dotazu, jejichž spuštění je odložení nejsou provést, dokud se spustí dotaz. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Při volání stejnou funkci mimo dotazu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří jednoduchý dotaz z výrazu volání metody. Toto je syntaxe SQL (parametr `@p0` je vázána na konstantu předaná):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří následující:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
 V následujícím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz, zobrazí se o vložený volání do metody generované uživatelem definované funkce `ReverseCustName`. Funkce není okamžitě spustit, protože spuštění dotazu je odložen. SQL sestavených pro tento dotaz přeloží volání uživatelem definované funkce v databázi (viz následující dotaz SQL kód).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Viz také  
 [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
