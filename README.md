# Mzzza
Документация  / Критерии MVP Сроки / Структура и логика проекта / RoadMap / Инфраструктура  / Технологии  / API







/////////Документация 

 
 
 
 
 
//////////////// 
------------------------
 ///////////////
 
 
 

 
 
 
 
  /////////Критерии MVP Сроки
 
 
 
 
 
 
//////////////// 
------------------------
 ///////////////
 
 
 
 
 


/////////Структура и логика проекта
 
 
 
 
 
 
//////////////// 
 Серверная часть+
 ///////////////
 
 Обработчики запросов используют асинхронные функции, которые принимают ноль или более параметров. Эти параметры могут быть извлечены из запроса (см. `FromRequest`Трейт) и возвращают тип, который можно преобразовать в `HttpResponse`(см. `Responder`Трейт):

```rust
use actix_web::{get, post, web, App, HttpResponse, HttpServer, Responder};

#[get("/")]
async fn hello() -> impl Responder {
    HttpResponse::Ok().body("Hello world!")окументация
}

#[post("/echo")]
async fn echo(req_body: String) -> impl Responder {
    HttpResponse::Ok().body(req_body)
}

async fn manual_hello() -> impl Responder {
    HttpResponse::Ok().body("Hey there!")
}
```

Обратите внимание, что к некоторым из этих обработчиков информация о маршрутизации присоединена напрямую с помощью встроенных макросов. Они позволяют указать метод и путь, на который должен ответить обработчик. Ниже вы увидите, как регистрироваться `manual_hello`(т. Е. Маршруты, не использующие макрос маршрутизации).

Затем создайте `App`экземпляр и зарегистрируйте обработчики запросов. Используется `App::service`для обработчиков, использующих макросы маршрутизации, и `App::route`для обработчиков, маршрутизируемых вручную, с объявлением пути и метода. Наконец, приложение запускается внутри, `HttpServer`которое будет обслуживать входящие запросы, используя вас `App`в качестве «фабрики приложений».








/////////Инфраструктура
 
 
 
 
 
//////////////// 
----------------------
 ///////////////

Инфраструктура
