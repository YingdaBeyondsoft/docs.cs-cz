---
title: Základní datové typy
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 977f99f129d591898953ed24ad5acdaa3ae9a88a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365982"
---
# <a name="basic-data-types"></a>Základní datové typy
Protože dotazy LINQ to SQL převede Transact-SQL před byly spouštěny na serveru Microsoft SQL Server. Technologie LINQ to SQL podporuje většinu stejné vestavěné funkce systému SQL Server podporuje pro základní datové typy.  
  
## <a name="casting"></a>Přetypování  
 Implicitním nebo explicitním přetypování jsou povolené ze zdroje typu CLR na cíl, typ CLR, pokud neexistuje podobné platný převod v rámci systému SQL Server. Další informace o přetypování CLR najdete v tématu [CType – funkce](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) a [jako](~/docs/csharp/language-reference/keywords/as.md). Po převodu přetypování změnit chování operace provedené na CLR výraz tak, aby odpovídaly chování jiné CLR výrazů, které přirozeně mapovat na typ cíle. Přetypování jsou také nepřeložitelná v rámci mapování dědičnosti. Objekty lze převést na konkrétnější podtypů entity tak, aby jejich dílčí specifických dat je přístupný.  
  
## <a name="equality-operators"></a>Operátory rovnosti  
 Technologie LINQ to SQL podporuje následující operátory rovnosti na základní datové typy uvnitř LINQ dotazy SQL:  
  
-   Stejné a operátor nerovnosti: operátory rovnosti a nerovnosti jsou podporovány pro číselné <xref:System.Boolean>, <xref:System.DateTime>, a <xref:System.TimeSpan> typy. Další informace o tom operátory jazyka Visual Basic `=` a `<>`, najdete v části [operátory porovnání](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Další informace o porovnání operátory jazyka C# `==` a `!=`, najdete v části [== – operátor](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) a [! = – operátor](~/docs/csharp/language-reference/operators/not-equal-operator.md), v tomto pořadí  
  
-   Is – operátor: `IS` operátor má podporované překladu, pokud se používá mapování dědičnosti. Můžete použít místo přímo testování sloupce diskriminátoru určit, zda objekt je určitý typ entity a převádějí na kontrolu na sloupce diskriminátoru. Další informace o operátory jazyka Visual Basic a C# je najdete v tématu [je operátor](~/docs/visual-basic/language-reference/operators/is-operator.md) a [je](~/docs/csharp/language-reference/keywords/is.md).  
  
## <a name="see-also"></a>Viz také  
 [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
