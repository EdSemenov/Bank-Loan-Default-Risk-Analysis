## Исследование надёжности заёмщиков банка / Bank Loan Default Risk Analysis  
Данный проект - один из 16 проектов, выполненных в ходе обучения в Яндекс.Практикуме, профессии "Специалист по Data Science". 

### Цель проекта 
Исходная задача исследования: установить, влияет ли семейное положение и количество детей клиента на факт погашения кредита в срок. 
Задача была расширена - исследовано влияние всех доступных значимых признаков на факт погашения кредита в срок и важность признаков.

Входные данные от банка — статистика о платёжеспособности 21525 клиентов. Датасет не приведен, так как он не предназначен для публичного ознакомления. 

### Использованные инструменты:
pandas, numpy, matplotlib, seaborn, Mystem(pymystem3), Counter(collections), OrdinalEncoder (sklearn.preprocessing),  RandomForestClassifier  (sklearn.ensemble)

### Исследованные признаки: 
- children — количество детей в семье
- days_employed — общий трудовой стаж в днях
- dob_years — возраст клиента в годах
- education — уровень образования клиента
- education_id — идентификатор уровня образования
- family_status — семейное положение
- family_status_id — идентификатор семейного положения
- gender — пол клиента
- income_type — тип занятости
- debt — имел ли задолженность по возврату кредитов
- total_income — ежемесячный доход
- purpose — цель получения кредита

### Предобработка данных: 
- устранены 54 строки - полных дубликата 
- исправлены найденные аномалии/ошибки в количестве детей (123 строки)
- устранены смысловые дубликаты уровня образования клиента 
- устранены пропущенные значения признака "Пол"(1 строка)
- устранены ошибочные значения/аномалии признака "Возраст клиента" (101 строка)
- устранены смысловые дубликаты цели кредита: 38 вариантов описания сведены к 4 базовым
- обнаружены и маркированы пропущенные значения признака "Ежемесячный доход клиента" в объеме 10% от выборки
- обнаружены пропущенные и аномальные значения признака "Количество лет трудового стажа" и отсутствие приемлемых значений признака. После изучения принято решение отказатьяс от использования данного признака

### Исследовательский анализ данных:  
Наиболее и наименее опасные классы признаков с точки зрения наличия невозвращенного кредита изучались при помощи сравнительной визуализации распределения классов.
Мультиколлинеарность признаков была исследована при помощи тепловой карты. 
Важность признаков с точки зрения их влияния на целевой признак (наличие невозвращенного кредита) была изучена при помощи feature_importances_ модели классификации случайного леса

### Полученные выводы:

Наиболее "опасны" с точки зрения невозврата кредита (по сравнению со всей выборкой) клиенты, отвечающие одному или нескольким из следующих условий: 
- ежемесячный доход от 120 до 170 00;
- возраст 25-35 лет;
- неженат/не замужем или состоит в гражданском браке;
- цель кредита - покупка автомобиля или образование;
- нет детей;
- тип занятости - "сотрудник" 
- имеет среднее, начальное или незаконченное высшее образование; 
- пол - мужской

Наименее "опасны" с точки зрения невозврата кредита (по сравнению со всей выборкой) клиенты, отвечающие одному или нескольким из следующих условий:: 
- ежемесячный доход до 70 000  или  220 000; 
- возраст 45-65 лет;
- женат/замужем; 
- цель кредита - операции с недвижимостью;
- есть 1 или 2 ребенка;
- тип занятости - "компаньон", "пенсионер" или "госслужащий"; 
- имеет высшее образование; 
- пол - женский. 


Важность признаков в процентах по убыванию:
- уровень ежемесячного дохода - 27%
- возрастная группа - 15%
- семейный статус - 13%
- цель кредита - 13% 
- количество детей - 11%
- тип занятости - 10%
- образование - 8%
- пол - 3%