---
title: Ladění jazyka C# nebo Visual Basic Hello World .NET Core aplikace s Visual Studio 2017
description: Postup ladění aplikace Hello World napsané v C# nebo Visual Basic s Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 12/15/2017
ms.openlocfilehash: 3c130c2eebdf79c1db171cb2171aa68dfff728a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218427"
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a>Ladění aplikace Hello World s Visual Studio 2017

Pokud jste postupovali podle kroků v [sestavení C# Hello World aplikace s .NET Core ve Visual Studio 2017](.\with-visual-studio.md) nebo [sestavení jazyka Visual Basic Hello World aplikace s .NET Core ve Visual Studio 2017](vb-with-visual-studio.md) k vytvoření a spusťte jednoduché konzolové aplikace. Jakmile jste zapisovat a kompilované aplikace, můžete zahájit testování ho. Visual Studio zahrnuje komplexní sadu ladicí nástroje, které můžete použít při testování a řešení potíží s vaší aplikace.

## <a name="debugging-in-debug-mode"></a>Ladění v režimu ladění

*Ladění* a *verze* jsou dvě sady Visual Studio výchozí konfigurace sestavení. Aktuální konfigurace sestavení se zobrazí na panelu nástrojů. Na následujícím obrázku panelu nástrojů zobrazují, která je konfigurace zkompilovat svoji aplikaci v sadě Visual Studio **ladění** režimu.

   ![Panel nástrojů Visual Studio](./media/debugging-with-visual-studio/toolbar1.png)

Vždy začít testování váš program v režimu ladění. Ladění režimu vypne většina optimalizace kompilátoru a poskytuje bohatší informace během procesu vytváření.

## <a name="setting-a-breakpoint"></a>Nastavení boru přerušení

Spustit program v režimu ladění a zkuste několik ladění funkcí:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. A *zarážek* dočasně přeruší provádění aplikace *před* řádek se zarážkou spustí. 

   Nastavte zarážky v řádku, který čte `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` kliknutím na levém okraji okna kódu na tomto řádku nebo výběrem **ladění** > **Přepnout zarážku** položky nabídky řádek Vybrat. Jak ukazuje následující obrázek, označuje Visual Studio na řádku, na kterém je nastaven breakpoint zvýraznění ho a zobrazením červené kolečko jeho levého okraje.

   ![Visual Studio Program okno sadou zarážek](./media/debugging-with-visual-studio/setbreakpoint.png)

1. Spusťte program v režimu ladění výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů Stisknutím F5 nebo výběrem položky **ladění** > **spustit ladění**.

1. Zadejte řetězec v okně konzoly, když program vyzve k zadání názvu a stiskněte klávesu Enter.

1. Spuštění programu zastaví, když se dosáhne zarážce a před `Console.WriteLine` metody. **Automobily** zobrazuje hodnoty proměnných, které se používají kolem aktuálního řádku. **Místní hodnoty –** okno (které můžete zobrazit kliknutím **místní hodnoty –** kartě) zobrazuje hodnoty proměnných, které jsou definovány v metodě aktuálně spuštěné.

   ![Okno aplikace Visual Studio](./media/debugging-with-visual-studio/break.png)

1. Můžete změnit hodnotu proměnné, které chcete zjistit, jak ho ovlivní vašeho programu. Pokud **hodnot proměnných** nezobrazuje, zobrazit a vybrat **ladění** > **Windows** > **Immediate**položku nabídky. **Hodnot proměnných** umožňuje pracovat s aplikací, kterou ladíte.

1. Můžete interaktivně změnit hodnoty proměnných. Zadejte `name = "Gracie"` v **hodnot proměnných** a stiskněte klávesu Enter.

1. Zadejte `date = new DateTime(2016,11,01,11,59,00)` v **hodnot proměnných** a stiskněte klávesu Enter.

   **Hodnot proměnných** zobrazí hodnotu proměnné řetězce a vlastnosti <xref:System.DateTime> hodnotu. Kromě toho se aktualizuje hodnotu proměnné v **automobily** a **místní hodnoty –** systému windows.

   ![Automatické hodnoty – okno a příkazové podokno](./media/debugging-with-visual-studio/autosimmediate.png)

1. Pokračujte výběrem spuštění programu **pokračovat** tlačítka na panelu nástrojů nebo výběrem **ladění** > **pokračovat** položku nabídky. Hodnoty zobrazené v okně konzoly odpovídají změny provedené v **hodnot proměnných**.

   ![Okno konzoly zobrazující zadanou hodnotou konektoru na to, co je název vaší? řádek následovaný Hello Gracie 11/1/2016 v 11:59 am](./media/debugging-with-visual-studio/changed.png)

1. Stisknutím libovolné klávesy, chcete-li ukončit režim ladění aplikace a end.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. A *zarážek* dočasně přeruší provádění aplikace *před* řádek se zarážkou spustí. 

   Nastavte zarážky v řádku, který čte `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` kliknutím na levém okraji okna kódu na tomto řádku nebo výběrem **ladění** > **Přepnout zarážku** položky nabídky řádek Vybrat. Jak ukazuje následující obrázek, označuje Visual Studio na řádku, na kterém je nastaven breakpoint zvýraznění ho a zobrazením červené kolečko jeho levého okraje.

   ![Visual Studio Program okno sadou zarážek](./media/debugging-with-visual-studio/vb-setbreakpoint.png)

1. Spusťte program v režimu ladění výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů Stisknutím F5 nebo výběrem položky **ladění** > **spustit ladění**.

1. Zadejte řetězec v okně konzoly, když program vyzve k zadání názvu a stiskněte klávesu Enter.

1. Spuštění programu zastaví, když se dosáhne zarážce a před `Console.WriteLine` metody. **Automobily** zobrazuje hodnoty proměnných, které se používají kolem aktuálního řádku. **Místní hodnoty –** okno (které můžete zobrazit kliknutím **místní hodnoty –** kartě) zobrazuje hodnoty proměnných, které jsou definovány v metodě aktuálně spuštěné.

   ![Okno aplikace Visual Studio](./media/debugging-with-visual-studio/vb-break.png)

1. Můžete změnit hodnotu proměnné, které chcete zjistit, jak ho ovlivní vašeho programu. Pokud **hodnot proměnných** nezobrazuje, zobrazit a vybrat **ladění** > **Windows** > **Immediate**položku nabídky. **Hodnot proměnných** umožňuje pracovat s aplikací, kterou ladíte.

1. Můžete interaktivně změnit hodnoty proměnných. Zadejte `name = "Gracie"` v **hodnot proměnných** a stiskněte klávesu Enter.

1. Zadejte `currentDate = new DateTime(2016,11,01,11,59,00)` v **hodnot proměnných** a stiskněte klávesu Enter.

1. Pokračujte výběrem spuštění programu **pokračovat** tlačítka na panelu nástrojů nebo výběrem **ladění** > **pokračovat** položku nabídky. Hodnoty zobrazené v okně konzoly odpovídají změny provedené v **hodnot proměnných**.

   ![Okno konzoly zobrazující změněné hodnoty zadané v příkazové podokno](./media/debugging-with-visual-studio/changed.png)

1. Stisknutím libovolné klávesy, chcete-li ukončit režim ladění aplikace a end.
---

## <a name="setting-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Váš program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel není zadat nic? Toto můžete otestovat s ladění užitečná *podmíněného zarážek*, která zalomení programu spuštění, pokud jeden nebo více podmínek.

Pro nastavení podmíněné zarážky a testování, co se stane, když uživateli nepodaří zadejte řetězec, postupujte takto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Klikněte pravým tlačítkem myši na červenou tečku, který představuje bod přerušení. V místní nabídce vyberte **podmínky** otevřete **nastavení zarážek** dialogové okno. Zaškrtněte políčko pro **podmínky**.

   ![Panel nastavení zarážek](./media/debugging-with-visual-studio/breakpointsettings.png)

1. Pro **podmíněným výrazem** nahradit "například x == 5" s následující:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujete kód podmínku, který `String.IsNullOrEmpty(name)` volání metody, které je `true` buď protože *název* nemá přiřazenu hodnotu nebo proto, že jeho hodnota může být prázdný řetězec (""). Můžete také zadat *počet volání*, které přerušení spuštění programu před příkaz provést zadaného počtu opakování, nebo *podmínka filtru*, který přerušení program provádění například podle atributy jako identifikátor přístup z více vláken, název procesu nebo názvu vlákna.

1. Vyberte **zavřete** tlačítko zavřete dialogové okno.

1. Spusťte program v režimu ladění.

1. V okně konzoly stiskněte klávesu Enter po zobrazení výzvy zadejte své jméno.

1. Vzhledem k tomu, že jsme zadaná podmínka, `name` je buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, byly splněny, spuštění programu zastaví, když se dosáhne zarážce a před `Console.WriteLine` metody.

1. Vyberte **místní hodnoty –** okna, která zobrazuje hodnoty proměnných, které jsou místní vzhledem k aktuálně prováděné metoda, která je `Main` metoda v programu. Sledovat, která hodnota `name` proměnná `""`, nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte hodnota je prázdný řetězec zadáním následujícího příkazu v **hodnot proměnných**. Výsledkem je `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Vrací hodnotu true, po provedení příkazu příkazové podokno](./media/debugging-with-visual-studio/emptystring.png)

1. Vyberte **pokračovat** tlačítka na panelu nástrojů pro pokračování v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončení režimu ladění.

1. Zrušte zaškrtnutí zarážce kliknutím na tečky na levém okraji okna kódu nebo výběrem **ladění > Přepnout zarážku** položky nabídky řádek vybraný.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Klikněte pravým tlačítkem myši na červenou tečku, který představuje bod přerušení. V místní nabídce vyberte **podmínky** otevřete **nastavení zarážek** dialogové okno. Zaškrtněte políčko pro **podmínky**.

   ![Panel nastavení zarážek](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pro **podmíněným výrazem** nahradit "například x = 5" s následující:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujete kód podmínku, který `String.IsNullOrEmpty(name)` volání metody, které je `True` buď protože *název* nemá přiřazenu hodnotu nebo proto, že jeho hodnota může být prázdný řetězec (""). Můžete také zadat *počet volání*, které přerušení spuštění programu před příkaz provést zadaného počtu opakování, nebo *podmínka filtru*, který přerušení program provádění například podle atributy jako identifikátor přístup z více vláken, název procesu nebo názvu vlákna.

1. Vyberte **zavřete** tlačítko zavřete dialogové okno.

1. Spusťte program v režimu ladění.

1. V okně konzoly stiskněte klávesu Enter po zobrazení výzvy zadejte své jméno.

1. Vzhledem k tomu, že jsme zadaná podmínka, `name` je buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, byly splněny, spuštění programu zastaví, když se dosáhne zarážce a před `Console.WriteLine` metody.

1. Vyberte **místní hodnoty –** okna, která zobrazuje hodnoty proměnných, které jsou místní vzhledem k aktuálně prováděné metoda, která je `Main` metoda v programu. Sledovat, která hodnota `name` proměnná `""`, nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte hodnota je prázdný řetězec zadáním následujícího příkazu v **hodnot proměnných**. Výsledkem je `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Vrací hodnotu true, po provedení příkazu příkazové podokno](./media/debugging-with-visual-studio/vb-emptystring.png)

