# Проект "Оценка риска ДТП по маршруту движения каршеринга"

## Описание проекта

Заказ поступил от каршеринговой компании. Необходимо создать систему для оценки риска возникновения ДТП по маршруту движения. Если уровень риска высокий, то будет дано уведомление водителю и рекомендации по изменению маршруту движения.

## Таблицы:
<h3>case_ids (индексы происшествий)</h3>
<h3>parties (описание участников происшествия)</h3>

- case_id (уникальный номер зарегистрированного происшествия в таблице происшествий);
- party_number (номер участника происшествия) - от 1 до N: по числу участников происшествия;
- party_type (тип участника происшествия): 
    - 1 - Car (Авто);
    - 2 - Road bumper (Дорожные знаки);
    - 3 - Building (Строения);
    - 4 - Road signs (Отбойник);
    - 5 - Other (Другое);
    - 6 - Operator (Оператор);
    - _ - Not Stated (Не указано).
<a name='at_fault'></a>
- at_fault (виновность участника) - 0 или 1;
- insurance_premium (сумма страховки);
<a name='party_drug_physical'></a>
- party_drug_physical (состояние чуастника: физическое или с учетом принятых лекарств):
    - E - Under Drug Influence (Под воздействием лекарств);
    - F - Impairment Physical (Ухудшение состояния);
    - G - Impairment Unknown (Не известно);
    - H - Not Applicable (Не оценивался);
    - I - Sleepy / Fatigued (Сонный / усталый);
    - _ - Not Stated (Не указано).
<a name='party_sobriety'></a>
- party_sobriety (трезвость участника):
    - A - Had Not Been Drinking (Не пил);
    - B - Had Been Drinking, Under Influence (Был пьян, под влиянием);
    - C - Had Been Drinking, Not Under Influence (Был пьян, не под влиянием);
    - D - Had Been Drinking, Impairment Unknown (Был пьян, ухудшение неизвестно);
    - G - Impairment Unknown (Неизвестно ухудшение);
    - H - Not Applicable (Не оценивался);
    - _ - Not Stated (Не указано).
<a name='cellphone_in_use'></a>
- cellphone_in_use (наличие телефона в автомобиле) - 0 или 

<h3>vehicles (описание автомобиля)</h3>

- id (индекс текущей таблицы);
- case_id (идентификационный номер в базе данных);
<a name='vehicle_type'></a>
- vehicle_type (тип кузова):
    - MINIVAN;
    - COUPE;
    - SEDAN;
    - HATCHBACK;
    - OTHER.
<a name='vehicle_transmission'></a>
- vehicle_transmission (тип КПП):
    - auto (Автоматическая).
    - manual (Ручная).
    - _ - Not Stated (Не указано)
<a name='vehicle_age'></a>
- vehicle_age (возраст автомобиля).

<h3>collisions (информация о происшествия)</h3>

- case_id (идентификационный номер в базе данных);
- collision_date (дата происшествия);
- collision_time (время происшествия);
- intersection (является ли место происшествия перекрестком):
    - Y — Intersection (перекрёсток);
    - N — Not Intersection (не перекрёсток);
    - _ Not stated (Не указано).
<a name='weather_1'></a>
- weather_1 (погода):
    - A — Clear (Ясно);
    - B — Cloudy (Облачно);
    - C — Raining (Дождь);
    - D — Snowing (Снегопад);
    - E — Fog (Туман);
    - F — Other (Другое);
    - G — Wind (Ветер);
<a name='collision_damage'></a>
- collision_damage (серьезность происшествия):
    - Fatal TC (Не подлежит восстановлению);
    - Severe Damage (Серьезное повреждение);
    - Middle Damage (Машина в целом на ходу);
    - Small Damage (Отдельный элемент под замену / покраску);
    - Scratch (Царапина).
<a name='primary_collision_factor'></a>
- primary_collision_factor (основной фактор аварии):
    - A - Code Violation (Нарушение правил ПДД);
    - B - Other Improper Driving (Другое неправильное вождение);
    - C - Other Than Driver (Кроме водителя);
    - D - Unknown (Неизвестно);
    - E - Fell Asleep (Заснул);
    - _ - Not Stated (Не указано).
<a name='road_surface'></a>
- road_surface (состояние дороги):
    - A — Dry (Сухая);
    - B — Wet (Мокрая);
    - C — Snowy or Icy (Заснеженная или обледенелая);
    - D — Slippery (Muddy, Oily, etc.) (Скользкая, грязная, маслянистая и т. д.);
    - _ Not Stated (Не указано).
<a name='lighting'></a>
- lightning (освещение):
    - A — Daylight (Дневной свет);
    - B — Dusk-Dawn (Сумерки-Рассвет);
    - C — Dark-Street Lights (Темно-Уличные фонари);
    - D — Dark-No Street Lights (Темно-Нет уличных фонарей);
    - E — Dark-Street Lights Not Functioning (Темно-Уличные фонари не работают);
    - _ Not Stated (Не указано).
<a name='county_city_location'></a>
- county_city_location (номер географических районов, где произошло ДТП);
- county_location (названия географических районов, где произошло ДТП);
<a name='direction'></a>
- direction (направление движения):
    - N — North (Север)
    - E — East (Восток)
    - S — South (Юг)
    - W — West (Запад)
    - _ — Not State (Не указано)
    - на перекрёстке
- distance (расстояние до главной дороги в метрах);
<a name='location_type'></a>
- location_type (тип дороги):
    - H — Highway (Шоссе);
    - I — Intersection (Перекрёсток);
    - R — Ramp (or Collector) (Рампа);
    - _ — Not State Highway (Не указано).
