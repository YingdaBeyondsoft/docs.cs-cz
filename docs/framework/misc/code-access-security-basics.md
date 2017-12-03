---
title: "Základy zabezpečení přístupu kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08ce62f54e70fe1650914060ade0f52357f8a736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="code-access-security-basics"></a><span data-ttu-id="7b7d9-102">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-102">Code Access Security Basics</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="7b7d9-103">Každá aplikace, která cílí modul common language runtime (to znamená, každá spravované aplikace) musí spolupracovat s modulem runtime zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-103">Every application that targets the common language runtime (that is, every managed application) must interact with the runtime's security system.</span></span> <span data-ttu-id="7b7d9-104">Pokud spravované aplikace je načtena, jeho hostitel je automaticky přidělí sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-104">When a managed application is loaded, its host automatically grants it a set of permissions.</span></span> <span data-ttu-id="7b7d9-105">Tato oprávnění jsou určena pomocí nastavení zabezpečení hostitele nebo pomocí izolovaného prostoru, které je aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-105">These permissions are determined by the host's local security settings or by the sandbox the application is in.</span></span> <span data-ttu-id="7b7d9-106">V závislosti na tato oprávnění aplikace buď běží správně, nebo vygeneruje výjimka zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-106">Depending on these permissions, the application either runs properly or generates a security exception.</span></span>  
  
 <span data-ttu-id="7b7d9-107">Výchozího hostitele pro aplikací klasické pracovní plochy umožňuje kód pro spuštění v režimu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-107">The default host for desktop applications allows code to run in full trust.</span></span> <span data-ttu-id="7b7d9-108">Proto pokud aplikace cílí na plochu, má neomezený oprávnění nastavená.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-108">Therefore, if your application targets the desktop, it has an unrestricted permission set.</span></span> <span data-ttu-id="7b7d9-109">Jiným hostitelům nebo izolovaných prostorů poskytují omezené oprávnění nastavená pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-109">Other hosts or sandboxes provide a limited permission set for applications.</span></span> <span data-ttu-id="7b7d9-110">Protože sadu oprávnění, můžete změnit mezi hostiteli, je třeba navrhnout vaše aplikace používat jenom oprávnění, která umožňuje cílového hostitele.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-110">Because the permission set can change from host to host, you must design your application to use only the permissions that your target host allows.</span></span>  
  
 <span data-ttu-id="7b7d9-111">Musíte být obeznámeni s následující koncepty zabezpečení přístupu kódu k psaní aplikací efektivní cílených modul common language runtime:</span><span class="sxs-lookup"><span data-stu-id="7b7d9-111">You must be familiar with the following code access security concepts in order to write effective applications that target the common language runtime:</span></span>  
  
