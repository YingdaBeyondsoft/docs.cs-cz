---
title: "Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti"
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
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti
Chcete-li vyhledat adresáře v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metoda. Tato metoda přebírá řetězec, který představuje vzor hledání. Délce jednoho znaku (?) i více znak (*) můžete použít zástupné znaky v vzor hledání, ale musí být zadány v Závěrečná část názvu zástupné znaky. Například `directory1/*ect*` je platný hledaný řetězec, ale `*ect*/directory2` není.  
  
 Chcete-li vyhledat soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metoda. Omezení pro zástupné znaky ve vyhledávacích řetězců, které se vztahují na <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> platí také pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Ani jeden z těchto metod je rekurzivní. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> třída neposkytuje žádné metody pro výpis všech adresářů nebo souborů v úložišti. Ale rekurzivní metody jsou uvedeny v následujícím příkladu kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje postup vytvoření souborů a adresářů v izolovaném úložišti. Nejprve je úložiště, které je pro uživatele, domény a sestavení izolované načíst a uložena v umístění `isoStore` proměnné. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda se používá k vytvoření několik různých adresářů a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> konstruktor vytvoří některé soubory v těchto adresářích. Kód pak prochází výsledky `GetAllDirectories` metoda. Tato metoda používá <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> k vyhledání všech názvů adresářů v aktuálním adresáři. Tyto názvy jsou uložené v pole a potom `GetAllDirectories` volání sebe, předávání v každý adresář, který najde. V důsledku toho jsou vráceny všechny názvy adresářů v matici. V dalším kroku kód zavolá `GetAllFiles` metoda. Tato metoda volá `GetAllDirectories` a zjistěte, názvy všech adresáře a poté zkontroluje každý adresář pro soubory pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metoda. Výsledkem je vrácený v poli pro zobrazení.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Izolovaná úložiště](../../../docs/standard/io/isolated-storage.md)