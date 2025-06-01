<h1 align="center">
Repo Visitor Counter API<a name="readme-top"></a>
</h1>

<div align="center">
  <img src="./Readme Resources/Repo Visitor Counter API Logo.png" alt="Logo" width="120"/>
</div>

## **İçindekiler**

- [API Hakkında](#api-hakkında)
- [Dokümantasyon](#dokümantasyon)
- [İstek Örnekleri](#i̇stek-örnekleri)
- [Lisans](#lisans)
- [İletişim](#i̇letişim)


![-----------------------------------------------------](./Readme%20Resources/Line.png)

## API Hakkında

Bu repo, GitHub repo ziyaretlerini takip eden sayaç API'nin dokümantasyonunu içerir.

HTTP GET istekleriyle `repo`, `bg_color`, `txt_color`, `show_date`, `show_repo_name`, `show_brand`
parametrelerini alır ve belirli bir repoya yapılan ziyaretlerin sayısını izler ve bu bilgileri
dinamik olarak oluşturulmuş bir PNG resim olarak sunar.

Yanıltıcı sonuçları önleyebilmek adına aynı repo için aynı IP adresinden gelen istekler yalnızca 10
dakikada bir kaydedilir. 


![-----------------------------------------------------](./Readme%20Resources/Line.png)

## Dokümantasyon

Base URL: `https://toktasoft.com/api/repo-visitor-counter`

API 6 farklı parametre almaktadır.

| Parametre                              | Zorunlu Mu?                 | Değerler                                 | Varsayılan Değer                  | Açıklama                                                                       |
| -------------------------------------- | --------------------------- | ---------------------------------------- | --------------------------------- | ------------------------------------------------------------------------------ |
| <p align="center">`repo`</p>           | <p align="center">evet</p>  | `Repo'nun API veritabanındaki ID değeri` |                                   |                                                                                |
| <p align="center">`bg_color`</p>       | <p align="center">hayır</p> | `RGB renk kodları`                       | <p align="center">34,39,46</p>    | Resmin arkaplan rengi için RGB renk kodunun yazıldığı parametre                |
| <p align="center">`txt_color`</p>      | <p align="center">hayır</p> | `RGB renk kodları`                       | <p align="center">197,239,222</p> | Yazı rengi için RGB renk kodunun yazıldığı parametre                           |
| <p align="center">`show_date`</p>      | <p align="center">hayır</p> | `1`<br>`0`                               | <p align="center">0</p>           | `1` veya `0`'dan başka bir değer girilirse 0 değeri yazılmış gibi işlem görür. |
| <p align="center">`show_repo_name`</p> | <p align="center">hayır</p> | `1`<br>`0`                               | <p align="center">0</p>           | `1` veya `0`'dan başka bir değer girilirse 0 değeri yazılmış gibi işlem görür. |
| <p align="center">`show_brand`</p>     | <p align="center">hayır</p> | `1`<br>`0`                               | <p align="center">1</p>           | `1` veya `0`'dan başka bir değer girilirse 1 değeri yazılmış gibi işlem görür.<br>Ayrıcalıklı olmayan kullanıcılar parametreye 0 değerini yazsalar bile API sağlayıcı adı resim üzerinde gösterilmeye devam edilir. |

API'yi kullanmak isteyen kullanıcıların repolarını API veritabanına kaydettirmek için iletişime geçmesi gerekmektedir.

- **Repo ve Kullanıcı Yönetimi:** Kullanıcılar API veritabanına kayıtlı repolarıyla eşleştirilir. Yalnızca ayrıcalıklı kullanıcılar `show_brand` parametresini kontrol edebilir.
- **Ziyaret Sayısı Takibi:** Her başarılı istek sonrası ilgili repo için aylık ve toplam ziyaretçi sayıları güncellenir.


![-----------------------------------------------------](./Readme%20Resources/Line.png)

## İstek Örnekleri

İstek örnekleri `curl` komut satırı aracı kullanılarak gösterilmiştir.

✅**Sadece zorunlu olan parametre isteği**

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz)

✅**Repo adı bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_repo_name=1"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_repo_name=1)

✅**Tarih bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1)

✅**Tarih ve repo adı bilgisinin yazdırıldığı istek**

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1"
```
![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1)

✅**Tarih ve repo adının yazdırıldığı, API sağlayıcı bilgisinin yazdırılmadığı istek**

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=0"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=0)

✅**Tarih, Repo adı, API sağlayıcı bilgisinin yazdırıldığı ve renklerin değiştirildiği istek**

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=1&bg_color=0,0,0&txt_color=0,255,0"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&show_date=1&show_repo_name=1&show_brand=1&bg_color=0,0,0&txt_color=0,255,0)

❌**Yanlış İstek**

`repo` parametresine API veritabanında bulunmayan bir ID değeri yazılırsa hata mesajı yazan resim döndürülür.

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=bulunmayaniddegeri"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=bulunmayaniddegeri)

❌**Yanlış İstek**

`bg_color` ve `txt_color` parametrelerine RGB formatında olmayan değerler yazılırsa hata mesajı yazan resim döndürülür.

```sh
curl -X GET "https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&bg_color=-11,0,0&txt_color=300,300,300"
```

![Repo Visitor Counter](https://toktasoft.com/api/repo-visitor-counter?repo=h2fktgj3v8e69nz&bg_color=0,0,0&txt_color=300,300,300)


![-----------------------------------------------------](./Readme%20Resources/Line.png)

<div align="center">
  <a href="https://github.com/mustafatoktas/W.BE_RepoVisitorCounterAPI"><img src="https://toktasoft.com/api/repo-visitor-counter?repo=j9rm7kp2vdcxsau&show_repo_name=1&show_date=1&show_brand=0&txt_color=209,215,224&bg_color=45,52,58" alt="Repo Visitor Counter"/></a>
</div>

<br>
  
<div align="center">
  <a href="https://buymeacoffee.com/mustafatoktas"><img src="./Readme Resources/Communication/Buy Me a Coffee.png" alt="Buy Me a Coffee" height="64"/></a>
</div>


![-----------------------------------------------------](./Readme%20Resources/Line.png)

## Lisans

```
Copyright 2024-2025 Mustafa TOKTAŞ

Licensed under the GNU General Public License v3.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    https://www.gnu.org/licenses/gpl-3.0.html

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```


![-----------------------------------------------------](./Readme%20Resources/Line.png)

## İletişim

<a href="mailto:info@mustafatoktas.com"             ><img src="./Readme Resources/Communication/Mail.png"     alt="Mail"     width="64"/></a>
<a href="https://t.me/mustafatoktas00"              ><img src="./Readme Resources/Communication/Telegram.png" alt="Telegram" width="64"/></a>
<a href="https://www.linkedin.com/in/mustafatoktas/"><img src="./Readme Resources/Communication/LinkedIn.png" alt="LinkedIn" width="64"/></a>

<p align="center">
  <a href="#readme-top"><img src="./Readme Resources/Back to Top.png" alt="Back to Top" height="64"/></a>
</p>
