# Важная информация!

## при оформлениии заказа такси, клиент должен отправить поле 'payment_type' 1 - нал, 2 - безнал, 3 - бонусы! При типе оплаты безнал запрос make-order/ вернет URL на который необходимо переотправить пользователя для ввода карты

## ПРИ ПОЛУЧЕНИИ УВЕДОМЛЕНИЯ С КОДОМ 0(НОЛЬ) ВЫ ДОЛЖНЫ ВЫВЕСТИ И КЛИЕНТУ, И ВОДИТЕЛЮ ОГРОМНЫЙ ТЕКСТ, ЧТО ОПЛАТА ОНЛАЙН НЕ ПРОШЛА ОПЛАТИТЕ НАЛОМ


### Firebase account :
`` taxi.plus.kz@gmail.com 
``
` Taxi1234 `


### Режимы такси (order_type)

* taxi - 1
* lady taxi - 2
* инва taxi - 3
* межгорож - 4 
* грузоперевозка - 5
* эвакуатор - 6

### Роли пользователей:

* 1 - User
* 2 - Driver
* 3 - Admin 

### Статус заказа:

* 1 - В ожидании
* 2 - В пути к клиенту
* 3 - Ожидает клиента
* 4 - В пути с клиентом
* 5 - Завершен
* 0 - Отменен



## API:

#### Коды ответа сервера: 
* 200 - OK
* 400 - Error
* 401 - Unauthorized
* 404 - Invalid url

### Base URL - ```http://185.236.130.126/profile/```

## Запрос на проверку номера
(Пока так, как будет смс сервис допилим)

#### ```path:     Base URL  + /check-phone/```
#### Method: POST

```
fields: 
{
    "phone" - required,
}
response:
{
    "state" - required
    "type" - required
    "token" - optional
    "message" - optional
}

```

## Запрос на получение доп. опций для водителя
(Пока так, как будет смс сервис допилим)

#### ```path:     Base URL  + /get-facilities/```
#### Method: GET

```
response:
{
    "state" - required
    "Facilities": [
    	{
            "id": 1,
            "name": "Кондиционер"
       }
    ]
 }

```

## Запрос на получение доп. опций для водителя


#### ```path:     Base URL  + /get-facilities/```
#### Method: GET

```
response:
{
    "state" - required
    "Facilities": [
    	{
            "id": 1,
            "name": "Кондиционер"
       }
    ]
 }

```



## Запрос на регистрацию стороннего водителя


#### ```path:     Base URL  + /driver-sign-up/```
#### Method: POST

```
application/json: 

{
	"name" : "Водитель первый",
	"phone" : "+77011481923",
	"gender" : 1,
	"car_number" : "X 013 WWS",
	"car_model" : 1,
	"year_of_birth" : 1990,
	"car_year" : 1993,
	"taxi_park_id" : 1
	"facilities" : [1, 2, 3]
}

response:
{
    "state" - required
    "token" - optional
}

```

## Запрос на загрузку аватарки

#### ```path:     Base URL  + /upload-avatar/```
#### Method: POST

```
fields: 
{
    "token" - required,
    "file" - required
}
response:
{
    "state" - required
    "message" - optional
    "path" - optional путь на аватарку
}

```

## Запрос на загрузку аватарки

#### ```path:     Base URL  + /upload-avatar/```
#### Method: POST

```
fields: 
{
    "token" - required,
    "file" - required
}
response:
{
    "state" - required
    "message" - optional
    "path" - optional путь на аватарку
}

```



## Запрос на получение аватарки

#### ```path:     Base URL  + /get-avatar/```
#### Method: POST

```
fields: 
{
    "token",
}
response:
{
    "state" 
    "avatar" 
}

```

## Запрос на получение сохраненных адресов

#### ```path:     Base URL  + /get-addresses/```
#### Method: POST

```
fields: 
{
    "token",
}
response:
{
    "state" 
    "addresses"  - массив объектов
}

```


## Запрос на получение истории поездок

#### ```path:     Base URL  + /get-orders/```
#### Method: POST

```
fields: 
{
    "token",
}
response:
{
    "state" 
    "orders"  - массив объектов
}

```





## Запрос на получение количества бонусов

#### ```path:     Base URL  + /get-bonuses/```
#### Method: POST

