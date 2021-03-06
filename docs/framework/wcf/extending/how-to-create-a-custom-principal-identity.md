---
title: 'Postupy: vytvoření vlastní objekt Identity'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: e3ecee7be32cef7fc5371e56cfc32e2d0ef7ae6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488036"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Postupy: vytvoření vlastní objekt Identity
<xref:System.Security.Permissions.PrincipalPermissionAttribute> Je deklarativní způsob řízení přístupu metod služby. Při použití tohoto atributu <xref:System.ServiceModel.Description.PrincipalPermissionMode> výčet Určuje režim pro provedení kontroly autorizace. Když tento režim je nastaven na <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umožní uživateli zadat vlastní <xref:System.Security.Principal.IPrincipal> třída vrácený <xref:System.Threading.Thread.CurrentPrincipal%2A> vlastnost. Toto téma ukazuje scénář při <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> se používá v kombinaci s vlastní zásady autorizace a vlastní objekt.  
  
 Další informace o používání <xref:System.Security.Permissions.PrincipalPermissionAttribute>, najdete v části [postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Odkazy na následující obory názvů jsou potřeba pro kompilaci kódu:  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
