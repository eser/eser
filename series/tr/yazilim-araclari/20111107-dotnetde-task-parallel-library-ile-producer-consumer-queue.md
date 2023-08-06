# .NET’de Task Parallel Library ile Producer/Consumer Queue

Diskden bir klasör içerisindeki tüm dosyaları okumak, elimizde bulunan birden fazla URL adresinden feedleri veya web sayfalarını download etmek ve elimizdeki verilerin güncel kopyalarının olup olmadığını kontrol etmek. Bütün bu örnekler için genellikle bir döngü yapısı kullanırız. Fakat kodu yazma amacımız belirli bir sırayı takip etmesi değil de, tüm sistem kaynaklarını kullanarak işlemi gerçekleştirmesi olduğunda birden fazla thread ile işlem yapmak en uygun çözümdür.

Threading’le ilgili biraz bilginiz varsa “Producer/Consumer Queue” kavramını duymuşsunuzdur. Bu kavramı en basit haliyle “dış bir kaynaktan beslenen iş kuyruğu, ve bu iş kuyruğundan objeleri çeken birden fazla thread” olarak tanımlayabiliriz.

Klasik thread yaklaşımında kullanacağımız kadar thread oluşturur ve bu threadlerin sürekli veya iş kuyruğu tamamiyle boşalana kadar kuyruktaki objeleri aldığı bir yapı oluştururuz. Yönetimi low-level bilgi gereksinimi istediğinden zor ve mantık hatalarına açık bir yöntemdir.

.NET CLR bu nedenle .NET 2.0 ile birlikte ThreadPool yapısı, ardından .NET 4.0 ThreadPool üzerine oturttuğu daha high-level bir yapı olan TPL yani Task Parallel Library ile oluşabilecek sorunlar konusunda yazılımcılara çözümler sunmakta. ThreadPool ve TPL’in çalışma mekaniği yapılacak her kalem iş’e bir Task (Görev) olarak bakmak, ve bu işleri yazılımcının yalnızca tanımlayıp kodların işletim kısmıyla ilgilenmemesini, ancak bu görevleri iptal etmek veya görevler tamamlandığında haberdar olmak gibi genel kısımlarda yazılımcının kod yazmasını sağlar.

Fakat .NET 4.0 ile gelip, işlemcinin sanal/fiziksel tüm çekirdeklerini sonuna kadar kullanmamızı sağlayan TPL’in bir kaç eksikliğinin olduğunu fark ettim. Çalışacak maximum thread sayısına biz karar veremiyoruz, dolayısıyla vermiş olduğumuz her kalem iş .NET tarafından içeride bir yerlerde kuyruğa dahil edildiğinden kod ile bu kuyruğu izleyemiyoruz.

Bu nedenle kendi yazdığım ve aslında .NET’de oluşturduğum bir kütüphane olan Tasslehoff’un parçası olan `ChannelTaskQueue`’nun kodlarını GitHub üzerinden paylaşıyorum: 

%[https://github.com/eser/tasslehoff-library/tree/master/Threading]
