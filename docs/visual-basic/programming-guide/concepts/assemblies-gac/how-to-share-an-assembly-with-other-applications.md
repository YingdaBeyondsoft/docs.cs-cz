---
title: "Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 491791ba9b6f0cf6da86a160eddf8e78109b11c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)
Sestavení může být privátní nebo sdílené: ve výchozím nastavení, většiny programů jednoduché skládat z privátní sestavení, protože není určen pro použití jinými aplikacemi.  
  
 Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěny v [globální mezipaměti sestavení](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Sdílení sestavení  
  
1.  Vytvoření vašeho sestavení. Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Přiřadíte vaše sestavení silným názvem. Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Informace o verzi přiřadíte vaše sestavení. Další informace najdete v tématu [Správa verzí sestavení](https://msdn.microsoft.com/library/51ket42z).  
  
4.  Přidejte vaše sestavení do globální mezipaměti sestavení. Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Přístup k typům obsažený v sestavení z jiných aplikací. Další informace najdete v tématu [postupy: odkazování sestavení silným názvem](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Viz také  
 [Programování konceptů](../../../../visual-basic/programming-guide/concepts/index.md) [sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)