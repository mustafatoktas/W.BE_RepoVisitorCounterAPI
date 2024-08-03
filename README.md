<h1 align="center">Repo Visitor Counter API</h1>

<div align=center>
  <img src="./Readme%20Resources/Repo Visitor Counter API Logo.png" alt="Logo" width="120" heigh="120"/>
</div>

## **İçindekiler**

- [API Hakkında](#api-hakkında)
- [Dokümantasyon](#dokümantasyon)
- [İstek Örnekleri](#i̇stek-örnekleri)
- [Lisans](#lisans)
- [İletişim](#i̇letişim)


![-----------------------------------------------------](./Readme%20Resources/Çizgi.png)

![Resim](https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=j9rm7kp2vdcxsau&show_repo_name=1&show_date=1&show_brand=1)


![-----------------------------------------------------](./Readme%20Resources/Çizgi.png)

## API Hakkında

Bu repo, PHP diliyle geliştirilmiş olan GitHub repo ziyaretlerini takip eden sayaç API'nin
dokümantasyonunu içerir.

HTTP GET istekleriyle `repo`, `bg_color`, `txt_color`, `show_date`, `show_repo_name`, `show_brand`
parametrelerini alır ve belirli bir repoya yapılan ziyaretlerin sayısını izler ve bu bilgileri
dinamik olarak oluşturulmuş bir PNG görüntü olarak sunar.

Yanıltıcı sonuçları önleyebilmek adına aynı repo için aynı IP adresinden gelen istekler yalnızca 10
dakikada bir kaydedilir. 


![-----------------------------------------------------](./Readme%20Resources/Çizgi.png)

## Dokümantasyon

Base URL: `https://toktasoft.com/api/github2/repo-visitor-counter.php`

API 6 farklı parametre almaktadır.

| Parametre                              | Zorunlu Mu?                 | Değerler                                 | Varsayılan Değer                  | Açıklama                                                                       |
| -------------------------------------- | --------------------------- | ---------------------------------------- | --------------------------------- | ------------------------------------------------------------------------------ |
| <p align="center">`repo`</p>           | <p align="center">evet</p>  | `Repo'nun API veritabanındaki ID değeri` |                                   |                                                                                |
| <p align="center">`bg_color`</p>       | <p align="center">hayır</p> | `RGB renk kodları`                       | <p align="center">34,39,36</p>    | Resmin arkaplan rengi için RGB renk kodunun yazıldığı parametre                |
| <p align="center">`txt_color`</p>      | <p align="center">hayır</p> | `RGB renk kodları`                       | <p align="center">197,239,222</p> | Resimdeki yazılar için RGB renk kodunun yazıldığı parametre                    |
| <p align="center">`show_date`</p>      | <p align="center">hayır</p> | `1`<br>`0`                               | <p align="center">0</p>           | `1` veya `0`'dan başka bir değer girilirse 0 değeri yazılmış gibi işlem görür. |
| <p align="center">`show_repo_name`</p> | <p align="center">hayır</p> | `1`<br>`0`                               | <p align="center">0</p>           | `1` veya `0`'dan başka bir değer girilirse 0 değeri yazılmış gibi işlem görür. |
| <p align="center">`show_brand`</p>     | <p align="center">hayır</p> | `1`<br>`0`                               | <p align="center">1</p>           | `1` veya `0`'dan başka bir değer girilirse 1 değeri yazılmış gibi işlem görür.<br>Ayrıcalıklı olmayan kullanıcılar parametreye 0 değerini yazsalar bile marka adı resim üzerinde gösterilemeye devam edilir. |

API'yi kullanmak isteyen kullanıcıların repolarını API veritabanına kaydettirmek ve repo ID alabilmek için iletişime geçmesi gerekmektedir.

- **Repo ve Kullanıcı Yönetimi:** Kullanıcılar API veritabanına kayıtlı repolarıyla eşleştirilir. Ayrıcalıklı kullanıcılar `show_brand` parametresini kontrol edebilir.
- **IP Adresi Takibi:** API, aynı IP adresinden aynı repo için yapılan istekleri 10 dakikada bir kaydeder, böylece yanıltıcı ziyaret sayıları önlenir.
- **Ziyaret Sayısı Takibi:** Her başarılı istek sonrası ilgili repo için aylık ve toplam ziyaret sayıları güncellenir.


![-----------------------------------------------------](./Readme%20Resources/Çizgi.png)

## İstek Örnekleri

İstek örnekleri `curl` komut satırı aracı kullanılarak gösterilmiştir.

✅**Sadece zorunlu olan parametre isteği**

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz"
```

✅**Repo adı bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz&show_repo_name=1"
```

✅**Tarih bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz&show_date=1"
```

✅**Tarih ve Repo adı bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1"
```

✅**Tarih, Repo adı ve API sağlayıcı bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=1"
```

✅**Tarih, Repo adı, API sağlayıcı bilgisinin yazdırıldığı ve renklerin değiştirildiği istek**

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=1&bg_color=0,0,0&txt_color=255,255,255"
```

❌**Yanlış İstek**

`repo` parametresine API veritabanında bulunmayan bir ID değeri yazılırsa resim oluşturulmaz.

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=11111111111"
```

❌**Yanlış İstek**

Geçersiz bir RGB renk kodu yazılırsa resim oluşturulmaz.

```sh
curl -X GET "https://toktasoft.com/api/github2/repo-visitor-counter.php?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=1&bg_color=0,0,0&txt_color=300,300,300"
```


![-----------------------------------------------------](./Readme%20Resources/Çizgi.png)

## Lisans
    Copyright 2024 Mustafa TOKTAŞ

    Licensed under the GNU General Public License v3.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        https://www.gnu.org/licenses/gpl-3.0.html

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


![-----------------------------------------------------](./Readme%20Resources/Çizgi.png)

## İletişim

<a href="mailto:info@mustafatoktas.com"              target="_blank"> <img src="./Readme Resources/İletişim/Mail.png"     alt="Mail"     width="64" heigh="64"/> </a>
<a href="https://t.me/mustafatoktas00"               target="_blank"> <img src="./Readme Resources/İletişim/Telegram.png" alt="Telegram" width="64" heigh="64"/> </a>
<a href="https://www.linkedin.com/in/mustafatoktas/" target="_blank"> <img src="./Readme Resources/İletişim/LinkedIn.png" alt="LinkedIn" width="64" heigh="64"/> </a>
