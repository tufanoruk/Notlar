# OpenAPI

OpenAPI özellikle ağ üzerinden REST tabanlı olarak verilen servislerin arayüzlerini tanımlama için kullanılan bir standarttır. Arayüz tanımı bir standarda bağlandığında, arayüzde tanımlanan servisi verecek sunucu/servis ve onu kullanacak istemci uygulaması için kod üreten araçlar geliştirmek mümkündür.

Arayüz, geliştirme detayını (algoritmayı) kullanıcıdan saklar. Arayüze programlama en temel yazılım geliştirme kavramlarında biridir. Yazılım kütüphaneleri bu mantığa dayanır.

OpenAPI ve ondan önceki WSDL (Web Definition Language), [OMG CORBA](https://www.omg.org/corba/) IDL (Interface Definition Language) gibi standartlar ağ üzerinde bulunan servislerin kütüphane mantığı ile geliştirilmesi ve kullanımına olanak sağlar. Bu yapının sağladığı faydaları aşağıda sıralayabiliriz.

* Servis veren uygulama ile alan (istemci) uygulama (kullanılan kod üreticinin desteklediği) farklı dillerde yazılabilir.
  
* Bu sayede hem servis hem servisi kullanan uygulama için en uygun geliştirme dili ve araçları kullanılabilir,

* Servis ya da istemciyi geliştirne kişi en yetkin olduğu programla dilini ve araçları kullanılabilir,

* İstemci uygulamasını geliştirien kişi, sanki kendi kapsamında (scope) bir arayüzü çağrıyormuş gibi uzaktaki servisi çağırır, sonucunu alır,
  
* İletşim altyapısı, ağ programlama ve mesajlaşma ağ paketlerinin yapısıyla (wire format) uğraşmak durumunda kalmaz. Uygulamasının algoritmasına yoğunlaşacak daha fazla zamanı olur.
   

---

[OMG CORBA](https://www.omg.org/corba/) IDL (Internface Definition Language), ilk nesil web arayüz tanımlama standardı WSDL (Web Service Description Languagae) buna örnek verilebilir. Arayüz tanımala standarları kullanılarak 