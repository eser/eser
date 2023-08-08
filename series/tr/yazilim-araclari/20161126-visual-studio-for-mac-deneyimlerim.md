# Visual Studio for Mac deneyimlerim

Her ne kadar tooling konusunda yavaş kaldıklarını düşünsem de, .NET Core cephesinde Microsoft’un oluşturduğu yol haritasında ilerlediğini hissedebilmeye başladık.

Elimizdekiler:

*   .NET Standard 2.0’ın frameworkler arasında uyumu arttırması,
*   Visual Studio for Mac’in duyurulması,
*   Yakında çıkacak Visual Studio 2017,
*   Ve 1.0.1 sürümünde olan .NET Core

.NET Core beni fazlasıyla heyecanlandırıyor, Microsoft ismini ilk telafuz etmeye başladığından bu yana sürece tanıklık etmeye çalışıyorum.

Platformu tam destekleyen bir IDE’ye sahip olup, bir iki proje geliştirdikten ve mevcut NuGet paketlerimi .NET Core’a uyumlu hale getirdikten sonra üzerinde ancak sağlıklı yorum yapabileceğimi düşünüyor, şimdilik fikirlerimi kendime saklıyorum.

Fakat Microsoft’dan beklemediğim, beni şaşırtan bazı sakarlıklara denk geldiğim için, bunlar da platform’un tasarımı ile ilgili olmadığından bu yazıyı hazırladım. Sonuçta macOS üzerinde pek fazla .NET Core deneyimlemeye çalışan kişi olmadığına inanıyorum.

**Problem 1:**  
Visual Studio for Mac’i macOS Sierra’ma kurmayı denediğimde aşağıdaki mesajı aldım:

Takıldığım bir başka nokta da Visual Studio for Mac’i Console Application geliştirmek için kullanabilir miyim sorusuna yanıt alamamış olmak oldu. Ürünün sitesinde yalnızca Mobile Development odaklı özellikleri vurgulanmış, en iyisi başka bir zaman tekrar denemekti.

**Problem 2:**  
Farklı bir zaman diliminde tekrar bir download denemesinde bulundum. Bu sefer kurulumun çalışmasında bir sorun yoktu. Kurulum downloadlara başladı ve neden olduğunu bilmediğim bir şekilde Xamarin bileşenlerini indirmeyi 2–3 kere denedikten sonra vazgeçti.

Bu bir download hatası mıydı? Benim geçici bir bağlantı problemim miydi? (Ki internette dolaşmaya devam edebiliyordum) Bilmiyorum. Fakat network kablom çıkmış olsa dahi beni o an bir mesajla uyarıp “tekrar dene” seçeneği sunmasını beklerdim. Hatalardan sonra tekrar kurulumu yeniden başlatabiliyorsunuz, ama bir network hatası için çok büyük bir ceza.

**Problem 3:**  
Kurulumu tamamlayabildikten sonra, hemen yeni bir Console Application oluşturmayı ve hiçbir değişiklik yapmaksızın çalıştırmayı deniyorum ve karşılaştığım durum:

**Problem 4:**  
IDE’yi boşverip .NET Core sitesinden 1.0.1 sürümü kurulumuyla gelen pkg’i indirip çalıştırma yoluna gittim.

Burada da bir bilgilendirme eksiği ile karşılaştım. .NET Core’un önceki sürümlerine sahip isem nasıl bir işlem gerçekleştirmem gerektiğiyle ilgili bir içeriğe erişemedim.

pkg’i kurup bash’de ilk projemi oluşturmak için adım attığımda aşağıdaki hatayı aldım:

```sh
~$ dotnet -bash: dotnet: command not found
```

Hatayı kendim gidererek ilerleyebildim. Bu arada siz de başlıktaki hatayı aratıp bu yazıya denk geldiyseniz, eksik path tanımını aşağıda olduğu gibi bir symbolic link aracılığı ile atlatabilirsiniz:

```sh
ln -s /usr/local/share/dotnet/dotnet /usr/local/bin/
```

Alternatif olarak, `~/.bash_profile` dosyanıza aşağıdaki satırı ekleyebilirsiniz:

```sh
export PATH=$PATH:/usr/local/share/dotnet
```

Sonuçta karşılaştığım bu hatalar beni ürünün henüz test senaryolarının pek olgunlaşmadığı yönünde düşündürüyor.

Yine de bir kez daha .NET Core’dan oldukça umutlu olduğumu belirtmek isterim. .NET sevdiğim bir platform, Visual Studio 2017’in çıkışı ve tooling’in artmasıyla artık benim de üzerine yatırım yapabileceğim bir olgunluğa sahip olacak. Sabırsızlıkla bekliyoruz :)
