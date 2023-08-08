# Hayal kırıklığına uğramamak için sorgulanması gerekenler

Lisansüstü eğitim “öğrenci olmak” pratiği olanlar için nispeten kolay, fakat hızlı bitirmek istediğinizde neredeyse her dersin ciddi ödev/araştırmaları altında boğulabileceğiniz bir süreçtir. Ben ufak bir hile yapıp (elbetteki mevzuatta yer alan bir hakkımı kullanıp) ortalamamı yükseltmek için yazılım mühendisliği ile ilgili ek bir seçiminde bulunmuştum.

O derste aldığım en yararlı bilgi 90larda amerikan yazılım endüstrisinde production’a çıkan yazılım projesi oranının %60’larda olduğu ve bununla ilgili sektörün nasıl refleksler geliştirdiği üzerine olmuştur.

Bugün bir istatistik olsa eminim ülkemizde hayal kırıklığı ile sonuçlanan yazılım projesi oranı %60’dan yüksek çıkacaktır. Hem de önümüzde hali hazırda başarılı olan modeller ve sistemler var iken.

Hepimizin platform, yazılım ve programlama dillerinden tutun, iş arkadaşlarımıza, işverenlerimize hatta gelirimize kadar hayal kırıklıklarımız mevcut.

Ben konuyu naçizane kendi üslubumca değerlendirmek isterim. Elbette ki burada toplumsal tespitlerden çok profesyonel kalıplarda kalmayı tercih ediyorum.

Hayal kırıklığı yaşadığımız şeyi X’in yerine koyarak sormamız gereken birkaç soru olduğuna inanıyorum.

*   Bu hayal kırıklığı X’in karşılayacağını iddia ettiği ve karşılamadığı durumlardan mı dolayı mı oluştu?
*   X’in başarısızlık riskine karşı organizasyonunuzun toleranslı olup olmadığı konusunda bir analiz yapmış mıydınız?
*   X ona yüklediğiniz anlam için doğru tercih miydi? Farklı tercihler var mıydı? Bunların kıyaslaması sağlıklı yapıldı mı?
*   Organizasyonunuz operasyonunuz için kusur barındırıyor muydu? X taşımaması gereken bir yükü taşıyor muydu?

Şimdi örnek senaryo üzerinden bir uyarlama yapalım ve sorulara bir kez de bu şekilde bakalım. Diyelim ki Node.js ile yapılmış bir projeniz var ve Node.js’in size yaşattığı deneyimler nedeniyle hayal kırıklığı yaşadınız.

*   Node.js ile uygulamanızı yazdınız ve production’a çıktınız. Node.js’den kaynaklı bir memory leak ile karşılaştınız. Node.js’i tercih etmeden önce ön araştırma yapmış mıydınız? En azından “known issues”a göz geçirmiş miydiniz?

Şu anda uygulamanız çalışmaz halde bunun için alternatif bir planınız var mıydı? Önlem olarak alabileceğiniz önceden planlanmış bir aksiyonunuz yok mu? Servisin bir bölümünü geçici olarak kapatmak, kısa sürede workaround yazabilmek, v.s.?

*   En başta tek seçeneğiniz Node.js miydi? Stres test ile şu anda yaşadığınız sorunun benzerini bu tercihi yaparken oluşturabilmiş miydiniz? Madem sıfır risk toleransınız vardı Node.js gibi nispeten yeni bir ekosistem yerine daha olgun bir platform seçemez miydiniz?
*   Node.js yazabilen tek senior yazılımcınız şu anda problemi düzeltmekle mi ilgileniyor? Test yazmak, sistemi izlemek, continuous integration oluşturmak gibi DevOps operasyonlarını atlayarak mı bugünlere geldiniz?

Bu soruları çevrenizdeki insanlara, yeni gireceğiniz bir işe veya başka kavramlara da uyarlayabileceğinizi düşünüyorum.
