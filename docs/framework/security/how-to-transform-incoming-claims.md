---
title: 'Postupy: Transformovat příchozí deklarace identity'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: cb71e320116c3af73139f1a8083fa62e8a7e21a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400169"
---
# <a name="how-to-transform-incoming-claims"></a>Postupy: Transformovat příchozí deklarace identity
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET pracujícím s deklaracemi a transformaci příchozí deklarace identity. Také poskytuje pokyny k testování aplikace k ověření, že transformované deklarace identity jsou uvedené při spuštění aplikace.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – implementace deklarace identity pomocí vlastní ClaimsAuthenticationManager transformace  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích  
  
-   Transformovat příchozí deklarace identity přidáním deklaraci identity role správce  
  
-   Testování aplikace webových formulářů ASP.NET, abyste viděli, zda pracuje správně  
  
## <a name="overview"></a>Přehled  
 WIF zpřístupní třídy s názvem <xref:System.Security.Claims.ClaimsAuthenticationManager> umožňující uživatelům úpravám deklarací identity, než se mají zobrazovat předávající stranu aplikaci. <xref:System.Security.Claims.ClaimsAuthenticationManager> Je užitečné pro oddělené oblasti zájmu mezi ověřování a základního kódu aplikace. Následující příklad ukazuje, jak přidat roli do deklarací identity ve příchozí <xref:System.Security.Claims.ClaimsPrincipal> který může být vyžadován na základě RP.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – implementace deklarace identity pomocí vlastní ClaimsAuthenticationManager transformace  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.  
  
2.  V sadě Visual Studio, klikněte na tlačítko **soubor**, klikněte na tlačítko **nový**a potom klikněte na **projektu**.  
  
3.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
4.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
5.  Klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.  
  
6.  **Identit a přístupu** se zobrazí v okně. V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.  
  
7.  V *Default.aspx* souboru, nahraďte existující kód následující a pak soubor uložte:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  Otevření souboru kódu s názvem *Default.aspx.cs*. Nahraďte stávající kód následující příkaz, pak uložte soubor:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Krok 2 – implementace deklarace identity pomocí vlastní ClaimsAuthenticationManager transformace  
 V tomto kroku se přepíše výchozí funkce v <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy pro přidání role správce do příchozí objekt zabezpečení.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>K implementaci pomocí vlastní ClaimsAuthenticationManager transformace deklarací identity  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **přidat**a potom klikněte na **nový projekt**.  
  
2.  V **přidat nový projekt** vyberte **knihovny tříd** z **Visual C#** šablony seznamu, zadejte `ClaimsTransformation`a potom stiskněte klávesu **OK**. Vytvoří se nový projekt ve složce řešení.  
  
3.  Klikněte pravým tlačítkem na **odkazy** pod **ClaimsTransformation** projektu a pak klikněte na **přidat odkaz na**.  
  
4.  V **správce odkazů** vyberte **System.IdentityModel**a potom klikněte na **OK**.  
  
5.  Otevřete **Class1.cs**, nebo pokud neexistuje, klikněte pravým tlačítkem na **ClaimsTransformation**, klikněte na tlačítko **přidat**, pak klikněte na tlačítko **třídy...**  
  
6.  Přidejte následující direktivy using do souboru kódu:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  Přidejte následující třídy a metody do souboru kódu.  
  
    > [!WARNING]
    >  Následující kód je pro demonstrační účely pouze; Ujistěte se, abyste ověřili určený oprávnění v produkčním kódu.  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  Uložte tento soubor a sestavení **ClaimsTransformation** projektu.  
  
9. Ve vašem **TestApp** projekt ASP.NET, klikněte pravým tlačítkem na odkazy a pak klikněte na tlačítko **přidat odkaz na**.  
  
10. V **správce odkazů** vyberte **řešení** v levé nabídce vyberte **ClaimsTransformation** z vyplněná možnosti a pak klikněte na tlačítko  **OK**.  
  
11. V kořenovém **Web.config** souboru, přejděte na  **\<system.identityModel >** položku. V rámci  **\<identityConfiguration >** elementy, přidejte následující řádek a soubor uložte:  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku testování vaší aplikace webových formulářů ASP.NET a ověřte, že deklarace identity jsou uvedené Pokud se uživatel přihlásí pomocí ověřování pomocí formulářů.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů  
  
1.  Stiskněte klávesu **F5** sestavení a spuštění aplikace. By se měla zobrazit s *Default.aspx*.  
  
2.  Na *Default.aspx* stránky, měli byste vidět tabulku pod **vaše deklarace identity** záhlaví, která zahrnuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu. Poslední řádek by měla zobrazit následujícím způsobem:  
  
    ||||||  
    |-|-|-|-|-|  
    |MÍSTNÍ ÚŘAD|MÍSTNÍ ÚŘAD|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|Správce|http://www.w3.org/2001/XMLSchema#string|
