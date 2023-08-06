# PHP neden zamanın ruhunu yansıtmıyor?

Sabah twitter üzerinden “php’nin kotu kararlar aldigini dusunuyorum. 4–5 sene once hem modern hem de populer bir dil olmayi basariyordu php. bugun ise basaramiyor.” yorumunu yapmıştım. Kapalı bir ifadeydi, haliyle nedenlerine yer verilmemişti.

Biraz açmak istiyorum.

4–5 sene önce PHP neler yapıyordu:

*   MySQL paketi yetersiz olduğu için MySQLi’yi ortaya atıyordu. Transaction desteği geliyordu.
*   PHP 5 ile object oriented yapısını yeniden ele almış PHP durak vermiyor, SPL ile dile yeni objeler katıyordu.
*   PHP’nin en güçlü yanı kütüphanesiydi sürekli yeni fonksiyonlar ekliyorlar, bunlara özellikler getiriyorlardı.
*   PDO ile veritabanı katmanını soyutlaştırıyor. Mümkün olduğunca abstraction üzerinden yazılımcı problemlerini çözmeye çalışıyorlardı.
*   Düzenli kodlar üretilebilsin diye en popüler framework’ü CodeIgniter olmasına rağmen topluluğa öncülük ediyor ve Namespaceleri ortaya atıyordu.

Bugün neler yapıyor:

*   Yalnızca performans tarafında iyileştirmeler yapıyor.
*   Dil sentaksını genişletmeye çalışıyor.
*   Kod tekrarının daha az olması için anonymous method ve classları oyuna sokuyor.

Neler yapmıyor’a geçmeden önce “PHP her request’de tüm kodu tekrardan interpreter’dan geçirip işlem tamamlandığında bunu yok eden bir yapıya sahip” olduğunu hatırlayalım.

*   Paket yönetimi ile ilgili sırtını tamamen composer’a dayıyor. Her requestte tekrardan dependency sınıfları teker teker aranıyor. Bunu kendi application server’ında çalışan Node.js bile iç mesele olarak halletmiş.
*   Asenkron işlemler yapmak imkansız. (async ile threading farklı konulardır)
*   Mikroservislerin, container bazlı uygulamaların üretildiği dünyada soket iletişimi nonblocking değil.
*   Zamanında PDO, MySQLi için hem sınıf hem fonksiyon interface’i sunan PHP değilmiş gibi, ısrarla isimlendirme sorunu olan fonksiyonları statik kütüphanelere taşımıyor. strpos() -> Str::pos(), str\_replace() -> Str::replace() gibi.
*   Symfony, Laravel, Doctrine gibi en popüler frameworklerinin kullanmasına, topluluktan talep olmasına rağmen rağmen ısrarla annotation desteği getirmiyor.
*   Application context’i yok. Her requestte aynı kodlar neden bootstrap edip duruyor anlayamıyorum. Artık CGI’a mahkum değiliz.

Ben PHP 7’nin changeloglarına baktığımda performans iyileştirmelerine rağmen halen cpu’nun ancak tek core’unu kullanabilen, async işlem yapamayan, modern yazılım ihtiyaçlarını karşılamamaya başlayan, topluluğuna önderlik edemeyen bir ürün görüyorum. 1999’dan beri yazdığım PHP için bunu 2 senedir her geçen gün daha fazla hissediyor ve yeni projelere Node.js ile başlayan biri olarak PHP’de bir şeylerin değişmeye başlaması gerektiğini düşünüyorum. Karşı tezleri memnuniyetle dinlemeye hazırım.
