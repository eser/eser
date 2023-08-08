# **Sezon 1 Bölüm 1** Web Geliştirme

İşte Fantastik 4️⃣’lümüz:

1️⃣ Scoped CSS’ler (@scope olan) Chrome 118 ile birlikte gelmeye başlıyor. Bence dahiyane bir implementasyon. Ne olduğunu anlamadıysanız tweet’in altına mesaj bırakın ayrıca anlatabilirim. https://caniuse.com/css-cascade-scope

2️⃣ CSS Nesting için ise şimdilik Firefox 117 bekleniyor. O zamana kadar PostCSS burada W3C standartına yakın bir transpile işlemi için size destek olabiliyor. SASS/LESS kullanıyorsanız bir daha düşünün. https://caniuse.com/css-nesting

3️⃣ CSS Nesting demişken, SASS/LESS ile farklarından bir tanesi her satırda “&” diye referanslamak gerekiyordu ya. CSS Working Group geçenlerde onun kullanımını diğer preprocessorlarda olduğu gibi “rahatlatmaya” razı oldu. https://github.com/w3c/csswg-drafts/issues/7961

4️⃣ TypeScript 5.2 ile birlikte artık TC39’un decorator implementasyonuna geçtik diyebiliriz. (Eskiden TypeScript’in kendi bir decorator implementasyonu vardı, NestJS ve Angular sevdalıları burada mıydı?) Ancak artık TypeScript’in arayı doldurduğu “--emitDecoratorMetadata” özelliği artık çalışmayacak. Biz decoratorların çalışması için runtime ve browser’lara gelecek v8 ve diğer JavaScript engine güncellemelerini bekleyeceğiz. https://github.com/tc39/proposal-decorator-metadata ve https://devblogs.microsoft.com/typescript/announcing-typescript-5-0/#decorators

Browserların sürüm numaralarını konuşmayalı yıllar olmuş değil mi?
