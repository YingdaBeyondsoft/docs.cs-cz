---
title: Navrhování kontraktů služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 163c551103a68ac320e482b1daa0a0c19b2b8fed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809924"
---
# <a name="designing-service-contracts"></a>Navrhování kontraktů služby
Toto téma popisuje, jaké služby měnící se, jak jsou definovány, jaké operace jsou k dispozici (a důsledky pro základní výměny zpráv), jaké typy dat jsou použité a další problémy, které vám pomůžou návrh operace, které odpovídají požadavky na vaše scénáře.  
  
## <a name="creating-a-service-contract"></a>Vytvoření kontraktu služby  
 Služby vystavit počet operací. V aplikacích Windows Communication Foundation (WCF), definujte operace vytváření metodu a označením pomocí <xref:System.ServiceModel.OperationContractAttribute> atribut. Potom k vytvoření kontraktu služby, seskupit vaše operace, buď deklarativně v rámci rozhraní označené pomocí <xref:System.ServiceModel.ServiceContractAttribute> atribut, nebo pomocí je definování v třídě s atributem stejné. (Základní příklad najdete v tématu [postupy: definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Všechny metody, které nemají <xref:System.ServiceModel.OperationContractAttribute> atribut nejsou operací služby a nejsou vystavené služby WCF.  
  
 Toto téma popisuje následující body rozhodnutí při navrhování kontraktu služby:  
  
-   Jestli se má použít třídy nebo rozhraní.  
  
-   Jak určit typy dat, které chcete exchange.  
  
-   Typů exchange vzorů, které můžete použít.  
  
-   Jestli můžete provést explicitní zabezpečení požadavky součástí kontraktu.  
  
-   Omezení pro operace vstupy a výstupy.  
  
## <a name="classes-or-interfaces"></a>Třídy nebo rozhraní  
 Třídy a rozhraní představují seskupení funkce, a proto i lze použít k definování kontraktu služby WCF. Doporučujeme však používat rozhraní, protože se přímo modelu kontraktů služby. Bez implementace rozhraní definovat více než seskupení metod s určitým podpisy. Implementovat rozhraní kontraktu služby a služby WCF byla implementována.  
  
 Všechny výhody spravovaná rozhraní platí pro rozhraní kontraktu služby:  
  
-   Rozhraní kontraktu služby můžete rozšířit libovolný počet dalších rozhraní kontraktu služby.  
  
-   Na jednu třídu můžete implementovat libovolný počet kontraktů služby implementací rozhraní kontraktu těchto služeb.  
  
-   Implementace kontraktu služby můžete upravit změnou implementaci rozhraní, zatímco kontrakt služby zůstává stejná.  
  
-   Verze můžete implementací rozhraní stará a nová služby. Původní klienti připojovat k původní verzi, zatímco novější klienti mohou připojit na novější verzi.  
  
> [!NOTE]
>  Když je zděděný z dalších rozhraní kontraktu služby, nejde přepsat vlastnosti operace, jako je název nebo obor názvů. Když zkusíte to udělat, vytvoříte nové operace v aktuální kontrakt služby.  
  
 Příklad použití rozhraní k vytvoření kontraktu služby, naleznete v části [postupy: vytvoření služby pomocí rozhraní kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Můžete však použití třídy a definování kontraktu služby ve stejnou dobu implementace tohoto kontraktu. Výhoda vytváření vašim službám použitím <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> přímo na třídy a metody pro třídu, v uvedeném pořadí, je rychlost a jednoduchost. Nevýhodou je, že spravované třídy nepodporují vícenásobná dědičnost a v důsledku jejich můžete implementovat pouze jeden kontrakt služby najednou. Kromě toho všechny změny podpisy třída nebo metoda upravuje veřejného kontraktu pro tuto službu, která klientům zabránit, beze změny pomocí služby. Další informace najdete v tématu [implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Příklad, který používá třídu k vytvoření kontraktu služby a implementuje ve stejnou dobu, naleznete v části [postupy: vytvoření služby s třídou kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 V tomto okamžiku byste měli porozumět rozdílu mezi definování vaší kontrakt služby s použitím rozhraní a pomocí třídy. Dalším krokem je rozhodnutí, jaké data mohou být předána přepínat mezi službou a jeho klienty.  
  
## <a name="parameters-and-return-values"></a>Parametry a návratové hodnoty  
 Každá operace má návratovou hodnotu a parametr, i když jsou tyto `void`. Ale na rozdíl od místní metodu, ve kterém můžete předat odkazy na objekty z jednoho objektu do druhého, operací služby nepředávejte odkazy na objekty. Místo toho předají kopie objektů.  
  
 To je důležité, protože používá parametr každý typ, nebo může vracet hodnota musí být serializovatelný; To znamená musí být možné převést objekt daného typu do datového proudu bajtů a z datového proudu bajtů do objektu.  
  
 Primitivní typy jsou serializovatelný ve výchozím nastavení, jako jsou mnoho typů v rozhraní .NET Framework.  
  
> [!NOTE]
>  Hodnota názvy parametrů v podpis operace jsou součástí kontraktu a velká a malá písmena. Pokud chcete použít stejný název parametru místně, ale název upravit v publikovaných metadat, najdete v článku <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Kontrakty dat  
 Aplikace orientované na služby, jako je aplikace Windows Communication Foundation (WCF) jsou navrženy pro spolupráci s co největší počet klientských aplikací v Microsoft i jiných společností než Microsoft platformy. Široké interoperability možné, se doporučuje, aby označíte vaší typů s <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy pro vytvoření kontraktu dat, což je část kontrakt služby, který popisuje data, vaše operací služby Exchange.  
  
 Kontrakty dat jsou výslovný souhlas styl kontrakty: žádný typ nebo data člen je serializováno, pokud použijete explicitně atribut kontraktu dat. Kontrakty dat se nevztahují k oboru přístupu spravovaného kódu: private členy můžete serializovat a odeslat jinde veřejně přístupná. (Například základní kontrakt dat najdete v části [postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF zpracovává definici základní protokolu SOAP zprávy, které operace funkci povolit, jakož i serializace datové typy do a z textu zprávy. Tak dlouho, dokud datové typy musejí být serializovatelná, není potřeba myslet podpůrné infrastruktuře exchange zpráva při navrhování vaše operace.  
  
 I když používá Typická aplikace WCF <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy pro vytvoření kontrakty dat pro operace, můžete použít jiné mechanismy serializace. Standardní <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.IXmlSerializable> mechanismy všechny fungují pro zpracování serializace datové typy do základní protokolu SOAP zprávy, které je přenos z jedné aplikace do jiné. Další strategie serializace můžete použít, pokud vaše datové typy vyžadují speciální podpory. Další informace o možnosti pro serializaci datových typů v aplikacích WCF najdete v tématu [zadání přenos dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapování parametry a návratové hodnoty na výměny zpráv  
 Operace služby jsou podporovány základní výměnou zpráv protokolu SOAP, které přenášejí data aplikací a zpět, kromě dat vyžaduje aplikaci, aby podporovala určité standardní zabezpečení, transakce a funkce související s relací. Protože to je případ, podpis operace služby stanoví určité základní *vzorce výměny zpráv* (MEP) podporující přenos dat a funkcím pro operace vyžaduje. Můžete zadat tří vzorů v programovací model WCF: požadavek nebo odpověď, jednosměrné a vzory duplexní zprávy.  
  
##### <a name="requestreply"></a>Požadavek nebo odpověď  
 Vzor požadavek nebo odpověď je jedním ve kterém žádost odesílatele (klientské aplikace) obdrží odpověď, pomocí kterého jsou korelována žádost. Toto je výchozí MEP, protože umožňuje operace, ve kterém jeden nebo více parametrů jsou předány operaci a návratovou hodnotu je předán zpět do volající. Například následující příklad kódu C# ukazuje operace základní služby, která přijímá jeden řetězec a vrátí řetězec.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Zde je ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Tato operace podpisu stanoví formu základní výměny zpráv. Pokud neexistovala žádná korelace WCF nemůže zjistit, kterou operaci je určené návratovou hodnotu.  
  
 Všimněte si, že pokud zadáte jiný základní vzor zprávy, dokonce i operace služby, které vracejí `void` (`Nothing` v jazyce Visual Basic) jsou požadavek nebo odpověď výměny zpráv. Výsledek pro vaši operaci je, že pokud klient asynchronně vyvolá operaci, klient se zastaví zpracovávání, dokud je přijatá návratový zpráva, i když je prázdná v případě, že normální zpráva. Následující příklad kódu C# ukazuje operaci, která nevrátí, dokud klient přijal prázdný zprávu v odpovědi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Zde je ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 V předchozím příkladu může zpomalit výkon klienta a kratší reakční doby, pokud trvá dlouhou dobu provést operaci, ale existují výhody požadavek nebo odpověď operace i když se vrátí `void`. Nejobvyklejší ten je, že chyb SOAP mohou být vráceny ve zprávě s odpovědí, který označuje, že došlo k nějaké chyby související se službou, v komunikaci nebo zpracování. SOAP chyb, které jsou určené v kontraktu služby se předávají do klientské aplikace jako <xref:System.ServiceModel.FaultException%601> objektu, kde parametr typu je typ zadaný v kontrakt služby. To usnadňuje oznamující klientů o chybové stavy v služby WCF. Další informace o výjimek, chyb protokolu SOAP a zpracování chyb najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Příkladem klienta a požadavek nebo odpověď služby najdete v sekci [postupy: vytvoření kontraktu požadavku a odpovědi](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Další informace o problémech s nástrojem vzoru požadavku a odpovědi najdete v tématu [služby požadavku a odpovědi](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednosměrné  
 Pokud klient aplikace služby WCF nesmí počkejte na dokončení operace a nezpracovává chyb SOAP, operaci můžete zadat vzor jednosměrný zprávy. Jednosměrná operace je jedním ve kterém klienta vyvolá operace a bude pokračovat zpracování poté, co WCF zapíše zpráva k síti. Obvykle to znamená, že pokud je velmi velkých dat odeslaných v odchozí zprávy klient pokračuje, téměř okamžité spuštění (Pokud dojde k chybě při odesílání dat). Tento typ vzorce výměny zpráv podporuje chování jako událost od klienta k aplikaci služby.  
  
 Výměna zpráv, ve kterém jeden zprávy a nejsou přijaty žádné nemůže podporovat operace služby určující návratovou hodnotu než `void`; v takovém případě <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
 Žádná zpráva návratový také znamená, že může být žádná chyba protokolu SOAP vrátil označíte, všechny chyby při zpracování nebo komunikace. (Informace o chybě komunikace, když operace jsou Jednosměrná operace vyžaduje vzorce výměny zpráv duplexní.)  
  
 Chcete-li určit jednosměrný zpráva systému exchange pro operaci, která vrátí `void`, nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost, která má `true`, jako v následujícím příkladu kódu C#.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Zde je ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Tato metoda je stejná jako předchozím příkladu požadavek nebo odpověď, ale nastavení <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true` znamená, že i když je stejný jako metodu, operace služby neodesílá návratové zprávy a klienti vrátí okamžitě jednou odchozí zprávy předání do vrstvy kanálu. Příklad, naleznete v části [postupy: vytvoření kontraktu One-Way](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Další informace o vzoru jednosměrný najdete v tématu [One-Way služby](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Duplexní vzor je charakterizovaná schopnost službu a klienta k odesílání zpráv do sebe navzájem nezávisle zda pomocí jednosměrné nebo požadavek nebo odpověď zasílání zpráv. Tato forma obousměrné komunikace je užitečná pro služby, které musí komunikovat přímo na klienta nebo pro zajištění asynchronní prostředí serveru exchange zprávu, včetně událostí jako chování obou stranách.  
  
 Duplexní vzor je trochu složitější než požadavek nebo odpověď nebo jednosměrný vzory z důvodu další mechanismus pro komunikaci s klientem.  
  
 K návrhu duplexního kontraktu, musíte také návrh kontraktu zpětného volání a přiřazení typu kontraktu zpětného volání k <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnost <xref:System.ServiceModel.ServiceContractAttribute> atribut, který označuje vaší kontrakt služby.  
  
 Implementovat duplexní vzor, je nutné vytvořit druhý rozhraní, které obsahuje deklarace metody, které se nazývají na straně klienta.  
  
 Příklad vytvoření služby a klienta, který přistupuje k této službě naleznete v části [postupy: vytvoření duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) a [postupy: přístup k službám pomocí duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Pracovní vzorek, najdete v části [duplexní](../../../docs/framework/wcf/samples/duplex.md). Další informace o problémech s použitím duplexní kontrakty najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Když služba přijme zprávu o duplexní, vypadá na `ReplyTo` element v této příchozí zprávy k určení místa k odeslání odpovědi. Pokud není zabezpečena kanálu, který se používá k přijetí zprávy, pak nedůvěryhodného klienta může odeslat škodlivý zprávu s cílový počítač `ReplyTo`, tečka na začátku k odepření služby (DOS) tento cílový počítač.  
  
##### <a name="out-and-ref-parameters"></a>Parametry Ref a Out  
 Ve většině případů můžete použít `in` parametry (`ByVal` v jazyce Visual Basic) a `out` a `ref` parametry (`ByRef` v jazyce Visual Basic). Protože obě `out` a `ref` parametry znamenat, že data jsou vrácena z operace, o operaci zápisu, například následující Určuje, že je požadavek nebo odpověď operace vyžaduje to i v případě, že operace podpis vrátí `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Zde je ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedinou výjimkou jsou případy, ve kterých vaše podpis má konkrétní strukturu. Například můžete použít <xref:System.ServiceModel.NetMsmqBinding> vazby ke komunikaci s klienty pouze v případě metodu použitou k deklarovat operace vrátí `void`; může existovat žádná hodnota výstupu toho, jestli je vrácená hodnota `ref`, nebo `out` parametr.  
  
 Kromě toho pomocí `out` nebo `ref` parametry vyžaduje, aby měl operaci základní zprávu odpovědi pro přenos zpět upravený objekt. Pokud tuto operaci je jednosměrná operace, <xref:System.InvalidOperationException> v době běhu je vyvolána výjimka.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Zadejte úroveň ochrany zprávy na kontraktu  
 Při navrhování vaší kontrakt, musíte se rovněž rozhodnout úroveň ochrany zprávy služeb, které implementují vaše smlouvy. To je nutné pouze v případě, že zabezpečení zpráv se použije pro vazbu v koncovém bodu této smlouvy. Pokud má vazbu zabezpečení je vypnuté. (to znamená, pokud se nastaví vazby poskytované systémem <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> na hodnotu <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) pak nemáte při rozhodování o úroveň ochrany zprávy pro kontrakt. Ve většině případů vazby poskytované systémem se zabezpečením na úrovni zpráv použijí poskytují dostatečnou úroveň ochrany a nemáte vzít v úvahu úroveň ochrany pro každou operaci, nebo pro každou zprávu.  
  
 Úroveň ochrany je hodnota, která určuje, zda zprávy (nebo části zprávy) podporující služby jsou podepsané, podepsané a šifrovaná nebo odeslán bez informace podpisy nebo šifrování. Úroveň ochrany lze nastavit v různých oborech: na úrovni služby, určité operace, zprávy v rámci této operace, nebo část zprávy. Hodnoty nastavené na jeden obor stát výchozí hodnota pro menší obory, pokud není explicitně přepsána. Konfigurace vazeb nemůže poskytovat úroveň ochrany vyžaduje minimální pro kontrakt, je vyvolána výjimka. A pokud žádné hodnoty pro úroveň ochrany jsou explicitně nastavená na kontrakt, konfigurace vazeb řídí úroveň ochrany pro všechny zprávy, pokud má vazby zabezpečení zpráv. Toto je výchozí chování.  
  
> [!IMPORTANT]
>  Rozhodnutí, jestli se explicitně nastavit různé obory kontraktu, na méně než úroveň plná ochrana <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> je obecně rozhodnutí, která obchoduje určitý stupeň zabezpečení pro zvýšení výkonu. V těchto případech musí svoje rozhodnutí o základem vaše operace a hodnoty dat, která si vyměňují. Další informace najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md).  
  
 Například následující příklad kódu nenastaví buď <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> nebo <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> vlastnost kontrakt.  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();    
}  
```  
  
 Zde je ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Při interakci s `ISampleService` implementace v koncový bod s výchozí <xref:System.ServiceModel.WSHttpBinding> (výchozí hodnota <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, což je <xref:System.ServiceModel.SecurityMode.Message>), všechny zprávy jsou šifrovaný a podepsaný, protože to je výchozí úroveň ochrany. Ale když `ISampleService` služba se používá výchozí hodnota je <xref:System.ServiceModel.BasicHttpBinding> (výchozí <xref:System.ServiceModel.SecurityMode>, což je <xref:System.ServiceModel.SecurityMode.None>), všechny zprávy jsou odesílány jako text, protože neexistuje žádné zabezpečení pro tuto vazbu, a proto je ignorován úroveň ochrany (to znamená, zprávy jsou šifrované ani podepsané). Pokud <xref:System.ServiceModel.SecurityMode> byl změněn na <xref:System.ServiceModel.SecurityMode.Message>, pak tyto zprávy by být šifrovaný a podepsaný (vzhledem k tomu, který by vazby výchozí úroveň ochrany).  
  
 Pokud chcete explicitně zadat nebo upravit požadavky na ochranu pro vaše smlouvy, nastavte <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost (nebo `ProtectionLevel` vlastnosti v menší oboru) na úroveň vyžaduje vaše kontrakt služby. V takovém případě pomocí explicitní nastavení vyžaduje, aby připojení pro podporu tohoto nastavení minimálně pro obor použít. Například následující příklad kódu určuje jeden <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> hodnotu explicitně, pro `GetGuid` operaci.  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();    
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();    
}  
```  
  
 Zde je ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<ServiceContract()> _   
Public Interface IExplicitProtectionLevelSampleService   
    <OperationContract()> _   
    Public Function GetString() As String   
    End Function   
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _   
    Public Function GetInt() As Integer   
    End Function   
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _   
    Public Function GetGuid() As Integer   
    End Function   
  
End Interface  
```  
  
 Služba, která implementuje to `IExplicitProtectionLevelSampleService` smlouvy a má koncový bod, který používá výchozí <xref:System.ServiceModel.WSHttpBinding> (výchozí hodnota <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, což je <xref:System.ServiceModel.SecurityMode.Message>) má následující chování:  
  
-   `GetString` Operace zprávy jsou šifrovaný a podepsaný.  
  
-   `GetInt` Operace zprávy jsou zasílány jako nešifrovaný a bez znaménka (tj, plain) text.  
  
-   `GetGuid` Operace <xref:System.Guid?displayProperty=nameWithType> je vrácený v zprávu, která je šifrovaný a podepsaný.  
  
 Další informace o úrovních ochrany a jejich použití najdete v tématu [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md). Další informace o zabezpečení najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Další požadavky operace podpisu  
 Některé funkce aplikace vyžadují konkrétní typ operace podpisu. Například <xref:System.ServiceModel.NetMsmqBinding> vazba podporuje trvanlivý služeb a klientů, ve kterých můžete aplikaci restartujte uprostřed komunikace a pokračovat tam, kde bylo přerušeno bez chybí všechny zprávy. (Další informace najdete v tématu [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) Trvanlivý operace však vyžaduje pouze jeden `in` parametr a mít žádnou návratovou hodnotu.  
  
 Dalším příkladem je použití <xref:System.IO.Stream> typů v operacích. Protože <xref:System.IO.Stream> parametr obsahuje obsah celé zprávy, pokud vstup nebo výstup (to znamená, `ref` parametr `out` parametr nebo vrací hodnotu) je typu <xref:System.IO.Stream>, pak musí být pouze vstupu nebo výstupu, zadané v vaší operace. Kromě toho parametr nebo návratový typ musí být buď <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, nebo <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Další informace o datových proudů najdete v tématu [velkého množství dat a Streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Názvy oborů názvů a maskováním  
 Názvy a obory názvů .NET typů v definici kontrakty a operace jsou důležitá, když kontrakty se převedou na WSDL a když se vytváří a odesílají zprávy kontrakt. Proto důrazně doporučujeme, aby názvy kontraktu služby a obory názvů jsou explicitně nastavit pomocí `Name` a `Namespace` vlastnosti všech podporu smlouvy atributy, jako <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>a další atributy kontrakt.  
  
 Jeden důsledkem je, že pokud nejsou explicitně nastavit názvy a obory názvů, použití IL maskováním na sestavení mění názvy typů kontraktu a obory názvů a má za následek změny schématu WSDL a výměny přenosu, které obvykle nezdaří. Pokud nenastavíte názvy kontraktu a obory názvů explicitně ale chcete použít maskováním, použijte <xref:System.Reflection.ObfuscationAttribute> a <xref:System.Reflection.ObfuscateAssemblyAttribute> atributy, aby se zabránilo změně kontrakt zadejte názvy a obory názvů.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření kontraktu žádosti a odpovědi](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)  
 [Postupy: Vytvoření jednosměrného kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)  
 [Postupy: Vytvoření duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Určování přenosu dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Použití relací](../../../docs/framework/wcf/using-sessions.md)  
 [Synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [Spolehlivé služby](../../../docs/framework/wcf/reliable-services.md)  
 [Služby a transakce](../../../docs/framework/wcf/services-and-transactions.md)