```
fields: 
{
    "token",
}
response:
{
    "state" 
    "balance" 
}

```

## Запрос на отправление push_id

#### ```path:     Base URL  + /set-push-id/```
#### Method: POST

```
fields: 
{
    "token",
    "push_id"
    "lat"
    "long"
    "platform" 0 - android, 1 - ios!
}
response:
{
    "state" 
    "is_active" - если придет 0 необходимо НЕ ДАВАТЬ ПОЛЬЗОВАТЕЛЮ ВОЗМОЖНОСТИ ОТПРАВЛЯТЬ КАКИЕ ЛИБО ЗАПРОСЫ С АЛЕРТОМ ВЫ НАХОДИТЕСЬ НА МОДЕРАЦИИ АДМИНИСТРАТОРА
    "is_session_opened" -открыта ли смена водителя
    "balance"

}

```

## Запрос на Получение стоимости на открытие смены водителя

#### ```path:     Base URL  + /get-session-price/```
#### Method: POST

```
fields: 
{
    "token",

}
response:
{
    "state" 
    "six_hours_price" 
    "unlim_price" 
}

```



## Запрос на Получение марок автомобилей
#### ```path:     Base URL  + /get-car-models/```
#### Method: GET

```

response:
{
    "models" 
    "type" 
}

```



## Запрос на Получение моделей автомобилей
#### ```path:     Base URL  + /get-car-submodels/```
#### Method: GET

```

fields:
{
    id

}
response:
{
    "models" 
    "type" 
}

```

## Запрос на Получение списка таксопарков
#### ```path:     Base URL  + /get-taxi-parks/```
#### Method: GET

```


response:
{
    "taxi_parks" 
}

```




## Запрос на авторизацию: Первый шаг
#### ```path:     Base URL  + /send-sms/```
#### Method: POST

```

fields:{
	phone - PHONE FORMAT: 77005554797!!! ПЛЮС СЕМЬ И ВОСЕМЬ НЕ РАБОТАЮТ!!!
}
response:
{
    "state" 
}

```


## Запрос на авторизацию: Второй шаг
#### ```path:     Base URL  + /verify-code/```
#### Method: POST

```

fields:{
	phone - PHONE FORMAT: 77005554797!!! ПЛЮС СЕМЬ И ВОСЕМЬ НЕ РАБОТАЮТ!!!
	code - КОД ИЗ СМС
}
response:
{
    "state" 
    token
    type
}

```


## Запрос на получение цены
#### ```path:     Base URL  + /get-price/```
#### Method: POST

```

fields:{
	token
	longitude_a
	latitude_a
	latitude_b
	longitude_b
	type : INT 1 - taxi, 2 - lady taxi, 3 - mejgorod, 4 - evakuator, 5 - gruz
}
response:
{
    price_list
}

```




## Запрос на открытые смены
#### ```path:     Base URL  + /start-session/```
#### Method: POST

```

fields:{
	token
	duration - если на 6 часов, то не отправляйте этот параметр, 
	если на двеннадцать, то отправляйте это: akbdciamidoandnasu27ˆ81n
}
response:
{
    price_list
}

```

## Запрос на регистрацию пользователя
#### ```path:     Base URL  + /sign-up/```
#### Method: POST

```

fields:{
	"phone",
	"name"
}
response:
{
    "state",
    "message"
    "token"
}

```

## Запрос на сохранение адреса
#### ```path:     Base URL  + /save-address/```
#### Method: POST

```

fields:{
	"token",
	"address",
	"latitude",
	"longitude"
}
response:
{
    "state",
    "message"
}

```


## Запрос на оформление заказа
#### ```path:     Base URL  + /make-order/```
#### Method: POST

```

fields:{
	"token", 
	"longitude_b",
	"latitude_b",
	"longitude_a",
	"latitude_a",
	"service_id",    
	"comment", 		 optional
	"date",		    optional
	"payment_type" 
}
response:
{
    "state",
    "message"
}

```



## При получении уведомления с типом (type) 1 Вы отправляете запрос на:
#### ```path:     Base URL  + /check-location/```
#### Method: POST

```

fields:{
	"token", 
	"longitude",
	"latitude",
	"order_id",
}
response:
{
    "state",
    "message"
}

```

