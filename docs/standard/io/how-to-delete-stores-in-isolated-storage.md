---
title: 'Postupy: Odstraňování úložišť v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 776984cf1cc17d5c1becc91d4491fa6dbc9e2c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572324"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Postupy: Odstraňování úložišť v izolovaném úložišti
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje dvě metody pro odstraňování souborů izolovaného úložiště:  
  
-   Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a odstraní úložiště, který volá ho. Nejsou žádná oprávnění požadovaná pro tuto operaci. Kód, který může přistupovat k úložišti data můžete odstranit nebo všemi uvnitř ho.  
  
-   Statickou metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> trvá <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> hodnota výčtu a odstranění všech úložišť pro uživatele, který běží kódu. Tato operace vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> oprávnění <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití statické a instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody. Třída získá dvě úložiště; jedna je pro uživatele a sestavení izolované a druhá je pro uživatele, domény a sestavení izolované. Úložiště uživatele, domény a sestavení je pak odstraní volání <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metoda souboru izolovaného úložiště `isoStore1`. Poté jsou odstraněny všechny zbývající úložiště pro uživatele voláním statickou metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
