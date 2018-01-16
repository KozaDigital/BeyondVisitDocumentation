[Tüm Dökümantasyonlar](https://github.com/KozaDigital/BeyondVisitDocumentation/blob/master/README.md)

BeyondVisit Partner entegrasyonu
===================

Entegrasyon aşamaları 
1. [Login Tokeni Alma](#anahtar)
2. [Oturum Açma](#oturum)

<a name="anahtar"></a>
Login Tokeni Alma 
================

<a href="https://app.getpostman.com/run-collection/739da96bea5df8c10dc9" target="_blank">![Run in Postman](https://run.pstmn.io/button.svg)</a>

Kullanıcı girişi yapılmak istendiği zaman önce login tokeni üretmelisiniz. 
Login tokenini üretek için ``http://panel.beyondvisit.com/external/LoginToken`` servis adresine aşağıdaki parametreleri içeren bir post isteği atmanız gerekmektedir.
```json
    {
        "apiKey":"<api_key>",
        "sign":"<MD5(apikey+secretkey)>",
        "userToken": "<userToken>"
    }
```
## Kullanımı
**userToken**
*Type: String,*
*MaxLength: 32*
>CreateUser servis metodunun sonucu olarak dönen userToken değeridir.


Sonuç
======
Bu istekten 2 farklı sonuç alabilirsiniz;

## Başarılı
```json
    { 
        "status" : true, 
        "message" : "Success", 
        "loginToken" : "[user_login_token]",
        "userCode" : "[user_code]"
    }
```
Başarılı olması durumunda gelen cevaptaki `loginToken` alanını kullanının login işlemini gerçekleştirmek için kullanılacaktır.

## Başarısız
```json
    { 
        "status"  : false,
        "code"    : 1, 
        "message" : "User not found with token: [userToken]" 
    }
```
`status` ***true*** olmadığı sürece token oluşturma işlemi başarısız sonuçlanmış demektir.Hata mesajı örnekteki gibi belirtilir.

Hata kodları ve açıklamaları

| code | message                                 |
|------|-----------------------------------------|
| 1    | User not found with token: [userToken]  |
| 2    | Authentication failed                   |
| 3    | ApiKey not found                        |


`userCode` alanı scriptlerde kullanılacak olan kullanıcı kodudur.


<a name="oturum"></a>
BeyonVisit üzerinde oturum açma 
=============================

Login tokeni alma işlemi gerçekleştirdikten sonra alınan `loginToken` değeri kullanılarak kullanıcının browserini aşağıdaki url ye yönlendirmelisiniz.

    http://panel.beyondvisit.com/external/Login/{loginToken}

Tüm adımların doğru gerçekleştirilmesi durumunda kullanıcı panele erişebilir olacaktır.

Sisteminiz üzerinden login işleminin daha sonra tekrar gerçekleştirilmek istendiğinde `Login Token Alma` işleminden itibaren bu adımlar tekrarlanmalıdır.
