---
title: Aktivita stromu kontroly
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 4f2ca6bff27cfe0e3362e2a3b95cd08a0f8d5297
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516838"
---
# <a name="activity-tree-inspection"></a>Aktivita stromu kontroly
Kontroly stromu aktivity se používá aplikace autory pracovního postupu ke kontrole pracovních hostovaných aplikací. Pomocí <xref:System.Activities.WorkflowInspectionServices>, pracovní postupy můžete vyhledávat konkrétní podřízené aktivity, jednotlivé aktivity a jejich vlastnosti můžete provést výčet a do mezipaměti metadat runtime aktivit v určitém čase. Toto téma obsahuje přehled <xref:System.Activities.WorkflowInspectionServices> a způsobu jeho použití kontrola strom aktivity.  
  
## <a name="using-workflowinspectionservices"></a>Pomocí WorkflowInspectionServices  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Metoda se používá k výčet všech aktivit ve stromové struktuře zadaný aktivity. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Vrátí vyčíslitelnou dotýká všechny aktivity v rámci stromu včetně podřízených prvků, obslužné rutiny delegáta, proměnné výchozí hodnoty a argument výrazy. V následujícím příkladu se vytváří definice pracovního postupu pomocí <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>a výrazy. Po vytvoření definice pracovního postupu je volána a potom `InspectActivity` metoda je volána.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Výčet aktivit, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> je volána v kořenové aktivity a znovu rekurzivně na každý vrácený aktivity. V následujícím příkladu <xref:System.Activities.Activity.DisplayName%2A> každou aktivitu a výrazu v rámci aktivity stromu je zapsán do konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Tento ukázkový kód poskytuje následující výstup.  
  
 **Položky seznamu 1**  
**Položky seznamu 2**   
**Položky seznamu 3**   
**Položky seznamu 4**   
**Položky seznamu 5**   
**Přidat do kolekce položky.**   
**Pořadí**   
 **Literál < seznamu\<řetězec >>**  
 **Chvíli**  
 **AddToCollection\<řetězec >**  
 **VariableValue < ICollection\<řetězec >>**  
 **LambdaValue\<řetězec >**  
 **LocationReferenceValue < seznamu\<řetězec >>**  
 **LambdaValue\<logická hodnota >**  
 **LocationReferenceValue < seznamu\<řetězec >>**  
 **ForEach\<řetězec >**  
 **VariableValue < IEnumerable\<řetězec >>**  
 **WriteLine**  
 **DelegateArgumentValue\<řetězec >**  
 **Pořadí**  
 **WriteLine**  
 **Literál\<řetězec >** načíst konkrétní aktivitu místo vytváření výčtů pro všechny aktivity, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> se používá. Obě <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> a <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> provést ukládání do mezipaměti metadat, pokud `WorkflowInspectionServices.CacheMetadata` nebyla volána dříve. Pokud <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> byla volána poté <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> je založena na existující metadata. Proto pokud byly provedeny změny stromu od posledního volání <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> může vrátit neočekávané výsledky. Pokud byly provedeny změny do pracovního postupu po volání <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, metadata znovu do mezipaměti voláním <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metoda. Ukládání do mezipaměti metadat je popsané v další části.  
  
### <a name="caching-metadata"></a>Ukládání do mezipaměti metadat  
 Ukládání do mezipaměti metadat pro aktivitu sestavení a ověří popis aktivity argumenty, proměnné, podřízené aktivity a delegáti aktivity. Metadata, ve výchozím nastavení, se uloží do mezipaměti modulem runtime při aktivitu je připravený pro provedení. Pokud chce, aby se autora hostitele pracovního postupu pro ukládání do mezipaměti metadat pro aktivitu nebo stromu aktivity před tím, např. Chcete-li provést všechny náklady na předem, pak <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> lze použít pro ukládání do mezipaměti metadat v požadované době.
