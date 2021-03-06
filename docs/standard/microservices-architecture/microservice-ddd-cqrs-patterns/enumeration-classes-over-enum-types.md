---
title: Pomocí třídy výčtu místo typy výčtu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí třídy výčtu místo typy výčtu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 1b2569caa7e7a6a899a6765d2e39d0fff8e37e2f
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251191"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Pomocí třídy výčtu místo typy výčtu

[Výčty](../../../../docs/csharp/language-reference/keywords/enum.md) (nebo *typy výčtu* pro zkrácení) jsou dynamické jazyk obálku kolem integrální typu. Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot. Klasifikace podle velikosti (malé, střední, velký) je dobrým příkladem. Pomocí výčty pro tok řízení nebo robustnější abstrakce může být [code pach](http://deviq.com/code-smells/). Tento typ využití vede k křehké kód s mnoha příkazy toku řízení kontrola hodnoty výčtového typu.

Místo toho můžete vytvořit výčet tříd, které povolit všechny bohaté funkce jazyka objektově orientovaný.

Ale to není důležité téma a v mnoha případech pro jednoduchost, můžete pořád použít regular [typy výčtu](../../../../docs/csharp/language-reference/keywords/enum.md) , pokud vaši volbu.

## <a name="implementing-an-enumeration-base-class"></a>Implementace základní třídu – výčet

Řazení mikroslužbu v eShopOnContainers poskytuje implementaci základní třída výčtu ukázka, jak je znázorněno v následujícím příkladu:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

Tuto třídu můžete použít jako typ v žádné entity nebo hodnota objektu jako následující CardType výčet tříd:

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }

    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a>Další zdroje

-   **Na výčtu jsou evil – aktualizace**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **ADAM Hardman. Jak výčty šíří nákazy – A jak ho Vytvrdit**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Třídy – výčet**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Výčet alternativy v jazyce C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Základní třída výčet v eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Ukázka třídy výčet v eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Předchozí] (implementace – hodnota objects.md) [Další] (domain modelu layer-validations.md)
