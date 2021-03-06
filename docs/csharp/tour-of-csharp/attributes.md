---
title: C# atributy - přehled používání jazyka C#
description: Další informace o deklarativní programování pomocí atributů v jazyce C#
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 671023f268ae78d63db8868ef6046b8f13880659
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
ms.locfileid: "34312232"
---
# <a name="attributes"></a>Atributy

Typy, členů a ostatní entity v programu v C# podporovat modifikátory, které řídí některé aspekty jejich chování. Například usnadnění metody je řízena pomocí `public`, `protected`, `internal`, a `private` modifikátory. C# umožňuje zobecnit této funkci tak, aby uživatelem definované typy deklarativní informací lze připojit k programu entity a načítat za běhu. Programy zadejte tyto informace další deklarativní definice a používání ***atributy***.

Následující příklad deklaruje `HelpAttribute` atribut, který je možné použít u entity program poskytnout odkazy na jejich související dokumentaci.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Všechny třídy atributů odvozena od <xref:System.Attribute> základní třída poskytuje standardní knihovny. Tím, že jejich jména, společně s všechny argumenty uvnitř hranaté závorky těsně před přidružené deklaraci, můžete použít atributů. Pokud název atributu končí na `Attribute`, tuto část názvu lze vynechat, když je atribut. Například `HelpAttribute` je možné následujícím způsobem.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Tento příklad se připojí `HelpAttribute` k `Widget` třídy. Přidá další `HelpAttribute` k `Display` metodu v třídě. Veřejné konstruktory atribut třídy řídit informace, které je třeba zadat při atribut je připojen k programu entity. Další informace se dá zajistit pod položkou veřejné vlastnosti třídy atributů pro čtení a zápis (například odkaz na `Topic` vlastnost dříve).

Vyžádání konkrétní atribut prostřednictvím reflexe v konstruktoru pro třídy atributů vyvolání informací uvedených v programu zdroj a se vrátí výsledný instance atributu. Pokud Další informace se poskytovaly prostřednictvím vlastnosti, tyto vlastnosti jsou nastaveny na dané hodnoty před vrácením instance atributu.

>[!div class="step-by-step"]
[Předchozí](delegates.md)
