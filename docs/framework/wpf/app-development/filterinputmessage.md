---
title: FilterInputMessage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b3a0e58c7485d46f004db7ea52215be60340b68
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="filterinputmessage"></a><span data-ttu-id="66f6a-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="66f6a-102">FilterInputMessage</span></span>
<span data-ttu-id="66f6a-103">Voláno rozhraním PresentationHost.exe vždy, když je přijata zpráva, pokud je vrácen E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="66f6a-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66f6a-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66f6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66f6a-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="66f6a-106">[v] Zpráva WM_INPUT odeslána do okna, který je získávání nezpracovaná vstup.</span><span class="sxs-lookup"><span data-stu-id="66f6a-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="66f6a-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66f6a-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="66f6a-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="66f6a-108">HRESULT:</span></span>  
  
 <span data-ttu-id="66f6a-109">S_OK - filtr nemohl zpracovat zprávu a může dojít k dalšímu zpracování.</span><span class="sxs-lookup"><span data-stu-id="66f6a-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="66f6a-110">S_FALSE - filtr zpracovat tuto zprávu a mělo dojít k žádné další zpracování.</span><span class="sxs-lookup"><span data-stu-id="66f6a-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="66f6a-111">E_NOTIMPL – Pokud je tato hodnota se vrátí, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) není volán znovu.</span><span class="sxs-lookup"><span data-stu-id="66f6a-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="66f6a-112">To může být vrácena z hostitelskou aplikaci, která je jenom zajímá poskytování vlastních průběh a chyby uživatelského rozhraní pro PresentationHost.exe není zajímá předávaná nezpracovaná vstupní zprávy ze PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="66f6a-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66f6a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66f6a-113">Remarks</span></span>  
 <span data-ttu-id="66f6a-114">PresentationHost.exe je cílem různé nezpracovaná vstupní zařízení, včetně klávesnice, myš a vzdálené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="66f6a-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="66f6a-115">V některých případech je závislá na vstupu, které by jinak spotřebovat PresentationHost.exe chování v hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66f6a-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="66f6a-116">Hostitelskou aplikaci může například závisí na příjem určité vstupní zprávy a určete, zda se má zobrazit konkrétní prvky rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66f6a-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="66f6a-117">Povolit hostitelskou aplikaci pro příjem nezbytné vstupní zpráv k poskytování těchto chování, PresentationHost.exe předává odpovídající nezpracovaná vstupní zprávy do aplikace hostované voláním [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="66f6a-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="66f6a-118">Aplikace hostované přijímá nezpracovaná vstupní zprávy pomocí registrace sady nezpracovaná vstupní zařízení (zařízení standardu HID) vrácený [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="66f6a-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f6a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="66f6a-119">See Also</span></span>  
 [<span data-ttu-id="66f6a-120">WM_INPUT oznámení</span><span class="sxs-lookup"><span data-stu-id="66f6a-120">WM_INPUT Notification</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)