# Git

Git, Linus Torvalds (Linux'un orjinatörü) tarafından geliştirilmiş bir kod konfigürasyon kontrol aracı. Geliştirildiği güne kadar kullanılan kod konfigürasyon kontrol araçlarından farklı bir yapısı var. Dolayısıyla eski araçları kullandıysanız Git'e adapte olmak biraz zaman alabilir.

SCCS ve sonraki türevleri RCS, CVS ve Subversion (SVN), kod ağacını merkezi bir yerde tutar ve geliştirici ağaçtan istediği dosyayı ya da dalı (ya da isterse tüm ağacı) geliştirme ortamına alarak çalışır. Kodunu konfigürasyona girmeden çakışmaları (conflict) çözerek ana kod ağacına yükler (commit). Git'de ise proje kod deposu tarihçesiyle birlikte geliştiricinin çalıştığı dizindedir (```.git``` dizini) ve tüm projeyi içerir.  Geliştiricinin yerelindeki proje uzaktaki bir Git deposuyla (Github, Bitbucket ya da yerel ağda bulunan bir git sunucusu) eş tutulabilir.  Projede çalışanlar projenin kopyasını (clone) alarak gelişitmeye dahil olurlar. Dolayısyla projedeki kişi kadar proje kodunun kopyası vardır. Bu dağıtıklık yedeklilik de sağlar. tüm proje kodu her zaman makinede olduğu için konfigürasyon kontrol yönetimi de çok hızlı şekilide yapılır.

Dağıtık mimarisiyle Git geliştiricilerin ana kod deposuna erişimleri olmadan çalışmalarına olanak sağlar, bu yapı hız ve yedeklilike gelen güvenlik de sağlar ([Linus Git talk](https://youtu.be/4XpnKHJAok8)). Bu avantajları ve yazılım proje geliştirme yapıları dağınıklaştıkça projelerde de Git kullanımı yaygınlaşmıştır.

VSCode'un git ile entegre çalışması için makinenizde git komut satırı kurulmuş olması yeterlidir. Linux ve MacOS'larda git geliştirme araçalrı içinde vardır. Windows için de kurulumu mevcuttur.

```text
 % git --version
git version 2.24.3 (Apple Git-128)
```

Dolayısıyla VSCode'a herhengi bir eklenti eklemeden Git ile çalışmaya başlayabilirsiniz. Ben sadece [gitignore](https://github.com/github/gitignore) ve [git history](https://github.com/DonJayamanne/gitHistoryVSCode) eklentilerini ekledim.
