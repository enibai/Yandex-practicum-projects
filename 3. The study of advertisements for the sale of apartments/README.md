# Исследование объявлений о продаже квартир.

<h1>Оглавление:<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Описание-проекта:" data-toc-modified-id="Описание-проекта:-0.1"><span class="toc-item-num">0.1&nbsp;&nbsp;</span>Описание проекта:</a></span></li><li><span><a href="#Описание-данных:" data-toc-modified-id="Описание-данных:-0.2"><span class="toc-item-num">0.2&nbsp;&nbsp;</span>Описание данных:</a></span></li></ul></li><li><span><a href="#Шаг-1.-Импортирую-необходимые-библиотеки,-открываю-файл-с-данными-и-изучаю-общую-информацию." data-toc-modified-id="Шаг-1.-Импортирую-необходимые-библиотеки,-открываю-файл-с-данными-и-изучаю-общую-информацию.-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Шаг 1. Импортирую необходимые библиотеки, открываю файл с данными и изучаю общую информацию.</a></span><ul class="toc-item"><li><span><a href="#Вывод:" data-toc-modified-id="Вывод:-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Вывод:</a></span></li></ul></li><li><span><a href="#Шаг-2.-Предобработка-данных." data-toc-modified-id="Шаг-2.-Предобработка-данных.-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Шаг 2. Предобработка данных.</a></span><ul class="toc-item"><li><span><a href="#Исправляю-стиль-в-заголовках-столбцов." data-toc-modified-id="Исправляю-стиль-в-заголовках-столбцов.-2.1"><span class="toc-item-num">2.1&nbsp;&nbsp;</span>Исправляю стиль в заголовках столбцов.</a></span></li><li><span><a href="#Столбец-total_images-(число-фотографий-квартиры-в-объявлении)." data-toc-modified-id="Столбец-total_images-(число-фотографий-квартиры-в-объявлении).-2.2"><span class="toc-item-num">2.2&nbsp;&nbsp;</span>Столбец <code>total_images</code> (число фотографий квартиры в объявлении).</a></span></li><li><span><a href="#Столбец-last_price-(цена-на-момент-снятия-с-публикации)." data-toc-modified-id="Столбец-last_price-(цена-на-момент-снятия-с-публикации).-2.3"><span class="toc-item-num">2.3&nbsp;&nbsp;</span>Столбец <code>last_price</code> (цена на момент снятия с публикации).</a></span></li><li><span><a href="#Столбец-total_area-(площадь-квартиры-в-м²)." data-toc-modified-id="Столбец-total_area-(площадь-квартиры-в-м²).-2.4"><span class="toc-item-num">2.4&nbsp;&nbsp;</span>Столбец <code>total_area</code> (площадь квартиры в м²).</a></span></li><li><span><a href="#Столбец-first_day_exposition-(дата-публикации)." data-toc-modified-id="Столбец-first_day_exposition-(дата-публикации).-2.5"><span class="toc-item-num">2.5&nbsp;&nbsp;</span>Столбец <code>first_day_exposition</code> (дата публикации).</a></span></li><li><span><a href="#Столбец-rooms-(число-комнат)." data-toc-modified-id="Столбец-rooms-(число-комнат).-2.6"><span class="toc-item-num">2.6&nbsp;&nbsp;</span>Столбец <code>rooms</code> (число комнат).</a></span></li><li><span><a href="#Столбец-studio-(квартира-студия)." data-toc-modified-id="Столбец-studio-(квартира-студия).-2.7"><span class="toc-item-num">2.7&nbsp;&nbsp;</span>Столбец <code>studio</code> (квартира-студия).</a></span></li><li><span><a href="#Столбец-kitchen_area-(площадь-кухни-в-м²)." data-toc-modified-id="Столбец-kitchen_area-(площадь-кухни-в-м²).-2.8"><span class="toc-item-num">2.8&nbsp;&nbsp;</span>Столбец <code>kitchen_area</code> (площадь кухни в м²).</a></span></li><li><span><a href="#Столбец-floors_total-(всего-этажей-в-доме)." data-toc-modified-id="Столбец-floors_total-(всего-этажей-в-доме).-2.9"><span class="toc-item-num">2.9&nbsp;&nbsp;</span>Столбец <code>floors_total</code> (всего этажей в доме).</a></span></li><li><span><a href="#Столбец-ceiling_height-(высота-потолков-в-м)." data-toc-modified-id="Столбец-ceiling_height-(высота-потолков-в-м).-2.10"><span class="toc-item-num">2.10&nbsp;&nbsp;</span>Столбец <code>ceiling_height</code> (высота потолков в м).</a></span></li><li><span><a href="#Столбец-living_area-(жилая-площадь-в-м²)." data-toc-modified-id="Столбец-living_area-(жилая-площадь-в-м²).-2.11"><span class="toc-item-num">2.11&nbsp;&nbsp;</span>Столбец <code>living_area</code> (жилая площадь в м²).</a></span></li><li><span><a href="#Столбец-floor-(этаж)." data-toc-modified-id="Столбец-floor-(этаж).-2.12"><span class="toc-item-num">2.12&nbsp;&nbsp;</span>Столбец <code>floor</code> (этаж).</a></span></li><li><span><a href="#Столбец-is_apartment-(апартаменты)." data-toc-modified-id="Столбец-is_apartment-(апартаменты).-2.13"><span class="toc-item-num">2.13&nbsp;&nbsp;</span>Столбец <code>is_apartment</code> (апартаменты).</a></span></li><li><span><a href="#Столбец-open_plan-(свободная-планировка)." data-toc-modified-id="Столбец-open_plan-(свободная-планировка).-2.14"><span class="toc-item-num">2.14&nbsp;&nbsp;</span>Столбец <code>open_plan</code> (свободная планировка).</a></span></li><li><span><a href="#Столбец-balcony-(число-балконов)." data-toc-modified-id="Столбец-balcony-(число-балконов).-2.15"><span class="toc-item-num">2.15&nbsp;&nbsp;</span>Столбец <code>balcony</code> (число балконов).</a></span></li><li><span><a href="#Столбец-locality_name-(название-населённого-пункта)." data-toc-modified-id="Столбец-locality_name-(название-населённого-пункта).-2.16"><span class="toc-item-num">2.16&nbsp;&nbsp;</span>Столбец <code>locality_name</code> (название населённого пункта).</a></span></li><li><span><a href="#Столбец-airports_nearest-(расстояние-до-ближайшего-аэропорта-в-м)." data-toc-modified-id="Столбец-airports_nearest-(расстояние-до-ближайшего-аэропорта-в-м).-2.17"><span class="toc-item-num">2.17&nbsp;&nbsp;</span>Столбец <code>airports_nearest</code> (расстояние до ближайшего аэропорта в м).</a></span></li><li><span><a href="#Столбец-city_centers_nearest-(расстояние-до-центра-города-в-м)." data-toc-modified-id="Столбец-city_centers_nearest-(расстояние-до-центра-города-в-м).-2.18"><span class="toc-item-num">2.18&nbsp;&nbsp;</span>Столбец <code>city_centers_nearest</code> (расстояние до центра города в м).</a></span></li><li><span><a href="#Столбец-parks_around_3000-(число-парков-в-радиусе-3-км)." data-toc-modified-id="Столбец-parks_around_3000-(число-парков-в-радиусе-3-км).-2.19"><span class="toc-item-num">2.19&nbsp;&nbsp;</span>Столбец <code>parks_around_3000</code> (число парков в радиусе 3 км).</a></span></li><li><span><a href="#Столбец-parks_nearest-(расстояние-до-ближайшего-парка-в-м)." data-toc-modified-id="Столбец-parks_nearest-(расстояние-до-ближайшего-парка-в-м).-2.20"><span class="toc-item-num">2.20&nbsp;&nbsp;</span>Столбец <code>parks_nearest</code> (расстояние до ближайшего парка в м).</a></span></li><li><span><a href="#Столбец-ponds_around_3000-(число-водоёмов-в-радиусе-3-км)." data-toc-modified-id="Столбец-ponds_around_3000-(число-водоёмов-в-радиусе-3-км).-2.21"><span class="toc-item-num">2.21&nbsp;&nbsp;</span>Столбец <code>ponds_around_3000</code> (число водоёмов в радиусе 3 км).</a></span></li><li><span><a href="#Столбец-ponds_nearest-(расстояние-до-ближайшего-водоёма-в-м)." data-toc-modified-id="Столбец-ponds_nearest-(расстояние-до-ближайшего-водоёма-в-м).-2.22"><span class="toc-item-num">2.22&nbsp;&nbsp;</span>Столбец <code>ponds_nearest</code> (расстояние до ближайшего водоёма в м).</a></span></li><li><span><a href="#Столбец-days_exposition-(сколько-дней-было-размещено-объявление,-от-публикации-до-снятия)." data-toc-modified-id="Столбец-days_exposition-(сколько-дней-было-размещено-объявление,-от-публикации-до-снятия).-2.23"><span class="toc-item-num">2.23&nbsp;&nbsp;</span>Столбец <code>days_exposition</code> (сколько дней было размещено объявление, от публикации до снятия).</a></span></li></ul></li><li><span><a href="#Шаг-3.-Расчёты-и-добавление-результатов-в-таблицу." data-toc-modified-id="Шаг-3.-Расчёты-и-добавление-результатов-в-таблицу.-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Шаг 3. Расчёты и добавление результатов в таблицу.</a></span><ul class="toc-item"><li><span><a href="#Рассчитываю-и-добавляю-в-датасет-столбец-с-ценой-за-квадратный-метр." data-toc-modified-id="Рассчитываю-и-добавляю-в-датасет-столбец-с-ценой-за-квадратный-метр.-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>Рассчитываю и добавляю в датасет столбец с ценой за квадратный метр.</a></span></li><li><span><a href="#Добавляю-в-датасет-столбец-floor_category,-который-будет-содержать-три-категории-этажности-квартиры-(первый,-последний-и-другой)." data-toc-modified-id="Добавляю-в-датасет-столбец-floor_category,-который-будет-содержать-три-категории-этажности-квартиры-(первый,-последний-и-другой).-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>Добавляю в датасет столбец <code>floor_category</code>, который будет содержать три категории этажности квартиры (первый, последний и другой).</a></span></li><li><span><a href="#Добавляю-в-датасет-столбцы-living_and_total_area_ratio-(соотношение-жилой-и-общей-площади)-и-kitchen_and_total_area_ratio-(отношение-площади-кухни-к-общей-площади)." data-toc-modified-id="Добавляю-в-датасет-столбцы-living_and_total_area_ratio-(соотношение-жилой-и-общей-площади)-и-kitchen_and_total_area_ratio-(отношение-площади-кухни-к-общей-площади).-3.3"><span class="toc-item-num">3.3&nbsp;&nbsp;</span>Добавляю в датасет столбцы <code>living_and_total_area_ratio</code> (соотношение жилой и общей площади) и <code>kitchen_and_total_area_ratio</code> (отношение площади кухни к общей площади).</a></span></li></ul></li><li><span><a href="#Шаг-4.-Исследовательский-анализ-данных." data-toc-modified-id="Шаг-4.-Исследовательский-анализ-данных.-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Шаг 4. Исследовательский анализ данных.</a></span><ul class="toc-item"><li><span><a href="#Строю-гистограмму-по-значениям-столбца-last_price." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца-last_price.-4.1"><span class="toc-item-num">4.1&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца <code>last_price</code>.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца--total_area." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца--total_area.-4.2"><span class="toc-item-num">4.2&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца  <code>total_area</code>.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца--rooms." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца--rooms.-4.3"><span class="toc-item-num">4.3&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца  <code>rooms</code>.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца--ceiling_height." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца--ceiling_height.-4.4"><span class="toc-item-num">4.4&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца  <code>ceiling_height</code>.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца--days_exposition." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца--days_exposition.-4.5"><span class="toc-item-num">4.5&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца  <code>days_exposition</code>.</a></span></li><li><span><a href="#Смотрю,-зависит-ли-цена-от-площади,-числа-комнат,-удалённости-от-центра-и-этажа." data-toc-modified-id="Смотрю,-зависит-ли-цена-от-площади,-числа-комнат,-удалённости-от-центра-и-этажа.-4.6"><span class="toc-item-num">4.6&nbsp;&nbsp;</span>Смотрю, зависит ли цена от площади, числа комнат, удалённости от центра и этажа.</a></span></li><li><span><a href="#Нахожу-ТОП-10-населённых-пунктов-по-числу-объявлений." data-toc-modified-id="Нахожу-ТОП-10-населённых-пунктов-по-числу-объявлений.-4.7"><span class="toc-item-num">4.7&nbsp;&nbsp;</span>Нахожу ТОП-10 населённых пунктов по числу объявлений.</a></span></li><li><span><a href="#Выясняю,-какая-область-входит-в-центр-Санкт-Петербурга." data-toc-modified-id="Выясняю,-какая-область-входит-в-центр-Санкт-Петербурга.-4.8"><span class="toc-item-num">4.8&nbsp;&nbsp;</span>Выясняю, какая область входит в центр Санкт-Петербурга.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца-last_price-для-центральной-зоны." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца-last_price-для-центральной-зоны.-4.9"><span class="toc-item-num">4.9&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца <code>last_price</code> для центральной зоны.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца-total_area-для-центральной-зоны." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца-total_area-для-центральной-зоны.-4.10"><span class="toc-item-num">4.10&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца <code>total_area</code> для центральной зоны.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца-rooms-для-центральной-зоны." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца-rooms-для-центральной-зоны.-4.11"><span class="toc-item-num">4.11&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца <code>rooms</code> для центральной зоны.</a></span></li><li><span><a href="#Строю-гистограмму-по-значениям-столбца-ceiling_height-для-центральной-зоны." data-toc-modified-id="Строю-гистограмму-по-значениям-столбца-ceiling_height-для-центральной-зоны.-4.12"><span class="toc-item-num">4.12&nbsp;&nbsp;</span>Строю гистограмму по значениям столбца <code>ceiling_height</code> для центральной зоны.</a></span></li><li><span><a href="#Смотрю,-зависит-ли-цена-квартир-в-центре-от-площади,-числа-комнат,-удалённости-от-центра-и-этажа." data-toc-modified-id="Смотрю,-зависит-ли-цена-квартир-в-центре-от-площади,-числа-комнат,-удалённости-от-центра-и-этажа.-4.13"><span class="toc-item-num">4.13&nbsp;&nbsp;</span>Смотрю, зависит ли цена квартир в центре от площади, числа комнат, удалённости от центра и этажа.</a></span></li><li><span><a href="#Сравнительный-вывод:" data-toc-modified-id="Сравнительный-вывод:-4.14"><span class="toc-item-num">4.14&nbsp;&nbsp;</span>Сравнительный вывод:</a></span></li></ul></li><li><span><a href="#Общий-вывод:" data-toc-modified-id="Общий-вывод:-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Общий вывод:</a></span></li></ul></div>

