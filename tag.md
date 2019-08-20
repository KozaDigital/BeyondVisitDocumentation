[Tüm Dökümantasyonlar](https://github.com/KozaDigital/BeyondVisitDocumentation/blob/master/README.md)

BeyonVisit Tag Kurulumu
======================

1. [Tüm Sayfalar](#tum)
2. [Ürün Detayı Sayfası](#urun)
3. [Sepet Sayfası](#sepet)
4. [Sipariş Sonu Sayfası](#siparis)
5. [Kategori Ürün Listeleme ve Arama Sayfası](#kategori)
6. [Arama Sayfası](#arama)
7. [Üye Giriş Sayfası](#giris)
8. [Üye Kayıt Sayfası](#kayit)
9. [Üye Çıkış Sayfası](#cikis)

<a name="tum"></a>

# 1. Tüm sayfalar
Tüm sayfalarda `</head>` öncesi yer alması gereken script tag'i

```html
<!--BeyondVisit Tag Start-->
<script>
    (function (w, d) {
        var n = d.createElement("script"); 
        n.src = "//<domain>.beyondvisit.com/robot.js";
        n.async=1;
        d.getElementsByTagName("head")[0].appendChild(n);
    }(window, document));
    window.beyondvisit_q= window.beyondvisit_q||[];
    window.beyondvisit_q.push({
        event:"view",
        values:
        {
            PageType:"<page_type>"
        }
    });
</script>
<!--BeyondVisit Tag End-->
```

**\<domain\>**
*type: String `required`*
>Bizimle anlaştığınız web sitenizin Domaini. (`******`)

**\<page_type\>**
*type: String:Any `required`*
>Mevcut sayfanın türü. 

<a name="urun"></a>

# 2. Ürün Detay Sayfası
Ürün detayı sayfasında olması gereken script tag'i.

```html
    <!--BeyondVisit Product Tag Start-->
    <script>
    window.beyondvisit_q.push({
        event:"product",
        values:
        {
            Sku:"<product_code>",
            Title:"<product_title>",
            Category:"<product_category>"
        }
    });
    </script>
    <!--BeyondVisit Product Tag End-->
```

**\<product_code\>**
*type: String `required`*
>Ürünün kodu. 

**\<product_title\>**
*type: String*
>Ürünün başlığı. 

**\<product_category\>**
*type: String*
>Görüntülenen ürünün kategori adı. 

<a name="sepet"></a>
# 3. Sepet Sayfası
Sepet sayfasında yer alması gereken script tag'i.

```html
    <!--BeyondVisit Cart Tag Start-->
    <script>
        window.beyondvisit_q.push({
            event:"cart",values:[
            {Sku:"<product_code>",Price_Sell:"<price_sell>",Currency:"<currency>",Quantity:"<quantity>"},
            ..
            ...
            ....
            ]
        });
    </script>
    <!--BeyondVisit Cart Tag End-->
```

**\<product_code\>**
*type: String:Any `required`*
*MaxLength: 128*
>Ürün kodu.

**\<price_sell\>**
*type: Number `required`*
>Satış Fiyatı.


**\<currency\>**
*type: String:Any _optional_*
>Para Birimi


**\<quantity\>**
*type: Integer `required`*
>Ürün adeti. 

<a name="siparis"></a>
# 4. Sipariş Sonu Sayfası
Siparişin onaylanmasından sonra açılan sayfa tagi

```html
    <!--BeyondVisit Order End Tag Start-->
    <script>
        window.beyondvisit_q.push({
            event:"order",
            values:
            {
             OrderNumber:"<order_number>",
             TotalPrice:"<total_price>",
             Currency:"<currency>",
             PaymentType:"<payment_type>",
             ShippingPrice:"<shipping_price>"
            }
         });
    </script>
    <!--BeyondVisit Order End Tag End-->
```

**\<order_number\>**
*type: String `required`*
*MaxLength: 255*
>Sipariş Numarası

**\<total_price\>**
*type: Number `required`*
*MaxLength: 100*
>Sipariş edilen toplam tutar.

**\<currency\>**
*type: String*
>Para Birimi.

**\<payment_type\>**
*type: String*
*MaxLength: 40*
>Ödeme yöntemi tercihi.

**\<shipping_price\>**
*type: Number*
>Ödeme yöntemi tercihi.

<a name="kategori"></a>
# 5. Kategori Ürün Listesi Sayfası
Kategori ürün listeleme sayfasında olması gereken script tag'i.

```html
    <!--BeyondVisit Category Tag Start-->
    <script>
    window.beyondvisit_q.push({
        event:"category",
        values:
        [
            "<product_code>"
            ..
            ...
        ]
    });
    </script>
    <!--BeyondVisit Category Tag End-->
```

**\<product_code\>**
*type: String:Any `required`*
*MaxLength: 128*
>Ürün kodu.

<a name="arama"></a>
# 6. Arama Sayfası
Arama Sayfasında olması gereken script tag'i.

```html
    <!--BeyondVisit Search Tag Start-->
    <script>
    window.beyondvisit_q.push({
        event:"search",
        values:
        {
            SearchKey:"<search_key>"
        }
    });
    </script>
    <!--BeyondVisit Search Tag End-->
```

**\<search_key\>**
*type: String `required`*
*MaxLength: 128*
>Aranan Kelime

<a name="giris"></a>
# 7. Üye Giriş Sayfası
Üye Giriş Sayfasında olması gereken script tag'i.

```html
    <!--BeyondVisit SignIn Tag Start-->
    <script>
        window.beyondvisit_q.push({
            event:"signIn",
            values:
            {
             FirstName:"<member_firstname>",
             LastName:"<member_lastname>",
             Email:"<member_email>",
            }
         });
    </script>
    <!--BeyondVisit SignIn Tag End-->
```

**\<member_firstname\>**
*type: String `required`*
>Giriş yapmış Üye'nin adı.

**\<member_lastname\>**
*type: String `required`*
>Giriş yapmış Üye'nin soyadı.

**\<member_email\>**
*type: String `required`*
>Giriş yapmış Üye'nin email adresi.

<a name="kayit"></a>
# 8. Üye Kayıt Sayfası
Üyelik kaydının tamamlandığı sayfada yer alması gereken script tag'i.

```html
    <!--BeyondVisit SignUp Tag Start-->
    <script>
    window.beyondvisit_q.push({
        event:"signUp",
        values:
        {
            MemberCode:"<member_code>",
            MemberGroup:"<member_group>",
            Company:"<member_company>",
            FirstName:"<member_firstname>",
            LastName:"<member_lastname>",
            Email:"<member_email>",
            Gender:"<member_gender>",
            BirthDate:"<member_birthdate>",
            Country:"<member_country>",
            City:"<member_city>",
            Adress:"<member_address>",
            PostalCode:"<member_postalcode>",
            IDnumber:"<member_idnumber>",
            Phone1:"<member_phone1>",
            Phone2:"<member_phone2>",
            Phone3:"<member_phone3>"
        }
    });
    </script>
    <!--BeyondVisit SignUp Tag End-->
```

**\<member_code\>**
*type: String*
>Üye Kod.

**\<member_group\>**
*type: String*
>Üye Grubu.

**\<member_company\>**
*type: String*
>Firma Adı.

**\<member_firstname\>**
*type: String `required`*
>Üye Adı.

**\<member_lastname\>**
*type: String `required`*
>Giriş yapmış Üye'nin soyadı.

**\<member_email\>**
*type: String `required`*
>Giriş yapmış Üye'nin email adresi.

**\<member_gender\>**
*type: String*
>Üye'nin Cinsiyeti.

**\<member_birthdate\>**
*type: String*
>Üye'nin Doğum tarihi.

**\<member_country\>**
*type: String*
>Ülke.

**\<member_city\>**
*type: String*
>Şehir.

**\<member_address\>**
*type: String*
>Adres Bilgisi.

**\<member_postalcode\>**
*type: String*
>Posta Kodu.

**\<member_idnumber\>**
*type: String*
>Kimlik Numarası.

**\<member_phone1\>**
*type: String*
>Telefon Numarası 1.

**\<member_phone2\>**
*type: String*
>Telefon Numarası 2.

**\<member_phone3\>**
*type: String*
>Telefon Numarası 3.

<a name="cikis"></a>
# 9. Üye Çıkış Sayfası
Üye'nin çıkış yaptığı sayfa için script tag'i.

```html
    <!--BeyondVisit SignOut Tag Start-->
    <script>
    window.beyondvisit_q.push({
        event:"signOut",
        values:
        {
            Email:"<member_email>"
        }
    });
    </script>
    <!--BeyondVisit SignOut Tag End-->
```

**\<member_email\>**
*type: String `required`*
>Çıkış yapmış Üye'nin email adresi.
