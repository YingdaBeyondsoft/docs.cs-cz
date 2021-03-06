---
title: extern (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 996888a585f8355bdda14e09b6bb9544257ae824
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172290"
---
# <a name="extern-c-reference"></a>extern (Referenční dokumentace jazyka C#)
`extern` Modifikátor se používá k deklaraci metodu, která je implementována externě. Běžně se používají `extern` se modifikátor s `DllImport` atributu při použití zprostředkovatele komunikace s objekty služby volat nespravovaný kód. V takovém případě metoda musí být deklarován také jako `static`, jak je znázorněno v následujícím příkladu:  
  
```csharp  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 `extern` – Klíčové slovo můžete také definovat alias externí sestavení, která vám umožní tak, aby odkazovaly různé verze stejné komponenty z v rámci jednoho sestavení. Další informace najdete v tématu [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).  
  
 Jedná se o chybu používat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) a `extern` modifikátory společně k úpravě stejného člena. Pomocí `extern` modifikátor znamená, že je metoda implementována mimo kód C# zatímco pomocí `abstract` modifikátor znamená, že není zadaný implementace metody ve třídě.  
  
 Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++. Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.  
  
## <a name="example"></a>Příklad  
 **Příklad 1.** V tomto příkladu program od uživatele přijímá řetězec a zobrazí v okně se zprávou. Program používá `MessageBox` metoda naimportované z knihovny User32.dll.  
  
 [!code-csharp[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a>Příklad  
 **Příklad 2.** Tento příklad ukazuje programu C#, který volá do knihovny jazyka C (nativní knihovny DLL).  
  
 1. Vytvoření následujícího souboru C a pojmenujte ji `cmdll.c`:  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a>Příklad  
 2. Otevřete okno sady Visual Studio x64 (nebo x32) nativní nástroje pro příkazový řádek z instalačního adresáře nástroje Visual Studio a kompilaci `cmdll.c` souboru zadáním **cl /LD cmdll.c** na příkazovém řádku.  
  
 3. Ve stejném adresáři, vytvořte následující soubor C# a pojmenujte ji `cm.cs`:  
  
```csharp  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a>Příklad  
 3. Otevřete okno sady Visual Studio x64 (nebo x32) nativní nástroje pro příkazový řádek z instalačního adresáře nástroje Visual Studio a kompilaci `cm.cs` souboru zadáním:  
  
> **CSC cm.cs** (pro x64 příkazového řádku)   
>  —nebo—  
> **CSC /platform:x 86 cm.cs** (pro x32 příkazového řádku)  
  
 Tím se vytvoří spustitelný soubor `cm.exe`.  
  
 4. Run `cm.exe`. `SampleMethod` Metoda předá hodnotu 5 soubor knihovny DLL, která vrátí hodnotu násobí hodnotou 10.  Program vytvoří následující výstup:  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
