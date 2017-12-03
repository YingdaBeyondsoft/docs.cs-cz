---
title: "Postupy: Šifrování elementů XML pomocí symetrických klíčů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56bce016d16b9bf12446ba7b31725d49c48988a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="339b2-102">Postupy: Šifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="339b2-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="339b2-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="339b2-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="339b2-104">XML – šifrování umožňuje uložit nebo přenosu citlivých XML bez obav data snadno čitelná.</span><span class="sxs-lookup"><span data-stu-id="339b2-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="339b2-105">Tento postup dešifruje element XML pomocí algoritmus Advanced Encryption (Standard AES), také označován jako Rijndael.</span><span class="sxs-lookup"><span data-stu-id="339b2-105">This procedure decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="339b2-106">Informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="339b2-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="339b2-107">Použijete-li k šifrování dat XML symetrický algoritmus jako je AES, musíte použít stejný klíč k šifrování a dešifrování dat XML.</span><span class="sxs-lookup"><span data-stu-id="339b2-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="339b2-108">V příkladu v tomto postupu se předpokládá, že šifrované XML bude dešifrována pomocí stejného klíče, a že šifrování a dešifrování strany souhlasit na algoritmus a klíč pro použití.</span><span class="sxs-lookup"><span data-stu-id="339b2-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="339b2-109">V tomto příkladu se neukládají ani šifrování AES klíč v šifrované kódu XML.</span><span class="sxs-lookup"><span data-stu-id="339b2-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="339b2-110">Tento příklad je vhodný pro situace, kdy jediná aplikace potřebuje k šifrování dat na základě relace klíče uložené v paměti, nebo podle kryptograficky silnou klíče odvozeného z hesla.</span><span class="sxs-lookup"><span data-stu-id="339b2-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="339b2-111">V situacích, kdy je potřeba sdílet šifrovaná data XML dvě nebo více aplikací zvažte použití schématu šifrování na základě asymetrického algoritmu nebo certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="339b2-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="339b2-112">K zašifrování elementu XML symetrického klíče</span><span class="sxs-lookup"><span data-stu-id="339b2-112">To encrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="339b2-113">Generování symetrického klíče pomocí <xref:System.Security.Cryptography.RijndaelManaged> třídy.</span><span class="sxs-lookup"><span data-stu-id="339b2-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="339b2-114">Tento klíč se použije k zašifrování elementu XML.</span><span class="sxs-lookup"><span data-stu-id="339b2-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="339b2-115">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="339b2-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="339b2-116"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.</span><span class="sxs-lookup"><span data-stu-id="339b2-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="339b2-117">Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte novou <xref:System.Xml.XmlElement> objekt představující element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="339b2-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="339b2-118">V tomto příkladu `"creditcard"` je zašifrován element.</span><span class="sxs-lookup"><span data-stu-id="339b2-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="339b2-119">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování <xref:System.Xml.XmlElement> pomocí symetrického klíče.</span><span class="sxs-lookup"><span data-stu-id="339b2-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="339b2-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda vrací šifrovaný element jako pole bajtů šifrované.</span><span class="sxs-lookup"><span data-stu-id="339b2-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="339b2-121">Vytvořit <xref:System.Security.Cryptography.Xml.EncryptedData> objektu a jeho naplnění identifikátor adresy URL elementu XML – šifrování.</span><span class="sxs-lookup"><span data-stu-id="339b2-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="339b2-122">Tento identifikátor URL umožňuje dešifrování objektu strany vědět, že soubor XML obsahuje element šifrované.</span><span class="sxs-lookup"><span data-stu-id="339b2-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="339b2-123">Můžete použít <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pole k určení identifikátoru adresy URL.</span><span class="sxs-lookup"><span data-stu-id="339b2-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="339b2-124">Vytvoření <xref:System.Security.Cryptography.Xml.EncryptionMethod> objekt, který je inicializován na identifikátor URL kryptografický algoritmus používaný k vygenerování klíče.</span><span class="sxs-lookup"><span data-stu-id="339b2-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="339b2-125">Předat <xref:System.Security.Cryptography.Xml.EncryptionMethod> do objektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="339b2-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="339b2-126">Přidat element šifrovaná data, která mají <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="339b2-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="339b2-127">Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu s <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="339b2-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="339b2-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="339b2-128">Example</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="339b2-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="339b2-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="339b2-130">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="339b2-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="339b2-131">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="339b2-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="339b2-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="339b2-132">.NET Framework Security</span></span>  
 <span data-ttu-id="339b2-133">Nikdy uložení kryptografického klíče v podobě prostého textu nebo přenos klíče mezi počítači v podobě prostého textu.</span><span class="sxs-lookup"><span data-stu-id="339b2-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="339b2-134">Místo toho použijte zabezpečené kontejneru klíčů pro ukládání kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="339b2-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="339b2-135">Po dokončení pomocí kryptografického klíče, vymazat z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="339b2-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339b2-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="339b2-136">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="339b2-137">Postupy: dešifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="339b2-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)