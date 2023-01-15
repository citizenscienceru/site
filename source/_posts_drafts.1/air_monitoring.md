---
 title: Оценка качества воздуха - sensor.community
 date: 2021-05-13 21:03:53
 tags: air
 location: дома
 participation: пассивное
 description: Сборка и установка датчика оценки качества воздуха.
 description_short: Оценка качества воздуха, не требующая активых действий
 logo: logo.webp
 small_logo: small_logo.webp
 logo_path: air-quality
 url: https://sensor.community/ru/
---

# Что это

# Зачем

# Как участвовать

## Прошивка
Есть несколько способов прошивки:

### Прошивка через программу

#### Windows
* [Скачиваем программу под вашу операционную систему](https://firmware.sensor.community/airrohr/flashing-tool/);
* Подключите ESP32 модуль через USB кабель. Модуль должен мигнуть синим светодоидом;
* Запустите приложение от имени администратора;
* Приложение запросит доступ в интернет. Не забудьте дать разрешение частным сетям:
![Настройка программы для GIMPS под Windows](/img/projects/air_monitoring/1.webp)
* Выберите какую прошивку хотите установить. Для русскоговорящих рекомендую latest_ru.bin и нажмите кнопку "загрузить":
![Настройка программы для GIMPS под Windows](/img/projects/air_monitoring/2.webp)
* Во время загрузки будет мигать синий светодиод на модуле. По окончании загрузки будет так:
![Настройка программы для GIMPS под Windows](/img/projects/air_monitoring/2.webp)

Теперь можно приступать к сборке датчика.

#### Linux
* [Скачиваем программу под вашу операционную систему](https://firmware.sensor.community/airrohr/flashing-tool/)
* В Linux необходимо дать разрешение на запуск: chmod +x airRohr-firmware-flasher-0.3.4-Ubuntu_20.04_amd64_BETA
* Запустите программу

А вот тут у нас возникла проблема - не найдена библиотека libz.so ... Исправить пока так и не получилось.

### Прошивка через программу для Arduino
TODO :)
## Сборка датчика
### Детали
Для минимального датчика нам понадобятся:

* Сам датчик мелкодисперсных частиц SDS011. Выглядит [так](https://aliexpress.ru/item/33036019736.html?sku_id=10000009394777477&spm=a2g2w.productlist.list.8.663d5d27t3srj2).
* Модуль ESP32. Правильная версия "ESP8266 Node MCU v3 ch340".
* Провода. Например [такие](https://aliexpress.ru/item/32954115546.html?sku_id=12000020932487890). Выбирать "Мама-мама" - Female-female, F-F, длину я бы брал самую короткую, из соображений экологичности.
* Трубка. Я покупал строительный (гидростатический уровень)[https://market.yandex.ru/product--uroven-gidrostaticheskii-7m-art-20122/101797717451?nid=61113&show-uid=16678416741241467615216001&context=search&glfilter=21194330%3A34068023&text=%D0%B3%D0%B8%D0%B4%D1%80%D0%B0%D0%B2%D0%BB%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9%20%D1%83%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C&rs=eJwz2sOo1MTIpX1h84UdF7ZcbLiw4cKmC7sv7LjYfmHrxcYLu4CiOxUuNgMl9gEltl7Ye7FH4NaZXi4lFg4GAQYgyS8gpsGQRYr-Kg5jEwMzCwMj4wbGO0s_snYxMnEwBDBWsXKAeLMYSTELAL2ObDw%2C&sku=101797717451&cpc=Ox3bwkvvc9A0Nx1BYDjHAfu6jRWwNAJP4ZCgowb0g9n0ksyuPF5qdKZNqrM8X8pYQbZjb2iUXc1-hjVEteLVDpuzIp2vye1ZbM-NZpM3UMHiwSRuRNKNM8YEGZ41kcRvKxlnReBtfqin9m1_Uau5BJGZGdKaKjtDio5T3Y_Wj_zUgMC77n51V1kj9_4toqOm&do-waremd5=A4oZsgig-R5JMOmSzl2FjQ]. Можно взять трубку от кислородной маски, которые дают в больницах.
* Корпус (ведро от варенья и т.д.) или электромонтажную коробку (Класс IP34 достаточно). Например [такая](https://www.maxidom.ru/catalog/korobki-raspredelitelnye-bez-klemm/1001454087/). Главное чтобы вода не попадала внутрь.

Для датчика посложнее:

* Датчик температуры и влажности DHT22
* Датчик температуры и давления BMP280/BME280
* (Двусторонний скотч)[https://www.ozon.ru/product/skotch-dvuhstoronniy-akrilovyy-dlya-avto-20-mm-h-5-m-3m-6008f-kleykaya-lenta-226677672/?asb=K5M4sCKVZlhcRrEhpT5T%252BOQtTaoJzoF5JItj8ahPfo4Km6kGHIX%252Bur2EvP%252BAI9Ht&asb2=_mmIdUzdIXaqwJU4MI-mZu-6hM-39HCZ7iJpusj3axCvBETKxrvTthXz6NNOfXcTRm_zxiubP7UCLNSWSiekF52jh0DTDacVcG1PhLb5UKYas2OocWhCQqJv3ey-g4-dfrs76Iq086vjOcqiAzglZg&keywords=%D0%B4%D0%B2%D1%83%D1%85%D1%81%D1%82%D0%BE%D1%80%D0%BE%D0%BD%D0%BD%D0%B8%D0%B9+%D1%81%D0%BA%D0%BE%D1%82%D1%87+3%D0%BC&sh=BsXzFn34Zw]

Рекомендую "походить" по AliExpress и выбрать продавца с рейтингом не ниже 4 и хорошей ценой. Так же смотрите чтобы у этого продавца уже были продажи данного товара.

Так же понадобится нож, часовая отвёртка, стяжка.
### Сборка без пайки
#### Подключение сенсора частиц SDS011

* Отсоедините контакт от USB платы (сама USB плата более не понадобится):

![Отсоедините контакт от USB платы](/img/projects/air_monitoring/1.png)

* Надавите острым предметом на выступающую часть разъема и немного потяните за провод. 
Внимание! Не вырывайте провод из разъема слишком сильно! Он должен выходить легко.

![Отсоедините провод](/img/projects/air_monitoring/2.png)

*  Высвободившийся из центра провод вставьте в крайний разъем так, чтобы он надежно зафиксировался.

![Перенос провода](/img/projects/air_monitoring/2.png)

* 

В ходе написания использовались материалы:

[Habr]()

[Google документ](https://docs.google.com/document/d/1cDL0KtBHc0Q2Dq_zfSVBFS6UNHIDVBUb3gaUc5YoP2w/edit)