### Описание проекта:
В моем распоряжении данные сервиса по продаже недвижимости - архив объявлений о продаже квартир в Санкт-Петербурге и соседних населённых пунктах за несколько лет. Нужно научиться определять рыночную стоимость объектов недвижимости. Задача - установить параметры. Это позволит построить автоматизированную систему: она отследит аномалии и мошенническую деятельность. 

По каждой квартире на продажу доступны два вида данных. Первые вписаны пользователем, вторые получены автоматически на основе картографических данных. Например, расстояние до центра, аэропорта, ближайшего парка и водоёма. 

### Описание данных:
Датасет `real_estate_data` содержит:
- **`airports_nearest`** - расстояние до ближайшего аэропорта в метрах (м);
- **`balcony`** - число балконов;
- **`ceiling_height`** - высота потолков (м);
- **`city_centers_nearest`** - расстояние до центра города (м);
- **`days_exposition`** - сколько дней было размещено объявление (от публикации до снятия);
- **`first_day_exposition`** - дата публикации;
- **`floor`** - этаж;
- **`floors_total`** - всего этажей в доме;
- **`is_apartment`** - апартаменты (булев тип);
- **`kitchen_area`** - площадь кухни в квадратных метрах (м²);
- **`last_price`** - цена на момент снятия с публикации;
- **`living_area`** - жилая площадь в квадратных метрах (м²);
- **`locality_name`** - название населённого пункта;
- **`open_plan`** - свободная планировка (булев тип);
- **`parks_around_3000`** - число парков в радиусе 3 км;
- **`parks_nearest`** - расстояние до ближайшего парка (м);
- **`ponds_around_3000`** - число водоёмов в радиусе 3 км;
- **`ponds_nearest`** - расстояние до ближайшего водоёма (м);
- **`rooms`** - число комнат;
- **`studio`** - квартира-студия (булев тип);
- **`total_area`** - площадь квартиры в квадратных метрах (м²);
- **`total_images`** - число фотографий квартиры в объявлении.

