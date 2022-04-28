# Servis "Docker"laştırma

Servis "Docker"laştırmayı öğrenmek için uzun zaman önce bir kaç teknolojinin entegrasyonu tecrübesi için yaptığım [HostPing](https://github.com/tufanoruk/HostPing) servisi ile çalışmaya karar verdim. Bu servisi seçmemin nedeni gayet basit ama farklı teknolojileri (apache http, js, perl, gcc) içeriyor olması.

Önce iki tanımı vereyim.

**İmaj** : Bir plana göre (Docker  File) Container içeriğini taşıyan dosyalar bütünü

**Container**:  Çalışan imaj

HostPing apache (ya da bezeri) webserver üzerinde çalışan, girilen IP/FQDN'e erişim kontrol ederek sonucu gösteren basit bir servis. Ön yüz (frontend) Twitter [bootstrap](https://getbootstrap.com/1.0.0/), [JQuery](https://jquery.com/) kullanıyor. Arka yüz (backend) Perl (perl ICMP root hakkı gerektirdiği için basit bir setuid sarmalayıcı -wrapper- uygulama ile tetiklenen) ile yazılmış "[Richardson  Maturity Level](https://martinfowler.com/articles/richardsonMaturityModel.html) 0" bir REST servisi.

Bir servisi "docker"laştırmak için makinenizde docker kurulu olmasını vurgamlamaya gerk yok sanırım. İş temelde "docker build" komutuna sağlanacak "Docker file"ı yazmada. [VScode Docker eklentisi](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) "docker"laştırma çalışmalarına kolaylık sağlıyor. Makinenize yüklü imajları görebiliyorsunuz, çalıştırıp sonlandırabiliyorsunuz, çalışan "container"ın dizin yapısında dolaşabiliyor, dosya alıp yükleyebiliyorsunuz ve shell açabiliyorsunuz. Bunların hepsini "docker" komutu ile de yapmak mümkün. Hangisini terch ederseniz. Ben özellikle bir "container"ı çalıştırırken komut satırından parameterleri girme kolaylığı açısından komut satırını tercih ettim ama diğer işlemlerde VSCode Docker eklentisinin sağladığı kolaylıklardan faydalandım.

Bunun gibi basit, tek başına çalışan bir servisi "docker"laştırmak temelde [Docker File](https://docs.docker.com/engine/reference/builder/) yazılmasını içeriyor o kadar ("container"ın dışarı erişmesi için docker network tanımı da gerekiyor ama ondan daha sonra bahsedeceğim).

Docker File, seçeceğiniz temel bir docker imajına uygulamanızla ilgili dosyaları eklemek ve ayarları yapmaya olanak veriyor. "docker build" komutu ile de Docker File içide tanımlanan adımlar icra edilerek imaj oluşturuluyor. Bu imajı da herhangi uyumlu bir container çalıştırma ortamında çalıştırabiliyorsunuz.

Öncelikle servisin bir geliştirme makinesinde çalışması için gerekli araç, modül ve dosyaları tespit etmek gerekti. Servis basit olduğu için bu pek zor olmadı. Gereken araçlar;

- apache http server
- Perl
- Perl CGI, JSON, Net::Ping ve Time::Hires modülleri
- gcc build ortamı

dosyalar

- Apache httpd konfigürasyon dosyası (httpd.conf)
- httpd.conf'a eklenecek (Include) servis konfigürasyon dosyası (hostping.conf)
- ve proje dosyaları (perl backend uygulaması ve wrapper, hostping.html, js modülleri, css vs)

Temel imaj olarak önce [apache httpd](https://hub.docker.com/_/httpd) imajını kullanmak istedim. Ancak imaja servisin çalışması için gerekli Perl modüllerinin ve derleme ortamının kurulmasının zorluğu nedeniyle temel [alpine linux](https://hub.docker.com/_/alpine) imajını tercih ettim. Ortaya çıkan Docker File aşağıda (en son hali için proje dizinine bakabilirsiniz).

```Docker {.line-numbers}
FROM alpine:3.15
RUN apk add perl && \
    apk add perl-cgi && \
    apk add perl-json && \
    apk add apache2 && \
    apk add build-base
COPY . /var/www/HostPing/
COPY conf/docker-httpd.conf /etc/apache2/httpd.conf
COPY conf/docker-hostping.conf  /etc/apache2/conf.d/hostping.conf
RUN gcc -o /var/www/HostPing/WebContent/hostping.ks \
            /var/www/HostPing/src/hostping.c && \
    rm /var/www/HostPing/src/hostping.c
RUN apk del build-base
RUN chown root.root /var/www/HostPing/WebContent/hostping.ks  
RUN chmod 4755 /var/www/HostPing/WebContent/hostping.ks
EXPOSE 80
CMD ["httpd", "-DFOREGROUND" ]
```

1\. satırda oldukça küçük (<6MB) alpine linux dağıtımıyla imaj oluşturmaya başlıyor.

2-6. satırlarda gerekli uygulama ve modüller bu temel linux imajına kuruluyor.

7-9. satırlarda uygulama içeriği imajda uygun yerlere kopyalanıyor.

10-12. satırlarda Perl arkayüz uygumalasını setuid olarak çalıştıracak C kodu derleniyor.

13\. satırda derleme ortamı imajdan kaldırılıyor.

14 ve 15. satırlarda setuid ayarları yapılıyor.

16\. satırda "container"ın 80 portu dışarıdan (host) erişime açılıyor.

17\. satırda da httpd uygulaması çalıştırılıyor.

Container, Docker File'ın son ve tek olması gereken "CMD" satırını icra ettikten sonra sonlanıyor. Normalde daemon olarak arka planda (background) çalışması gereken httpd, container çalıştığına sonlanmaması için önplanda (foragroud) çalıştırılıyor.

Imajın ufak olmasını sağlamak için oldukça küçük bir linux dağıtımından başlamış olsam da sonunda imaj büyüklüğü 244MB oldu!

Yerel makinenize kopyaladığınız (git clone?, tar copy) projede Docker File'ın olduğu dizinde aşağıdaki komutla "docker container" imajını yaratabilirsiniz.

```bash
% docker build -t hostping:latest .
```

Yapılan imaj aşağıdaki komutla çalıştırılır

```bash
% docker run --rm -it hostping:latest
```

Internet tarayıcınızla <http://localhost/hostping> adresine giderek servise erişebilirsiniz. Ancak ağ düzenlemesi (docker network) yapılmadığı için çalışan container içinden dışarı (ne imajı çalıştıran host, ne de Internet) erişemezsiniz. Bunun için yapılması gerekenleri bilahare yazacağım.
