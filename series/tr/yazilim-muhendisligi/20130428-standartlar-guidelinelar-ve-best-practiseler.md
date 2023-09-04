# Standartlar, guidelinelar ve best practiseler

Yazılım firmaları her ne kadar hizmet/çözüm sağlıyor olsalar dahi, sektör olarak
somut çıktımız yalnızca kod üretiminden ibaret. Bu üretim süreci boyunca code
review’ından, configuration management’ına kadar bir dizi araç kullanıyoruz.

Ben kişisel bir tercih olarak Crucible gibi araçlardan aldığım yardımın yanısıra
iki haftada bir üretilen kodu hardcopy olarak inceliyorum. Ekip arkadaşlarımın
ve açık kaynak olarak elime ulaşan bu kodları incelemek beni bir anlamda
eğitiyor.

Bu sürekli eğitim sürecinin bana öğrettikleri arasında önemli bir payı şu
çıkarım oluşturuyor:

- Olası bugların, regressionların, uyum sorunlarının büyük bir çoğunluğunun
  standartlar ve guidelinelara uyulmadığı noktalarda,
- Performans kayıplarının ve anlaşılmaz kodların ise best practise’lerin
  uygulanmadığı senaryolarda,

meydana gelmekte.

Bu nedenle genel kanının aksine yazılım hatalarının dikkatsizlikten değil,
araştırma ve eğitim eksikliğinden kaynaklandığını düşünmekteyim.

Eğitim aldığım iki farklı üniversitenin yazılım bölümlerinin çatısı altında
standartların anlatıldığına ve öneminin vurgulandığına denk gelmemiş olmam basit
bir rastlantı olmamalı.

Mevcut durum hakkında elbette derin study case’ler yapılarak incelemek daha
doğru olur fakat ben burada kendi perspektifimden yorumlarımı paylaşarak da bir
noktaya dikkat çekebileceğimi düşündüm.

Öncelikle yukarıda kullandığım kavramlar arasındaki farkları açıklamak
gerekirse:

**Standart**, özellikle platformlar ve kültürler arası iletişimler — aktarımlar
için kullanılır. Örneğin Unicode standartı sayesinde bugün Facebook gibi bir
platformda kril alfabesiyle yazılmış bir yazıyı ekranımızda okuyabiliyoruz.
Unicode’dan önce browser’ın dil ayarlarından bir kaç ayar değişikliği yapmamız
gerekirdi, bunun sonucunda da artık alfabemizde kullandığımız “ğüşöçı” gibi
karakterleri görememeye başlayacaktık. Kısacası siz unicode gibi bir standartı
yazılım içerisinde kullanmadığınızda yazdığınız iletişim formu japonca destek
sayfası olan bir firma tarafından kullanılamayacak.

**Guideline** ise bu kadar geniş çaplı bir mesele değil, bulunduğunuz ekipçe
proje başlarken gerek requirementlara gerekse keyfinize göre karar
verebileceğiniz bir dizi kurallar bütünü. Kod yazım kurallarından tutun,
veritabanında her kaydın ne zaman değiştirildiğine dair bir field kullanıp
kullanmayacağınıza yönelik kararlardan bahsediyorum.

**Best practise**’i ise bir işi yapmanın en doğru yolu olarak özetleyebilirim.
Tüm kullanıcıları veritabanından liste olarak çektiniz, bu kullanıcıların her
birinin aynı zamnada kaç yorumda bulunduğunu yazmak istiyorsunuz fakat
veritabanı veya veri depo yapınız basit bir JOIN ile işinizi görmeyecek şekilde
tasarlanmış. 20 kullanıcının listelendiği döngüde 20 kere ayrı sorgu yapmaktansa
olayın en başında 20 kullanıcının kimlik bilgilerini alıp, bu bilgilerle tek bir
seferde yorumları çekip kullanıcılara pay etmek çoğu zaman best practise’dir.

Benim naçizane görüşüm çalışmalarımızda bu kavramlarla “aşina” olmak yaptığımız
işin kalitesini yükseltecektir.
