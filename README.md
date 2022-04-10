# Giriş

Yakın zamanda yazılım teknolojileriyle iligi yaptığım çalışmaları, öğrendiklerimi, aldığım dersleri ve okumaları burada paylaşıyorum. Konularla ilgili çok fazla İngilizce kaynak olduğu için Türkçe olarak yazacağım. İçeriğe ek olarak öğrenme sürecinin de yazılım teknolojilerine yeni başlayan ya da başlayacak olanlar için faydalı olacağını düşünüyorum. Zira arkasında uzun senelerin tecrübesi var.

Öncelikle yıllarda önce teknoloji öğrenmekle ilgili yaptığım denemeleri güncel geliştirme ortam ve araçlarına taşıyarak başlamaya karar verdim. Geliştirme ortamı olarak [VSCode](https://code.visualstudio.com)'u seçtim. Geçmişte  yoğun olarak kulllandığım [Vi](https://en.wikipedia.org/wiki/Vi), [Emacs](https://www.gnu.org/software/emacs/) ve [Eclipse](https://www.eclipse.org/ide/)'den sonra çalışma sürecini hızlandıran kolaylıklar sağlıyor. Ama temelde yapılan iş her zaman aynı. Yazılım geliştiricinin günlük çalışma rutini aşağıdaki şekilde.

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
[Kodlama Pratiği](KodlamaPratiği.md)
[Kaynaklar](Kaynaklar.md)
