# Eksik parça: Data tanımlama

Son bir kaç haftamı .NET platformuna adayıp OData + Entity Framework ve Web API
ile geçirmişken “Data” kavramı üzerine düşünecek zamanım da oldu.

Bu sürede kazandığım deneyimlerimi sonra aktarmayı planlıyorum, ama öncesinde
“uzak servis üzerinde yer alan izole veri” isimli bulmacada eksik parçanın ortak
bir entity tanımlama formatı olduğuna kanaat getirmiş durumdayım.

Microsoft dünyasından uzaklaşmaksızın yorumlarsak; .NET Framework 5 ile Entity
Framework 7’ün gelişi yakın. EF7 daha hafif olma iddiası ile “Code First”
dışındaki tüm yaklaşımlardan bünyesini arındıracağını duyurdu. Bu kararı
elbetteki kullanıcıların class aracılığı ile entity tanımlamaya olumlu tepki
vermelerinden dolayı kolayca alabiliyorlar. Fakat halen bu alanda araç kutusu
eksiksiz görünen Microsoft’un dahi kendi “Entity Data Model” (EDM)si hem Entity
Framework hem de OData kütüphaneleri tarafından “paslaşır” bir biçimde
kullanılamıyor.

Resmi daha da genişletip, JavaScript yazan Frontend Developer’ından, bir API’ye
entegre olmayı bekleyen fakat PHP kullanan müşteriye kadar gittiğimizde hem
herhangi bir ORM üzerinde POCO sınıflarını dil-bağımsız oluşturabilecek,
veritabanına verdiğimizde anında fiziksel olarak tablo/görünüm/ilişkileri
oluşturabilecek, hatta Visio gibi bir tool’a verdiğimizde bize UML çizmesini
sağlayacak bir data tanımlama dili yok kabul görmüş olan.

Data yapılan işin bu kadar merkezinde iken, data’yı ve data ilişkilerini halen
her platforma özgü tanımlıyor olmak büyük sorun bana kalırsa.
