---
title: "Postupy: Připojování k textovým souborům v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41ab4491dbc21936c6fbfe9440fcbaeaaac6f1dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="64a22-102">Postupy: Připojování k textovým souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64a22-102">How to: Append to Text Files in Visual Basic</span></span>
<span data-ttu-id="64a22-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metodu můžete použít k připojení do textového souboru zadáním, že `append` parametr je nastaven na `True`.</span><span class="sxs-lookup"><span data-stu-id="64a22-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="64a22-104">Pro připojení do textového souboru</span><span class="sxs-lookup"><span data-stu-id="64a22-104">To append to a text file</span></span>  
  
-   <span data-ttu-id="64a22-105">Použití `WriteAllText` metoda, cílový soubor a řetězec, který má být připojen a nastavení `append` parametru `True`.</span><span class="sxs-lookup"><span data-stu-id="64a22-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="64a22-106">Tento příklad zapíše řetězec `"This is a test string."` do souboru s názvem `Testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="64a22-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-append-to-text-files_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="64a22-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="64a22-107">Robust Programming</span></span>  
 <span data-ttu-id="64a22-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="64a22-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="64a22-109">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="64a22-110">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="64a22-111">`File`odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="64a22-112">Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="64a22-113">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="64a22-114">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="64a22-115">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="64a22-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a22-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="64a22-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [<span data-ttu-id="64a22-117">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="64a22-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)