---
title: Kopírování existující uzly z jednoho dokumentu do jiného
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca36ffdd2eb5eb3acfbacbd543eebf17cfffb5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573923"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Kopírování existující uzly z jednoho dokumentu do jiného
**ImportNode** metoda je mechanismus, pomocí kterého uzel nebo celý uzlu podstrom se zkopíruje z jednoho **třídou XMLDocument nastavenou na** do jiného. Uzel vrácená z volání je kopii uzlu ze zdrojového dokumentu, včetně hodnot atributů, je název uzlu, typ uzlu a všechny atributy o oboru názvů jako je například předpona, místní názvem a oborem názvů identifikátor URI (Uniform Resource). Zdrojový dokument se nezmění. Po naimportování uzlu, máte ho přidat do stromu pomocí jedné z metody použité k vložení uzlů.  
  
 Pokud uzel je připojen k jeho nový dokument, nový dokument vlastní uzlu. Z důvodu je, že má každý uzel, při vytváření dokument vlastnícím i v případě, že uzly jsou vytvořeny v samostatné dokumentu fragmenty. Toto je požadavek z XML modelu DOM (Document Object) a vynucování záměrné vytvoření objektu pro vytváření na **třídou XMLDocument nastavenou na** třídy. Například **CreateElement**, je jediným způsobem, jak vytvořit nové uzly.  
  
 V závislosti na typu uzlu importované uzlu a hodnota *hloubkové* parametr, další informace se zkopíruje podle potřeby. Tato metoda se pokusí zrcadlení chování očekáváno, pokud fragment XML nebo zdroji HTML byl zkopírován z jednoho dokumentu do jiné, monitorování účtů pro fakt, že pro formát XML, může mít dva dokumenty definice typu jiného dokumentu (specifikace DTD).  
  
 Následující tabulka popisuje konkrétní chování pro každý typ uzlu, který lze importovat.  
  
|Typ uzlu|*hloubkové* parametr je true|*hloubkové* parametr je hodnota false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> Je nastaven na **true** na XmlAttribute. Následníky zdroj **XmlAttribute** jsou rekurzivně importovat a výsledný uzly znovu sestaveny na formuláři odpovídající podstrom.|*Hloubkové* parametr nelze použít u **XmlAttribute** uzly, proto, že vždy provádějí jejich podřízené uzly s nimi při importu.|  
|XmlCDataSection|Zkopíruje uzlu, včetně jeho data.|Zkopíruje uzlu, včetně jeho data.|  
|XmlComment|Zkopíruje uzlu, včetně jeho data.|Zkopíruje uzlu, včetně jeho data.|  
|XmlDocumentFragment|Následníky zdrojový uzel jsou rekurzivně importovat a výsledný uzly znovu sestaveny na formuláři odpovídající podstrom.|Prázdná **XmlDocumentFragment** je vytvořena.|  
|XmlDocumentType|Zkopíruje uzlu, včetně jeho data.*|Zkopíruje uzlu, včetně jeho data.*|  
|XmlElement.|Následníky elementu zdroje jsou rekurzivně importovat a výsledný uzly znovu sestaveny na formuláři odpovídající podstrom. **Poznámka:** výchozí atributy zkopírován. Pokud dokument importována do definuje výchozí atributy pro tento název elementu, těch, které jsou přiřazeny.|Zadaný atribut uzly source element importují a vygenerovaného **XmlAttribute** uzly jsou připojené k nového elementu. Nebudou zkopírovány podřízených uzlů. **Poznámka:** výchozí atributy zkopírován. Pokud dokument importována do definuje výchozí atributy pro tento název elementu, těch, které jsou přiřazeny.|  
|XmlEntityReference|Vzhledem k tomu, že zdrojový a cílový dokumenty může mít entit definované odlišně, tato metoda zkopíruje jen **XmlEntityReference** uzlu. Text, kterým není součástí. Jestli má dokument cílové entity definované, jeho hodnota je přiřazena.|Vzhledem k tomu, že zdrojový a cílový dokumenty může mít entit definované odlišně, tato metoda zkopíruje jen **XmlEntityReference** uzlu. Text, kterým není součástí. Jestli má dokument cílové entity definované, jeho hodnota je přiřazena.|  
|XmlProcessingInstruction|Zkopíruje hodnota cíle a data z importovaných uzlu.|Zkopíruje hodnota cíle a data z importovaných uzlu.|  
|XmlText|Zkopíruje uzlu, včetně jeho data.|Zkopíruje uzlu, včetně jeho data.|  
|XmlSignificantWhitespace|Zkopíruje uzlu, včetně jeho data.|Zkopíruje uzlu, včetně jeho data.|  
|XmlWhitespace|Zkopíruje uzlu, včetně jeho data.|Zkopíruje uzlu, včetně jeho data.|  
|XmlDeclaration|Zkopíruje hodnota cíle a data z importovaných uzlu.|Zkopíruje hodnota cíle a data z importovaných uzlu.|  
|Všechny ostatní typy uzlu|Nelze importovat, tyto typy uzlů.|Nelze importovat, tyto typy uzlů.|  
  
> [!NOTE]
>  I když DocumentType uzly lze importovat, dokument může mít pouze jeden DocumentType. Ano Jakmile před vložením do stromu, budete muset Ujistěte se, že jste importovali typu dokumentu, neexistuje žádný typ dokumentu v dokumentu. Informace o odebrání uzlů najdete v tématu [odebrání uzlů, obsah a hodnoty z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
