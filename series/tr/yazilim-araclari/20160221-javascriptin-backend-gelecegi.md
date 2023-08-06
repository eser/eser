# JavaScript’in backend geleceği

Geçtiğimiz 8–9 sene içerisinde frontend development tarafında artan ihtiyaçlara paralel olarak; backend’den aşina olduğumuz kod tasarım konseptlerinin (patternler, separation concernler, frameworkler, v.s.) frontend tarafında da konjonktürel olarak uygulanabilir hale gelmesiyle JavaScript neredeyse bir yükseliş dönemine girmişti. Bu popülerlik başta ECMA olmak üzere herkesi JavaScript üzerinden daha da üretken olma yoluna soktu.

İnanılmaz verimli bir kaç senenin ardından, tjholowaychuk’un Node.js’den Go’ya geçişi ile birlikte JavaScript’in yakaladığı ivme duraksamaya girdi. En azından “mükemmel” olduğu ilüzyonu ile dokunulmazlık zırhının eskisi kadar güçlü değildi artık.

Bunda elbette ki “öncül”lerin Node.js ekosisteminde ürün geliştirip, deneyimlerini yaşamaları ve daha sonra süreci değerlendirip “feedback” vermeye başlamaları da etkili oldu.

Bugünlerde ise her gün twitter’da JavaScript hakkında değerlendirmeler okumaya başladım. Twitter fiziksel limitleri nedeniyle bu konuların “derinlemesine” konuşulabileceği bir mecra olmadığından bu değerlendirmeleri sağlıklı bulmuyordum. Yine benzer Quora’nın derinliklerinde “neden JavaScript’le olmadı” benzeri başlıklara sahip yazıları okuma fırsatı buldum.

Görünen o ki 2 yıl önce “MEAN Stack” diye pazarlanan JavaScript’in backend’deki geleceğine dair genel kanı “olumsuz” olmaya doğru yol alıyor. Her genel kanı gibi bunu da edinilen “sonuç”lar belirliyor.

Ben “genel kanı”ların “deneyimler karşılığında oluşan sağlıklı önyargı”ları yansıttığını düşünsem de, bunları oluşturan duruma özel konuları incelemeden hemen kabul etmek konusunda oldukça tutucuyumdur. Çünkü sonuçların (başarısız veya başarılı girişimler) süreçten bağımsız olarak değerlendirildiğinde tek başına bir veri niteliği taşımadığını düşünmekteyim. Tüm bir değerlendirme yaptığımda ise “henüz” beni JavaScript’in backend geleceğinin pek parlak olmadığı konusunda halen ikna edebilmiş bir görüş bulunmamakta.

Buradan hareketle JavaScript’in backend’deki durumuna ilişkin üretilen bazı ortak argümanları buraya taşıyarak, kendi mesleki görüşümle yanıtlamaya çalışacağım.

Bunu yaparken de her ne kadar JavaScript’in backend tarafında “uygulanabilirliği”ni Node.js ile sınırlı görmesem de, öncül olduğu ve yazının yazıldığı tarihteki en ciddiye alınır girişim olduğu için Node.js ekosistemi özelinde değerlendirme yapacağım.

Yapmayacağım şey ise JavaScript ve Node.js’in güçlü yanlarından ve avantajlarından bahsetmek olacak. Yazıyı okumadan önce konular hakkında zaten bilginizin olduğu varsayımında bulunuyorum.

**İddia 1: Debug ve profiling zor**  
PHP gibi bir application’a (apache, fpm, v.s.) modül olarak çalışan platformlara göre Node.js’in bu konularda araç zenginliğinden dahi bahsedebiliriz. Hatta belirli kod parçalarını ayırıp Node.js yorumlayıcı veya browser üzerinde debug/profile edebilmek ufak da olsa bir avantaj sağladığını belirtmek gerekiyor.

Java veya C# gibi dillerin IDE’lerindeki rahatlıktan bahsedemeyiz ama benim kullandığım Visual Studio Code yaklaşık bir IDE desteği sağlamaya çalışıyor.

Eğer konu ürettiğimiz kodun değil de, Node.js’in runtime stabilitesinden kaynaklı durumların profiling’i ise; bunun “stabilite” başlığında değerlendirmek isterim.

