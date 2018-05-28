### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream pomocí nativních rozhraní API pro dekompresi

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.2, provádění dekompresi v <code>T:System.IO.Compression.DeflateStream</code> došlo ke změně třídy používat nativní rozhraní API systému Windows ve výchozím nastavení. Obvykle výsledkem zlepšování výkonu. Cílení na rozhraní .NET Framework verze 4.7.2 nebo vyšší pomocí nativní implementaci všech aplikací .NET. Tato změna může vést k určité rozdíly v chování, které zahrnují:<ul><li>Zprávy o výjimkách se můžou lišit. Typ došlo k výjimce, ale zůstává stejná.</li><li>Některé speciální situacích, jako je například nemá dostatek paměti pro dokončení operace, může být zpracovány jinak.</li><li>Existují známé rozdíly k analýze záhlaví gzip (Poznámka: pouze <code>GZipStream</code> nastavení pro dekompresi má vliv):</li><li>Výjimky při analýze neplatné záhlaví může být vyvolána v různých časech.</li><li>Nativní implementaci vynutí, že hodnoty pro některé vyhrazené příznaky v záhlaví gzip (tj. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) jsou nastaveny podle specifikace, což může způsobit, že je vyvolána výjimka, které dřív byly ignorovány neplatné hodnoty.</li></ul>|
|Návrh|Pokud dekompresi pomocí nativních rozhraní API se negativně ovlivněn chování vaší aplikace, můžete zamítnutí této funkce můžete přidat <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> přepnout <code>runtime</code> části souboru app.config a jeho nastavení na hodnotu <code>true</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|
