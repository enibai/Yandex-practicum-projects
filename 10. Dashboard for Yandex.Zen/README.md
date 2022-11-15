# Дашборд для Яндекс.Дзен.

<h1>Оглавление:<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Техническое-задание:" data-toc-modified-id="Техническое-задание:-0.1"><span class="toc-item-num">0.1&nbsp;&nbsp;</span>Техническое задание:</a></span></li><li><span><a href="#Вопросы-менеджеров:" data-toc-modified-id="Вопросы-менеджеров:-0.2"><span class="toc-item-num">0.2&nbsp;&nbsp;</span>Вопросы менеджеров:</a></span></li></ul></li><li><span><a href="#Шаг-1.-Импортирую-необходимые-библиотеки,-открываю-файл-с-данными-и-изучаю-общую-информацию." data-toc-modified-id="Шаг-1.-Импортирую-необходимые-библиотеки,-открываю-файл-с-данными-и-изучаю-общую-информацию.-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Шаг 1. Импортирую необходимые библиотеки, открываю файл с данными и изучаю общую информацию.</a></span><ul class="toc-item"><li><span><a href="#Подключаюсь-к-базе-данных." data-toc-modified-id="Подключаюсь-к-базе-данных.-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Подключаюсь к базе данных.</a></span></li><li><span><a href="#Пишу-SQL-запрос,-для-получения-всех-данных,-сохраняю-данные-в-dash_visits." data-toc-modified-id="Пишу-SQL-запрос,-для-получения-всех-данных,-сохраняю-данные-в-dash_visits.-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Пишу SQL-запрос, для получения всех данных, сохраняю данные в <code>dash_visits</code>.</a></span></li><li><span><a href="#Изучаю-общую-информацию." data-toc-modified-id="Изучаю-общую-информацию.-1.3"><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Изучаю общую информацию.</a></span></li><li><span><a href="#Вывод:" data-toc-modified-id="Вывод:-1.4"><span class="toc-item-num">1.4&nbsp;&nbsp;</span>Вывод:</a></span></li></ul></li><li><span><a href="#Шаг-2.-Сохраняю-датасет-в-CSV-файл." data-toc-modified-id="Шаг-2.-Сохраняю-датасет-в-CSV-файл.-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Шаг 2. Сохраняю датасет в CSV файл.</a></span></li><li><span><a href="#Общий-вывод:" data-toc-modified-id="Общий-вывод:-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Общий вывод:</a></span></li></ul></div>

### Техническое задание:

- Бизнес-задача: анализ взаимодействия пользователей с карточками Яндекс.Дзен;
- Насколько часто предполагается пользоваться дашбордом: не реже, чем раз в неделю;
- Кто будет основным пользователем дашборда: менеджеры по анализу контента;

- Состав данных для дашборда:
    - История событий по темам карточек (два графика - абсолютные числа и процентное соотношение);
    - Разбивка событий по темам источников;
    - Таблица соответствия тем источников темам карточек;
    
- По каким параметрам данные должны группироваться:
    - Дата и время;
    - Тема карточки;
    - Тема источника;
    - Возрастная группа;
    
- Характер данных:
    - История событий по темам карточек - абсолютные величины с разбивкой по минутам;
    - Разбивка событий по темам источников - относительные величины (% событий);
    - Соответствия тем источников темам карточек - абсолютные величины;
    
- Важность: все графики имеют равную важность;
- Источники данных для дашборда: cырые данные о событиях взаимодействия пользователей с карточками (таблица `log_raw`);
- База данных, в которой будут храниться агрегированные данные: дополнительные агрегированные таблицы в БД `zen`;
- Частота обновления данных: один раз в сутки, в полночь по UTC;
- Какие графики должны отображаться и в каком порядке, какие элементы управления должны быть на дашборде (уточнено при создании макета дашборда).

### Вопросы менеджеров:
- Cколько взаимодействий пользователей с карточками происходит в системе с разбивкой по темам карточек?
- Как много карточек генерируют источники с разными темами?
- Как соотносятся темы карточек и темы источников?
***
## Общий вывод:
Работу над этим проектом я провел на удаленной машине в сервисе Yandex.Cloud. Мной был установлен PostgreSQL и развернута база данных. Затем я написал скрипт пайплайна, который позволил собирать данные за определенный временной период, и настроил его автономную работу через crontab. Для визуализации собранных данных я написал скрипт дашборда с несколькими фильтрами и также запустил его на удаленной машине. По результатам была подготовлена презентация с полученными графиками. 

Всего, за изучаемый период, в системе с разбивкой по темам карточек происходит **310207** взаимодействий пользователей с карточками.

Больше всего посещений у следующих тем источников:
- `Семейные отношения` – **33309**;
- `Россия` - **29831**;
- `Полезные советы` - **27412**;
- `Путешествия` - **24124**;
- `Знаменитости` - **23945**;
- `Кино` - **20084**;
- `Дети` – **15243**.

Составить топ тем карточек на каждую конкретную минуту с разбивками по темам и возрастным группам, можно используя необходимые фильтры в самом дашборде:

[Дашборд](https://public.tableau.com/app/profile/evgeny.babaevsky/viz/Dashbord_for_Yandeks_Dzen/Dashboard1?publish=yes), [Презентация](https://disk.yandex.ru/i/waZRx9l2AeX0zw).