# PHP SPL: PHP Standard Library

PHP’nin 5.1 sürümüyle birlikte “Standard PHP Library” (SPL) isimli bir kavram
tanıtıldı. SPL içerisinde, PHP geliştiricilerinin çok kullanıldığına kanaat
getirdikleri bir takım hazır tip ve fonksiyon tanımları mevcut. Bu tanımlar PHP
bünyesinde servis edilerek, bir çok kütüphane ve yazılımcının bir standart
üzerinden çalışmasına imkan veriyor. Ne yazık ki bir çok geliştirici SPL’den
habersiz olarak geliştirme yapmaya devam ediyor.

[PHP Manual’ın SPL ile ilgili bölümü](http://tr.php.net/spl)nü paste etmektense
burada bir özet geçmek isterim.

### Veri tipleri

[**SplStack**](http://tr.php.net/manual/en/class.splstack.php): Bir array
üzerinde _array\_pop_, _array\_push_ dışında bir işlem yapmıyorsanız array
alternatifidir.

[**SplQueue**](http://tr.php.net/manual/en/class.splqueue.php): Bir array
üzerinde `array_shift`, `array_push` dışında bir işlem yapmıyorsanız array
alternatifidir.

[**SplPriorityQueue**](http://tr.php.net/manual/en/class.splpriorityqueue.php):
Bir array’e eklediğiniz elemanların önemlilik sıraları varsa ve bu elemanları
array’i okurken her zaman önem sırasına göre almak istiyorsanız array
alternatifidir.

[**SplFixedArray**](http://tr.php.net/manual/en/class.splfixedarray.php): Bir
array’e ekleyeceğiniz eleman sayısını önceden biliyorsanız array alternatifidir.

### Iteratorler

[**DirectoryIterator**](http://tr.php.net/manual/en/class.directoryiterator.php):
Bir dizin içeriğini okur.

[**LimitIterator**](http://tr.php.net/manual/en/class.limititerator.php): Başka
bir iterator’un belirli eleman aralığını kullanır. (İlk 5 eleman gibi)

### Interfaceler

[**Countable**](http://tr.php.net/manual/en/class.countable.php): Sınıfın
`count` fonksiyonu ile sayılabilir olmasını sağlar.

[**Serializable**](http://tr.php.net/manual/en/class.serializable.php)\*:
Sınıfın `serialize` ve `unserialize` fonksiyonlarıyla çalışabilmesini sağlar.

[**ArrayAccess**](http://tr.php.net/manual/en/class.arrayaccess.php)\*: Sınıfın
array gibi davranmasını, oluşan nesnenin `$nesne[‘eleman’]` biçiminde erişimini
sağlar.

[**Traversable**](http://tr.php.net/manual/en/class.traversable.php)\*: Sınıfın
foreach ile dolaşılabileceği bilgisidir. `Iterator` veya `IteratorAggregate` ile
birlikte kullanılır.

[**Iterator**](http://tr.php.net/manual/en/class.iterator.php)\*: Sınıfın
`foreach` ile dolaşılabilmesini sağlar.

[**IteratorAggregate**](http://tr.php.net/manual/en/class.iteratoraggregate.php):
Yine sınıfın dolaşılabilmesini sağlayan bir iterator sınıfına sahip olduğunu
belirtir.

### Design Pattern yardımcıları

[**SplObserver**](http://tr.php.net/manual/en/class.splobserver.php): Observer
design pattern’deki gözetleyen ve güncellemeleri alan sınıf interface’i.

[**SplSubject**](http://tr.php.net/manual/en/class.splsubject.php): Observer
design pattern’de gözeticilerin abone oldukları sınıf interface’i.

### Fonksiyonlar

[**iterator\_to\_array**](http://tr.php.net/manual/en/function.iterator-to-array.php):
Elinizdeki bir iterator’ı foreach’le dönmeksizin array’e dönüştürür.

[**iterator\_apply**](http://tr.php.net/manual/en/function.iterator-apply.php):
Bir iterator’ın her elemanı için parametre olarak verdiğiniz fonksiyonu
çalıştırır.

[**iterator\_count**](http://tr.php.net/manual/en/function.iterator-count.php):
`count` ile sayamadığınız bir iterator’ın eleman sayısını verir.

### Exceptionlar

Kendi Exceptionlarınızı yalnızca `Exception` sınıfından değil, bir çok yer
sınıftan türetebilir böylece istisnai durumları yakalarken daha net tip
ayrımlarında bulunabilirsiniz. Hatta benim önerim, PHP gibi interpreter tabanlı,
runtime’ı request-response ile sınırlı (tek tüketimlik) bir ortam için mümkün
olduğunca mevcut sınıfları kullanın. SPL’nin önemi de bu noktada belirginleşiyor
zaten. Exceptionların anlamlarını teker teker yazmak isterdim ama isimleri zaten
yeterince açıklayıcı, burada önemli olan bu Exceptionların inheritance yapısı, o
da şu şekilde:

[Exception](http://tr.php.net/manual/en/class.exception.php)

Son olarak, kesin bir çizgi olmamakla birlikte, ben kendi yorumumca:
`LogicException`‘ı kullanıcı/programcı tarafından yanlış bir işlem yapıldığında,
`RuntimeException`‘ı ise bir işlem gerçekleştirirken bir zorluk oluştuğunda
kullanıyorum. `ErrorException` zaten PHP’nin hata oluştuğunda kullandığı özel
bir sınıf.