- party_count (количество участников);
<a name='pcf_violation_category'></a>
- pcf_violation_category (категория нарушения):
   - 01 - Driving Under the Influence of Alcohol or Drug - Вождение или езда в состоянии алкогольного или наркотического опьянения;
   - 02 - Impeding Traffic - Препятствие движению транспорта;
   - 03 - Unsafe Speed - Превышение скорости;
   - 04 - Following Too Closely - Опасное сближение;
   - 05 - Wrong Side of Road - Неправильная сторона дороги;
   - 06 — Improper Passing - Неправильное движение;
   - 07 — Unsafe Lane Change - Небезопасная смена полосы движения;
   - 08 — Improper Turning - Неправильный поворот;
   - 09 — Automobile Right of Way - Автомобильное право проезда;
   - 10 — Pedestrian Right of Way - Пешеходное право проезда;
   - 11 — Pedestrian Violation - Нарушение пешеходами;
   - 12 — Traffic Signals and Signs - Дорожные сигналы и знаки;
   - 13 — Hazardous Parking - Неправильная парковка;
   - 14 — Lights - Освещение;
   - 15 — Brakes - Тормоза;
   - 16 — Other Equipment - Другое оборудование;
   - 17 — Other Hazardous Violation - Другие нарушения;
   - 18 — Other Than Driver (or Pedestrian) - Кроме водителя или пешехода;
   - 19 — Speeding - Скорость;
   - 20 — Pedestrian dui - Нарушение пешехода;
   - 21 — Unsafe Starting or Backing - Опасный старт;
   - 22 — Other Improper Driving - Другое неправильное вождение;
   - 23 — Pedestrian or “Other” Under the Influence of Alcohol or Drug - Пешеход или «Другой» в состоянии алкогольного или наркотического опьянения;
   - 24 — Fell Asleep - Заснул;
   - 00 — Unknown - Неизвестно;
   - _ - Not Stated - Не указано.
- type_of_collision (тип аварии):
   - A — Head-On (Лоб в лоб);
   - B — Sideswipe (Сторона);
   - C — Rear End (Столкновение задней частью);
   - D — Broadside (Боковой удар);
   - E — Hit Object (Удар объекта);
   - F — Overturned (Опрокинутый);
   - G — Vehicle (транспортное средство/ Пешеход);
   - H — Other (Другое);
   - _ - Not Stated (Не указано).
- motor_vehicle_involved_with (дополнительные участники ДТП):
    - Other motor vehicle (Другой автомобиль);
    - Fixed object (Неподвижный объект);
    - Parked motor vehicle (Припаркованный автомобиль);
    - Pedestrian (Пешеход);
    - Bicycle (Велосипедист);
    - Non-collision (Не столкновение);
    - Other object (Другой объект);
    - Motor vehicle on other roadway (Автомобиль на другой проезжей);
    - Animal (Животное);
    - Train (Поезд).
<a name='road_condition_1'></a>
- road_condition_1 (дорожное состояние):
    - A — Holes, Deep Ruts (Ямы, глубокая колея);
    - B — Loose Material on Roadway (Сыпучий материал на проезжей части);
    - C — Obstruction on Roadway (Препятствие на проезжей части);
    -  D — Construction or Repair Zone (Зона строительства или ремонта);
    - E — Reduced Roadway Width (Уменьшенная ширина проезжей части);
    - F — Flooded (Затоплено);
    - G — Other (Другое);
    - H — No Unusual Condition (Нет ничего необычного);
    - _ — Not Stated (Не указано).
<a name='control_device'></a>
- control_device (устройство управления):
    - A — Functioning (Функционирует);
    - B — Not Functioning (Не функционирует);
    - C — Obscured (Затемнённый);
    - D — None (Нет);
    - _ Not Stated (Не указано).

## План работы:
1. [Загрузка таблицы SQL](#download)
2. [Первичное исследование таблиц](#primary_analysis)
3. [Cтатистический анализ факторов ДТП](#statistics_analysis)
    - [Количество аварий по месяцам](#collisions_month)
    - [Задачи для коллег](#tasks_for_colleagues)
        - [Самые частые основные факторы ДТП](#frequent_reasons)
        - [Анализ серьезности повреждений транспортного средства по состоянию участника](#road_damage_relation)
        - [Анализ зависимости степени трезвости участника и основного фактора аварии](#sobriety_reason_relation)
        - [Зависимость между категорией нарушения и состоянием участника](#violation_state_relation)
        - [Анализ корреляции степени трезвости участника и его виновности](#sobriety_fault_relation)
        - [Анализ влияния дорожного состояния на серьезность повреждений транспортного средства](#road_state_relation)
4. [Создание модели для оценки водительского риска](#model_creation)
    - [Отбор параметров](#parameters_selection)
    - [Исследовательский анализ отобранных параметров](#selected_eda)
    - [Подготовка данных](#data_preparation)
    - [Выбор метрики для оценки качества моделей](#metric_selection)
    - [ML-модели](#ml_models)
        - [DecisionTreeClassifier](#tree)
        - [RandomForestClassifier](#RandomForestClassifier)
        - [LGBMClassifier](#lgbm)
        - [Нейронная сеть](#neural_net)
    - [Выводы по моделям](#conclusions_on_models)
5. [Анализ важности факторов ДТП](#factors_importance)
    - [Матрица ошибок](#confusion_matrix)
    - [Важность факторов](#feature_importance)
6. [Выводы](#conclusions)

## Решенные задачи

1. Осуществлена загрузка библиотек и файлов
