---
title: x:XData – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 3a16379fd6104342529723bf6d0bc9fb4762cf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565360"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData – vnitřní typ jazyka XAML
Umožňuje umístění XML datové ostrůvky v produkční XAML. Elementy XML v rámci `x:XData` by neměla být zpracována XAML procesorů, jako by byly součástí výchozí funguje oboru názvů jazyka XAML nebo jakékoli jiné oboru názvů jazyka XAML. `x:XData` může obsahovat libovolný ve správném formátu XML.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`elementDataRoot`|Jeden kořenový element island závorkách data. Pro většinu případné příjemci považuje za neplatný kód XML, který nemá jeden kořenový. Konkrétně je jeden kořenový povinný, pokud `x:XData` slouží jako zdroj dat XML pro WPF nebo mnoha jiných technologií, využívající zdroje XML pro datovou vazbu.|  
|`[elementData]`|Volitelné. Soubor XML, který představuje XML data. Jako datový element může obsahovat libovolný počet elementů a vnořených elementů může obsahovat další prvky; Obecná pravidla XML však použít.|  
  
## <a name="remarks"></a>Poznámky  
 Elementy XML v rámci `x:XData` objekt lze znovu deklarovat všechny možné obory názvů a předpony obsahující XMLDOM v rámci data.  
  
 Programový přístup k datům XML a `x:XData` vnitřní typ jazyka XAML je možné v rozhraní .NET Framework XAML Services prostřednictvím <xref:System.Windows.Markup.XData> třídy.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 `x:XData` Objekt primárně slouží jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider>, nebo případně jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> vlastnost (v jazyce XAML, to je obvykle vyjádřena v syntaxi element vlastnost).  
  
 Data by měl obvykle znovu definovat základní obor názvů XML v rámci island data jako novou výchozí obor názvů XML (nastavit na prázdný řetězec). Toto je nejjednodušší pro jednoduché datové ostrovy, protože <xref:System.Windows.Data.Binding.XPath%2A> výrazy, které se používají k odkazu a vytvoření vazby na data se můžete vyhnout zahrnutí předpony. Komplexnější datové ostrůvky může definovat více předpon pro data a používat konkrétní předponu pro obor názvů XML v kořenovém adresáři. V takovém případě všechny <xref:System.Windows.Data.Binding.XPath%2A> výraz odkazy by měla obsahovat předponu odpovídající mapované na obor názvů. Další informace najdete v tématu [přehled vazby dat](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Technicky `x:XData` lze použít jako obsah žádnou vlastnost typu <xref:System.Xml.Serialization.IXmlSerializable>. Ale <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> je pouze viditelného implementace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Přehled datových vazeb](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rozšíření značek datové vazby](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
