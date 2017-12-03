---
title: "Postupy: Zápis znaků do řetězce"
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
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="6c6b1-102">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="6c6b1-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="6c6b1-103">Následující příklady kódu zápis znaků synchronně a asynchronně z pole znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="6c6b1-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c6b1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c6b1-104">Example</span></span>  
 <span data-ttu-id="6c6b1-105">Následující příklad zapíše 5 znaků synchronně z pole na řetězec.</span><span class="sxs-lookup"><span data-stu-id="6c6b1-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="6c6b1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c6b1-106">Example</span></span>  
 <span data-ttu-id="6c6b1-107">Další příklad načte všechny znaky asynchronně z <xref:System.Windows.Controls.TextBox> řízení a ukládá je do pole.</span><span class="sxs-lookup"><span data-stu-id="6c6b1-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="6c6b1-108">Poté asynchronně zapíše každý znak písmeno nebo mezer na samostatný řádek následovaný konec řádku k <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6c6b1-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6c6b1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c6b1-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="6c6b1-110">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="6c6b1-110">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="6c6b1-111">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="6c6b1-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="6c6b1-112">Postupy: vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="6c6b1-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="6c6b1-113">Postupy: čtení a zápisu do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="6c6b1-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="6c6b1-114">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="6c6b1-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="6c6b1-115">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="6c6b1-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="6c6b1-116">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="6c6b1-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="6c6b1-117">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="6c6b1-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)