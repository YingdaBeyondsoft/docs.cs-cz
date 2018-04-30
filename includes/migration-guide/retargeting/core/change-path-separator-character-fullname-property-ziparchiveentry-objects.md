### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="6fc0d-101">Změna v cestě oddělovací znak ve vlastnosti FullName položky ZipArchiveEntry objektů</span><span class="sxs-lookup"><span data-stu-id="6fc0d-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6fc0d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6fc0d-102">Details</span></span>|<span data-ttu-id="6fc0d-103">Pro aplikace, které cílí na rozhraní .NET Framework 4.6.1 a novější verze, cesta oddělovací znak změnil ze zpětné lomítko (&quot;&quot;) na dopředné lomítko (&quot;/&quot;) v <xref:System.IO.Compression.ZipArchiveEntry.FullName> vlastnost <xref:System.IO.Compression.ZipArchiveEntry> objekty vytvořené přetíženími <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash (&quot;&quot;) to a forward slash (&quot;/&quot;) in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="6fc0d-104">Tato změna přináší implementace rozhraní .NET do souladu s části 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. ZIP archivy k dekomprimaci na jiné operační systémy. Dekompresi soubor zip vytvořené aplikace s cílem předchozí verzi rozhraní .NET Framework na jiný systém než Windows operační systémy, třeba Macintosh nepodaří zachovat strukturu adresáře.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="6fc0d-105">Například na Macintosh, vytvoří sadu souborů, jejichž název souboru zřetězí cesta k adresáři, společně s žádné zpětné lomítko (&quot;&quot;) znaků a název souboru.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-105">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash (&quot;&quot;) characters, and the filename.</span></span> <span data-ttu-id="6fc0d-106">V důsledku toho není zachován struktura adresářů dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-106">As a result, the directory structure of decompressed files is not preserved.</span></span>|
|<span data-ttu-id="6fc0d-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="6fc0d-107">Suggestion</span></span>|<span data-ttu-id="6fc0d-108">Dopad na tuto změnu. Soubory ZIP, které jsou dekomprimovat operačního systému Windows pomocí rozhraní API v rozhraní .NET Framework <xref:System.IO?displayProperty=nameWithType> oboru názvů musí být minimální, protože tato rozhraní API může bezproblémově zpracovat buď lomítko (&quot;/&quot;) ani zpětné lomítko (&quot; \&potřebná;) jako cesta oddělovací znak. Pokud se tato změna není žádoucí, se můžete rozhodnout mimo ho přidáním nastavení konfigurace, pro které [ \<runtime >](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-108">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a slash (&quot;/&quot;) or a backslash (&quot;\&quot;) as the path separator character.If this change is undesirable, you can opt out of it by adding a configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="6fc0d-109">Následující příklad ukazuje, jak `<runtime>` části a `Switch.System.IO.Compression.ZipFile.UseBackslash` výslovný nesouhlas s přepínači:</span><span class="sxs-lookup"><span data-stu-id="6fc0d-109">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><span data-ttu-id="6fc0d-110">Kromě toho aplikace, které cílí na předchozích verzích rozhraní .NET Framework, ale běží v rozhraní .NET Framework 4.6.1 a novějším můžete vyjádřit výslovný souhlas toto chování přidáním nastavení konfigurace, pro které [ \<runtime >](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-110">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="6fc0d-111">Následující příklad zobrazuje i `<runtime>` části a `Switch.System.IO.Compression.ZipFile.UseBackslash` přepínač výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-111">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="6fc0d-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6fc0d-112">Scope</span></span>|<span data-ttu-id="6fc0d-113">Edge</span><span class="sxs-lookup"><span data-stu-id="6fc0d-113">Edge</span></span>|
|<span data-ttu-id="6fc0d-114">Version</span><span class="sxs-lookup"><span data-stu-id="6fc0d-114">Version</span></span>|<span data-ttu-id="6fc0d-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6fc0d-115">4.6.1</span></span>|
|<span data-ttu-id="6fc0d-116">Typ</span><span class="sxs-lookup"><span data-stu-id="6fc0d-116">Type</span></span>|<span data-ttu-id="6fc0d-117">Změna orientace</span><span class="sxs-lookup"><span data-stu-id="6fc0d-117">Retargeting</span></span>|
|<span data-ttu-id="6fc0d-118">Ovlivněné rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6fc0d-118">Affected APIs</span></span>|<ul><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType></li></ul>|
