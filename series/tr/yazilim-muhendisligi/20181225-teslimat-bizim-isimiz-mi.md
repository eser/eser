# Teslimat bizim işimiz (mi?)

Bana göre işim hiçbir zaman bir çözüm sağlanana dek kod yazmak olmadı. Hatta
maaşımın karşılığını geliştirme yaptığım sürelerde değil, bunun dışında kalan
sürelerde hakkettiğimi düşünüyorum. Buradaki argümanım çok basit: “Hedef çözüm
sağlamak ise karmaşık veya sorunlu bir işi nihayete erdirebilmek için karmaşık
bir çözüm ortaya koymak için çalışabilirsiniz. Veya önce problemi sadeleştirip
onun dengi sadelikte çözüm üzerinde çalışabilirsiniz.”.

Karmaşıklıktan uzaklaştırılan ama yönetilmeye devam edilebilen her iş zamanımız
başta olmak üzere her türlü sınırlı sermayemizden edilen net kazanç benim için.

[Twitter](https://twitter.com/eser)’da, herhangi bir
[konuşma](../../../presentations/tr/README.md)da denk geldiyseniz genellikle
Serverless, Cloud ve DevOps çözümleri konusunda az da olsa evangelist
yaklaşımımı fark etmişsinizdir. Bu konuların beni heyecanlandırmasının nedeni,
hepsinin temelinde işi gerçekleyenler için karmaşık olan problemleri onlardan
uzaklaştırıp, daha soyut bir üst katmanda çözümler üretmelerine imkan veriyor
olmaları. Bugün tam da bu kavramların kesişimiyle ilgili bir şeyler aktarmak
istiyorum. Bir yazılımın teslimat süreci, kulağımıza daha aşina gelecek
ifadelerle belirtmek gerekirse “derleme işleminden başlayarak canlıya çıkana
kadar gelişen olaylar”.

2006’da çalıştığım devBiz’e girerken şirket ortaklarından ve benim için değerli
isimlerden biri olan Hakan Eskici bana Mike Gunderloy’un “Coder to Developer:
Tools and Strategies for Delivering Your Software” kitabını vermişti. İlk kez
yazılım için entegrasyon (integration), teslimat (delivery) ve yükleme
(deployment) tanımları ile orada karşılaşmıştım.

Mike Gunderloy — Coder To Developer

Bu kavramları ezberimden aktarmam gerekirse,

**Integration**: Bir geliştirme sürecinde yapılan tüm ekleme ve değişikliklerin
yazılımın tamamına ve bağlılıklarına olan uygunluğu/entegrasyonunu sınayan ve
sağlayan süreçtir. Genellikle çıktısı test edilmiş, derlenmiş yazılım dosyaları
olur.

**Delivery**: Bir yazılımın paketlenmesi ve bu paketin hedefine ulaştırılma
sürecidir. Genellikle çıktısı lisansları, konfigürasyonu, imzaları ve sürüm
bilgisi eklenmiş halde kuruluma hazır yazılım paketidir. Docker Image’dan tutun,
bir zip dosyasına herhangi bir biçimde paketlenmiş olabilir.

**Deployment**: Bir yazılımın bir sisteme/ortama yüklenmesi ve yüklendiği
ortamda çalışmaya başlayarak şekilde ayağa kaldırılması sürecidir.

Siz bu kavramları son yıllarda başlarına bir “Continuous” ifadesi ile birlikte
duymaktasınız, **Continuous Integration**, **Continuous Delivery** ve
**Continuous Deployment**. Bu da yapmış olduğunuz bir değişikliği merkezi bir
Git/SCM sunucusuna gönderdiğiniz anda bu süreçlerin otomatik olarak başlaması ve
tanımlanan görevlerin sizin tetiklemenize gerek kalmaksızın kendiliğinden
işletilmesi, eğer bir hata ile karşılaşılırsa da bundan haberdar olmanız
anlamına geliyor.

Bu süreçlerin tümünü işler hale getirmek ve işletmek günümüzde DevOps
yetkinliğine ve/veya kimliğine sahip kimselerin yükümlülüğü. Ancak her ne kadar
her gün bir yenisi tanıtılan DevOps araçları ve pratikleri ile DevOps
süreçlerinde hedeflere ulaşılsa da; elinizdekilerle bir süreci uçtan uca
tasarladığınızda mutlaka aklınızdakini/beklentinizi birebir uygulayamadığınız
birçok durum oluşuyor. Hatta elinizdeki senaryo ve hizmet bağımlılıkları
nedeniyle çok temiz, esnek ve olan biteni kavramanın zaman almayacağı bir yapı
yerine kompleksiteye boğulmuş olmaktan kaçılamıyor.

Konuyla ilgili Fatih Kadir Akın’la bir konuşmamızdan sonra durumun vehametini
şöyle bir tweet’le paylaşmıştı kendisi:

%[https://twitter.com/fkadev/status/1074972412184354816]

Peki neyi sorunlu görüyorum ve ne iyileştirilebilir? Hemen açıklayayım…

Geliştiricinin ve DevOps’un işi paket hazırlayana kadar olabilirdi. Elimizde
geliştiricilerin müdehale ettiği bir kod tabanı var. Bu kod tabanının
derlenmesi, test edilmesi, buradan docker image oluşturma v.b. paketlenme
işlemlerinin _pipeline as code_ pratiğiyle DevOps’cular tarafından da
sağlandığını düşünelim. Buraya kadar bir sorun yok.

Ancak bu noktadan sonra DevOps’cunun oluşan çıktının nereye, hangi senaryoyla,
ne zaman teslim edileceği ve yükleneceğini tasarlaması; buna bağlı olarak
başarısızlık, felaket ve sistem yetersizliği durumlarında sistemlerin nasıl
davranacağına dair de önlemler alması bekleniyor.

İşte bu noktada aslında DevOps idealize edildiği gibi hem yazılımın içerisini ve
işleyişini bilen, aynı yazılım ekibinden biri/birileri olamıyor. Çünkü yukarıda
bahsi geçen süreçler için AWS hizmetlerinden, Azure’a, Kubernetes’den Packer’a,
Spinnaker’dan Jenkins’e birçok araca hakim olmak zorunda bırakılıyor. Bu da bir
DevOps uzmanı için mesainin aslında ilgili yazılımın kod tabanından uzak, bu
araçlara daha yakın geçmesine neden oluyor.

Bu sürece uçtan uca baktığımda “paketleme” olarak ifade ettiğim noktadan
sonrasını tamamiyle “karmaşa” ve “üstlenilmemesi/devredilmesi gereken bir yük”
olarak görüyorum. Bir örnekle anlatmam gerekirse; esas işi e-ticaret olan bir
web sitesinin satın alınan ürünü paketledikten sonra bir araca binip müşterisine
kapıda teslimat yapmasına benzetiyorum bu durumu. Bu da beni bu yazının
başlığındaki teslimat’ı biz mi yapmalıyız sorusuna getiriyor.

Diğer yandan iyimser kalmamı sağlayan bir etken var: Cloud Hizmetleri.

Yukarıda Serverless’ın ismini geçirmemin nedeni temelde size sunduğu en büyük
hizmetin sizi uygulama mimarisi tasarlamaktan bir nebze kurtarıyor olmasıydı.
İleride AWS, Azure, v.b. servislerin birçok senaryoda yaptığı gibi teslimat
işlerinden de bizi kurtaracak çözümler sunacağına emin gibiyim.

Zaten bugün de yine anahtar teslim bir ürün söz konusu olmasa da Container
Registry ve Function hizmetleri kullanılarak bir app service’e deployment
yaparak benzer bir süreç işletebiliyorsunuz. Hatta Azure’un App Service for
Containers’ıyla birlikte Azure Container Registry’den webhook’lar aracılığıyla
Continuous Deployment yapmanıza izin veriyor. Belki daha farklı ürünler de
vardır ancak konumuz tam anlamıyla ürünlerin getirdiği çözümler değil.

Benim tartışmaya açtığım konu daha çok süreçteki rol ve sorumluluklar üzerine.
Ben derim ki; Developer ve DevOps’un sorumluluğu oluşturduğu paketi bir
container/file storage’a yüklediği anda sona ermeli. Geri kalan noktada
yazılımın ne kadar kaynakla, ne zaman, blue/green’le mi yoksa başka bir
stratejiyle mi yükleneceği tamamiyle hosting’i gerçekleştirdiğimiz servisin
orkestrasyonuyla ilerlemeli.

Bu uzun konunun ertesinde belki aşina olmadığınız birçok kavramdan bahsetmiş
olabilirim. Eğer bu konular ilginizi çektiyse, aklınızda soru işaretleri
oluştuysa onları dinlemek adına [bir YouTube yayınıma](https://eser.live)
beklerim İlerleyen günlerde özellikle pipeline oluşturmak, CI/CD entegrasyonu,
cloud hizmetleri, serverless gibi konularla ilgili içeriklere de yer vermeye
çalışacağım.

Bir sonraki yazıya dek, sağlıcakla kalın.
