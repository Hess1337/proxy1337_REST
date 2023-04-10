# proxy1337_REST
Api Proxy1337
## CreateNewKey {#CreateNewKey}

Cоздание нового ключа.

> POST dev/createKey/

~~~json
  {
    "email" : "admin@proxy1337.com",
  }
~~~
На вашу электронную почту прийдет уведомление с вашим ключом авторизации

## GetBasePrivate {#GetBasePrivate}

Получение базы доступных серверных и мобильных прокси

> GET dev/getBasePrivate/
~~~json
  {
		"id": "7",
		"name": "Серверные / IPv4 / Россия / #1",
		"nameEn": "Server / IPv4 / Russia / #1",
		"country": "ru",
		"countryName": "Россия",
		"countryNameEn": "Russia",
		"periods": [
			30,
			60,
			90
		],
		"product_type": "proxy",
		"total_over": "1256",
		"lat": "59.8983",
		"lon": "30.2618"
	}
~~~
Поле                 | Описание
---------------------|-------------------
id                   | Статичный числовой айди  
name                 | Имя прокси (Ru)
nameEn               | Имя прокси (En)
country              | Код страны в Alpha-2 ISO 3166-1
countryName          | Имя страны прокси (Ru)
countryNameEn        | Имя страны прокси (En)
periods              | Периоды, доступные к покупке для данного товара
total_over           | Кешированные данные по остаткам прокси (Обновляются раз в 30 минут)
lat                  | Координаты прокси (Ширина)
lon                  | Координаты прокси (Долгота)

## getBalance {#getBalance}

Получение баланса API ключа

> GET dev/getBalance/
~~~json
  {
     "balance": "1337",
  }
~~~
