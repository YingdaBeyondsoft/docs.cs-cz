---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651489"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).
Pokud má procedury [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, nelze definovat přetížené verze trvá jednorozměrné pole pro parametr pole. Další informace najdete v tématu "Implicitní přetížení pro ParamArray parametr" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Chcete-li přetížení procedury, která přebírá proměnné počet parametrů  
  
1.  Zjistí, že postup a volání výhody logiku kód z přetížený verze více než `ParamArray` parametr. Najdete v části "Přetížení a ParamArrays" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
2.  Určete, které počtu zadaných hodnot postupu by měl přijmout v proměnné části Seznam parametrů. To může zahrnovat i v případě žádná hodnota, a v případě jedné jednorozměrné pole může obsahovat.  
  
3.  Pro každý přijatelné počet zadaných hodnot zápisu `Sub` nebo `Function` deklarace příkaz, který definuje odpovídající seznam parametrů. Nepoužívejte buď `Optional` nebo `ParamArray` – klíčové slovo v této verzi přetížená.  
  
4.  V každé deklaraci předcházet `Sub` nebo `Function` – klíčové slovo s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.  
  
5.  Následující každá deklarace psát kód postup, který by měl spustit, když kód volání poskytuje hodnoty pro seznam parametrů tohoto prohlášení.  
  
6.  Terminate – každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup definovaný s [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr a potom ekvivalentní sadu přetížené procedury.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Tento postup se seznam parametrů, která přebírá jednorozměrné pole pro parametr pole nelze přetížení. Můžete však použít signatur implicitní přetížení. Následující deklarace znázornění.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Kód v přetížené verze nemá k ověření, zda jeden nebo více hodnot pro zadaný kód volání `ParamArray` parametr, nebo pokud ano, kolik. Visual Basic předá ovládacího prvku na verzi odpovídající volání seznam argumentů.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Protože procedura se `ParamArray` parametr je ekvivalentní sadu přetížené verze, tento postup nelze přetížení se seznamem parametr odpovídající některé z těchto implicitní přetížení. Další informace najdete v tématu [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace. Pokud přijmete pole parametrů, doporučujeme otestovat délka pole Kód volání do ní předán a proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Nepovinné parametry](./optional-parameters.md)  
 [Pole parametrů](./parameter-arrays.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)  
 [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Řešení přetížení](./overload-resolution.md)
