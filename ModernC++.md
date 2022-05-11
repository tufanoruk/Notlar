# Modern C++

Yeni çıkan onlarca programlama diline rağmen C++ hala en çok kullanılan [programlama dillerinden](https://spectrum.ieee.org/top-programming-languages-2021) biri ve öyle de olmaya devam edecek görünüyor. Bu dili C++98 ile bırakmıştım. Kendimi tazelemek amacıyla yaptığım [denemelerde](KodalamaPratiği.md) modern C++ kullanmayı seçtim. Çalışmaları yaptığım tarih itibarıyla (2022 ilk yarı) hemen tüm popüler C++ deleyiciler (gcc, clang, Apple clang, MSVC, Intelc++, sunCC) C++14 özelliklerini (stdc++ dahil) [destekliyor](https://en.cppreference.com/w/cpp/compiler_support). Derleyicilerin gelişmesi dilin özelliklerinde göre daha yavaş olduğu için birkaç sene geriden gitmekte fayda var. 

C++ (C geçmişi sayesinde) derlenerek çalıştığı platformda yerli (native) olarak çalıştığından, olası en yüksek performansı elde etmeye olanak sağlıyor Bu nedenle ağırlıklı olarak sistem ve ağ (networking) programlama amacıyla kullanılıyor. C++14, stdc++ ve [boost](https://www.boost.org) gibi taşınabilir kütüphaneleri kullanarak geliştirlen tüm programlar, ilgili derleyicilerin desteklediği tüm platformlarda çalışıyor. Bu da C++'a performansla birlikte kaynak kod seviyesinde yüksek taşınabilirlik avantajı sağlıyor.

Modern C++ bana neredeyse yeni bir dil hissiyatı verdi ve oldukça beğendim. C++17, 20 ve sonrasında daha da fazla iyileştirmeler ve kolaykıllar mevcut. <https://en.cppreference.com> sayfasından detayları inceleyebilirsiniz.

C++14'le denemeler yaparken ilk bakışta gördüklerim,

* en önemlisi önceleri farklı kütüphanelerde (STL, Boost) yer alan veri yapıları, algoritmalar, daha da zenginleştirilerek standart kütüphaneye (stdc++) girmiş. 
* "lambda" fonksiyonu özelliği gelmiş,
* "container" veri yapıları için "for" komutu kolaylaştırılmış, 
* "default constractor" ve "destructor" yönetimi  daha belirginleştirilmiş, "move constractor" tanımı gelmiş (copy ve assignment sonucunda oluşan bellek yönetimi görünür kılıyor)
* derleme sırasında yakalanan hata ve uyarılar arttırılmış, 
* enum gerçek bir tip olarak tanımlanabiliyor (type safety)
* "container" ve "struct" tip tanımlamalarında değişkenlere ilk değer verilebiliyor.
* Tarih ve saatle ilgili tipler ve işlemler stdc++ kütüphanesine eklenmiş,
* "if" komutu içinde de değişken tanımı yapılabiliyor ("for" gibi)
* "pointer" ile erişilen belleğin yönetim kolaylığı için "smart pointer" (shared_ptr ve uniqueu_ptr) ile birlikte bellek sahipliği yönetimi için "move" (bir "pointer"ın gösterdiği belleğin sahipliğinin başka bir "pointer"a taşınması) mekanizması getirilmiş. Bu yapılar "new/malloc" kullanımını ele alarak C/C++ programlarında (yanlış programlama sonucu) karşılaşılan "memory leak" problemlerini engellemeye yardımcı oluyor.
* "nullptr" artık makro (NULL) ya da "int" değil, std::nullpter_t tipi bir sabit.
* "regex" (regular expression) stdc++ kütüphanesine eklenmiş
* "thread" programlama için "atomic, mutex, lock, futures" yapıları stdc++ kütüphanesine eklenmiş.

Bunlar benim ilk etapta görebildiklerim. <https://en.cppreference.com>'u inceledikçe ve bu özellikleri kullandıkça dili daha çok seveceğinizi düşünüyorum.
