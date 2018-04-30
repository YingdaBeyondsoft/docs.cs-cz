### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="719f5-101">Vazby WCF s režim zabezpečení TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="719f5-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

|   |   |
|---|---|
|<span data-ttu-id="719f5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="719f5-102">Details</span></span>|<span data-ttu-id="719f5-103">Od verze rozhraní .NET Framework 4.6.1, vazby WCF, který používá režim zabezpečení TransportWithMessageCredential lze přijímat zprávy s nepodepsané &quot;k&quot; hlavičky pro zabezpečení asymetrické klíče. Ve výchozím nastavení, nepodepsané &quot;k&quot; bude pokračovat hlaviček zamítnutí v rozhraní .NET 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="719f5-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be setup to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET 4.6.1.</span></span> <span data-ttu-id="719f5-104">Jsou pouze přijaty pokud aplikace požádá do tento nový režim operace pomocí Switch.System.ServiceModel.AllowUnsignedToHeader konfigurace přepínače. Protože se jedná o funkci přihlášení, by neměly ovlivnit chování existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="719f5-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span>|
|<span data-ttu-id="719f5-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="719f5-105">Suggestion</span></span>|<span data-ttu-id="719f5-106">Protože se jedná o funkci přihlášení, by neměly ovlivnit chování existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="719f5-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span> <span data-ttu-id="719f5-107">Chcete-li určit, zda se má použít nové chování, nebo Ne, použijte následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="719f5-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span><pre><code>&lt;runtime&gt;<br />&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;<br />&lt;/runtime&gt;</code></pre>|
|<span data-ttu-id="719f5-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="719f5-108">Scope</span></span>|<span data-ttu-id="719f5-109">Transparentní</span><span class="sxs-lookup"><span data-stu-id="719f5-109">Transparent</span></span>|
|<span data-ttu-id="719f5-110">Version</span><span class="sxs-lookup"><span data-stu-id="719f5-110">Version</span></span>|<span data-ttu-id="719f5-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="719f5-111">4.6.1</span></span>|
|<span data-ttu-id="719f5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="719f5-112">Type</span></span>|<span data-ttu-id="719f5-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="719f5-113">Runtime</span></span>|
|<span data-ttu-id="719f5-114">Ovlivněné rozhraní API</span><span class="sxs-lookup"><span data-stu-id="719f5-114">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
