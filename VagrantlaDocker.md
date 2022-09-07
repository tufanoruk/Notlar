# "Vagrant Box"da "Docker Container" 

"Docker Container"ı [Vagrant](https://www.vagrantup.com) box ile derleyip çalıştırma ile iligli notlarımı burada toparladım.

Öncelike neden buna ihtiyaç duyduğumu açıklayayım. Kullanılabilecek [Docker ağ](https://docs.docker.com/network/) seçenekleri Linux host makinelerinde daha zengin. Windows ve MacOS makinelerinde sadece "bridge" ağ sağlıklı çalışırken Linux host makinlerinde "host", "ipvlan", "macvlan" gibi diğer ağ konfigürasyonları da başarılı şekilde çalışıyor. "bridge" ağ yapısında olan bir "container" sadece o "bridge"e bağlı diğer "container"larla haberleşebiliyor. Dış dünyaya (çalıştığı host dahil) erişemiyor.

Öğrenme amaçlı "dockerize" ettiğim [HostPing](https://github.com/tufanoruk/HostPing) servisinin dış dünyaya (Internet) erişimi gerekiyor. Bunu MacOS bir host makinede sağlamanın kolay yolu dockerize HostPing servisini Linux bir Vagrant box üzerinde çalıştırmak, zira "[docker host networking](https://docs.docker.com/network/host/)" MacOS'da (ve Windows'da) çalışmıyor.  Büyük ihtimalle bu yapı Windows host makinlerle de çalışacaktır. 

Yapılması gereken sadece uygun bir Vagrantfile yazılması. [HostPing](https://github.com/tufanoruk/HostPing) için olanı aşağıda paylaşıyorum. 

```Ruby {.line-numbers}
Vagrant.configure("2") do |config|

  config.vm.box = "hashicorp/bionic64"

  config.vm.network "forwarded_port", guest: 80, host: 8081

  config.vm.provision "docker" do |d|

    d.build_image "/vagrant",
      args: "-t hostping:latest"

    d.run "hostping:latest",
      args: "--network host"

    end
end
```

Linux box olarak Vagrant'ın önerdiği "hashicorp/bionic64" (ubuntu 18.x) kullandım. 3\. satırda bu tanımlı. 5\. satırda VM'i çalıştıran host makinesinin 8081 "port"unu VM'in (guest) 80 portuna "forward" edecek konfigürasyon tanımlanıyor. HostPing container çalıştığı host'da (bu durumda Vagrant box'da) 80 portuna eşlenmiş durumda. Bu sayede servis çalıştığında <http://localhost:8081/hostping> ile servise erişilebilecek.

```text
    host:8081 --> guest:80 --> container:80
```

9\. satırdan itibaren Linux "Vagrant box"a docker kurulması, HostPing container "build" edilmesi ve sonrasında da çalıştırılması adımları var.

HostPing servisini Vagrant box üzerinde docker container olarak çalıştırmak için projenin Vagrantfile olan dizinde

```shell
% vagrant up
```

demek yeterli. Bu komutla vagrant

- "hashicorp/bionic64" Linux'u host makineye yüklüyor ve açıyor (3\. satır).
  - Vagranfile olan dizin (HostPing proje dizini) "box"da /vagrant altına mount edilir. Dolayısya tüm proje dosyaları Vagrant box ile /vagrant dizininde paylaşılıyor.
- host makinenin 8081 portunu "guest"in 80 portu ile ilişkilendiriyor (5\. satır)
- "box"a docker kuruyor ([vagrant docker provision](https://www.vagrantup.com/docs/provisioning/docker)) (7\. satır)
- /vagrant dizinindeki Dockerfile ile hostping:latest etiketli "container"ı oluşturuyor (build) (9-10 satırlar).
- "box"da hostping:latest "container"ı "host networking" ile çalıştırıyor.

Bu aşamadan sonra makinenizde <http://localhost:8081/hostping> ile HostPing servisine erişerek dışarıdaki herhangi bir makineyi "ping"leyebilirsiniz.
