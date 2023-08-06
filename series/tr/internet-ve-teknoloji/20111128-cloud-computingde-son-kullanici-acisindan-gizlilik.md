# Cloud computing’de son kullanıcı açısından gizlilik

Geçtiğimiz hafta ODTÜ’nün KKTC kampüsünde gerçekleşen Cloud Computing and Internet Security Seminer’ine katıldım. IBM, Tubitak ve Kaspersky’den gelen konuşmacılar temsili olarak geldikleri kurumların Cloud Computing’e nasıl baktıkları hakkında bende bazı izlenimler bıraktılar.

Cloud Computing Client-Server mimarisindeki “Server”ın monarşik rolünü tamamen kaldırıyor. Ve devamında cloud avantajlarını kullanmak isteyen her organizasyon/proje için hem yazılım hem de donanım olarak sıfırdan bir yapılandırma gerektiriyor. Bu da bir çok IT firması için yeni fırsatlar anlamına geldiğinden Cloud Computing’i IT sektörünün yeni para kazanma metodu olarak değerlendirmeliyiz.

Her ne kadar servis üreten yazılım firmalarının güçlenmesi beni mesleki olarak memnun edecek olsa da, bu senaryo benim gibi özgürlükçü birinin zihninde ister istemez kaygılar oluşuyor. İşyerleri için Dedicated Hostinglerin, kişiler için de External Disklerin azaldığı yerlerine verilerin servislere taşındığı bir dünyadan bahsediyoruz. Başka bir değişle kişisel/kurumsal datanız üzerindeki sahipliğinizi tamamiyle servisi aldığımız firmanın/organizasyonun sanal storage’ı ile paylaşıyoruz. Bu firmalarınsa bizim haklarımıza ne kadar saygı göstermesi gerektiğini ise ancak ve ancak geleneksel yasalar belirleyebiliyor.

“E yasa işte?” demek yeterli olmuyor. Facebook ve Google gibi firmalar şimdiden kişisel bilgilerimizle bizi profilleyerek yasal yollardan olsa dahi bizim tercih etmeyeceğimiz şekilde gizlilik haklarımızı çiğneyebiliyorlar. Şu an bir telefon aldığınızı, arayanın mobil operatörünüzün olduğunu ve “x firması ile bilgilerinizi paylaşmak isteyip istemediğini” varsayın, cevabınız %80 hayır olurdu. Fakat social networkler ve çeşitli servisler bunu haberiniz olmadan yapıyorlar.

Bir çözümüm olmasaydı bu yazıyı yazmayı da düşünmüyor olacaktım, işte benim çözümüm. Cloud Computing, OpenSource Community’den ilham almalı ve servis-kullanıcı ilişkisini lisans zorunluluğu ile yönetmeli. Kullanıcıların ortak kullanacağı lisans tipleriyle şu an Apple’dan tutun Google’a kadar bizim hakkımızda bilgi sahibi olan kurumların ellerindeki datamız üzerinde söz sahibi olmamız sağlanabilir. Aklıma gelen örnek bir kaç kullanım şekli:

*   Kişisel bilgileri servislerin kullanımına açmak,
*   Kişisel bilgileri ancak servisde tanımlı kişilerin (kullanıcının kendisi, arkadaş listesi, v.s.) kullanımına açmak,
*   Kişisel bilgilerden edinilecek gelirin kullanıcıyla paylaşılmak kaydıyla bilgileri servisin kullanımına açmak,
*   Kişisel bilgileri yalnızca gelir amacı taşımayan organizasyonlarca kullanımına açmak.
*   Kişisel bilgilerin servis tarafından kullanılmaması.
*   Kişisel bilgilerin ve yedeklerinin servis üzerinden kullanıcının istediği an silinmesi.
*   Kişisel bilgilerin servis üzerinden kullanıcının istediği an download edebilmesi veya başka bir servise taşınması.

“Taşınması” evet, madem Cloud Computing’den bahsediyoruz ben Gmail üzerindeki tüm bilgimi Fastmail’e geçirmek için işlemleri başlatabilmeliyim. XMPP gibi protokoller arası konuşma sağlayan ekstra protokollere Cloud sistemlerin kullanıcılar ve abonelikler üzerinden konuşacağı varyasyonları olması gerekiyor diye düşünüyorum. Aslında bu alanda prototip olarak bir çalışmam da mevcut, bir ihtiyaç olduğu gerçek.
