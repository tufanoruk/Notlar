# Docker

"container" teknolojisinden ve "docker"dan bahsetmeye gerek yok. Bu konularla ilgili çok fazla kaynak mevcut. Öğrenmek için öncelikle ortamınızda Docker kurulmalı. Kurulumla "docker/getting-started "container" imajı da geliyor, en azından benim en son kurduğum zaman (Mart 2022) ve sürümle gelmişti.

```text
% docker --version
Docker version 20.10.13, build a224086
```

```text
% docker images
REPOSITORY               TAG       IMAGE ID       CREATED          SIZE
docker/getting-started   latest    083d7564d904   9 months ago     28MB
```

Bu gelen imajı çalştırdığınızda bir docker container nasıl yapıldığını anlatan, Internet tarayıcınızla erişebileceğiniz (<http://localhost:8080/tutorial/>) bir eğitim sayası sağlıyor. buradaki adımlarla ilk "conatiner" imajınızı oluşturabilirsiniz.

Bu sayfada ["Liz Rice"ın goto; 2018 konferansı](https://youtu.be/8fi7uSYlOdc)nda container teknolojisinde kullanılan Linux kernel "Namespaces" ve "cgroups"u Go program örneği ile açıkladığı videoya ulaşabilirisiniz. Seyredilmesini tavsiye ederim. "Container" teknolojisinin altında neler olduğunu anlamak için oldukça fadalandım.

Docker Desktop ile çalışılan Linux harici bir makinelerde Docker "conatiner"lar bir VM'de çalıştırılıoyor (MacOS için bu VM eskiden VirtualBox iken halihazırda HyperKit hipervizör kullanılıyor, Windows için bu Oracke VirtualBox). Bu nedenle Docker "Container"ın kullandığı Volume'ları bu VM içinde aramak gerekli.

```text
Please keep in mind, Docker for Mac runs a docker engine in a Linux VM, not your Mac OS, so you can't find the volume's mount point in your Mac OS file system. The volume files should existing in that Linux VM's file system.

However, you can login Docker for Mac's VM via screen:

$ screen ~/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux/tty  
#user: root
#password: xxxxxx
Then you can view the docker's volumes:

$ ls -ltrh /var/lib/docker/volumes
total 148
drwxr-xr-x    3 root     root          4096 May 16 13:20 04576d248c19b1210d47e94c8211493428cd3c3aa71dfe3fa0f4214589a6f875
drwxr-xr-x    3 root     root          4096 May 16 13:20 31af0f01492d8f7b832dad75e731b754302e84fbecfa7c654d7de10465bec204
etc.
```

Ancak güncel MacOS Docker Desktop kurulumlarından komut satırından (screen ya da başka şekildie) yukarıdaki dosyaya erişime izin vermiyor. Docker Dessktop ya da VSCode ile Volume dosyalarına erişilebiliyor.

VSCode ile erişim için [Docker eklentisi](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) kurulmuş olmalı. "Named Volume"a VSCode ile erişmek için bu "Named Volume"u mount eden bir "Dev Container" VSCode içinde çalıştırılarak erişim sağlanıyor.

"Volume Mount" dışında "Bind Mount" mekanizmasıyla da yerel makinedeki bir dizin Docker container içine mount edilebiliyor. Bu yöntem özellikle geliştirme ortamları için kullanılıyor. Zira proje dizini mount eden bir "container"a proje ile ilgili tüm geliştirme araçlarnı çalışılan makineyi bozmadam eklemek mümkün oluyor. Yani geliştirme ortamı "container" içinde, dosyaları yerel makinede oluyor. @@TODO VSCode "devcontanier"ın da bu mekanizmayı kullandığını düşünüyorum. Emin olunaca bu yazıyı gözden geçireceğim.

VSCode Docker eklentisi ile daha kolay çalışmak için devconatiner CLI'ı PATH'e eklemekte fayda var "F1 -> Remote Containers : Install devcontainer CLI" ile bu yapılabiliyor.
