# WordPress’in kerameti

Konuyla ilgili twitter’da çok değerli Erhan Yakut’un tweet’ine yanıt vermemle
başlayan tartışmayı, söyleyeceklerim biraz uzun olduğu için buraya taşımak
istedim.

Tweet’i buraya almak gerekirse:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1659040552520/q8SgYR7DR.png)

%[https://twitter.com/yakuter/status/1134379969608540161]

En üstteki 10 milyon web sitesinden %34’ünün WordPress çalıştırdığı bilgisine
istinaden PHP’e ufak bir övgü var burada. Burada Internet’in en büyük 10 milyon
sitesinden bahsettiğimizin tekrar üzerine basayım, bu bilgiyi bir cebimize
atalım.

Ben ilgili tweet’e vermiş olduğum yanıtta şunu savundum:

%[https://twitter.com/eserozvataf/status/1134380938350202880]

Bunun karşılığında birçok kişi karşı arguman olarak “PHP’nin kolay
kurulabilirliği”, “5 TL’lik shared hosting’de çalışabilmesi” cümleleriyle
portatifliğini öne sürdüler. Şimdi bunlara yanıt vermek isterim;

Öncelikle PHP’nin portatifliği gerçekten takdire şayan. Bu portatifliğin
getirisi olarak artılarının/eksiklerinin olduğunu ve implementasyonunda
“uygulama mantığı” yer almadığı için birçok izolasyon sorunları yaşanabildiğini
şerh düşerek burada takdirimi yenileyeyim. FaaS seven ve evanjelistliğini yapan
biri olarak, PHP portatifliğini övmesem eksik kalır.

Ancak esas yanıtım şu: WordPress’in yaygınlığında elbette kolay kurulum ve ucuz
maliyet genel kullanım için bir etkendir; Ancak en üst 10 milyon web sitesinden
bahsederken bu %34’lük payda portatiflik etkenlerini gözlemleyebileceğimizi
düşünmüyorum. Türkiye’de dahi ortalama 2–3 dedike sunucu aracılığıyla host
edilen WordPress tabanlı web siteleri varken ve bu firmaların ceplerinden zaten
bakım maliyetleri çıkıyorken bu etkenlerin etkisi bana uzun süredir kurumsalda
çalışan bir profesyonel olarak gerçekçi gelmiyor.

Bir deneyimim ile devam edeyim, geçen yıl çalıştığım birime Türkiye’nin ilk
3’deki bir holding’in şirketlerini de etkileyecek çapta bir karar için uzman
görüşü soruldu. Buna istinaden CMS’ler ve platformlarla ilgili deneyimlerim
nedeniyle işi ben üstlenip bir rapor hazırladım. Bu iş öyle bir çaptaydı ki
holding bünyesinde “içerik” kelimesi geçtiği anda artık nihai olarak seçilen
çözüm kullanılıyor olacaktı. Hatta buna bağlı olarak bünyesinde olduğum firmanın
dışarı vermiş olduğu teklifler dahi bu altyapı gözönünde bulundurarak
verilecekti.

Rapor tamamlandığında yaklaşık 7–8 çözümü marketlerinden desteğine, lisanslama
politikalarından güvenlik açıklarına birçok alanda değerlendirmiştim. Vermiş
olduğum uzman görüşünde WordPress’i 5 üzerinden 4,5 puanlamama ve
değerlendirmede WordPress’e en çok yaklaşan ekosistemin puanı 2,5-3’lerde
kalmasına rağmen nihai karar WordPress olmadı.

Çünkü WordPress’in yumuşak karnı PHP idi. Ne bir holding gibi bir yapı için
hemen elde edilebilir, çok ciddi garantiler veren (kişisel garantilerin ötesinde
şeylerden bahsediyoruz) bir yetkinliğe ulaşabiliyorlardı ne de PHP’nin dolaylı
ya da dolaysız şekilde bir güvenlik açığı oluştuğunda/yük aldığında buna
karşılık verebilecek bir operasyon — kurumsal destek planları oluşturulabilirdi.

Raporumda “kolay kurulabilir” ve “portatif” gibi zaten operasyon işi olan
kısımları değerlendirmeye almadığımı belirtmeme gerek yok sanırım.

Sözün özü tekrar başa geleceğim. Internet’in en üst 10 milyon sitesinden
bahsediyoruz. Etkenler çok daha farklı.

Bu nedenle ben WordPress’in başarısını “başarılı bir ürün” olmasına bağlıyorum.
Aksi takdirde Ghost (herhangi bir rakibi) JavaScript ile değil PHP ile
yazılsaydı WordPress kadar başarılı olabilirdi diyebilirdik. Ancak böyle bir
yaklaşım yalnızca WordPress’in mevcut başarısını küçük görmek anlamına gelir.
