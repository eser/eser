# PHP neden zamanın ruhunu yansıtmıyor?

Sabah twitter üzerinden “PHP’nin kötü kararlar aldığını düşünüyorum. 4–5 sene
önce hem modern hem de popüler bir dil olmayı başarıyordu PHP. bugün ise
başaramıyor.” yorumunu yapmıştım. Kapalı bir ifadeydi, haliyle nedenlerine yer
verilmemişti.

Biraz açmak istiyorum.

2010'ların başında PHP neler yapıyordu:

- MySQL paketi yetersiz olduğu için MySQLi’yi ortaya atıyordu. Transaction
  desteği geliyordu.
- PHP 5 ile object oriented yapısını yeniden ele almış PHP durak vermiyor, SPL
  ile dile yeni objeler katıyordu.
- PHP’nin en güçlü yanı kütüphanesiydi sürekli yeni fonksiyonlar ekliyorlar,
  bunlara özellikler getiriyorlardı.
- Extensionlar sayesinde genişlemeye tam destek veriyordu.
- PDO ile veritabanı katmanını soyutlaştırıyor. Mümkün olduğunca abstraction
  üzerinden yazılımcı problemlerini çözmeye çalışıyorlardı.
- Düzenli kodlar üretilebilsin diye en popüler framework’ü CodeIgniter olmasına
  rağmen topluluğa öncülük ediyor ve Namespaceleri ortaya atıyordu.

2015'lerde PHP neler yapıyor:

- Performans tarafında iyileştirmeler yapıyor.
- Dil sentaksını genişletmeye çalışıyor.
- Kod tekrarının daha az olması için anonymous method ve classları oyuna
  sokuyor.

Özetle PHP eskiden dikey büyüyerek platforma yeni olanaklar sunarken, şimdi daha
çok özelliklerini konsolide ederek muhafaza etme konumuna geçti.

Ben bu ivmedeki düşüklüye ve eski cesaretli "yapı sökümcü" ruhun kaybına
razı olamıyorum. Hem PHP'e internallarını öğrenecek kadar yatırim yaptım, hem de
gönülden sevdiğim bir üründen bahsediyorum. Paralelde diğer programlama
dillerinin de kullanıcısı olduğum için yeni proje başlangıçlarında elim diğer
platformlara kaymaya başladı yılların PHP kullanıcısı olmama rağmen.

Öncelikle mimari bir dönüşüm lazımdı. Shared hosting'lerin olduğu dünyada CGI
üzerinden PHP devrim yapmış olabilir. Ancak şu anda containerların,
fonksiyonların portatif hale geldiğı bir dünyada PHP yeni bir şeyler
söyleyemedi. Halen “PHP her request’de tüm kodu tekrardan interpreter’dan
geçirip işlem tamamlandığında bunu yok eden bir yapıya sahip”. Evet bu kulağa
çok deterministik gelse dahi ben programlama ihtiyaçları hızla artan biri olarak
long-serving processler/application serverlar üzerinden PHP ile koşan bir
runtime da tasarlamayı isterdim.

- Paket yönetimi ile ilgili sırtını tamamen composer’a dayıyor. Her requestte
  tekrardan dependency sınıfları teker teker aranıyor. Bunu kendi application
  server’ında çalışan birçok platform dille bütünleşik bir şekilde sundu. En
  garibanları Node.js bile NPM ile PHP'den daha ileride.
- Asenkron işlemler yapmak imkansız. (async ile threading farklı konulardır)
- Mikroservislerin, container bazlı uygulamaların üretildiği dünyada soket
  iletişimi nonblocking değil.
- Zamanında PDO, MySQLi için hem sınıf hem fonksiyon interface’i sunan PHP
  değilmiş gibi, ısrarla isimlendirme sorunu olan fonksiyonları statik
  kütüphanelere taşımıyor. Cesaret eksiği büyük sorun. strpos() -> Str::pos(),
  str\_replace() -> Str::replace() gibi.
- Symfony, Laravel, Doctrine gibi en popüler frameworklerinin kullanmasına,
  topluluktan talep olmasına rağmen rağmen ısrarla dahili bir annotation desteği
  getirmiyor.
- Application context’i yok. Her requestte aynı kodlar neden bootstrap edip
  duruyor anlayamıyorum. Artık CGI’a mahkum değiliz.

Ben PHP 7’nin changeloglarına baktığımda performans iyileştirmelerine rağmen
halen CPU’nun ancak tek core’unu kullanabilen, async işlem yapamayan, modern
yazılım ihtiyaçlarını karşılamamaya başlayan, topluluğuna önderlik edemeyen bir
ürün görüyorum. 1999’dan beri yazdığım PHP için bunu 2 senedir her geçen gün
daha fazla hissediyor ve yeni projelere başka teknolojiler ile başlamaya
yaklaşmış biri olarak PHP’de bir şeylerin değişmeye başlaması gerektiğini
düşünüyorum.

Aksi takdirde shared web hostinglerde kaç tane wordpress kurulu olduğu ile gurur
duymakla yetineceğiz. Bunun yerine kariyerinin yeni başında olan insanların
PHP’yi tercih etmesi için geleceğe yönelik modern yaklaşımları benimsemek
gerekiyor.

RPCler, GraphQLler, socketlerden bahsettiğimiz dünyada, frontend tooling
yükselirken PHP bu cephelere girebiliyor mu? OOP tarafında .NET veya Java'ya
alternatif olmak istiyorsa alanının en hızlı, güvenilir ve iyi araçlara sahip
platformu olmak için atılımları var mı?

Karşı tezleri memnuniyetle dinlemeye hazırım.
