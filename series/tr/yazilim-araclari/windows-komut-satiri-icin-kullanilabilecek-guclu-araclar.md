# Windows Komut Satırı için kullanılabilecek güçlü araçlar

Microsoft kullanıcı deneyimlerinde 2010'a kadar grafik arabirimi kullanımını arayüzünde herhangi bir ayrıma gitmeyi tercih etmedi. Hatta bu süreç içerisinde mümkün oldukça her işlemin grafik arabirimi üzerinden gerçekleştirilebilmesi yönünde inisiyatifler aldı.

.NET Core ve Windows 10 ile birlikte bu kararlılıkta ciddi değişimler gözlemleyebiliyoruz. Örneğin Windows 10 Anniversary Update 1 ile birlikte bash’ın Windows’a gelişi, Windows içerisinde tanımlanan bir “Developer Mode” seçeneği, .NET Core’u yüklemek için dahi komut satırı araçlarının önplanda tanıtılması v.s.

Önümüzdeki süreçte Microsoft kendi teknolojilerine odaklanmış yazılımcıların da Visual Studio dışında bir yazılım geliştirme ekosisteminde, diğer teknoloji ve parçalarla uyum içerisinde çalışmasının önemli bir gereksinim olduğunun farkında olsa gerek.

Bu araçların büyük bir çoğunluğunun çalıştığı platform tabii ki, macOS, Linux gibi işletim sistemlerinde olduğu gibi komut satırı olacak. Ve nasıl masaüstünüzü, start menüsünü rahat kullanmak günlük bir ihtiyaç ise komut satırında da rahat hissedebildiğiniz kadar yazılım geliştiricileri kendilerini üretken hissedecekler.

Ben bu noktada kendi sıfırdan kurulum reçetemi paylaşıp, windows komut satırında hangi araçları kullandığımı listelemek istiyorum.

**1\. Chocolatey**

[https://chocolatey.org/install](https://chocolatey.org/install)

Paket yöneticisi program kurulum ve güncelleme yönetimi için kritik önem taşıyor. Apt, Yum, Brew gibi örnekler zaten işletim sistemlerinin önemli bir parçası iken son dönemlerde Microsoft’un da Chocolatey projesine desteği ile Windows için 3. parti geliştirilen bu aracın şu sıralar oldukça popülerlik kazandığından bahsedebiliriz.

Ben aşağıdaki diğer programların kurulumunu chocolatey üzerinden yapıyorum.

**2\. Clink**

[https://chocolatey.org/packages/clink](https://chocolatey.org/packages/clink)

bash kullanıcıdan gelen komut girişlerini okumak için *readline* isimli bir kütüphane kullanır. Clink basitçe anlatmak gerekirse aynı deneyimi yaşamanız için *readline*’ı windows’un komut satırı arabirimini sağlayan *cmd.exe*’ye uyarlar.

**3\. Sudo, Make, OpenSSH, Curl, Vim, Git**

[https://chocolatey.org/packages](https://chocolatey.org/packages)

Sırasıyla,

Komutları Administrator hakları ile başlatabilmeniz için *sudo*,  
 Makefile’ları windows ortamında çalıştırabilmeniz için *make*,  
 Komut satırından putty gibi yazılımlara gerek kalmaksızın ssh bağlantısı kurabilmek için *win32-openssh*,  
 Komut satırından http istekleri yapabilmek için *curl*,  
 Komut satırında gelişkin bir editor olan *vim*,  
 Yine GitHub for Windows veya herhangi bir IDE/text editor desteğine gerek duymaksızın Git erişimi için *git*,

paketlerini chocolatey üzerinden indirebilirsiniz.

**4\. DOSKey ile aliaslar ve diğer konfigurasyonlar**

[https://gist.github.com/eserozvataf/e8eb6f8e7f57418a1775b2b68960a0a1](https://gist.github.com/eserozvataf/e8eb6f8e7f57418a1775b2b68960a0a1)

MS-DOS’un 5.0 sürümüyle hayatımıza giren DOSKey aslında komut satırı için bir makro aracı. Halen günümüzde de Windows komut satırında yer aldığı için kendisini bash’da yer alan `alias` komutunun bir benzeri işlevle kullanıyorum. Bu sayede evde kullandığım macOS'dan işyerinde kullandığım Windows'a geçtiğim anda komut satırına `ls` yazdıktan sonra hatamı `dir` yazarak düzeltmek zorunda kalmıyor, sistemler arasındaki farkı minimize edebiliyorum.

Mevcut kullandığım makrolar aşağıdaki gibi:

```
DOSKEY ls=dir /B $* DOSKEY ll=dir $* DOSKEY clear=cls DOSKEY open=start $* DOSKEY service=net $2 $1 DOSKEY apt-get=choco $*
```

Maalesef `cmd.exe` kendi çalıştığı anda belirli başlı komutları bizim için işletmiyor (`.bashrc` veya `bash_profile` benzeri bir işlevden bahsediyorum). Bu nedenle yukarıdaki makroları açılan her komut satırı için tekrardan tanımlamam gerekiyor. Eskiden aşina olduğumuz `AUTOEXEC.BAT` çoktan tarihe karışmış durumda. Bu nedenle ben kendi kullanıcı dizinime bir `env.cmd` dosyası oluşturarak her komut satırını açtığımda elle kendisini çalıştırıyorum. Yukarıdaki linkten benim kullandığım `env.cmd`nin içerine ulaşabilirsiniz.

Diğer bir değişiklik ise benim artık sıkıldığım, belki sizin de değiştirirek keyif alabileceğiniz prompt. Sizden komut isteyen `C:\Windows\system32>` yazısını değiştirmek istiyorsanız, [Scott Hanselman'ın A better PROMPT for CMD.EXE or Cool Prompt Environment Variables and a nice transparent multi-prompt yazısı](http://www.hanselman.com/blog/ABetterPROMPTForCMDEXEOrCoolPromptEnvironmentVariablesAndANiceTransparentMultiprompt.aspx)nı takip ederek gerekli değişiklikleri gerçekleştirebilirsiniz.

Benim tercihim aşağıdaki gibi:

```
SET PROMPT=$+[$m$p]
```