1. Vyberte **pokračovat** tlačítka na panelu nástrojů pro pokračování v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončení režimu ladění.

1. Zrušte zaškrtnutí zarážce kliknutím na tečky na levém okraji okna kódu nebo výběrem **ladění > Přepnout zarážku** položky nabídky řádek vybraný.
---
## <a name="stepping-through-a-program"></a>Procházení program

Visual Studio také umožňuje krok řádek po řádku prostřednictvím programu a monitorovat jeho spuštění. By normálně, nastavit zarážky a pomocí této funkce lze podle toku programu, když malou část kódu programu. Vzhledem k tomu, že váš program je malá, můžete krokovat úplný program následujícím způsobem:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Na řádku nabídek zvolte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio klade důraz a zobrazuje šipku vedle položky na další řádek provádění.

   ![Visual Studio – okno](./media/debugging-with-visual-studio/stepinto1.png)

   V tomto okamžiku **automobily** ukazuje, že váš program je definovaný jenom jednu proměnnou `args`. Protože žádných argumentů příkazového řádku nebyly předány programu, jeho hodnota může být pole prázdný řetězec. Kromě toho Visual Studio otevřel okna konzoly prázdné.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio teď klade důraz na další řádek provádění. Jak ukazuje obrázek, trvá méně než jeden milisekundu ke spouštění kódu vytvořeného mezi poslední příkaz a tato. `args` zůstane pouze deklarované proměnnou, a v okně konzoly zůstává prázdné.

   ![Visual Studio – okno](./media/debugging-with-visual-studio/stepinto2.png)

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio označuje příkaz, který obsahuje `name` přiřazení proměnné. **Automobily** okno ukazuje, že `name` je `null`, a v okně konzoly zobrazí řetězec "Jaký je název vaší?".

