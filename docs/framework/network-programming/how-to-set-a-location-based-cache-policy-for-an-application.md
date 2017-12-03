---
title: "Postupy: nastavení zásad na základě umístění mezipaměti pro aplikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a145bf30930c9be81dc92f3a9f1eebda046b7e8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="e8518-102">Postupy: nastavení zásad na základě umístění mezipaměti pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="e8518-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="e8518-103">Na základě umístění mezipaměti zásady umožňují aplikace explicitně definujte chování ukládání do mezipaměti na základě umístění požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="e8518-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="e8518-104">Toto téma popisuje nastavení zásad mezipaměti prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="e8518-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="e8518-105">Informace o nastavení zásad pro aplikaci pomocí konfiguračních souborů najdete v tématu [ \<requestCaching – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e8518-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="e8518-106">Nastavení zásad na základě umístění mezipaměti pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="e8518-106">To set a location-based cache policy for an application</span></span>  
  
1.  <span data-ttu-id="e8518-107">Vytvoření <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> objektu.</span><span class="sxs-lookup"><span data-stu-id="e8518-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2.  <span data-ttu-id="e8518-108">Objekt zásad nastavte jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8518-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="e8518-109">Nastavení zásad, která přebírá požadované prostředky z mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8518-109">To set a policy that takes requested resources from a cache</span></span>  
  
-   <span data-ttu-id="e8518-110">Vytvořit zásadu, která přebírá požadované prostředky z mezipaměti, pokud je k dispozici a jinak, zasílá požadavky na server, nastavením mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="e8518-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="e8518-111">Žádost o lze splnit všechny mezipaměti mezi klientem a serverem, včetně vzdálené mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="e8518-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="e8518-112">Chcete-li nastavit zásady, které brání žádné mezipaměti poskytuje prostředky</span><span class="sxs-lookup"><span data-stu-id="e8518-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
-   <span data-ttu-id="e8518-113">Vytvořit zásadu, která brání poskytnutí požadované prostředky podle nastavení úrovně do mezipaměti žádné mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="e8518-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="e8518-114">Tato úroveň zásad odebere zdroj z místní mezipaměti, pokud je přítomen a označuje vzdálené mezipamětí, že se mělo odstranit také prostředku.</span><span class="sxs-lookup"><span data-stu-id="e8518-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="e8518-115">Nastavení zásad, který vrací požadované prostředky, pouze pokud jsou v místní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8518-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
-   <span data-ttu-id="e8518-116">Vytvořit zásadu, která vrátí požadované prostředky, pouze pokud jsou v místní mezipaměti podle nastavení úrovně do mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="e8518-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="e8518-117">Pokud požadovaný prostředek není v mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e8518-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="e8518-118">Chcete-li nastavit zásady, které brání poskytuje prostředky místní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8518-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
-   <span data-ttu-id="e8518-119">Vytvořit zásadu, která brání poskytnutí požadované prostředky podle nastavení úrovně do mezipaměti v místní mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="e8518-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="e8518-120">Pokud požadovaný prostředek je v zprostředkující mezipaměti a znovu je úspěšně ověřeny, zprostředkující mezipaměti můžete poskytnout požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="e8518-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="e8518-121">Nastavení zásad, který brání poskytuje všechny mezipaměti požadované prostředky</span><span class="sxs-lookup"><span data-stu-id="e8518-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
-   <span data-ttu-id="e8518-122">Vytvořit zásadu, která brání poskytnutí požadované prostředky podle nastavení úrovně do mezipaměti žádné mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="e8518-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="e8518-123">Prostředek vrácená serverem mohou být uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e8518-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="e8518-124">Nastavení zásad, která umožňuje všechny mezipaměti k poskytování požadované prostředky, pokud prostředek na daném serveru není novější než kopie uložené v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8518-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
-   <span data-ttu-id="e8518-125">Vytvořit zásadu, která umožňuje všechny mezipaměti k poskytování požadované prostředky, pokud prostředek na daném serveru není novější než kopie uložené v mezipaměti nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="e8518-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e8518-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8518-126">See Also</span></span>  
 [<span data-ttu-id="e8518-127">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="e8518-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="e8518-128">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8518-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="e8518-129">Na základě umístění mezipaměti zásad</span><span class="sxs-lookup"><span data-stu-id="e8518-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="e8518-130">Zásady založené na čase mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8518-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="e8518-131">\<requestCaching – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e8518-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)