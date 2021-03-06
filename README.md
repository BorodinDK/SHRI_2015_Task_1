Табло аэропорта
========

Ссылка на рабочий пример – [borodindk.github.io/SHRI_2015_Task_1](http://borodindk.github.io/SHRI_2015_Task_1)

Данные представленные в этой таблице я спарсил с официального сайта [аэропорта Шереметьево](http://svo.aero/timetable/today/).

###Информация по вёрстке
* Выделение вертикальных столбцов реализованно псевдоклассом ```:after```;
* Шапка таблицы вместе с чекбоксами зафиксирована вверху страницы;
* Открытие окон реализовано с помощью ссылок с решётками и псевдокласса ```:target```, при этом информация для окон дублируется в коде html;
* Чекбоксы позволяющие сортировать таблицу на прилёты и вылеты, так же осуществленны на CSS, с использованием псевдокласса ```:checked```
```CSS
#landing:checked ~ .table > article,
#takeoff:checked ~ .table > div{
	display: table;
	...
}
```
* Однако из за того что рейсы получили возможность сортироваться, возникает сложность с выделением нечётных строк таблицы, поэтому вместо простого селектора
 ```:nth-child(2n-1)``` приходится использовать более сложный, с учётом различных положений чекбоксов
```CSS
#landing:checked+#takeoff:not(:checked) ~ .table > article:nth-of-type(odd),
#landing:not(:checked)+#takeoff:checked ~ .table > div:nth-of-type(odd),
#landing:checked+#takeoff:checked ~ .table > .line:nth-child(2n-1){
	...
}
```

![скриншот табло аэропорта](http://denisborodin.ru/projects/yandex_shri/github_img/shri_task_1.jpg?4)

Работа выполнена без использования JavaScript.