-   <span data-ttu-id="7b7d9-112">**Typově bezpečný kód**: bezpečnost typů kód je kód, který přistupuje k typům pouze způsoby dobře definovaný, povolená.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-112">**Type-safe code**: Type-safe code is code that accesses types only in well-defined, allowable ways.</span></span> <span data-ttu-id="7b7d9-113">Třeba platný objekt odkazu na daný, bezpečnost typů kódu můžete získat přístup k paměti na pevné pozici, které odpovídají skutečným pole členů.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-113">For example, given a valid object reference, type-safe code can access memory at fixed offsets that correspond to actual field members.</span></span> <span data-ttu-id="7b7d9-114">Pokud kód přistupuje k paměťově na libovolné pozici mimo rozsah paměti, která patří do tohoto objektu veřejně zveřejněné pole, není bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-114">If the code accesses memory at arbitrary offsets outside the range of memory that belongs to that object's publicly exposed fields, it is not type-safe.</span></span> <span data-ttu-id="7b7d9-115">Chcete-li kód, abyste mohli využívat výhod zabezpečení přístupu kódu, je nutné použít kompilátoru, která generuje typ ověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-115">To enable code to benefit from code access security, you must use a compiler that generates verifiably type-safe code.</span></span> <span data-ttu-id="7b7d9-116">Další informace najdete v tématu [psaní zajišťující bezpečnost bezpečnost typů kódu](#typesafe_code) později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-116">For more information, see the [Writing Verifiably Type-Safe Code](#typesafe_code) section later in this topic.</span></span>  
  
-   <span data-ttu-id="7b7d9-117">**Imperativní a deklarativní syntaxe**: kód, který je cílem modul common language runtime mohou komunikovat se systémem zabezpečení pomocí vyžadování oprávnění náročné, zda volající zadali oprávnění a přepsání určité (nastavení zabezpečení zadané dostatečná oprávnění).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-117">**Imperative and declarative syntax**: Code that targets the common language runtime can interact with the security system by requesting permissions, demanding that callers have specified permissions, and overriding certain security settings (given enough privileges).</span></span> <span data-ttu-id="7b7d9-118">Používat dvě formy syntaxe prostřednictvím kódu programu interakci se systémem zabezpečení rozhraní .NET Framework: deklarativní nebo imperativní syntaxi.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-118">You use two forms of syntax to programmatically interact with the .NET Framework security system: declarative syntax and imperative syntax.</span></span> <span data-ttu-id="7b7d9-119">Deklarativní volání jsou prováděna pomocí atributů imperativní volání jsou prováděna pomocí nové instance tříd v rámci vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-119">Declarative calls are performed using attributes; imperative calls are performed using new instances of classes within your code.</span></span> <span data-ttu-id="7b7d9-120">Některá volání lze provést pouze imperativní, jiné mohou být provedeny pouze deklarativně a některá volání lze provést buď způsobem.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-120">Some calls can be performed only imperatively, others can be performed only declaratively, and some calls can be performed in either manner.</span></span>  
  
-   <span data-ttu-id="7b7d9-121">**Zabezpečené knihovny tříd**: zabezpečené knihovny tříd používá k zajištění, že volající knihovny mají oprávnění pro přístup k prostředkům, které knihovna poskytuje požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-121">**Secure class libraries**: A secure class library uses security demands to ensure that the library's callers have permission to access the resources that the library exposes.</span></span> <span data-ttu-id="7b7d9-122">Zabezpečené knihovny tříd může mít například metodu pro vytvoření souborů, které by požadovat, aby její volající měli oprávnění k vytvoření souborů.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-122">For example, a secure class library might have a method for creating files that would demand that its callers have permissions to create files.</span></span> <span data-ttu-id="7b7d9-123">Rozhraní .NET Framework se skládá z zabezpečené knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-123">The .NET Framework consists of secure class libraries.</span></span> <span data-ttu-id="7b7d9-124">Byste měli znát oprávnění požadovaná pro přístup k žádné knihovny, která používá váš kód.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-124">You should be aware of the permissions required to access any library that your code uses.</span></span> <span data-ttu-id="7b7d9-125">Další informace najdete v tématu [pomocí knihovny tříd zabezpečení](#secure_library) později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-125">For more information, see the [Using Secure Class Libraries](#secure_library) section later in this topic.</span></span>  
  
-   <span data-ttu-id="7b7d9-126">**Kód transparentní pro**: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kromě identifikace konkrétních oprávnění musí také zjistíte, zda váš kód se má spustit jako transparentní pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-126">**Transparent code**: Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], in addition to identifying specific permissions, you must also determine whether your code should run as security-transparent.</span></span> <span data-ttu-id="7b7d9-127">Kód transparentní pro zabezpečení nelze volat typy nebo členy, kteří jsou identifikovány jako kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-127">Security-transparent code cannot call types or members that are identified as security-critical.</span></span> <span data-ttu-id="7b7d9-128">Toto pravidlo se vztahuje na plně důvěryhodné aplikace a také částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-128">This rule applies to full-trust applications as well as partially trusted applications.</span></span> <span data-ttu-id="7b7d9-129">Další informace najdete v tématu [kód transparentní pro zabezpečení](../../../docs/framework/misc/security-transparent-code.md).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-129">For more information, see [Security-Transparent Code](../../../docs/framework/misc/security-transparent-code.md).</span></span>  
  
<a name="typesafe_code"></a>   
## <a name="writing-verifiably-type-safe-code"></a><span data-ttu-id="7b7d9-130">Zápis typ ověřitelný kód</span><span class="sxs-lookup"><span data-stu-id="7b7d9-130">Writing Verifiably Type-Safe Code</span></span>  
 <span data-ttu-id="7b7d9-131">Kompilace za běhu (JIT) provede ověření procesu, který kontroluje kód a pokusí se zjistit, zda kód je bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-131">Just-in-time (JIT) compilation performs a verification process that examines code and tries to determine whether the code is type-safe.</span></span> <span data-ttu-id="7b7d9-132">Kód, který je ověřené během ověření zajistit bezpečnost typů se nazývá *typ ověřitelný kód s*.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-132">Code that is proven during verification to be type-safe is called *verifiably type-safe code*.</span></span> <span data-ttu-id="7b7d9-133">Kód může být bezpečnost typů, ještě nemusí být typ ověřitelný z důvodu omezení proces ověření nebo kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-133">Code can be type-safe, yet might not be verifiably type-safe because of the limitations of the verification process or of the compiler.</span></span> <span data-ttu-id="7b7d9-134">Ne všechny jazyky jsou jazyky bezpečnost typů a některé kompilátory jazyka, jako je například Microsoft Visual C++, nelze vygenerovat typ ověřitelný spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-134">Not all languages are type-safe, and some language compilers, such as Microsoft Visual C++, cannot generate verifiably type-safe managed code.</span></span> <span data-ttu-id="7b7d9-135">Pokud chcete zjistit, jestli kompilátor jazyka, který používáte generuje typ ověřitelný kód, projděte si dokumentaci k kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-135">To determine whether the language compiler you use generates verifiably type-safe code, consult the compiler's documentation.</span></span> <span data-ttu-id="7b7d9-136">Pokud používáte kompilátor jazyka, který generuje typ ověřitelný kód jenom v případě, že se vyhnout určité jazykové konstrukty, můžete chtít použít [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md) k určení, zda kód je typ ověřitelný.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-136">If you use a language compiler that generates verifiably type-safe code only when you avoid certain language constructs, you might want to use the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md) to determine whether your code is verifiably type-safe.</span></span>  
  
 <span data-ttu-id="7b7d9-137">Kód, který není typu ověřitelný pokuste se spustit, pokud zásady zabezpečení umožňuje obejít ověření kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-137">Code that is not verifiably type-safe can attempt to execute if security policy allows the code to bypass verification.</span></span> <span data-ttu-id="7b7d9-138">Ale protože typ zabezpečení je nedílnou součást vámi vyžádaných mechanismus modulu runtime pro uzavírací sestavení, zabezpečení nelze spolehlivě vynutit, pokud kód porušuje pravidla zabezpečení typů.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-138">However, because type safety is an essential part of the runtime's mechanism for isolating assemblies, security cannot be reliably enforced if code violates the rules of type safety.</span></span> <span data-ttu-id="7b7d9-139">Ve výchozím nastavení je kód, který není bezpečný povoleno spustit pouze v případě, že pochází z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-139">By default, code that is not type-safe is allowed to run only if it originates from the local computer.</span></span> <span data-ttu-id="7b7d9-140">Proto mobilní kód by měl být bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-140">Therefore, mobile code should be type-safe.</span></span>  
  
<a name="secure_library"></a>   
## <a name="using-secure-class-libraries"></a><span data-ttu-id="7b7d9-141">Pomocí zabezpečené knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="7b7d9-141">Using Secure Class Libraries</span></span>  
 <span data-ttu-id="7b7d9-142">Pokud váš kód požadavky a je udělena oprávnění potřebná knihovna tříd, bude mít přístup do knihovny a prostředky, které zpřístupňuje knihovny bude chráněn před neoprávněným přístupem.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-142">If your code requests and is granted the permissions required by the class library, it will be allowed to access the library and the resources that the library exposes will be protected from unauthorized access.</span></span> <span data-ttu-id="7b7d9-143">Pokud váš kód nemá příslušná oprávnění, nebude mít přístup knihovny tříd k a škodlivý kód nebude možné použít kód nepřímý přístup k chráněným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-143">If your code does not have the appropriate permissions, it will not be allowed to access the class library, and malicious code will not be able to use your code to indirectly access protected resources.</span></span> <span data-ttu-id="7b7d9-144">Jiný kód, který volá kód musí také mít oprávnění k přístupu ke knihovně.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-144">Other code that calls your code must also have permission to access the library.</span></span> <span data-ttu-id="7b7d9-145">Pokud není, bude omezeno spuštěn rovněž vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-145">If it does not, your code will be restricted from running as well.</span></span>  
  
 <span data-ttu-id="7b7d9-146">Zabezpečení přístupu kódu nebude odstraněn možnost lidské chyby při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-146">Code access security does not eliminate the possibility of human error in writing code.</span></span> <span data-ttu-id="7b7d9-147">Ale pokud vaše aplikace používá knihovny tříd zabezpečený přístup k chráněným prostředkům, bezpečnostní riziko pro kód aplikace je zmenšit, protože knihovny tříd jsou podrobně zkoumány na potenciální problémy se zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-147">However, if your application uses secure class libraries to access protected resources, the security risk for application code is decreased, because class libraries are closely scrutinized for potential security problems.</span></span>  
  
## <a name="declarative-security"></a><span data-ttu-id="7b7d9-148">Deklarativní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7b7d9-148">Declarative Security</span></span>  
 <span data-ttu-id="7b7d9-149">Syntaxe deklarativní zabezpečení využívá [atributy](../../../docs/standard/attributes/index.md) umístit informace o zabezpečení do [metadata](../../../docs/standard/metadata-and-self-describing-components.md) z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-149">Declarative security syntax uses [attributes](../../../docs/standard/attributes/index.md) to place security information into the [metadata](../../../docs/standard/metadata-and-self-describing-components.md) of your code.</span></span> <span data-ttu-id="7b7d9-150">Atributy mohou být umístěny na úrovni sestavení, třída nebo člen označující typ požadavku, vyžádání nebo přepsání, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-150">Attributes can be placed at the assembly, class, or member level, to indicate the type of request, demand, or override you want to use.</span></span> <span data-ttu-id="7b7d9-151">Požadavky se používají v aplikacích, které cílí modul common language runtime k informování o oprávnění, které aplikace potřebuje nebo nechce systémem zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-151">Requests are used in applications that target the common language runtime to inform the runtime security system about the permissions that your application needs or does not want.</span></span> <span data-ttu-id="7b7d9-152">Požadavky a přepsání se používají v knihovnách pomáhá chránit prostředky z volající nebo přepsat výchozí chování zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-152">Demands and overrides are used in libraries to help protect resources from callers or to override default security behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b7d9-153">V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly důležité změny modelu zabezpečení rozhraní .NET Framework a terminologii.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-153">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="7b7d9-154">Další informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-154">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="7b7d9-155">Chcete-li použít volání deklarativní zabezpečení, musí inicializovat data o stavu objektu oprávnění tak, aby představoval určitou formu oprávnění, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-155">In order to use declarative security calls, you must initialize the state data of the permission object so that it represents the particular form of permission you need.</span></span> <span data-ttu-id="7b7d9-156">Každé z předdefinovaných oprávnění má atribut, který je předán <xref:System.Security.Permissions.SecurityAction> výčet popisující typ operace zabezpečení, kterou chcete provést.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-156">Every built-in permission has an attribute that is passed a <xref:System.Security.Permissions.SecurityAction> enumeration to describe the type of security operation you want to perform.</span></span> <span data-ttu-id="7b7d9-157">Oprávnění však přijmout vlastní parametry, které jsou výhradní k nim.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-157">However, permissions also accept their own parameters that are exclusive to them.</span></span>  
  
 <span data-ttu-id="7b7d9-158">Následující fragment kódu ukazuje deklarativní syntaxi pro vyžádání, že volající vašeho kódu mají vlastní oprávnění nazývané `MyPermission`.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-158">The following code fragment shows declarative syntax for requesting that your code's callers have a custom permission called `MyPermission`.</span></span> <span data-ttu-id="7b7d9-159">Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-159">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="7b7d9-160">V tomto příkladu deklarativní volání umístěno přímo před definici třídy určující, že toto oprávnění použít na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-160">In this example, the declarative call is placed directly before the class definition, specifying that this permission be applied to the class level.</span></span> <span data-ttu-id="7b7d9-161">Atribut je předána **SecurityAction.Demand** struktura k určení, že volající musí mít toto oprávnění, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-161">The attribute is passed a **SecurityAction.Demand** structure to specify that callers must have this permission in order to run.</span></span>  
  
```vb  
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1  
  
   Public Sub New()  
      'The constructor is protected by the security call.  
   End Sub  
  
   Public Sub MyMethod()  
      'This method is protected by the security call.  
   End Sub  
  
   Public Sub YourMethod()  
      'This method is protected by the security call.  
   End Sub  
End Class  
```  
  
```csharp  
[MyPermission(SecurityAction.Demand, Unrestricted = true)]  
public class MyClass  
{  
   public MyClass()  
   {  
      //The constructor is protected by the security call.  
   }  
  
   public void MyMethod()  
   {  
      //This method is protected by the security call.  
   }  
  
   public void YourMethod()  
   {  
      //This method is protected by the security call.  
   }  
}  
```  
  
## <a name="imperative-security"></a><span data-ttu-id="7b7d9-162">Imperativní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7b7d9-162">Imperative Security</span></span>  
 <span data-ttu-id="7b7d9-163">Imperativní syntaxe zabezpečení řeší volání zabezpečení tak, že vytvoříte novou instanci třídy oprávnění objektu, který chcete vyvolat.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-163">Imperative security syntax issues a security call by creating a new instance of the permission object you want to invoke.</span></span> <span data-ttu-id="7b7d9-164">Imperativní syntaxi můžete provádět požadavky a přepsání, ale ne požadavků.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-164">You can use imperative syntax to perform demands and overrides, but not requests.</span></span>  
  
 <span data-ttu-id="7b7d9-165">Před provedením volání zabezpečení, musí inicializovat data o stavu oprávnění objektu, tak, aby představoval určitou formu oprávnění, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-165">Before you make the security call, you must initialize the state data of the permission object so that it represents the particular form of the permission you need.</span></span> <span data-ttu-id="7b7d9-166">Například při vytváření <xref:System.Security.Permissions.FileIOPermission> objekt, můžete použít konstruktor k chybě při inicializaci **FileIOPermission** objektu tak, aby představoval buď neomezený přístup ke všem souborům nebo žádný přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-166">For example, when creating a <xref:System.Security.Permissions.FileIOPermission> object, you can use the constructor to initialize the **FileIOPermission** object so that it represents either unrestricted access to all files or no access to files.</span></span> <span data-ttu-id="7b7d9-167">Nebo můžete použít jiné **FileIOPermission** objekt, předání parametrů, které označují typ přístupu, které chcete objekt představují (to znamená, číst, připojit nebo zápisu) a jaké soubory chcete objekt, který chcete chránit.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-167">Or, you can use a different **FileIOPermission** object, passing parameters that indicate the type of access you want the object to represent (that is, read, append, or write) and what files you want the object to protect.</span></span>  
  
 <span data-ttu-id="7b7d9-168">Kromě vyvolání jediného objektu zabezpečení pomocí syntaxe naléhavého zabezpečení, můžete ho k chybě při inicializaci skupiny oprávnění v sadě oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-168">In addition to using imperative security syntax to invoke a single security object, you can use it to initialize a group of permissions in a permission set.</span></span> <span data-ttu-id="7b7d9-169">Například tato technika je jediný způsob, jak spolehlivě provést [assert](../../../docs/framework/misc/using-the-assert-method.md) volání na více oprávnění v jedné metodě.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-169">For example, this technique is the only way to reliably perform [assert](../../../docs/framework/misc/using-the-assert-method.md) calls on multiple permissions in one method.</span></span> <span data-ttu-id="7b7d9-170">Použití <xref:System.Security.PermissionSet> a <xref:System.Security.NamedPermissionSet> třídy pro vytvoření skupiny oprávnění a pak zavolají vhodnou metodu pro vyvolání požadovaného volání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-170">Use the <xref:System.Security.PermissionSet> and <xref:System.Security.NamedPermissionSet> classes to create a group of permissions and then call the appropriate method to invoke the desired security call.</span></span>  
  
 <span data-ttu-id="7b7d9-171">Imperativní syntaxi můžete provádět požadavky a přepsání, ale ne požadavků.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-171">You can use imperative syntax to perform demands and overrides, but not requests.</span></span> <span data-ttu-id="7b7d9-172">Může použít imperativní syntaxi pro požadavky a přepsání místo deklarativní syntaxe, když se stane pouze v době běhu známé informace, které potřebujete-li inicializovat stav oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-172">You might use imperative syntax for demands and overrides instead of declarative syntax when information that you need in order to initialize the permission state becomes known only at run time.</span></span> <span data-ttu-id="7b7d9-173">Například pokud chcete zajistit, že volající mají oprávnění pro čtení určitého souboru, ale neznáte název tohoto souboru do doby běhu, použijte imperativní požadavky.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-173">For example, if you want to ensure that callers have permission to read a certain file, but you do not know the name of that file until run time, use an imperative demand.</span></span> <span data-ttu-id="7b7d9-174">Je také možné použít imperativní kontroly místo deklarativních, když je potřeba určit v době běhu, zda obsahuje podmínku a na základě výsledku testu, vytvořit požadavek zabezpečení (nebo ne).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-174">You might also choose to use imperative checks instead of declarative checks when you need to determine at run time whether a condition holds and, based on the result of the test, make a security demand (or not).</span></span>  
  
 <span data-ttu-id="7b7d9-175">Následující fragment kódu ukazuje imperativní syntaxi pro vyžádání, že volající vašeho kódu mají vlastní oprávnění nazývané `MyPermission`.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-175">The following code fragment shows imperative syntax for requesting that your code's callers have a custom permission called `MyPermission`.</span></span> <span data-ttu-id="7b7d9-176">Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-176">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="7b7d9-177">Novou instanci třídy `MyPermision` je vytvořen v `MyMethod`, ochrana jenom tato metoda pomocí volání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-177">A new instance of `MyPermision` is created in `MyMethod`, guarding only this method with the security call.</span></span>  
  
```vb  
Public Class MyClass1  
  
   Public Sub New()  
  
   End Sub  
  
   Public Sub MyMethod()  
      'MyPermission is demanded using imperative syntax.  
      Dim Perm As New MyPermission()  
      Perm.Demand()  
      'This method is protected by the security call.  
   End Sub  
  
   Public Sub YourMethod()  
      'YourMethod 'This method is not protected by the security call.  
   End Sub  
End Class  
```  
  
```csharp  
public class MyClass {  
   public MyClass(){  
  
   }  
  
   public void MyMethod() {  
       //MyPermission is demanded using imperative syntax.  
       MyPermission Perm = new MyPermission();  
       Perm.Demand();  
       //This method is protected by the security call.  
   }  
  
   public void YourMethod() {  
       //This method is not protected by the security call.  
   }  
}  
```  
  
## <a name="using-managed-wrapper-classes"></a><span data-ttu-id="7b7d9-178">Použití tříd spravovaných obálek</span><span class="sxs-lookup"><span data-stu-id="7b7d9-178">Using Managed Wrapper Classes</span></span>  
 <span data-ttu-id="7b7d9-179">Většina aplikací a součástí (s výjimkou zabezpečených knihoven) by neměla přímo volat nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-179">Most applications and components (except secure libraries) should not directly call unmanaged code.</span></span> <span data-ttu-id="7b7d9-180">Tady je několik důvodů pro tento.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-180">There are several reasons for this.</span></span> <span data-ttu-id="7b7d9-181">Pokud kód volání nespravovaného kódu přímo, ho nebude možné spustit v mnoha případech, protože kód musí být udělena vysokou úroveň důvěryhodnosti pro volání nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-181">If code calls unmanaged code directly, it will not be allowed to run in many circumstances because code must be granted a high level of trust to call native code.</span></span> <span data-ttu-id="7b7d9-182">Pokud jsou zásady změněny a povolit takovou aplikaci spustit, může to významně oslabit zabezpečení systému, pokud aplikace můžete provádět skoro všechny operace.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-182">If policy is modified to allow such an application to run, it can significantly weaken the security of the system, leaving the application free to perform almost any operation.</span></span>  
  
 <span data-ttu-id="7b7d9-183">Kromě toho kód, který má oprávnění k přístupu nespravovaného kódu pravděpodobně může provádět skoro všechny operace pomocí volání nespravovaného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-183">Additionally, code that has permission to access unmanaged code can probably perform almost any operation by calling into an unmanaged API.</span></span> <span data-ttu-id="7b7d9-184">Například kód, který má oprávnění k volání nespravovaného kódu nemusí <xref:System.Security.Permissions.FileIOPermission> získat přístup k souboru; ho stačí zavolat nespravované (Win32) souboru API přímo, obcházení soubor spravované rozhraní API, která vyžaduje **FileIOPermission**.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-184">For example, code that has permission to call unmanaged code does not need <xref:System.Security.Permissions.FileIOPermission> to access a file; it can just call an unmanaged (Win32) file API directly, bypassing the managed file API that requires **FileIOPermission**.</span></span> <span data-ttu-id="7b7d9-185">Pokud spravovaný kód má oprávnění k volání nespravovaného kódu a volají přímo do nespravovaného kódu, bude systém zabezpečení nelze spolehlivě vynutit omezení zabezpečení, protože modul runtime nemůže vynutit taková omezení na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-185">If managed code has permission to call into unmanaged code and does call directly into unmanaged code, the security system will be unable to reliably enforce security restrictions, since the runtime cannot enforce such restrictions on unmanaged code.</span></span>  
  
 <span data-ttu-id="7b7d9-186">Pokud chcete aplikaci k provedení určité operace, která vyžaduje přístup k nespravovanému kódu, ho by to provést prostřednictvím důvěryhodné spravované třídy, které zabaluje požadovanou funkčnost (pokud taková třída existuje).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-186">If you want your application to perform an operation that requires accessing unmanaged code, it should do so through a trusted managed class that wraps the required functionality (if such a class exists).</span></span> <span data-ttu-id="7b7d9-187">Nevytvářejte obálkovou třídu sami Pokud již existuje v zabezpečené knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-187">Do not create a wrapper class yourself if one already exists in a secure class library.</span></span> <span data-ttu-id="7b7d9-188">Obálková třída, která musí být poskytnuta vysoký stupeň důvěryhodnosti, může volat nespravovaný kód, je zodpovědná za náročné, že jeho volající mít příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-188">The wrapper class, which must be granted a high degree of trust to be allowed to make the call into unmanaged code, is responsible for demanding that its callers have the appropriate permissions.</span></span> <span data-ttu-id="7b7d9-189">Pokud používáte obálkovou třídu, musí váš kód pouze k vyžádání a udělit oprávnění, která vyžaduje obálková třída.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-189">If you use the wrapper class, your code only needs to request and be granted the permissions that the wrapper class demands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7d9-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b7d9-190">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.NamedPermissionSet>  
 <xref:System.Security.Permissions.SecurityAction>  
 [<span data-ttu-id="7b7d9-191">Assert</span><span class="sxs-lookup"><span data-stu-id="7b7d9-191">Assert</span></span>](../../../docs/framework/misc/using-the-assert-method.md)  
 [<span data-ttu-id="7b7d9-192">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-192">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="7b7d9-193">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-193">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 [<span data-ttu-id="7b7d9-194">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b7d9-194">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="7b7d9-195">Metadata a komponenty popisující samy sebe</span><span class="sxs-lookup"><span data-stu-id="7b7d9-195">Metadata and Self-Describing Components</span></span>](../../../docs/standard/metadata-and-self-describing-components.md)