1. Odpověď na výzvu zadáte řetězec v okně konzoly a stisknutím klávesy Enter. Konzole je reagovat a zadáte řetězec nezobrazuje v okně konzoly ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda jasném zaznamená váš vstup.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio označuje příkaz, který obsahuje `date` (v jazyku C#) nebo `currentDate` (v jazyce Visual Basic) přiřazení proměnné. **Automobily** okno ukazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnoty vrácené volání <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda. V okně konzoly zobrazí také řetězec zadá, když konzole, budete vyzváni k zadání vstupu.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. **Automobily** v okně se zobrazí hodnota `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost. V okně konzoly se nezmění.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Volání sady Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metoda. Hodnoty `date` (nebo `currentDate`) a `name` proměnné se zobrazují v **automobily** okno a v okně konzoly zobrazí formátovaný řetězec.

1. Vyberte **ladění** > **Krokovat s Vystoupením** nebo stiskněte klávesu Shift a F11 klíč. To zastaví podrobné provádění. V okně konzoly zobrazí zprávu a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončení režimu ladění.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Na řádku nabídek zvolte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio klade důraz a zobrazuje šipku vedle položky na další řádek provádění.

   ![Visual Studio – okno](./media/debugging-with-visual-studio/vb-stepinto1.png)

   Na tento bod, protože nebyly předána žádných argumentů příkazového řádku programu, **automobily** okno ukazuje, že hodnota `args` proměnné je pole prázdný řetězec. Kromě toho Visual Studio otevřel okna konzoly prázdné.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio teď klade důraz na další řádek provádění. Jak ukazuje obrázek, trvá méně než jeden milisekundu ke spouštění kódu vytvořeného mezi poslední příkaz a tato. `args` zůstane pouze deklarované proměnnou, a v okně konzoly zůstává prázdné.

   ![Visual Studio – okno](./media/debugging-with-visual-studio/vb-stepinto2.png)

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio označuje příkaz, který obsahuje `name` přiřazení proměnné. **Automobily** okno ukazuje, že `name` je `Nothing`, a v okně konzoly zobrazí řetězec "Jaký je název vaší?".

1. Odpověď na výzvu zadáte řetězec v okně konzoly a stisknutím klávesy Enter. Konzole je reagovat a zadáte řetězec nezobrazuje v okně konzoly ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda jasném zaznamená váš vstup.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Visual Studio označuje příkaz, který obsahuje `date` (v jazyku C#) nebo `currentDate` (v jazyce Visual Basic) přiřazení proměnné. **Automobily** okno ukazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnoty vrácené volání <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda. V okně konzoly zobrazí také řetězec zadá, když konzole, budete vyzváni k zadání vstupu.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. **Automobily** v okně se zobrazí hodnota `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost. V okně konzoly se nezmění.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11. Volání sady Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metoda. Hodnoty `date` (nebo `currentDate`) a `name` proměnné se zobrazují v **automobily** okno a v okně konzoly zobrazí formátovaný řetězec.

1. Vyberte **ladění** > **Krokovat s Vystoupením** nebo stiskněte klávesu Shift a F11 klíč. To zastaví podrobné provádění. V okně konzoly zobrazí zprávu a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončení režimu ladění.
---

## <a name="building-a-release-version"></a>Vytváření prodejní verzi

Jakmile otestujete sestavení ladicí verze aplikace, musí také sestavit a otestovat prodejní verze. Prodejní verze zahrnuje kompilátoru optimalizace, které mohou někdy negativně ovlivnit chování aplikace. Optimalizace kompilátoru, které jsou určeny ke zlepšení výkonu můžete například vytvořit časování v asynchronní nebo vícevláknové aplikace.

Pro sestavení a otestování prodejní verze nástroje konzolové aplikace, změnit konfiguraci sestavení na panelu nástrojů z **ladění** k **verze**.

![Image](./media/debugging-with-visual-studio/toolbar2.png)

Když stisknutím klávesy F5 nebo zvolte **sestavit řešení** z **sestavení** nabídce sady Visual Studio zkompiluje prodejní verze nástroje konzolové aplikace. Jej můžete otestovat, jako jste to udělali ladicí verze aplikace.

Jakmile dokončíte ladění aplikace, dalším krokem je publikovat využít verzi vaší aplikace. Informace o tom, jak to udělat najdete v tématu [publikovat aplikace Hello World s Visual Studio 2017](./publishing-with-visual-studio.md).
