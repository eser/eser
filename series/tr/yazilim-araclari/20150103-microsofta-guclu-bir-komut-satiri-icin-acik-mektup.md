# Microsoft’a güçlü bir komut satırı için açık mektup

Steve Ballmer zamanında “sözde”, Satya Nadella ile birlikte ise kısa zamanda “özde” geliştirici dostu olan Microsoft’a açık mektubumdur.

Öncelikle hayatımda profesyonel olarak kazandığım gelirin büyük çoğunluğu Microsoft teknolojileri üzerinden oldu, 1997 yılından bu yana Microsoft teknolojilerini kullanarak yazılım geliştiriyorum. “Microsoft yazılımcısı” olduğum kadar, son 5–6 senelik yükselen trendlerle birlikte GNU/Linux — Özgür Yazılım cephesinde de dengeli bir şekilde yazılım geliştirmeye başladım. Artık favori bir platform benimsemek yerine birden fazla alanda üretim yapıyorum. Ve eminim tek alanla kısıtlı kalmayan, birden fazla platforma hakim olan tek yazılımcı değilim.

Microsoft şu ana dek kendi dünyası dışındaki araçların çoğunu “port” etti. .NET oldukça güçlü bir oluşumdu ve eğer eksik olduğu bir cephe oluşursa anında kendi alternatifini oluşturuyordu. Hibernate yerine NHibernate, GitHub yerine CodePlex, PIP/NPM yerine NuGet, Make yerine MSBuild, StyleCop, NUnit, Entity Framework vb. Bunlardan bazıları benim nezdimde sınıfta kalmış, bazıları ise güçlü birer araç olarak halen varlığını korumaktadır.

Uzun süredir ASP.NET yazarken bile Grunt’dan, NPM’den, PhantomJs’den yardım alırdım ama bu araçlar Microsoft platformları için üvey evlatlardı. Fakat şu sıralar ASP.NET MVC, Azure ve son olarak VS 2013 ile bir şeylerin değiştiğini hissedebiliyorum. Yalnızca Microsoft’un geliştirdiği değil, topluluktan gelen, topluluğun desteklediği araçlar da kendine .NET ve Microsoft ekosisteminde yer bulabilmeye başladılar.

Fakat ne yazık ki Windows halen bir geliştirici için çağın gereksinimlerini karşılayabilen bir platform değil. Yanlış anlaşılma olmasın, Windows inanılmaz olgun bir sistem, bir çok avantaja sahip fakat “eksik”. Ben bu eksikler arasından bana göre en kritik olanına, komut satırına odaklanmak istiyorum.

“Madem Microsoft ASP.NET vNext açılımını yapacak kadar olgunlaştı, neden yazılımcılar için daha fazlası olmasın?” motivasyonu ile Windows 10’un bir milat olmasını beklerken, ben kendi bulabildiğim eksikleri saymaya çalışacağım.

**Güçlü Komut Satırı:**  
Öncelikle bana lütfen PowerShell demeyin. PowerShell’e işiniz düşmediği sürece PowerShell kullanmazsınız, ben şahsen yolunu bile bilmiyorum. İşletim sisteminin kendi shell’ini esas alıyorum. Windows 10’da ilk kez komut satırı için bir geliştirme gelecek yıllar sonra, o da copy-paste tuşları. Komut satırında her şeyden önce bash kadar yetenekli olmalı. Neden “echo \`ls\`” gibi bir komut veremiyorum? Neden aliaslar yok?

**Komut Satırı Renk Kodları:**  
16’lık ANSI renk kodları ben Quick Basic kullanırken yeterli idi. Fakat 88/256’ın şu anda geçerli olması gereken standart olduğuna inanıyorum.

**GNU Araçları:**  
Şu anda GNU araçlarını haricen Windows’a kurup çalıştırabiliyorum. Oysa ki bunlar işletim sistemi ile birlikte gelebilir. İnsanlar type, find, mklink gibi komutları ezbere bilmiyorlar ama cat, grep, ln bir çok kişi tarafından halihazırda benimsenmiş durumda. Ayrıca ssh, curl gibi şu anda komut satırında yararlanılamayan araçlar da bir takım yazılımların dağıtılmasında anahtar görevi görüyor.

Örnek:

```sh
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

**Paket Yöneticisi:**  
“Git” kurmak istiyorum. Ve bunu yalnızca komut satırından çalıştıracağım. Bunun için msysgit kurmak durumunda kalıyorum. Oysa ki Debian’da olsam “apt-get install git” yazdıktan sonra git kullanabilir hale gelecektim.

**Path Ayracı:**  
Dosya pathleri için “/” ayracı artık Windows-dışı sistemlerde bir standart. Windows bir noktaya kadar pathleri “/” ile kullandığımızda bir çevirim gerçekleştiriyor. Fakat bunun Windows için de standart olması ne kaybettirir? /media/c/Program Files/ benzeri bir yapı belki Linux’un avantajlarından biri olan dizin-seviyesi partition desteği için ilk adım olabilir.

**CMD.EXE yerine Bash:**  
Çok radikal bir fikir olmasa Windows da bash kullansın diyebilirdim. Geriye dönük uyumluluk için CMD.EXE kalmaya devam eder, geliştirilmeye devam eden bash ise bir port olarak Windows’un komut arayüzü olurdu. Böylece shell scriptler de destekleniyor olurdu. Ama bunun yakın gelecekte olmasının mucize olduğunu düşünüyorum.

Benim tespitlerim bu kadar.

Yazılımcılar olarak bir çok araç kullanıyor ve yazıyoruz. Bu araçların kullanılması için komut satırı genelde önem arz ediyor. Modern web frameworkleri komut satırından vazgeçmeyi bırakalım, tamamiyle komut satırı kullanımına yönelmiş durumdalar. Bu araçları yazanlar Linux ve OS X için ortak komut yazabiliyorken uyumsuzluk çıkaran Windows için bu komutları yazmaya tenezzül dahi etmiyorlar.

Maddeleri “uygulanabilir”den “fantezi”ye doğru sıralamaya özen gösterdim. Bir gün işin Windows tarafında da kendimi “eksik hissetmeyeceğim” günü iple çekiyorum.
