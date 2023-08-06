# React’ın Vizyonu ve Hooks

Uzun bir aradan sonra tekrardan blog yazmaya başladım. Bu esnada geçen süreye KoçSistem’den ayrılarak Setur’a geçişimi, birçok yeni açık kaynak projeyi, [7 farklı organizasyonda konuşma](../../../presentations/tr/README.md)yı ve bir de yüksek lisans tezini sığdırabilmişim.

Genel olarak daha soft yetenekler, yazılım ürünleri, mimari, takım dinamikleri ve pratikler üzerine yazmayı seviyorum. Bu nedenle geliştirici perspektifinden çok daha farklı bir blog içeriğim olduğunu düşünüyorum. Ancak geçenlerde twitter üzerinde geliştirici perspektifiyle yapmış olduğum bir React eleştirisini net olarak ifade edebileceğim en uygun mecra da burası.

Eleştirim basitçe aşağıdaki tweet’de yer alıyor. Gelen yanıtlarla bir takım tartışmalar oldu. Ben de sonunda çamur atıp kaçmış olmamak üzere bu yazıyı planladım. Bugün ise ancak yazabiliyorum.

%[https://twitter.com/eserozvataf/status/1055860281425960961]

Bandı biraz geri saralım ve React’ın neden benim için fenomen bir view çözümü olduğunu açıklamaya çalışayım.

jQuery gibi çözümler hem plugin host, hem polyfill, hem animasyon kütüphanesi, hem DOM seçicisi ve manipulatörü, hem de bir web sayfasındaki akışı kontrol etmeye çalışıyordu. Bu yaklaşıma alternatif olarak React, kapsam olarak yalnızca kendisine verilen doküman yapısını (örneğin JSX) render etmekle sınırlı tuttu. Bunu yaparken de bilgisayar biliminin neredeyse 1960'ların sonunda konuştuğu bileşen-temelli UI yaklaşımından destek alıyordu. UNIX felsefesinin bir araçtan beklentisinin özeti gibiydi, “bir iş yap, onu doğru yap”.

Çevremde daha fazla hayranı olsa da Vue için aynı şeyi söyleyemeyeceğim örneğin. Çünkü Vue popülerite kaygısını belli edebiliyor. İlk sürümü angularjs yolundan giderken, ikinci sürümü React, bir sonraki sürümü ise React Hooks’a doğru evrilip amacını geliştiricinin konforunu arttırmak olarak belirleyebiliyor. Bu bir tercihti ve React konfor yerine mühendislik doğrularını seçiyordu. En azından ben öyle biliyordum.

React’ın yetersiz kaldığı yerde React-Router, Redux gibi diğer kütüphaneler devreye giriyordu. Vue’nun isviçre çakısı olmaya çalıştığı bir gerçeklikte, tornavida, çekiç ve çakı’nın montajda uygun yerlerde kullanılmasına benzetebilirdik bu durumu.

Ancak, kullandığım ürünleri changelog seviyesinde takip eden biri olarak, React 16'dan itibaren projenin yolunu değiştirdiğine tanık olduğumu düşünüyorum.

Fiber güncellemesi (React’ın bir süre önce farklı bir rendering yaklaşıma geçmesi) ile yalnızca Lifecycle’lar değişse, bu yeni rendering için bir takım bağlantılar dışarıda kalsa bundan daha doğal bir şey olamazdı.

Bunun yerine, yeni tanıtılan her feature ürünün kapsamına (product owner’lar neden bahsettiğimi daha net anlayacaktır) yapılmış bir eklenti olmaya başladı.

*   getDerivedStateFromProps ile react-redux,
*   yeni context api ile redux,
*   Suspense ile [react-loadable](https://www.npmjs.com/package/react-loadable),
*   useMemo ile memoize-\* kütüphaneleri,

adeta ürünün temeline yerleştirdi ve/veya yerleştirilmeye başlandı. Tıpkı vue’nun, vuex’e yaptığı gibi.

Şimdi bunların er ya da geç bir SPA’nın içinde mutlaka bulunması gereken konseptler/bileşenler olduğunu, React’ın çekirdeğine yakın çözümlerin çok daha güzel practiseler sunarak bunları geliştiricilere verebileceğini savunabilirsiniz. Ama bu yukarıda çizdiğim React portesinin dışında bir React’ı tarifliyor bana kalırsa. Kütüphane kimliğinden çatı/framework kimliğine doğru kayacak veya opinionated olacak bir React hoşuma gitmezdi.

Twitter’da sonra geriye dönüp acımasız bir üslupla yazdığımı hissettiğim “Geliştirilecek madde kalmamış, bunun yerine istekleri gerçekleştirmeye başladılar” eleştirimin dayanak noktası da biraz buydu.

Yazının “plot twist”i ise burada. Ben React Hooks’un React değil de tamamen farklı bir ürün olmasını savunsam da React Hooks’la yaptığım geliştirmeler ve ufak projeler sonucu yeni React’dan çok memnun kaldım.

React, Pure Component yazabileceğimiz, fonksiyon ile tanımlanan componentlerin 100% stateless functional component olduğu, lifecycle eventler ile ilerleyen bir yapı idi.

React Hooks ise functional componentlerin olduğu, “use” ile başlayan hook’lar ile kullanıcıya side effect’li (dolayısıyla aslında stateless olmayan) bileşenler kodları ürettiren apayrı bir yapı.

Fakat günün sonunda React Hooks ile yazılan yapıda,

*   Prop’ları paslamanın, state yönetmenin daha kolay olduğu,
*   Redux’a ve React-Redux’a ihtiyaç bırakmayan,
*   Fonksiyon olarak bileşen tanımlamanın lifecycle’larla yazılmış bir sınıftan kolay olduğu,
*   Lifecycle eventler yerine hook’ların kullanımı ile temiz, anlaşılır ve okunabilir kodların oluştuğu,

bir kod tabanı vaad ediyor.

React Hooks ile yazılmış bir örnek için, [kişisel web sitemin ana sayfasının kodu](https://github.com/eser/eser.ozvataf.com/blob/archived/old-site/src/app/pages/frontpage/index.tsx)nu inceleyebilirsiniz.

Son olarak birkaç saat önce Armağan Amcalar ve Fatih Kadir Akın ile Kod Analizi’nin ilk konuğu oldum. YouTube üzerinde canlı yayında [Evangelist](https://github.com/eser/evangelist) isimli açık kaynak projemi ellerinde küreklerle gömdüler. Daha sonra farklı bir proje ve soru/yanıt ile devam ettik. Hem tarihe not olması, hem de Kod Analizi’nin kitlelere ulaşması için buraya eklemek istedim.

%[https://www.youtube.com/watch?v=e-1aIc93QXg&list=PLWLiJPAYmgZAtN-trvpEpKysVL2LKMcO6&index=1]

React ve React Hooks üzerinden tartışmalar bana kalırsa henüz yeni başlıyor. Ben de birçok fikrimi elbette değiştirebilirim. Bu yazıda umarım biraz da olsa meramımı anlatabilmişimdir.

Sağlıcakla kalın.
