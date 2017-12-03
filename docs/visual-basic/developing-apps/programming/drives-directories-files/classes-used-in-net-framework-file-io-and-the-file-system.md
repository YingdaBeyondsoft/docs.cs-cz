---
title: "Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: abb2291ce797f3630eebd24e563994a2d86242bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="dbb7c-102">Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbb7c-102">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>
<span data-ttu-id="dbb7c-103">Následující tabulka uvádí třídy běžně používané pro rozhraní .NET Framework soubor vstupně-výstupních operací, rozděleny do třídy vstupně-výstupních souborů, třídy používané pro vytváření datových proudů a třídy používané pro čtení a zápis do datových proudů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-103">The following tables list the classes commonly used for .NET Framework file I/O, categorized into file I/O classes, classes used for creating streams, and classes used to read and write to streams.</span></span>  
  
 <span data-ttu-id="dbb7c-104">Zadat [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] dokumentaci a najít komplexnější seznam, najdete v části [– přehled knihovny tříd](https://msdn.microsoft.com/library/hfa3fa08).</span><span class="sxs-lookup"><span data-stu-id="dbb7c-104">To enter the [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] documentation and find a more comprehensive listing, see [Class Library Overview](https://msdn.microsoft.com/library/hfa3fa08).</span></span>  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a><span data-ttu-id="dbb7c-105">Vstupně-výstupních operací základní třídy pro soubory, jednotky a adresáře</span><span class="sxs-lookup"><span data-stu-id="dbb7c-105">Basic I/O Classes for Files, Drives, and Directories</span></span>  
 <span data-ttu-id="dbb7c-106">Následující tabulka uvádí a popisuje hlavní třídy používané pro soubor vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-106">The following table lists and describes the main classes used for file I/O.</span></span>  
  
|<span data-ttu-id="dbb7c-107">Třída</span><span class="sxs-lookup"><span data-stu-id="dbb7c-107">Class</span></span>|<span data-ttu-id="dbb7c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="dbb7c-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-109">Poskytuje statické metody pro vytváření, přesunutí a výčet prostřednictvím adresářů a podadresářů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-109">Provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-110">Poskytuje metody instance pro vytváření, přesunutí a výčet prostřednictvím adresářů a podadresářů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-110">Provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-111">Poskytuje metody instance pro vytváření, přesunutí a výčet prostřednictvím jednotky.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-111">Provides instance methods for creating, moving, and enumerating through drives.</span></span>|  
|<xref:System.IO.File?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-112">Poskytuje statické metody pro vytvoření, kopírování, odstranění, přesunutí a otevírání souborů a pomáhá při vytváření `FileStream`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-112">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-113">Definuje konstanty pro čtení, zápisu nebo přístup pro čtení a zápis do souboru.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-113">Defines constants for read, write, or read/write access to a file.</span></span>|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-114">Poskytuje atributy pro soubory a adresáře například `Archive`, `Hidden`, a `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-114">Provides attributes for files and directories such as `Archive`, `Hidden`, and `ReadOnly`.</span></span>|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-115">Poskytuje statické metody pro vytvoření, kopírování, odstranění, přesunutí a otevírání souborů a pomáhá při vytváření `FileStream`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-115">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-116">Určuje, jak otevřít soubor.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-116">Controls how a file is opened.</span></span> <span data-ttu-id="dbb7c-117">Tento parametr je zadán v mnoha z konstruktorů `FileStream` a `IsolatedStorageFileStream`a `Open` metody <xref:System.IO.File> a <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-117">This parameter is specified in many of the constructors for `FileStream` and `IsolatedStorageFileStream`, and for the `Open` methods of <xref:System.IO.File> and <xref:System.IO.FileInfo>.</span></span>|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-118">Definuje konstanty pro řízení typ přístupu, kterou může mít jiné datové proudy souboru do stejného souboru.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-118">Defines constants for controlling the type of access other file streams can have to the same file.</span></span>|  
|<xref:System.IO.Path?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-119">Poskytuje metody a vlastnosti pro zpracování řetězců adresářů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-119">Provides methods and properties for processing directory strings.</span></span>|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-120">Řídí přístup souborů a složek definováním <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> a <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> oprávnění.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-120">Controls the access of files and folders by defining <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> and <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> permissions.</span></span>|  
  
## <a name="classes-used-to-create-streams"></a><span data-ttu-id="dbb7c-121">Třídy používané k vytváření datových proudů</span><span class="sxs-lookup"><span data-stu-id="dbb7c-121">Classes Used to Create Streams</span></span>  
 <span data-ttu-id="dbb7c-122">Následující tabulka uvádí a popisuje hlavní třídy používané k vytváření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-122">The following table lists and describes the main classes used to create streams.</span></span>  
  
|<span data-ttu-id="dbb7c-123">Třída</span><span class="sxs-lookup"><span data-stu-id="dbb7c-123">Class</span></span>|<span data-ttu-id="dbb7c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="dbb7c-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-125">Přidá vyrovnávací vrstvu ke čtení a zápisu operace na jiný datový proud.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-125">Adds a buffering layer to read and write operations on another stream.</span></span>|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-126">Podporuje náhodný přístup k souborům pomocí jeho <xref:System.IO.FileStream.Seek%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-126">Supports random access to files through its <xref:System.IO.FileStream.Seek%2A> method.</span></span> <span data-ttu-id="dbb7c-127"><xref:System.IO.FileStream>ve výchozím nastavení otevře soubory synchronně, ale také podporuje asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-127"><xref:System.IO.FileStream> opens files synchronously by default but also supports asynchronous operation.</span></span>|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-128">Vytvoří datový proud, s jehož záložní úložiště je paměť, nikoli soubor.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-128">Creates a stream whose backing store is memory, rather than a file.</span></span>|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-129">Poskytuje základní datový proud dat pro přístup k síti.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-129">Provides the underlying stream of data for network access.</span></span>|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-130">Definuje datový proud, který odkazuje datových proudů na kryptografických transformace.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-130">Defines a stream that links data streams to cryptographic transformations.</span></span>|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a><span data-ttu-id="dbb7c-131">Třídy používané číst z a zapisovat do datových proudů</span><span class="sxs-lookup"><span data-stu-id="dbb7c-131">Classes Used to Read from and Write to Streams</span></span>  
 <span data-ttu-id="dbb7c-132">V následující tabulce jsou uvedeny konkrétní třídy používané pro čtení a zápis do souborů s datovými proudy.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-132">The following table shows the specific classes used for reading from and writing to files with streams.</span></span>  
  
|<span data-ttu-id="dbb7c-133">**– Třída**</span><span class="sxs-lookup"><span data-stu-id="dbb7c-133">**Class**</span></span>|<span data-ttu-id="dbb7c-134">**Popis**</span><span class="sxs-lookup"><span data-stu-id="dbb7c-134">**Description**</span></span>|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-135">Přečte kódované řetězce a primitivní datové typy z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-135">Reads encoded strings and primitive data types from a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-136">Zapíše kódované řetězce a primitivní datové typy <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-136">Writes encoded strings and primitive data types to a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-137">Přečte znaky z <xref:System.IO.FileStream>pomocí <xref:System.IO.StreamReader.CurrentEncoding%2A> převést znaků do a z bajtů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-137">Reads characters from a <xref:System.IO.FileStream>, using <xref:System.IO.StreamReader.CurrentEncoding%2A> to convert characters to and from bytes.</span></span> <span data-ttu-id="dbb7c-138"><xref:System.IO.StreamReader>má konstruktor, který se pokouší zjistit správný <xref:System.IO.StreamReader.CurrentEncoding%2A> pro daný datový proud, založené na přítomnost <xref:System.IO.StreamReader.CurrentEncoding%2A>-zvláštní preambule, jako je například značka pořadí bajtů.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-138"><xref:System.IO.StreamReader> has a constructor that attempts to ascertain the correct <xref:System.IO.StreamReader.CurrentEncoding%2A> for a given stream, based on the presence of a <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preamble, such as a byte order mark.</span></span>|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-139">Zapíše znaky `FileStream`pomocí <xref:System.IO.StreamWriter.Encoding%2A> převést znaky na bajty.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-139">Writes characters to a `FileStream`, using <xref:System.IO.StreamWriter.Encoding%2A> to convert characters to bytes.</span></span>|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-140">Přečte znaky z `String`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-140">Reads characters from a `String`.</span></span> <span data-ttu-id="dbb7c-141">Výstup může být buď datový proud v jakémkoli kódování nebo `String`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-141">Output can be either a stream in any encoding or a `String`.</span></span>|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|<span data-ttu-id="dbb7c-142">Zapíše znaky `String`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-142">Writes characters to a `String`.</span></span> <span data-ttu-id="dbb7c-143">Výstup může být buď datový proud v jakémkoli kódování nebo `String`.</span><span class="sxs-lookup"><span data-stu-id="dbb7c-143">Output can be either a stream in any encoding or a `String`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbb7c-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbb7c-144">See Also</span></span>  
 [<span data-ttu-id="dbb7c-145">Skládání datových proudů</span><span class="sxs-lookup"><span data-stu-id="dbb7c-145">Composing Streams</span></span>](https://msdn.microsoft.com/library/e4y2dch9)  
 [<span data-ttu-id="dbb7c-146">Vstupně-výstupních souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="dbb7c-146">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="dbb7c-147">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="dbb7c-147">Asynchronous File I/O</span></span>](https://msdn.microsoft.com/library/kztecsys)  
 [<span data-ttu-id="dbb7c-148">Základní informace o souborech vstupně-výstupních operací a systému souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbb7c-148">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)