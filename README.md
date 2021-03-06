jQueryMapi 
==============

###[Демо-страница](http://milaxcom.github.io/jQueryMapi/demo/) | [Скачать](https://github.com/milaxcom/jQueryMapi/archive/gh-pages.zip)

Модуль jQuery Mapi предназначен для инициализации карт на основе JSON-объекта. Поддерживаемые системы: Яндекс.Карты (RUS), Google Maps (MULTI), 2GIS (RUS).

######Модуль тестировался только в Google Chrome с jQuery 1.11.1 ввиду недостатка времени.

####Преимущества
- Предустановленные, наиболее популярные настройки карт.
- Генерация идентичных карт с использованием разных провайдеров, что дает возможность быстро менять провайдеров, если один из них не показывает нужные объекты или не удовлетворяет заказчика.
- Данные подгружаются из внешнего файла, что дает возможность легко собрать модуль для CMS.

###Подключение

```html
<script type="text/javascript" src="js/jquery-1.11.1.min.js"></script>
<script type="text/javascript" src="/jquery.mapi.js"></script>
```

Подключение API провайдеров (требуется подключение только необходимых API).
```html
<script type="text/javascript" src="http://api-maps.yandex.ru/2.1/?lang=ru_RU"></script>
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?v=3&language=ru"></script>
<script type="text/javascript" src="http://maps.api.2gis.ru/2.0/loader.js?pkg=basic" data-id="dgLoader"></script>
```


###Использование

Для автоматической инициализации требуется добавить контейнеру ```id```, который будет соответствовать ```id``` в JSON-объекте и класс ```mapi```.

Демо-пример [JSON-объекта](http://milaxcom.github.io/jQueryMapi/demo/storage.json).

```html
<div id="map1" style="width:300px;height:200px;" class="mapi"></div> 
```

Не рекомендуется инициализировать карту при загрузки страницы, если карта по-умолчанию скрыта от пользователя, например ч/з ```display:none;```. В таком случае параметры ширины и высоты не всегда и у всех провайдеров определяются верно и модуль выглядит не корректно. Есть «фиксы», которые решают проблему с каждым конкретным провайдером, но их требуется настраивать вручную.

#####Второй метод инициализации ч/з функцию, с указанием ID.

```html
<!-- HTML -->
<div id="map1" style="width:300px;height:200px;"></div>
```

```js
/* JavaScript */
mapi( "map1" );
```

В данном методе модуль будет искать ```id``` равный ```map1``` в JSON-объекте с данными. Если ```id``` не будет найден — инициализация не произойдет.

Данный метод имеет «надстройку» на jQuery, вызов можно совершить след. образом:

```js
/* JavaScript */
var $map = $("#map1");
$map.mapi();
```