## При получении уведомления с типом (type) 101 Вы открываете страницу с заказом:


```
response:
{
"order_id"
}

```

## При получении уведомления с типом (type) 201 Вы открываете вьюшку с инфо о водителем, принимаете поля driver_id, order_id и кидаете запрос на получение деталей водителя:
#### ```path:     Base URL  + /get-driver-info/```
#### Method: POST

```
fields:{
	"driver_id"
}
response:
{
"driver"
}

```

## Запрос на подтверждение водителя клиентом
#### ```path:     Base URL  + /accept-driver/```
#### Method: POST

```

fields:{
	'order_id',
	'driver_id'
}
response:
{
    "state",
    "order"
    "client",
    "driver"
}

```



## Запрос на получение деталей заказа
#### ```path:     Base URL  + /get-order-info/```
#### Method: POST

```

fields:{
	'order_id'
}
response:
{
    "state",
    "order"
    "client",
    "driver"
}

```

## Запрос на закрытие смены
#### ```path:     Base URL  + /close-session/```
#### Method: POST

```

fields:{
	'token'
}
response:
{
    "state"
}
    
```

## Запрос принятие заказа водителем
#### ```path:     Base URL  + /accept-order/```
#### Method: POST

```

fields:{
	'token'
	'order_id'
}
response:
{
    "state"
}
    
```

## Запрос на то, чтобы узнать открыта ли твоя смена
#### ```path:     Base URL  + /get-my-session/```
#### Method: POST

```

fields:{
	'token'

}
response:
{
    "state",
    "is_active" 1 OR 0; 1 - открыта 0 - закрыта
}
    
```


## Запрос на подтверждение водителем, что он прибыл на место отправки. Клиент получает уведомление с типом 401 и сообщает пользователю, что водитель приехал
#### ```path:     Base URL  + /driver-came/```
#### Method: POST

```

fields:{
	'token'
	'order_id'
}
response:
{
    "state",

}
    
```



## Запрос на подтверждение водителем, что он начал выполнение заказа. 
#### ```path:     Base URL  + /go/```
#### Method: POST

```

fields:{
	'token'
	'order_id'
}
response:
{
    "state",

}
    
```



## Запрос на закрытие заказа водителем. Клиенту приходит уведомление с типом 501, сообщает пользователю, что заказ окончен и просит оценить поездку

#### ```path:     Base URL  + /finish-order/```
#### Method: POST

```

fields:{
	'token'
	'order_id'
}
response:
{
    "state",

}
    
```



## Запрос на оценку водителя 
#### ```path:     Base URL  + /rate-driver/```
#### Method: POST

```

fields:{
	'token'
	'order_id'
	'value' - оценка от 1 до 5
}
response:
{
    "state",
}
    
```



## Запрос на получение реферальной ссылки
 
#### ```path:     Base URL + get-referal-link/```
#### Method: POST

```

response:{
    link
    state
}
 
   
```



## Запрос который отправляете после регистрации пользователя (ЛЮБОГО)
 
#### ```path:     http://185.236.130.126:443/check-referal```
#### Method: POST

```

fields:{
	'token'
}
 
   
```


## При получении пуш уведомления с кодом 601 Вы отрисовываете карту с водителем на ней, приния поля: lat, long, order_id
 



## Запрос на получение текущего состояния пользователя приложения
 
#### ```path:     Base URL + state/```
#### Method: POST

```

fields:{
	'token'
}respone{
   "state" - success
   "status" - 0-5 ||| 0 - Ничего активного нет. Остальные статусы можно посмотреть выше Статус Заказа
   "order_id" если у вас есть текущий заказ
}
 
   
```


## Запрос на получение заказов чата твоего таксопарка
 
#### ```path:     Base URL + get-own-orders/```
#### Method: POST

```

fields:{
	'token's
}respone{
   "state" - success
   "orders" 
}
 
   
```
## Запрос на получение заказов общего чата
 
#### ```path:     Base URL + get-shared-orders/```
#### Method: POST

```

fields:{
	'token's
}respone{
   "state" - success
   "orders" 
}
 
   
```

```
## Запрос на оставление жалобы на заказ
 
#### ```path:     Base URL + add-complaint/```
#### Method: POST

```

