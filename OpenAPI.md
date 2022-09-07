# OpenAPI

[OpenAPI](https://dev.to/mikeralphson/a-brief-history-of-the-openapi-specification-3g27) özellikle ağ üzerinden REST tabanlı olarak verilen servislerin arayüzlerini tanımlama için kullanılan bir standarttır. Arayüz tanımı bir standarda bağlandığında, arayüzde tanımlanan servisi verecek sunucu (server) ve onu kullanacak istemci (client) uygulaması için kod üreten araçlar geliştirmek mümkündür.

Arayüz, geliştirme detayını (algoritmayı) kullanıcıdan saklar. Arayüze programlama en temel yazılım geliştirme kavramlarında biridir. Yazılım kütüphaneleri bu mantığa dayanır.

OpenAPI ve ondan önceki WSDL (Web Definition Language), [OMG CORBA](https://www.omg.org/corba/) IDL (Interface Definition Language) gibi standartlar ağ üzerinde bulunan servislerin kütüphane mantığı ile geliştirilmesi ve kullanımına olanak sağlar. Bu yapının sağladığı faydaları aşağıda sıralayabiliriz.

* Servis veren sunucu uygulama ile servisi alan (istemci) uygulama (kullanılan kod üreticinin desteklediği) farklı dillerde yazılabilir.
  
* Bu sayede hem servis, hem de servisi kullanan uygulama için en uygun geliştirme dili ve araçları kullanılabilir,

* Servis ya da istemciyi geliştiren kişi en yetkin olduğu programlama dilini ve araçları kullanılabilir,

* İstemci uygulamasını geliştirien kişi, sanki kendi kapsamında (scope) bir arayüzü çağrıyormuş gibi uzaktaki servisi çağırır, sonucunu alır,
  
* İletşim altyapısı, ağ programlama ve mesajlaşma ağ paketlerinin yapısıyla (wire format) uğraşmak durumunda kalmaz. Uygulamasının algoritmasına yoğunlaşacak daha fazla zamanı olur.

OpenAPI, SmartBear [Swagger](https://swagger.io/resources/open-api/) projesinin "Linux Foundation"a (LF) devredilmiş halidir. OpeAPI3.0'den itibaren [API spesifikasyonu](https://spec.openapis.org) "LF OPENAPI Initiative" tarafından belirlenmekte. 

Spesifikasyona uygun olarak hazırlanan API tanımı

* API tasarım ve dokümantasyonun birlikte olmasına,
* API tanımın geliştirme çevrimine uyumlandırılmasına,
* Bir çok farklı dilde sunucu ve istemci kütüphanelerin oluşturlmasına,
* LF gibi çok büyük bir topluluk tarafından kullanılan ve geliştirilen bir çok [yardımcı aracın](https://openapi.tools/#sdk) kullanımına

olanak sağlar.

OpenAPI3.0 uyumlu API tanımları için kod üretim araçlarından biri olan "[openapi-generator](https://openapi-generator.tech/)" (6.0 sürümüyle) [aşağıdaki](#openapi-generator-list) sunucu ve istemciler için kütüphane ve dokümantasyon üretilebilmekte.

OpenAPI'nin tecrübe ettiğim en yoğun kullanımı 5G Core Network (CN) SBI (Service Based Interface) tanımları. 5G CN servislerinin hepsinin tanımı OpenAPI3.0 uyumlu [YAML dokümanları](https://github.com/jdegre/5GC_APIs) ile yapılmış durumda.

Özetle, WEB üzerinden (REST API ile) sağlayacağınız servislerin arayüzlerini OpenAPI spesifikasyonuna göre tanımlarsanız, (defacto) standartlara uyumlu geliştirme yapmamın birçok kolaylığından faydalanabilir, kendi ve servisinizde faydalanan "müşterilerin" geliştirme ve doğrulamalarını çok daha hızlı yapabilir, "müşteri" ile iletişimi ve aynı sayfada buluşmayı kolaylaştırmış olursunuz.

---

###### openapi-generator-list

```bash
% openapi-generator list   
The following generators are available:

CLIENT generators:
    - ada
    - android
    - apex
    - bash
    - c
    - clojure
    - cpp-qt-client
    - cpp-restsdk
    - cpp-tiny (beta)
    - cpp-tizen
    - cpp-ue4 (beta)
    - crystal (beta)
    - csharp
    - csharp-netcore
    - dart
    - dart-dio
    - eiffel
    - elixir
    - elm
    - erlang-client
    - erlang-proper
    - go
    - groovy
    - haskell-http-client
    - java
    - java-micronaut-client (beta)
    - javascript
    - javascript-apollo (beta)
    - javascript-closure-angular
    - javascript-flowtyped
    - jaxrs-cxf-client
    - jmeter
    - k6 (beta)
    - kotlin
    - lua (beta)
    - nim (beta)
    - objc
    - ocaml
    - perl
    - php
    - php-dt (beta)
    - powershell (beta)
    - python
    - python-experimental (experimental)
    - python-legacy
    - r
    - ruby
    - rust
    - scala-akka
    - scala-gatling
    - scala-sttp (beta)
    - scalaz
    - swift5
    - typescript (experimental)
    - typescript-angular
    - typescript-aurelia
    - typescript-axios
    - typescript-fetch
    - typescript-inversify
    - typescript-jquery
    - typescript-nestjs (experimental)
    - typescript-node
    - typescript-redux-query
    - typescript-rxjs


SERVER generators:
    - ada-server
    - aspnetcore
    - cpp-pistache-server
    - cpp-qt-qhttpengine-server
    - cpp-restbed-server
    - csharp-netcore-functions
    - erlang-server
    - fsharp-functions (beta)
    - fsharp-giraffe-server (beta)
    - go-echo-server (beta)
    - go-gin-server
    - go-server
    - graphql-nodejs-express-server
    - haskell
    - haskell-yesod (beta)
    - java-camel
    - java-inflector
    - java-micronaut-server (beta)
    - java-msf4j
    - java-pkmst
    - java-play-framework
    - java-undertow-server
    - java-vertx-web (beta)
    - jaxrs-cxf
    - jaxrs-cxf-cdi
    - jaxrs-cxf-extended
    - jaxrs-jersey
    - jaxrs-resteasy
    - jaxrs-resteasy-eap
    - jaxrs-spec
    - kotlin-server
    - kotlin-spring
    - kotlin-vertx (beta)
    - nodejs-express-server (beta)
    - php-laravel
    - php-lumen
    - php-mezzio-ph
    - php-slim4
    - php-symfony
    - python-aiohttp
    - python-blueplanet
    - python-fastapi (beta)
    - python-flask
    - ruby-on-rails
    - ruby-sinatra
    - rust-server
    - scala-akka-http-server (beta)
    - scala-finch
    - scala-lagom-server
    - scala-play-server
    - scalatra
    - spring


DOCUMENTATION generators:
    - asciidoc
    - cwiki
    - dynamic-html
    - html
    - html2
    - markdown (beta)
    - openapi
    - openapi-yaml
    - plantuml (beta)


SCHEMA generators:
    - avro-schema (beta)
    - graphql-schema
    - ktorm-schema (beta)
    - mysql-schema
    - protobuf-schema (beta)
    - wsdl-schema (beta)


CONFIG generators:
    - apache2
```

---

[OMG CORBA](https://www.omg.org/corba/) IDL (Internface Definition Language), ilk nesil web arayüz tanımlama standardı WSDL (Web Service Description Languagae) buna örnek verilebilir. Arayüz tanımala standarları kullanılarak
