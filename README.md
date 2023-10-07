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

## getOrder {#getOrder}
> POST dev/getOrder/
Получение заказа
~~~json
  {
     "order_id": "1337",
  }
~~~
Поле                 | Описание
---------------------|-------------------
order_id             | Номер заказа из {#buyProxy}

~~~json
  {
	{
	"orderId": 1337,
	"name": "\u0421\u0435\u0440\u0432\u0435\u0440\u043d\u044b\u0435 \/ Facebook \/ \u0421\u0428\u0410 \/ #6",
	"ip": "127.0.0.1",
	"port": 8000,
	"login": "66631b41",
	"password": "66631b41",
	"time": 1690745641,
	"expire": 1693337622,
	"port_http": "8000",
        "port_socks": "30011",
        "active_port": "http",
        "product_id": "594",
        "product_type": "proxy",
        "product_country": "us",
        "change_ip_link": "https://proxy1337.com/change_mobile/do/yiwdkI2TQ22",
        "rotate_can_change": "1",
        "rotate_min": "0",
        "rotate_max": "60",
        "rotate_active": "3"
	}
	{
	"orderId": 1338,
	"name": "\u0421\u0435\u0440\u0432\u0435\u0440\u043d\u044b\u0435 \/ Facebook \/ \u0421\u0428\u0410 \/ #6",
	"ip": "127.0.0.1",
	"port": 8000,
	"login": "66631b41",
	"password": "66631b41",
	"time": 1690745641,
	"expire": 1693337622,
	"port_http": "8000",
        "port_socks": "30011",
        "active_port": "http",
        "product_id": "594",
        "product_type": "proxy",
        "product_country": "us",
        "change_ip_link": "https://proxy1337.com/change_mobile/do/yiwdkI2TQ22",
        "rotate_can_change": "1",
        "rotate_min": "0",
        "rotate_max": "60",
        "rotate_active": "3"
	}

  }
~~~
Поле                 | Описание
---------------------|-------------------
orderId              | Номер заказа из {#buyProxy}
name          	     | Имя прокси
ip          	     | Айпи прокси
login         	     | Логин авторизации
password      	     | Пароль авторизации
time          	     | Время покупки (timestamp)
expire               | Дата окончания прокси (timestamp)
port_http            | http порт прокси
port_socks           | socks порт прокси
active_port          | Активный порт на данный момент
product_id           | Айди прокси из {#GetBasePrivate}
product_type         | Тип прокси (proxy - Серверный, mobile - Мобильный)
product_country      | Код страны в Alpha-2 ISO 3166-1
change_ip_link       | Ссылка для смены айпи адреса (Если прокси мобильный)
rotate_can_change    | Возможна ли смена айпи
rotate_min           | Минимально допустимое время смены айпи (В минутах)
rotate_max           | Максимально допустимое время смены айпи (В минутах)
rotate_active        | Время ротации прокси на данный момент

## createPayment {#createPayment} 
> POST dev/createPayment/
Пополнение баланса
~~~json
  {
     "sum": "1337",
  }
~~~
Поле                 | Описание
---------------------|-------------------
sum                  | Сумма пополнения
~~~json
  {
     "sum": 1337,
     "paymentLink": 'https://paymentlink',
  }
~~~
Поле                 | Описание
---------------------|-------------------
sum                  | Сумма пополнения
paymentLink          | Ссылка на мерчант для пополнения баланса ключа API

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