fields:{
	'token',
	'text',
	'order_id'
}respone{
   "state"
 
}
 
   
```


```
## Запрос на отказ/скрытие заказа
 
#### ```path:     Base URL + reject-order/```
#### Method: POST

```

fields:{
	'token',
	'order_id'
}respone{
   "state" -
 }
 
   
```


```
## Запрос на отмену заказа для пользователя
 
#### ```path:     Base URL + cancel-order/```
#### Method: POST

```

fields:{
	'token',
	'order_id'
}respone{
   "state" -
 }
 
   
```

```
## Запрос на получение истории заказов
 
#### ```path:     Base URL + get-all-orders/```
#### Method: POST

```

fields:{
	'token',
	'date' TIMESTAMP
}respone{
   "state" 
   "orders"
 }
 
   
```


## Запрос на получение действующих заказов

#### ```path:     Base URL  + get-active-orders/```
#### Method: POST

```
fields: 
{
    "token",
}
response:
{
    "state" 
    "orders"  - массив объектов
}

```


## Запрос на получение истории баланса

#### ```path:     Base URL  + get-balance-history/```
#### Method: POST

```
fields: 
{
    "token",
    "date"
}
response:
{
    "state" 
    "sum"  
}

```




## Запрос на получение пользователя

#### ```path:     Base URL  + get-user/```
#### Method: POST

```
fields: 
{
    "token"
}
response:
{
    "user"  
}

```




## Запрос на оставление рекомендации

#### ```path:     Base URL  + add-recomendation/```
#### Method: POST

```
fields: 
{
    "token", "text", "rating"

}
response:
{
    "state"  
}

```



## Запрос на получение списка городов и регионов

#### ```path:     Base URL  + get-regions/```
#### Method: GET

```
response:
{
    "state"
    "message"
}
```

    ```

    ## Запрос на отправку города

    #### ```path:     Base URL  + set-city/```
    #### Method: POST

    ```

    fields: 
    {
        "token", "city_id"

    }
    response:
    {
        "state"
        "message"
    }

    ```


    ## Запрос на смену роли

    #### ```path:     Base URL  + change-role/```
    #### Method: POST

    ```

    fields: 
    {
        "token", "role_id"

    }
    response:
    {
        "state"
        "message"
    }

    ```






```
Запрос на получение цен на публикацию или получение чата для водителя

path:     Base URL  + get-access-price/
Method: GET

  
response:
{
    "state"
    "types" : [
        {
            "id": 1,
            "type": "Межгород",
            "hour_price": 50,  -- цена за час просмотра чата
            "publish_price": 50 -- цена за одну публикацию в чате
        }    
    ] 
}

```




```
Запрос на покупку просмотра чата или публикацию в нем

path:     Base URL  + buy-access/
Method: POST

fields:{
    token
    type -- 1: междугородный, 2: грузотакси, 3: эвакуатор, 4: инватакси
    publish -- 1 - купить публикацию, 0 - купить просмотр чата на час
}
  
response:
{
    "state"

}

```





```
Запрос на оставление заявки на все типы кроме такси и леди такси
И для водителя и для клиента

path:     Base URL  + add-specific-order/
Method: POST

fields:{
    token
    type -- 1: междугородный, 2: грузотакси, 3: эвакуатор, 4: инватакси
    если это межгород:  
    seats_number, start_id, end_id, price, date
    если это не межгород:
    comment, start_string, end_string, price, date, 
}
  
response:
{
    "state"

}

```


```
Запрос на получение чатов 
И для водителя и для клиента

path:     Base URL  + get-specific-chats/
Method: POST

fields:{
    token
    type -- 1: междугородный, 2: грузотакси, 3: эвакуатор, 4: инватакси 
}
  
response:
{
    state
    chats

}

```


```
Запрос на междугородного чата конкретного направления 

path:     Base URL  + get-mejdugorodniy-chat/
Method: POST

fields:{
    token
    start_id
    end_id
}
  
response:
{
    state
    orders

}



```


# Logout
## path:     Base URL  + logout/

```
fields:{
    token
}
response:
{
    state
}


```


# Запрос на узнавание количества чатов водителя

## path:     Base URL  + how-many-chats/

```
fields:{
    token
}
response:
{
    state
    show_chat : true ili false
}


```


