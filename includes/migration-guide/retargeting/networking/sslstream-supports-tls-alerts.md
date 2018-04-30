### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="0352c-101">SslStream podporuje TLS výstrah</span><span class="sxs-lookup"><span data-stu-id="0352c-101">SslStream supports TLS Alerts</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0352c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0352c-102">Details</span></span>|<span data-ttu-id="0352c-103">Po selhání TLS handshake <xref:System.IO.IOException?displayProperty=name> s vnitřní <xref:System.ComponentModel.Win32Exception?displayProperty=name> první vstupně-výstupních operací čtení/zápisu operace bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0352c-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=name> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=name> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="0352c-104"><xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=name> Kód <xref:System.ComponentModel.Win32Exception?displayProperty=name> lze mapovat na TLS výstrah ze vzdálené strany pomocí této [Schannel dokumentaci](https://msdn.microsoft.com/library/windows/desktop/dd721886%28v=vs.85%29.aspx). Další informace najdete v tématu [dokument RFC 2246: výstrahu o chybě. oddíl 7.2.2](https://tools.ietf.org/html/rfc2246#section-7.2.2)chování v rozhraní .NET 4.6.2 a pod ním je, že kanál přenosu (obvykle připojení TCP) bude vypršení časového limitu během zápisu nebo čtení, když se nezdařilo druhou stranou ověření typu handshake a okamžitě později odmítl připojení.</span><span class="sxs-lookup"><span data-stu-id="0352c-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=name> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=name> can be mapped to the TLS Alert from the remote party using this [Schannel documentation](https://msdn.microsoft.com/library/windows/desktop/dd721886%28v=vs.85%29.aspx).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2)The behavior in .NET 4.6.2 and below is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>|
|<span data-ttu-id="0352c-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="0352c-105">Suggestion</span></span>|<span data-ttu-id="0352c-106">Aplikace volání síťová rozhraní API vstupně-výstupních operací, jako <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> by měla řídit <xref:System.IO.IOException> nebo <xref:System.TimeoutException?displayProperty=name>. Ve výchozím nastavení od verze .NET 4.7 je povolena funkce TLS výstrah.</span><span class="sxs-lookup"><span data-stu-id="0352c-106">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=name>.The TLS Alerts feature is enabled by default starting with .NET 4.7.</span></span> <span data-ttu-id="0352c-107">Cílení na rozhraní .NET 4.0 - .NET 4.6.2 aplikace spuštěné na rozhraní .NET 4.7 nebo vyšší systému bude mít tato funkce zakázaná zachování kompatibility. Je možné povolit nebo zakázat funkci pro .NET 4.6 a vyšší aplikací běžících na rozhraní .NET 4.7 nebo vyšší framework následující konfigurace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0352c-107">Applications targeting .NET 4.0 - .NET 4.6.2 running on a .NET 4.7 or higher system will have the feature disabled to preserve compatibility.The following configuration API is available to enable or disable the feature for .NET 4.6 and above applications running on .NET 4.7 or higher framework.</span></span><ul><li><span data-ttu-id="0352c-108">Prostřednictvím kódu programu:</span><span class="sxs-lookup"><span data-stu-id="0352c-108">Programmatically:</span></span></li></ul><span data-ttu-id="0352c-109">Musí být úplně první věcí, kterou aplikace nemá vzhledem k tomu, že bude ServicePointManager – inicializovat pouze jednou:</span><span class="sxs-lookup"><span data-stu-id="0352c-109">Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span><pre><code class="language-C#">AppContext.SetSwitch(&quot;TestSwitch.LocalAppContext.DisableCaching&quot;, true);&#13;&#10;AppContext.SetSwitch(&quot;Switch.System.Net.DontEnableTlsAlerts&quot;, true); // Set to &#39;false&#39; to enable the feature in .NET 4.6 - 4.6.2.&#13;&#10;</code></pre><ul><li><span data-ttu-id="0352c-110">AppConfig:</span><span class="sxs-lookup"><span data-stu-id="0352c-110">AppConfig:</span></span></li></ul><pre><code class="language-XML">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableTlsAlerts=true&quot;/&gt;&#13;&#10;&lt;!-- Set to &#39;false&#39; to enable the feature in .NET 4.6 - 4.6.2. --&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><ul><li><span data-ttu-id="0352c-111">Klíč registru (počítače globální):</span><span class="sxs-lookup"><span data-stu-id="0352c-111">Registry key (machine global):</span></span></li></ul><span data-ttu-id="0352c-112">Nastavte hodnotu na hodnotu "false" k povolení této funkce v rozhraní .NET 4.6 - 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0352c-112">Set the Value to 'false' to enable the feature in .NET 4.6 - 4.6.2.</span></span><pre><code>Key = HKLM\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts&#13;&#10;Type = String&#13;&#10;Value = &quot;true&quot;&#13;&#10;</code></pre>|
|<span data-ttu-id="0352c-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0352c-113">Scope</span></span>|<span data-ttu-id="0352c-114">Edge</span><span class="sxs-lookup"><span data-stu-id="0352c-114">Edge</span></span>|
|<span data-ttu-id="0352c-115">Version</span><span class="sxs-lookup"><span data-stu-id="0352c-115">Version</span></span>|<span data-ttu-id="0352c-116">4.7</span><span class="sxs-lookup"><span data-stu-id="0352c-116">4.7</span></span>|
|<span data-ttu-id="0352c-117">Typ</span><span class="sxs-lookup"><span data-stu-id="0352c-117">Type</span></span>|<span data-ttu-id="0352c-118">Změna orientace</span><span class="sxs-lookup"><span data-stu-id="0352c-118">Retargeting</span></span>|
|<span data-ttu-id="0352c-119">Ovlivněné rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0352c-119">Affected APIs</span></span>|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.WebRequest?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.Http?displayProperty=nameWithType></li></ul>|
