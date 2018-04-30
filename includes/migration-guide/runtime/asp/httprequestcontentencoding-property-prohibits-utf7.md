### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="e18f9-101">Vlastnost HttpRequest.ContentEncoding znemožňuje UTF7</span><span class="sxs-lookup"><span data-stu-id="e18f9-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e18f9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e18f9-102">Details</span></span>|<span data-ttu-id="e18f9-103">Od verze rozhraní .NET Framework 4.5, kódování UTF-7 zakázané <xref:System.Web.HttpRequest?displayProperty=name>s' subjektů.</span><span class="sxs-lookup"><span data-stu-id="e18f9-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="e18f9-104">Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.</span><span class="sxs-lookup"><span data-stu-id="e18f9-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="e18f9-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="e18f9-105">Suggestion</span></span>|<span data-ttu-id="e18f9-106">V ideálním případě aplikace by měla být aktualizovány nechcete použít v kódování UTF-7 <xref:System.Web.HttpRequest?displayProperty=name>s.</span><span class="sxs-lookup"><span data-stu-id="e18f9-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="e18f9-107">Alternativně může být obnovena starší verze chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atribut [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) elementu.</span><span class="sxs-lookup"><span data-stu-id="e18f9-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) element.</span></span>|
|<span data-ttu-id="e18f9-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e18f9-108">Scope</span></span>|<span data-ttu-id="e18f9-109">Edge</span><span class="sxs-lookup"><span data-stu-id="e18f9-109">Edge</span></span>|
|<span data-ttu-id="e18f9-110">Version</span><span class="sxs-lookup"><span data-stu-id="e18f9-110">Version</span></span>|<span data-ttu-id="e18f9-111">4.5</span><span class="sxs-lookup"><span data-stu-id="e18f9-111">4.5</span></span>|
|<span data-ttu-id="e18f9-112">Typ</span><span class="sxs-lookup"><span data-stu-id="e18f9-112">Type</span></span>|<span data-ttu-id="e18f9-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e18f9-113">Runtime</span></span>|
|<span data-ttu-id="e18f9-114">Ovlivněné rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e18f9-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