Пояснение: апартаменты - это нежилые помещения, которые не относятся к жилому фонду, но имеют необходимые условия для проживания.
***
## Общий вывод:
Полученные от сервиса по продаже недвижимости данные, имели большое количество пропусков и аномальных значений, часть которых пропуски допущенные людьми, часть результат технических ошибок. Используя логику и функции я заполнил пропуски там где это было уместно и измененил некорректные типы данных. Аномальные значения, как правило это максимальные и минимальные значения, я оставил в исходном виде, так как в данном исследовании меня интересуют центральные данные. Добавил в датасет столбцы с результатами необходимых рассчетов, произвел декомпозицию исходного датасета и категоризировал этажность квартир. Данные стали пригодными для анализа, чем я и занялся. 

Я построил гистограммы по основным столбцам датасета и выяснил, что чаще всего предпочтение отдается квартирам за **3-4 млн.р.**, площадью **30-45 м²**, с **1** или **2** комнатами и потолками **2.5 м**. На ценообразование больше всего влияют площадь квартиры и количество комнат.

После чего я определил топ-10 населенных пунктов по количеству объявлений и выяснил что самое большое количество объявлений и самая высокая цена за м² в **Санкт-Петербурге**, а самые низкие (из топ 10) значения в **Выборге**.

Затем я определил центральную часть Санкт-Петербурга, это радиус до **8 км**, отсортировал датасет по этой зоне и построил гистограммы по основным столбцам. Выяснилось, что в центральной части СПб люди во всех смыслах живут с большим размахом, чем в остальной части Лен. обл. и отдают предпочтение квартирам за **6 млн.р.**, площадью **40-70 м²**, с **2** или **3** комнатами и потолками **3 м**. Влияние на ценообразование не изменилось, разве что этаж квартиры стал влиять чуть больше.