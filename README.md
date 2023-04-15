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
На вашу электронную почту придет уведомление с вашим ключом авторизации

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

## buyProxy {#buyProxy}
> POST dev/buyProxy/
Покупка прокси
~~~json
  {
     "proxy_id": "1337",
     "proxy_count": "1337",
     "period": "1337"
  }
~~~
Поле                 | Описание
---------------------|-------------------
proxy_id             | Номер прокси из списка {#GetBasePrivate} [id]
proxy_count          | Количество покупаемых прокси
period               | Период покупки прокси, должен совпадать с "periods" из {#GetBasePrivate}
~~~json
  {
     "success": true,
     "order": 1337,
  }
~~~
Поле                 | Описание
---------------------|-------------------
success              | Статус запроса
order          	     | Номер заказа
## Коды ответов {#errors}
~~~json
  {
     "code": 404,
     "description": "Method not found",
  }
~~~
Поле                 | Описание
---------------------|-------------------
1              	     | Key not found (Ключ автризации не найден)
2		     | Not enough funds (Недостаточно средств)
3		     | Internal server error (Внутренняя ошибка сервера)
200		     | The operation was completed successfully (Операция успешна)
404		     | Method not found (Метод не найден)
500		     | Error in parameters (Ошибка параметров)
