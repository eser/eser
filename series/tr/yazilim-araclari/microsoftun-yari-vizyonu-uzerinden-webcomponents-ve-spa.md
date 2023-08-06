# Microsoft’un yarı vizyonu üzerinden WebComponents ve SPA

İyi bir kelime seçimi gibi duyulmasa da “yarı vizyon” tam olarak anlatmaya çalışacağım senaryoyla oturuyor.

Microsoft’un firma ve yaptıkları işler hacminde büyüklüğü tartışılmaz. Fakat birçok başarısız girişimini gözlemliyor, ciddi oranda profesyonelin geçim kaynağını sağlayan ekosistemlere sahip olmalarına rağmen düşük güvenilirliğe sahip olduğunu biliyoruz. Bu durum firmanın iyi yaptığı işlerin yanısıra bir o kadar kötü yaptığı işlerin de olduğu konusunda bize ipucu veriyor.

Yazı aslında Web Teknolojilerine odaklı fakat Microsoft’un bulunduğu konumla ilgili çarpıcı bir örnek paylaşmak istiyorum, mutlaka hikayenin bir kısmını siz de duymuşsunuzdur. Steve Jobs henüz iPad ile çıkagelmemişken Microsoft’un 2000lerin başında “Tablet PC”yi insanlara teşvik etme çabaları vardı. Yıl 2001'di, şu anda televizyonda reklamlarını son bir yıldır izlediğiniz katlanılabilir notebook’larda olduğu gibi tablet pc’nin ekranı katlanılabiliyor, henüz dokunmatik ekranların yaygın olmadığı o tarihte bir kalem yardımıyla Windows’u veya ARM işlemcili kopyaları için Microsoft’un Windows CE ismiyle geliştirdiği mobil işletim sistemini (iOS ve Android’den önce!) sunuyordu sizlere. 2001'de Microsoft’un bu arzına talep gelseydi olaylar çok farklı gelişecekti. (Kaynak: [Wikipedia](https://en.wikipedia.org/wiki/Microsoft_Tablet_PC))

Gelelim bu güne, benim gibi Web Teknolojileriyle de yakınen ilgilenen yazılımcılar şu anda fırında ısınmayı ve gelecek senelerde karşımıza çıkmayı bekleyen yeni web standartları için heyecanlanıyordur.

Angular 1.5, Polymer, React gibi kelimeleri duyduysanız Web Components; Electron’u, SPA’yı duyduysanız HTML Application kavramlarını biliyorsunuzdur. Bu iki kavram da Microsoft’un henüz JavaScript’i ECMAScript standartlarında kabul etmeyip JScript olarak isimlendirdiği, “DHTML” ismi çevresinde web uygulamaları konusunda kullanıcı tabanını heyecanlandırmaya çalıştığı, Internet Explorer’ın en büyük pazar payına sahip olduğu dönemlerde düşünülmüş ve Internet Explorer’a hatta bir kısmı Windows’a entegre edilmiş konseptler.

HTA ([HTML Application](https://en.wikipedia.org/wiki/HTML_Application)): Çalıştırılabilir bir HTA dosyası aracılığı ile tıpkı masaüstünüzde çalışan diğer uygulamalar gibi web uygulamanızın bir pencerede çalışması sağlanıyor. Üstelik farklı alt sayfalara linkler de yok, Microsoft diyor ki tek bir HTML ve script yığını ile tek HTML sayfadan oluşan bir uygulama yapabilirsin. Ekstra olarak bazı sistem çağrıları ve pencere özelliklerine ulaşabiliyorsunuz.

HTC ([HTML Components](https://en.wikipedia.org/wiki/HTML_Components)): Oluşturduğunuz bir element’e (veya html tag diyelim) bir davranış tanımlayıp JavaScript aracılığıyla nesneye gelen olay/eventleri o bileşene özel değerlendirebiliyorsunuz. Angular’ın 1.5, React’ın ve Polymer’in yapmayı sağlandığı şey de bu değil miydi?

Şu soruyu sormadan edemiyorum: Internet Explorer 5.5 gibi 2000'de çıkmış bir browser’ın getirdiği yenilikleri Microsoft topluluğa benimsetseydi ne olurdu? Bu kavramların özelliği veya benim anlatmaya çalıştığım “Microsoft ilk yaptı” değil, bu konseptlerin şu anda W3C standartlarına girmiş, yani topluluğun istediği ve benimsediği kavramlar olması. 15–16 sene önce DHTML üzerine çalışmalarım olmasa bugün ben de bu konseptlerin yeni yeni ortaya atılıyor olduğunu düşünecektim ama değiller.

Buradan hareketle Microsoft’un “ileriyi” görüp ihtiyaçlara göre bir çözüm ürettiğini fakat zamanlama, motivasyonunu insanlarla paylaştırma, insanlara fikrini benimsetme gibi konularda oldukça eksik kaldığını gözlemleyebileceğimizi düşünüyorum.

Buraya kadar “vizyonerlik” tanımı bozulmuyor esasında, “yarı vizyon” tespitim bundan sonrası ile ilgili. Microsoft da ilk harekete geçtiği andan itibaren kavramı geliştirmek yerine vazgeçmeye yakın bir çizgide duruyor. Silverlight, Windows Phone, WinFS gibi Microsoft’un yalnızca son 3 senede vazgeçtiği ürünlerden ciddi bir liste oluşturabilmek mümkün.

Artık topluluğu çağıran değil, topluluğun olduğu yere gitmeye çalışan daha akıllı bir Microsoft var gibi görünüyor ama bunun henüz TypeScript dışında bir ürünü olduğunu gözlemlemiyorum. Umarım zaman bize Microsoft’un potansiyelini gerçekleştirebildiği daha çok örnek gösterir.
