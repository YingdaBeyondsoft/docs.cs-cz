---
title: 'Postup: provedení parametrizované uložené procedury pomocí objekt EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 68589cf8906e35313e261e373cf87017ffe6f8f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760502"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Postup: provedení parametrizované uložené procedury pomocí objekt EntityCommand
Toto téma ukazuje, jak provést parametrizované uložené procedury pomocí <xref:System.Data.EntityClient.EntityCommand> třídy.  
  
### <a name="to-run-the-code-in-this-example"></a>Spustí kód v tomto příkladu  
  
1.  Přidat [školní modelu](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Import `GetStudentGrades` uložené procedury a zadejte `CourseGrade` jako návratový typ entity. Informace o tom, jak importovat uložené procedury najdete v tématu [postupy: Import uloženou proceduru](http://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).  
  
## <a name="example"></a>Příklad  
 Následující kód spustí `GetStudentGrades` uložené procedury kde `StudentId` povinný parametr. Výsledky jsou pak přečte <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
