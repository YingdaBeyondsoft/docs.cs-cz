### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) nevyvolá výjimku teď když .NET nemůže zpracovat certifikátu

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5.2 a starší verze, by tato metoda výjimku, pokud <code>true</code> byl předán pro parametr podrobné a k dispozici nebyly nainstalovány certifikáty, které nejsou podporované rozhraním .NET Framework. Metoda bude nyní úspěšné a vrátit platný řetězec, který vynechá části nepřístupný certifikátu.|
|Návrh|Žádný kód v závislosti na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> by měly být aktualizovány v některých případech, ve kterých rozhraní API by mít dřív vyvolala očekávat, že vrácený řetězec mohou vyloučit některé data certifikátu (například veřejný klíč, privátní klíč a rozšíření).|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

