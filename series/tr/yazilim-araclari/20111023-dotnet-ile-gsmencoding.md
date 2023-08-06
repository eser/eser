# .NET ile GsmEncoding

Cep telefonunlarımıza gelen kısa mesajlarda genel kanının aksine geleneksel 8bit’lik ASCII tablosu değil de, GSM operatörü tarafından özelleştirilebilen 7bit’lik GSM alfabesi kullanılmaktadır.

Bunun zorluğu ile en çok servis sağlayıcı tarafından filtrelenmeyen, daha doğrusu işin bu kısmını tamamiyle biz API kullanıcılarına bırakan kısa mesaj gönderimlerinde karşılaşırız. Sık karşılaştığım ve internet üzerinde pek kaynak bulamadığım için işin başa düştüğünü ve kendim .NET’in klasik Encoding’leri ile çevirim uyumlu bir sınıf yazmam gerektiğini düşündüm. GsmEncoding aslında Tasslehoff için yazdığım .NET kütüphanesinin bir parçası, kendisinin kaynak kodlarına GitHub üzerinden erişebilirsiniz:

%[https://github.com/eser/tasslehoff-library/tree/master/Text]

Kodları kullanmak için .NET’in CLR’ında herhangi bir Encoding’i nasıl kullanıyorsanız, yeni oluşturduğunuz bir `GsmEncoding` instance’ını da bu şekilde kullanmanız yeterli. Örneğin:

%[https://gist.github.com/eser/5099144]
