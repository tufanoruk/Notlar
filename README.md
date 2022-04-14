# Giriş

Yazılım teknolojileriyle iligi yaptığım çalışmaları, öğrendiklerimi, aldığım dersleri ve okumaları burada paylaşıyorum. Kapsamın yazılım teknolojilerine yeni başlayan ya da başlayacak olanlar için faydalı olacağını düşünüyorum. Zira arkasında uzun senelerin tecrübesi var.

Çalışmaya yıllarca önce teknoloji öğrenmekle ilgili yaptığım denemeleri güncel geliştirme ortam ve araçlarına taşıyarak başlamaya karar verdim. Geliştirme ortamı olarak [VSCode](https://code.visualstudio.com)'u seçtim. Geçmişte  yoğun olarak kulllandığım [Vi](https://en.wikipedia.org/wiki/Vi), [Emacs](https://www.gnu.org/software/emacs/) ve [Eclipse](https://www.eclipse.org/ide/)'den sonra çalışma sürecini hızlandıran kolaylıklar sağlıyor. Ama temelde yapılan iş her zaman aynı. 

1. Kodu yaz,
2. Konfigürasyon kontrole gir,
3. Derle / inşa et,
4. Çalıştır / test et / hata bul,
5. Başa dön.

Geçmişte komut satırından elle yapılan bu işleri tek arayüzden yapmak kolaylık sağlıyor. Ama komutların detayını ve elle nasıl yapılacağını bilmeden bu zengin geliştirme ortamlarını (IDE) kullanmak, özellikle ortam problemlerinin tespit ve çözümünde zorluklara neden olabilir. Bu nedenle kullanılan ortamdaki araçlarla işleri elle / komut satırından yapacak bilgiye ya da bu bilgiye nasıl ulaşılacağını (man sayfaları gibi) bilmek gerekli. Kısaca IDE'den yapılan temel işlerin (derleme, kod çalıştırma, test, debug, konfigürasyon kontrol, ...) komut satırından da nasıl yapıldığının bilinmesinin önemli. Bu bilindiği taktirde hangi IDE'nin kullanıdlığının çok önemi yok ve herhangi bir IDE'yi öğrenmek hızlı ve daha kolay olur.

Yazılım geliştiren bir kişinin programlama dili yanında mutlaka onun derleyicisi (compiler) / yorumlayıcı (interpreter)'sının CLI komutlarının neler oldığunu, inşa (build) için kullanılan mekanizmayı (autoconf, makefile, cmake, ant, maven, ...) bilmesi gerekli. Diğer önemli konu da konfigürasyon kontrol. Konfigürasyon kontrolün önemi ilk kodun yazıldığı günlerden itibaren anlaşılmış ve araçlar geliştirilmiş. Kabaca sırasıyla  [SCCS](https://en.wikipedia.org/wiki/Source_Code_Control_System), [CVS](https://www.gnu.org/software/trans-coord/manual/cvs/cvs.html), [SVN](https://subversion.apache.org) ve şimdi de ağrılıklı olarak [Git](https://git-scm.com) kullanılıyor. Ben de pek çok kişi gibi konfigürasyon kontrol aracı olarak Git ve uzak depo (remote repository) olarak da [GitHub](https://github.com/tufanoruk)'ı seçtim.

## İçerik

[VSCode](VSCode.md)

[Git](Git.md)

[Docker](Docker.md)

[Kodlama Pratiği](KodlamaPrati%C4%9Fi.md)

[Yazılım Mühendisliği](Yaz%C4%B1l%C4%B1mM%C3%BChendisli%C4%9Fi.md)

[Kaynaklar](Kaynaklar.md)

[Projelerden seçmeler](https://github.com/tufanoruk)
| Proje | Teknoloji | Not
|:---|:---|:---|
|[Mosquito performans](https://github.com/tufanoruk/mosq_perf)|C / MQTT|MQTT açık kaynak gelişitrmesi olan mosquito için gecikme, jitter ölçümü|
| [Kasa](https://github.com/tufanoruk/Kasa) | Python / AWS S3 |  Amazon S3 ve yerel makineye dosyaların yerelde şifrelenerek etkin şekilide yedeklenmesi|
| [PlatformData](https://github.com/tufanoruk/PlatformData) | Python / node / PubSub / MQTT / Web | Girilen rota, sürat ve mevki bilgisine göre platformnu ilerleten ve MQTT pubsub mekanizması ile bunu internet tarayıcı istemcilere dağıtan bir deneme|
|[Find Furthest Number](https://github.com/tufanoruk/ffn)|C++17 / Boost asio | İşe alımlarda uygulana yetenek / algılama testlerinde biri |
|[WordleHelper](https://github.com/tufanoruk/WordleHelper)|Python|Worlde kelme bulma oyununu oynerken kelime bulmaya yardımcı olan bir uygulama|