**İddia 2: Stabilite problemleri mevcut**  
Öncelikle *semantic versioning* hayranı olduğumu belirtmek isterim. Kendimi bildim bileli hiçbir şartta kendini henüz “1.0” olarak tanımlamamış bir ürünü de production’da kullandığımı hatırlamıyorum.

Fakat [Why did Koding switch from Node.js to Go?](https://www.quora.com/Why-did-Koding-switch-from-Node-js-to-Go) gibi hikayeleri okudukça da birçok hikayenin aslında Node.js’in “henüz kendini stabil ilan etmediği” günlere atıf ettiğini görüyorum.

*Yine de* bu eleştirilerin bugünün sürümleri olan 4.x ve 5.x için gerçekleştiklerini varsayıp yorumlamaya çalışalım. Burada stabilite problemleri iddiasına cevaben “stabilite problemi kesinlikle yoktur” gibi bir yanıt yazılamaz elbette. Ancak karşı argümanlar sunarak ilerlersek:

*   Bugüne kadar Node.js’in mimarisinden dolayı düzelemeyecek bir durum duyduğumu hatırlamıyorum. (varsa lütfen düzeltin)
    
*   Node.js yakın zamanda release cycle’ını LTS (long term support) sürümler üretecek şekilde güncellemiş görünüyor.
    
*   Google Chrome başta olmak üzere browserlardan text editorlere kadar bir çok yazılımda kullanılan V8'in runtime hatalarının zaman içerisinde düzelmesi siz “kusursuz başka bir platform” arayışı başlatıp bitirene kadar geçen süreden daha kısa olacaktır.
    
*   Başlıca şikayetler arasında duyduğum “memory leak” başınıza gelse dahi bunu tespit ettiğiniz anda workaroundlar sayesinde V8'e gelecek patch’den önce telafi edilebilir durumda.
    

**İddia 3: Bizim için hayal kırıklığı oldu**  
Bu yorum oldukça subjektif. Fakat ben bununla çok karşılaştığım için [Hayal kırıklığına uğramamak için sorulması gerekenler](../uretkenlik/20160221-hayal-kirikligina-ugramamak-icin-sorgulanmasi-gerekenler.md) yazımda konu olarak ele aldım.

Projenizin “bizim için hayal kırıklığı oldu” ile sonuçlanmasını istemiyorsanız; önceden ödevinizi iyi yapmanız veya bir danışmanlık almanız şart. Çünkü “bugünün mevcut sorunları” bugün başlanılacak bir projenin “hangi teknoloji ile yapılacağını” değiştirebilecek kadar ciddi bir faktör.

Diyelim bu durum sizin için geçerli oldu ve Node.js’den kaynaklı bir riskten ötürü JavaScript kullanmak beklentilerinizi karşılamıyor; ben bunu yine JavaScript’in sunucu taraflı geleceğini belirleyen bir parametre olarak kabul edemem.

Nedeni ise her platform tercihinin “proje başına” yapılmasının gerekliliğine inananan biri olarak, production’a çıkacak ciddi yazılımlar geliştirirken beklentilerin ve önceliklerin her projeye göre ciddi değişkenlikler gösterdiğine inanıyor olmam. Evet Java, .NET, Python v.s. gibi sağlamlığını ispat edebilmiş daha olgun alternatifler her zaman orada durmaktalar. Ama bu alternatiflerin de yer yer bazı stresleri kaldıramadığını bizzat kendim deneyimledim.

Bu nedenle benim için bir platformun bir projede “bekleneni en iyi veren tercih” olmaması, o platformun sonuna kadar üzerinin çizili olması anlamına gelmemekte.

**İddia 4: Geleceği muallak**  
Danışmanlık verdiğim kurumlarla teknoloji seçimi yaparken her zaman göz önünde bulundurduğum önemli bir parametre var. O da mevcut teknoloji üzerine farklı kurumlar tarafından yatırılan “sermaye”.

Şu anda yazılım alanında Microsoft gibi devlerin planlarını JavaScript’e yönlendirdiğini ve V8'e alternatif olacak bir JavaScript yorumlayıcı üzerinde çalıştıklarını biliyoruz. Yine Microsoft giderek open sourcelaşma yolunda .NET’den sonra en güvendiği platformu Node.js olarak belirlemiş olmalı ki gerek Node.js’e verdiği IDE desteği, gerekse .NET’in çoklu platformda çalışacak yeni ekosistemi .NET Core için yardımcı ürünlerin çoğunu Node.js platformunun üyelerinden seçiyor.

Ek olarak .NET’e senelerini vermiş bir profesyonel olarak Microsoft’un her zaman “yalnızca müşterisi” olduğumu düşündüm. Fakat Microsoft’dan bir yetkili ilk kez benim yazılım geliştirici görüşümü almak için beni bir Skype görüşmesine davet ettiğinde konu “Node.js hakkındaki görüşlerim”di.

PayPal’ın da yüzlerce “JavaScript mühendisi” yetiştirmekten övündüğünü, bu ciddiyette bir firmanın JavaScript üzerine bolca yatırım yaptığını gözden kaçırmamalıyız.

Örnekler elbette ki çoğaltılabilir. Fakat ana noktayı kaçırmamak gerekli. Sermaye o kadar önemli bir parametre ki, o ekosistemden beslenen büyük firma sayısı arttığı sürece Node.js’in sunucu taraflı performansı ne kadar kötüleşirse kötüleşsin bu durum birilerini farklı bir çözümle ürün devamlılığını sağlamak zorunda bırakacaktır.

Node.js’i önemli kılan ortaya çıkışındaki JavaScript dilinin gücünün backend’de kullanılabilecek olduğu teziydi. Node.js’in kendisi başarısızlığa doğru gitse dahi tezinin geçerliliğini yitirmeyeceğini düşünüyorum.

Zaten hali hazırda browserlardaki tahtı 20 yıldır sarsılmamış bir JavaScript’den bahsediyoruz. V8, SpiderMonkey, Carakan v.s. derken yakın gelecekte de JavaScript yorumlayıcılarının her geçen gün gelişeceği kolaylıkla tahmin edilebilir. Node.js’in da avantajı bunlar için bir çatı görevi sağlaması. Örneğin geçtiğimiz günlerde Microsoft’un Chakra isimli JavaScript yorumlayıcısı Node.js’e yapılan bir Pull Request ile artık V8 yerine alternatif olarak kullanılabilir hale geldi. Şu anda Node.js iki farklı yorumlayıcı ile çalışabiliyor.

**İddia 5: Yazdığınız kod gelecek sene çalışmayacak**  
JavaScript’in standartları ECMA tarafından belirlenmekte. Çok büyük bir sorun oluşturmadığı sürece geriye doğru uyumluluk sağladıklarını biliyoruz. Burada browser API’lerinden bahsetmiyorsak zaten JavaScript’in uğradığı değişiklikler çoğunlukla dile yeni yetenekler kazandırmaya yönelik.

Node.js ise *semantic versioning* sayesinde API’sinde olan bir değişiklikte sürüm değiştireceğini garantilemiş durumda. **NVM** gibi araçlar sayesinde aynı makine üzerinde farklı Node.js sürümleri de kullanabiliyorsunuz. Ben burada bir problem göremiyorum?

**İddia 6: Büyük mimariler için çok kötü**  
Aynı şeyi PHP ve C/C++ için de söyleyebiliriz. Fakat aynı dillerin kendi platformlarında en büyük codebase’lere ait projeler tarafından da kullanıldığını biliyoruz. Peki bu nasıl oluyor?

Kod Organizasyonu! Node.js’in mevcut ekosistemindeki frameworkler monolitik yapıların antitezi gibi duruyor. Bunun için kod organizasyonu ve dizin yapısını oluşturmak tamamiyle size kalıyor. Eğer bu konuda iyi bir tasarım çıkartamazsanız bu dertten muzdarip oluyorsunuz.

Belki de yapılan en büyük hata codebase’in sürümlenmemesi ve tasarımı konusunda yeteri profesyonel yaklaşımların gösterilmemesi olabilir.

**İddia 7: Bakımı Zor**  
Bakımın hangi açıdan zor olduğuna göre değişebilecek bir argümandan bahsediyoruz.

Eğer yeni özelliklerin eklenebilmesinden, kodun sürdürülebilirliğinden bahsediyorsak bu yine bir organizasyon sorunu. Coding Guidelineları takip etmez, kod organizasyonunu eksik yapar ve dökümantasyona önem verilmezse her platformda karşımıza çıkabilecek bir problemden bahsediyoruz.

Şayet sistem tarafında bir bakımdan söz ediyorsak Java’dan ve .NET’den sonra çalıştığım en fazla araca sahip ekosisteme sahip olduğunu, ve araç sayısına bakarsak en yüksek ivmeye sahip platform olduğundan rahatlıkla bahsedebiliriz.

**İddia 8: Hype**  
“Node.js çevresinde oluşan hype’dan dolayı oldukça yaygınlaştı ve dikkatleri çekti.” diyorsanız bir sonraki cümlenizde Node.js’in yerine ne koyduğunuzu açıklarken kendinizi izleyin. Eğer bu Python, Java v.s. değil de Go ise; Go’nun da bir hype ile bu noktaya gelmediğini iddia edemeyeceğinizi düşünüyorum. Burada “Go” yerine pazarlaması heyecan yaratmış, sizin de kod yazdıkça öğrenmenin mutluluğuyla çok sevdiğiniz fakat 5–6 proje sonra sıkılacağınız bir dili koyabilirsiniz.

JavaScript’e dönersek, hype’dan beslenmiyor demek ne kadar isabetli olur bilemiyorum ama client tarafındaki uzun yıllar sürdürdüğü popülerliğini göz önünde bulundurduğumuzda bunun gelip geçici olduğunu iddia etmek oldukça zor.

Fatih Kadir Akın’ın bu yazıya cevaben [Medium’da yer alan yazısı](https://medium.com/@fkadev/node-js-in-back-end-gelece%C4%9Fi-f246db981721) üzerine bu noktadan itibaren yeni iddiaları ekliyorum.

**İddia 9: Event Loop üzerine kurulu ve bu kötü bir şey**  
10 yıl önce Java’da veya .NET’de “ben web sayfası değil, backend development yapıyorum” diyebilmek için platformların paralel/çoklu işlem kabiliyetlerini kullanabilmek önemli bir eşikti benim için. GSM operatörleri ile sürekli soket üzerinden iletişimde olan, SMS/MMS toplu mesaj gönderimi yapan ve son kullanıcılara API sunan bir SaaS’da lead architect görevindeydim. Sabahlara kadar Thread optimizasyonu yaptığımı, en ufak yanlış hesapta sistem performansının anlık 5 kişiye zar-zor yanıt verebilecek hale geldiğini hatırlıyorum o günlerden.

.NET, Java v.b. platformlar bu gücü size kullandırabildiği için “güçlü bir platform” olarak tanımlanıyor. Fakat kağıt üzerinde basit olmasına rağmen antremanlı ve deneyimli değilseniz forklar, joinler ve senkronizasyon problemleri bilin ki sizi üzmeye geliyorlar.

Paralel/çoklu işlemleri gerçekleştirebilmek için en çok kullanılan mimarileri incelediğimizde:

*   Multi-threading / Multi-process yapılar
    
*   Event-driven yapılar
    
*   Hibrit yapılar
    

ile karşılaşacağız.

Bunlardan ilki gerçekten zahmet ve kontrol gerektiren bir yapı. Donanıma göre thread/process sayısını ayarlamak, elimizdeki işleme göre dinamik olarak bir thread havuzu mu yoksa sabit thread sayısı mı işimizi görecekse onun implementasyonu ile ilgilenmek, kullanılan değişken tanımlarının senkronizasyonu gibi faktörler yakanızı bırakmamakta.

İkincisi ise arayüzler, oyunlar ve komut satırlarının vazgeçilmezi ana/olay döngüsü etrafında sağlanıyor. İnanın kodda bu ana döngü gerçekten “çok çirkin” duruyor fakat performans olarak Thread’den pek de geride kalmayan, Thread’in de yukarıda saydığım dezavantajlarını barındırmayan bir yapı.

Üçüncüsü madde yani hibrit sistemler ise bu yazının konusu değil.

JavaScript burada belli ki bir tercihte bulunmuş. Nasıl .NET’e, Java’ya, Python’a pointerları yönetme gücünü bize bırakmadığı için kızmıyoruz, JavaScript’in de “JavaScript yazılımcısının bu kadar low-level optimizasyonlarla işi olmamalı” kararına hem katılıyor hem de saygı gösteriyorum. Node.js gibi single-thread üzerinden olmasa da event-driven mimariyi nginx’in, lighttpd’nin, tornado’nun, netty’nin de benimsediğini eklemek isterim. Dolayısıyla “event loop öcü değil” diyebiliriz.

Yarın öbür gün Thread’ler kolaylıkla JavaScript’e getirilebilir ve platformdaki yerini alabilir. Node.js de .NET runtime’ı gibi hibrit bir yapıya doğru geçiş yapar, teknik olarak mümkün bu. Fakat Thread gibi mekanizmaların yanlış kullanımı (ki çokça rastlanır) performanstan çok performans kaybı olarak yazılımcıya geri döner. Bunları bazen tam olarak fark edemezsiniz bile.

**İddia 10: Backend için nonblocking IO kullanışlı değil**  
[Değil mi?](http://stackoverflow.com/questions/10570246/what-is-non-blocking-or-asynchronous-i-o-in-node-js) Ben aksine, özellikle yukarıda da bahsetmiş olduğum mesajlaşma — kuyruklama — işleme — iletme işlemleri için tek bir CPU core’unun ve RAM veriminin maksimize edilerek kullanılmasının oldukça önemli olduğunu düşünmekteyim. Hardware’da pipelining’den tutalım birden fazla core içeren işlemciler kullanmamıza kadar elimizdeki her teknoloji işlemlerin nonblocking gerçekleşmesini hedef almışken biz işin software kısmında neden nonblocking IO’yu es geçiyoruz ki?

.NET 1.0'dan beri içinde Threading bulunmasına rağmen, 4.0 sürümü ile gelen “Task Parallel Library”nin pazarlamasını paralelizm üzerinden yapmıştı.

Dolayısıyla nonblocking IO’nun backend için yüksek işlem ölçeğine gidildikçe öneminin arttığını düşünmekteyim.

**İddia 11: Callback Hell’den Promise’lere oradan Async/Await’e geldik**  
Evet, iddia doğru olmasına rağmen bunun eleştirilmesini sıkıntılı buluyorum. En azından bir dilin gelişip olgunlaşmasına karşı çıkacak durumda olduğumuzu düşünmüyorum.

.NET’deki async/await’in JavaScript’e getirilmesini “tekerleği yeniden keşfetmek” olarak tanımlamaktan çok, başarılı bir modelin aynen uygulanması olduğunu düşünmekteyim.

.NET’de 1.1'den itibaren yer alan AsyncCallback/IAsyncResult tipleri JavaScript’deki Promise’e benzer görevde bir nesne tipiydi. 2012'de .NET 4.5 ile birlikte vitrindeki yerini alan async/await’in de JavaScript tarafından benimsenmesiyle bana göre *Callback Hell* olarak tanımladığımız sorundan kurtulmuş olduk.

Ayrıca eklenmesi gereken bir not da .NET’in async/await’in kazanımından sonra kendi kütüphanesindeki metodları mümkün olduğunca async olarak yazmaya başladığıdır.

JavaScript’in kendi içerisinde yaşadığı bir problemi başarılı bir uygulamayı benimseyerek aşıyor olması bana kötü değil, bilakis iyi bir strateji olarak geliyor.

**İddia 12: Node.js sezgisel değil**  
Genellikle bu eleştiriler Node.js API üzerinden şekil aldığı için en hak verdiğim iddia bu.

Yine de savunma makamı görevimi bozmaksızın API’ın her zaman değişebileceğini, maskelenebileceğini düşünmekteyim.

Özellikle Fatih Kadir Akın’ın yazısında callback üzerinden yaptığı eleştiriler Node.js tarafından kafa yorulduğunda aşılamayacak bir durum değil. Başka bir deyişle henüz bir PHP’den bahsetmiyoruz.

Örneğin ileride Node.js API’ının callback parametresi almayan kullanımları Promise döndürür, biz de bunlara da bir `await` ekleriz böylece herkes memnun olur.

```javascript
let file = await fs.readFile(“./a.txt”); console.log(file) //=> beklediğim şey.
```

Yine `SetTimeout` yerine bir `await delay(ms)` ile callback'den kurtulabilmemiz mümkün.

```javascript
console.log(1); await sleep(2000); console.log(2); console.log(3); await sleep(1000); console.log(4); // buradan devam ediyoruz :) promise.resolve'a da gerek yok :)
```

Böylece ben de async/await’e kullanım örnekleri vermiş oldum.

**İddia 13: Konvensiyon kötü, kod düzeni mevcut değil**  
“Büyük mimariler için çok kötü” iddiasında da kod organizasyonu demiştim. Bu da benzer bir konu. Yazılımı tasarlayan kişiye bağlı olarak sanat eseri de, çöp de çıkartabileceğiniz bir malzemeden söz ediyoruz.

.NET ve Java’nın “framework” odaklı platformlar olduğunu unutmayalım. Bu platformlar aynı zamanda uyulması gereken dizin yapısını da beraberinde getiriyor.

Fakat C/C++/PHP’de nasıl sabit bir yapıdan ve konvensiyondan bahsedemezsek JavaScript için de bu sabit yapıdan bahsedemiyoruz. Fakat bu alana dil girmedi diye dil veya Node.js eleştirilmemeli. Bu durum aksine bize bir özgürlük sağlamakta. Kısacası isteyenin istediği konvensiyonu takip edebilmesi konvensiyon olmaması anlamına gelmiyor.

Bu özgürlüğün bir avantajı da 50–100 satırlık bir .NET projesini önerdiği konvensiyon nedeniyle tek bir parça haline getiremezken, aynı JavaScript kodunu Amazon Web Services’da lambda’ya atıp mikroservise dönüştürebiliyorsunuz.

**İddia 14: Çok fazla transpiler karmaşası var**  
Evet, kesinlikle! Fakat bunu JavaScript’in ancak bugünlerine özel bir durum olarak okumak gerekli. Oldukça büyük, ihtiyaca yönelik değişiklikler bir anda dile eklendi ve V8'i geliştiren ekip buna adapte olmakta sıkıntılar yaşadı. Ben önümüzdeki sene bu konuyu tekrar konuşuyor olacağımızı düşünmüyorum.

**İddia 15: Statik type’lı diller daha olgun ve güçlü**  
Gereksinimler ve bunların tespit edilmesi işimizde büyük önem sahibi. Diğer yandan yazılım ekibinin bilgi birikimi, yeteneklerini hangi dilde daha net ortaya koyabildiği gibi pratik parametreler de tercihlerimizi etkileyen faktörler.

Ben kodlamaya 90larda başlamış biri olarak;

*   Pointerların, memory yönetiminin asla otomatik yönetilmemesi gerektiğini,
    
*   Interpreterlardan programlama dili değil ancak script olabileceğini,
    
*   Managed platformların asla başarıya ulaşamayacağını,
    

iddialarını bolca duydum. 2000'li yıllarda yukarıdaki önyargıların bir çoğunun çürüdüğünü söylemek yanlış olmaz.

Ben 2010'lu yıllarda da strictly-typed yaklaşımların “pointer”lar gibi geride bırakılacağını düşünmekteyim. Tabii ki type-hinting yaşayacaktır ama runtimeların konsantrasyonu dynamic type yorumlamasına daha da yanaşacaktır.

Big data işlemekten bahsedip JSON okumak için 30 satır kod, 20 explicit type casting’de bulunulduğumuzda sezgisellik de konvensiyon da geri planda kalmaya başlıyor.

İşte bu karmaşada benim “kontrolde vites arttırma” olarak ifade ettiğim bir durum gerçekleşiyor.

Eğer yazacağımız uygulama için Node.js de, Java da, C++ da uygunsa,

Benim ilk tercihim mümkün oldukça -zaman ve efor tasarrufu kaygısıyla- Node.js kullanmaktan yana olur.

Daha çok mu kontrol gereksinimi duyuyorum, Thread yönetimi mi yapacağım. Node.js’in üzerini çizip Java’yı gözüme kestiririm.

Yine mi tatmin olmadım? Pointer’a kadar inmem mi gerekiyor? Streamler üzerinde mi çalışacağım? C++ veya C ile yoluma devam edebilirim.

Özetle daha olgun platformlar var evet, ama Node.js’in de avantaj olarak bize sunduğu gerçekler var.

Sunduğum karşı fikirleri çürütecek itirazlar geldikçe veya yeni argümanlar eklendikçe bu yazıyı geliştirmeyi planlamaktayım. Onun için yorumları memnuniyetle yanıtlamak isterim :)
