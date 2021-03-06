---
title: Matematické funkce kanonickém tvaru
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9d823eb45babca4b8f5dd717b4fb92c1984d1c8c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765097"
---
# <a name="math-canonical-functions"></a>Matematické funkce kanonickém tvaru
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje matematické funkce kanonickém tvaru.  
  
 V následující tabulce jsou uvedeny výpočty [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`Abs(` `value` `)`|Vrátí absolutní hodnotu `value`.<br /><br /> **Argumenty**<br /><br /> `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|Vrátí nejmenší celé číslo, která není menší než `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, a `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|Vrátí největší celé číslo, která není větší než `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, a `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|Vrátí výsledek zadaného `value` do zadané `exponent`.<br /><br /> **Argumenty**<br /><br /> `value`: `Int32, Int64, Double`, Nebo `Decimal`.<br /><br /> `exponent`: `Int64``, Double`, Nebo `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|Vrátí celočíselnou část `value`, zaokrouhleno na nejbližší celé číslo.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, a `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` nebo `Decimal`.<br /><br /> `digits`: `Int16` nebo `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|Vrátí `value`zkrácený k nejbližší zadaný `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` nebo `Decimal`.<br /><br /> `digits`: `Int16` nebo `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Truncate(748.58,1)`|  
  
 Vrátí tyto funkce `null` -li zadány `null` vstupní.  
  
 Ekvivalentní funkce je k dispozici ve zprostředkovateli spravované klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
