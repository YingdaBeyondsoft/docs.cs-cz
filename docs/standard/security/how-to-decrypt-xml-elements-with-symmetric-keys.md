---
title: "Postupy: Dešifrování elementů XML pomocí symetrických klíčů"
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
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6bacdb47d1107f6a800d9beec2578c0f7085a894
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="4197b-102">Postupy: Dešifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="4197b-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="4197b-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4197b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="4197b-104">XML – šifrování umožňuje uložit nebo přenosu citlivých XML bez obav data snadno čitelná.</span><span class="sxs-lookup"><span data-stu-id="4197b-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4197b-105">Tento příklad kódu dešifruje element XML pomocí algoritmus Advanced Encryption (Standard AES), také označován jako Rijndael.</span><span class="sxs-lookup"><span data-stu-id="4197b-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="4197b-106">Informace o tom, jak šifrování elementu XML s použitím tohoto postupu najdete v tématu [postupy: šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4197b-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="4197b-107">Použijete-li k šifrování dat XML symetrický algoritmus jako je AES, musíte použít stejný klíč k šifrování a dešifrování dat XML.</span><span class="sxs-lookup"><span data-stu-id="4197b-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="4197b-108">Příklad v tomto postupu předpokládá, že šifrované XML byla zašifrována pomocí stejného klíče, a šifrování a dešifrování strany ke shodě o algoritmus a klíč k použití.</span><span class="sxs-lookup"><span data-stu-id="4197b-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="4197b-109">V tomto příkladu se neukládají ani šifrování AES klíč v šifrované kódu XML.</span><span class="sxs-lookup"><span data-stu-id="4197b-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="4197b-110">Tento příklad je vhodný pro situace, kdy jediná aplikace potřebuje k šifrování dat na základě relace klíče uložené v paměti, nebo podle kryptograficky silnou klíče odvozeného z hesla.</span><span class="sxs-lookup"><span data-stu-id="4197b-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="4197b-111">V situacích, kdy je potřeba sdílet šifrovaná data XML dvě nebo více aplikací zvažte použití schématu šifrování na základě asymetrického algoritmu nebo certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="4197b-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="4197b-112">K dešifrování symetrického klíče elementu XML</span><span class="sxs-lookup"><span data-stu-id="4197b-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="4197b-113">Zašifrování elementu XML vytvořených předtím klíčem pomocí technik popsaných v [postupy: šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4197b-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="4197b-114">Najít <`EncryptedData`> elementu (definované XML Encryption standard) v <xref:System.Xml.XmlDocument> objektu, který obsahuje XML zašifrované a vytvořte novou <xref:System.Xml.XmlElement> objekt představující tento element.</span><span class="sxs-lookup"><span data-stu-id="4197b-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="4197b-115">Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedData> objekt načtením nezpracovaná data XML z dříve vytvořeného <xref:System.Xml.XmlElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="4197b-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="4197b-116">Vytvořte novou <xref:System.Security.Cryptography.Xml.EncryptedXml> objektu a použít ho k dešifrování dat XML pomocí stejného klíče, která byla použita pro šifrování.</span><span class="sxs-lookup"><span data-stu-id="4197b-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="4197b-117">Nahraďte element šifrované element nově dešifrovaným ve formátu prostého textu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4197b-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="4197b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4197b-118">Example</span></span>  
 <span data-ttu-id="4197b-119">Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="4197b-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="4197b-120">Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="4197b-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="4197b-121">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít jej v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4197b-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4197b-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4197b-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4197b-123">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="4197b-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="4197b-124">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="4197b-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4197b-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4197b-125">.NET Framework Security</span></span>  
 <span data-ttu-id="4197b-126">Nikdy uložení kryptografického klíče v podobě prostého textu nebo přenos klíče mezi počítači v podobě prostého textu.</span><span class="sxs-lookup"><span data-stu-id="4197b-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="4197b-127">Po dokončení pomocí symetrický šifrovací klíč, zrušte ji z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="4197b-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4197b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4197b-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="4197b-129">Postupy: šifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="4197b-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)