---
title: 'Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b31a359167307a58d8393e9c29e7dab1575cfdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643663"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)
Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které mají silné názvy. Obě sestavení musí mít silné názvy. I když obě sestavení v tomto příkladu používat stejné klíče, můžete použít různé klíče pro dvě sestavení.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit podepsané sestavení a přátelských sestavení  
  
1.  Otevřete příkazový řádek.  
  
2.  Generování keyfile a zobrazit svůj veřejný klíč, použijte následující sekvence příkazů pomocí nástroje silného názvu. Další informace najdete v tématu [Sn.exe (nástroj silným názvem)][Sn.exe (nástroj silným názvem)](../../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
    1.  Vygenerovat klíč silné jméno – v tomto příkladu a uložit ho do souboru FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extrahování veřejný klíč z FriendAssemblies.snk a umístí jej do FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Zobrazí veřejný klíč uložený v souboru FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Vytvořte soubor jazyka Visual Basic s názvem `friend_signed_A` obsahující následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.  
  
     Nástroje pro silný název generuje nový veřejný klíč pokaždé, když ji spustí. Proto je potřeba nahradit veřejný klíč v následujícím kódu veřejný klíč, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Vytvořte soubor jazyka Visual Basic, který je pojmenován `friend_signed_B` a obsahuje následující kód. Protože friend_signed_A určuje friend_signed_B jako přátelského sestavení, můžete přístup k kód v friend_signed_B `Friend` typy a členy z friend_signed_A. Soubor obsahuje následující kód.  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  Kompilace a friend_signed_B se přihlaste pomocí následujícího příkazu.  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     Název sestavení generované kompilátorem musí odpovídat názvu sestavení friend předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Sestavení je možné nastavit explicitně pomocí `-out` – možnost kompilátoru. Další informace najdete v tématu [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Spusťte soubor friend_signed_B.exe.  
  
     Program zobrazí řetězec "Class1.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `Friend` typy a členy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Přátelská sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (nástroj pro silný název)] [Sn.exe (nástroj pro silný název)](../../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Vytváření a používání sestavení se silným názvem](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)
