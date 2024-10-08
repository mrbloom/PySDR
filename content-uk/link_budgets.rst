.. _link-budgets-chapter:

################################
Розрахунок бюджету лінії зв'язку
################################

У цій главі розглядаються розрахунок бюджету каналу зв'язку, значна частина глави присвячена роз'ясненню, що таке потужності передачі/прийому, втрати лінії передачі, коефіцієнту підсилення антени, шуму і с\ш (SNR).  Глава закінчується прикладом побудови бюджету каналу зв'язку для ADS-B, тобто сигналу, який передають комерційні літаками для обміну надсилання координат свойого місцезнаходження та обміну іншою інформацією.  

*************************
Вступ
*************************

Бюджет лінії зв'язку - це врахування всіх підсилень і втрат потужності сигналу на шляху від передавача до приймача в системі зв'язку.  Бюджет лінії розраховується в одному напрямку бездротового зв'язку.  Але більшість систем зв'язку є двонаправленими, для цих лінії зв'язку має бути окремо разрахований бюджет для прийому (downlink) та передачі (uplink).  "Результат" розрахунку бюджету лінії зв'язку показує вам приблизно, яке співвідношення сигнал/шум (в цьому підручнику скорочено с\ш (SNR) , або С/Ш (S/N) ) ви можете очікувати на вході вашого приймача.  Подальший аналіз необхідний для того, щоб перевірити, чи є це значення с\ш (SNR) достатньо високе для вашого застосування.

Мета вивчення розрахунку бюджету лінії зв'язку здебільшого не для того, щоб мати скласти фактичний бюджет певного каналу зв'язку, а для того, щоб розвинути системну точку зору на бездротовий зв'язок.

Спочатку ми розглянемо бюджет по потужності сигналу по прийому, потім бюджет потужності шуму і, нарешті, об'єднаємо ці два бюджети, щоб знайти с\ш (SNR) (потужність сигналу, поділена на потужність шуму).

************************************
Бюджет по прийому потужності сигналу
************************************

Нижче показано найпростішу схему типового бездротового з'єднання.  У цій главі ми зосередимося лише на одному напрямку, від передавача (Tx) до приймача (Rx).  Для даної системи ми знаємо потужність *передачі*; зазвичай це налаштовується в передавачі.  Нам треба визначити яка буде потужність *прийнята* в приймачі?

.. image:: ../_images/tx_rx_system.svg
   :align: center 
   :target: ../_images/tx_rx_system.svg

Для визначення потужності на вході приймача нам знадобляться чотири параметри, які наведені нижче з умовними позначеннями. У цьому розділі ми розглянемо кожен з них.

- **Pt** - Потужність передавача
- **Gt** - Коефіцієнт підсилення передавальної антени
- **Gr** - Коефіцієнт підсилення приймальної антени
- **Lp** - відстань між Tx і Rx (тобто, скільки втрат на шляху розповсюдження)

.. image:: ../_images/tx_rx_system_params.svg
   :align: center 
   :target: ../_images/tx_rx_system_params.svg
   :alt: Зображено параметри, з яких розраховується бюджет каналу зв'язку

Потужність передачі
#####################

Потужність передачі досить простий параметр; він має значення у ватах, дБВт або дБм (нагадаємо, що дБм - це скорочення від дБмВт).  Кожен передавач має один або кілька підсилювачів, і потужність передачі в основному залежить від цих підсилювачів.  Аналогією потужності передачі може бути номінальна потужність лампочки: чим вища потужність, тим більше світла вона випромінює.  Ось приклади приблизних значень потужності для різних технологій:

==================  ========= ==========
\                        Потужність 
------------------  --------------------
Bluetooth             10 мВт   -20 дБВт   
WiFi                 100 мВт   -10 дБВт
Базова станція LTE     1 Вт      0 дБВт
FM-станція            10 кВт    40 дБВт
==================  ========= ==========

Коефіцієнт підсилення антени
#############################

Коефіцієнт підсилення передавальної та приймальної антен має вирішальне значення для розрахунку бюджету лінії зв'язку. Що таке коефіцієнт підсилення антени, запитаєте ви?  Він показує на спрямованість антени.  Хоча його називають коефіцієнтом підсилення потужності антени, але це не повино вводить вас в оману, тому що єдиний спосіб для антени підвищити значення коефіцієнт підсилення - це більше сфокусувати енергію випромінювання в певну область.

Коефіцієнт підсилення вказується в дБ (без приведення до якоїсь одиниці); не соромтеся продивитися або нагадати собі, чому дБ без приведення до одиниць для нашого випадку, вцю іноформацію дивись в розділі :ref:`noise-chapter`. Зазвичай антени бувають або всеспрямованими, тобто їхня потужність випромінюється в усіх напрямках, або спрямованими, тобто їхня потужність випромінюється у певному напрямку.  Якщо вони всеспрямовані, їхній коефіцієнт підсилення буде від 0 дБ до 3 дБ.  Спрямована антена має вищий коефіцієнт підсилення, зазвичай 5 дБ або вище, і навіть може бути 60 дБ або близько того.

.. image:: ../_images/antenna_gain_patterns.png
   :scale: 80 % 
   :align: center 

Якщо використовується спрямована антена, вона повинна бути або встановлена в правильному напрямку, або прикріплена до механічного підвісу. Це також може бути фазована решітка, яка електроно керується (тобто за допомогою програмного забезпечення).

.. image:: ../_images/antenna_steering.png
   :scale: 80 % 
   :align: center 
   
Всеспрямовані антени використовуються, коли неможливо спрямувати пристрій у потрібному напрямку, наприклад така ситуація з антеною вашого мобільного телефона або ноутбука.  У технології 5G телефони можуть працювати у дуже високо-частотних діапазонах, таких як 28 ГГц (Verizon) і 39 ГГц (AT&T), використовуючи при цьому масив антен і електронне керування променем.

При розрахунку бюджета лінії зв'язку ми повинні припустити, що будь-яка спрямована антена, чи передавальна, чи приймальна, спрямована в правильному напрямку. Якщо антена не спрямована у вірному напрямку наш розрахунку бюджету не буде точним, і можуть виникнути втрати на лінії зв'язку (приклад: в супутникову тарілку на вашому даху попадає баскетбольний м'яч, який може її змістити). Загалом, наші розрахунки бюджета передбачають ідеальні обставини, але з додаванням додаткових втрат для врахування умов реального світу.

Втрати на шляху розповсюдження
##############################

Коли сигнал розповсюджується в атмосфері (або у вакуумі), його потужність зменшується.  Уявіть, що ви тримаєте маленьку сонячну панель перед лампочкою.  Чим далі знаходиться сонячна панель, тим менше енергії вона поглинає від лампочки.  **Потік - це термін у фізиці та математиці, який визначається як "кількість речовини, що проходить через ваш об'єкт".  Для нас це кількість електромагнітного поля, що потрапляє на нашу приймальну антену.  Ми хочемо знати, скільки енергії втрачається на певній відстані.

.. image:: ../_images/flux.png
   :scale: 80 % 
   :align: center 

Втрати у вільному просторі (FSPL) дають нам втрати  на заданій відстані якщо на шляху розповсюдження нема перешкод.  У загальному вигляді :math:`\mathrm{FSPL} = ( 4\pi d / \lambda )^2`. Для отримання додаткової інформації погугліть формулу передачі Фріса.  (Цікавий факт: імпеданс для сигнали у вільному просторі дорівнює 377 Ом.) Для розрахунку бюджету лінії  зв'язку ми можемо використовувати це ж рівняння, але з використанням всіх значень приведених до дБ:

.. math::
 \mathrm{FSPL}_{dB} = 20 \log_{10} d + 20 \log_{10} f - 147.55 \left[ dB \right]

Значення втрат буде в дБ, (без приведення доя коїсь одиниці), оскільки це втрати. :math:`d` - це відстань між передавачем і приймачем у метрах. :math:`f` - це частота несучої у Гц.  У цьому простому рівнянні є лише одна проблема: ми не завжди маємо відкритий вільний простір між передавачем і приймачем.  У приміщенні частоти сильно відбиваються (більшість частот можуть проходити крізь стіни, але не через метал або товсту кладку). Для таких ситуацій існують різні моделі для розрахунку не для вільного простору. Найпоширенішою формула розрахунку для міст і приміських районів (яка наприклад використовується для стільникового зв'язку) є формула для моделі Окумура-Хата:

.. math::
 L_{path} = 69.55 + 26.16 \log_{10} f - 13.82 \log_{10} h_B - C_H + \left[ 44.9 - 6.55 \log_{10} h_B \right] \log_{10} d

де :math:`L_{path}` - втрати на шляху в дБ, :math:`h_B` - висота передавальної антени над рівнем землі в метрах, :math:`f` - несуча частота в МГц, :math:`d` - відстань між точками Tx і Rx в км, а :math:`C_H` - "коефіцієнт коригування антени", який визначається залежно від розміру міста та діапазону несучої частоти:

:math:`C_H` для малих/середніх міст:

.. math::
 C_H = 0.8 + (1.1 \log_{10} f - 0.7 ) h_M - 1.56 \log_{10} f

:math:`C_H` для великих міст, коли :math:`f` нижче 200 МГц:

.. math::
 C_H = 8.29 ( log_{10}(1.54 h_M))^2 - 1.1
 
:math:`C_H` для великих міст, коли :math:`f` вище 200 МГц, але менше 1.5 ГГц:

.. math::
 C_H = 3.2 ( log_{10}(11.75 h_M))^2 - 4.97

де :math:`h_M` - висота приймальної антени над рівнем землі в метрах.

Не хвилюйтеся, якщо наведена вище модель Окумура-Хата здалася вам заплутаною; вона наведена тут головним чином для того, щоб продемонструвати, що моделі втрат у не вільному просторі набагато складніші, ніж наше просте рівняння FSPL.  Кінцевим результатом будь-якої з цих моделей є єдине число, яке ми можемо використати як втрати при розповсюджені при розрахунку нашого бюджету лінії зв'язку.  Ми будемо використовувати формулу FSPL до кінця цієї глави.

Додаткові втрати
################

У нашому бюджеті лінії зв'язку ми також хочемо врахувати додаткові втрати.  Ми об'єднаємо їх в одне значення, зазвичай вони становлять від 1 до 3 дБ.  Приклади додаткових втрат:

- Втрати в кабелі
- Втрати в атмосфері
- Недосконалість наведення антени
- Опади

На графіку нижче показано втрати в атмосфері в дБ/км на частоті (зазвичай наші частоти < 40 ГГц).  З аналізу графіку видно, що для зв'язку на коротких відстанях на частотах нижче 40 ГГц **і** втрати в атмосфері на відстані, що рівні або менші 1 км становлять не більше 1 дБ, і тому ми зазвичай можемо їх ігнорувати. Враховувати втрати в атмосфері на практиці потрібно лише у випадку супутникового зв'язку, коли сигнал проходить багато кілометрів крізь атмосферу.

.. image:: ../_images/atmospheric_attenuation.svg
   :align: center 
   :target: ../_images/atmospheric_attenuation.svg
   :alt: Графік залежності втрат в атмосфері в дБ/км від частоти, на якому видно піки від H2O (води) і O2 (кисню)

Рівняння потужності сигналу
############################

Тепер прийшов час скласти всі підсилення і втрати потужності, та обчислити потужність нашого сигналу на вході приймачі, :math:`P_r`:

.. math::
 P_r = P_t + G_t + G_r - L_p - L_{misc} \quad \mathrm{dBW}

Загалом, це просте рівняння. Ми додаємо підсилення і віднімаємо з них втрати. Дехто може навіть не вважати це рівнянням.  Зведемо потужності, коефіцієнти підсилення , і втрати в загальну "бухгалтерську" таблицю:

.. list-table::
   :widths: 15 10
   :header-rows: 0
   
   * - Pt = 1.0 Вт
     - 0 дБВт
   * - Gt = 100
     - 20.0 дБ
   * - Gr = 1
     - 0 дБ
   * - Lp
     - -162.0 дБ
   * - Lmisc
     - -1.0 дБ
   * - **Pr**
     - **-143.0 дБВт**

***********************
Розрахунок бюджету шуму
***********************

Тепер, коли ми знаємо потужність прийнятого сигналу, давайте перейдемо до шуму, оскільки для розрахунку SNR нам потрібні обидва показники.  Ми можемо розрахувати шум на вході приймача за тією ж схемою що і у розрахунку корисного сигналу.

Зараз саме час поговорити про те, звідки шум з'являється в нашій лінії зв'язку.  Відповідь: **У приймачі!** Сигнал не спотворюється шумом, поки ми не почнемо його приймати в приймачі. Дуже важливо зрозуміти цей факт! Багато студентів не зовсім його засвоюють, і в результаті роблять безглузді помилки.  Навколо нас у повітрі немає ніякого шуму. Шум виникає через те, що наш приймач має підсилювач та іншу електроніку, яка не є досконалою, і яка не працює при температурі 0 градусів Кельвіна (К).

Популярна і проста формула для бюджету шуму використовує підхід "kTB":

.. math::
 P_{noise} = kTB

- де :math:`k` - стала Больцмана = 1.38 x 10-23 Дж/К = **-228.6 дБВт/К/Гц**.  Для тих, кому цікаво, постійна Больцмана - це фізична константа, яка пов'язує середню кінетичну енергію частинок у газі з температурою газу.
- :math:`T` - шумова температура системи в К (хто-небудь пам'ятає кріокулери?), в значній мірі залежить від нашого підсилювача.  Це параметр, найважче визначити, і зазвичай він має дуже приблизне значення.  Ви платити більше за підсилювач у якого ця температура шуму нижча. 
- math:`B` - смуга пропускання сигналу в Гц, за умови, що ви відфільтровуєте шум поза смугою сигналу.  Отже, наприклад для сигналу downlink LTE шириною 10 МГц матиме значення :math:`B`, встановлене на 10 МГц, або 70 дБГц.

Тепер можно визначити величину шуму звичайним перемноженням (або додаванням якщо параметри приведені в дБ) для розрахунку відношення с\ш (SNR).

*************************
С/Ш (SNR)
*************************

Тепер, коли ми маємо обидва значення, ми можемо скористатися співвідношенням, щоб знайти с\ш (SNR) (див. розділ :ref:`noise-chapter` для отримання додаткової інформації про с\ш (SNR) ):

.. math::
   \mathrm{SNR} = \frac{P_{signal}}{P_{noise}}

.. math::
   \mathrm{SNR_{dB}} = P_{signal\_dB} - P_{noise\_dB}

Зазвичай прагнуть, щоб с\ш (SNR) був > 10 дБ, хоча це залежить від конкретного застосування. На практиці с\ш (SNR) можна перевірити, подивившись на БПФ прийнятого сигналу або обчисливши потужність з присутнім сигналом і без нього (нагадаємо, що дисперсія = потужність).  Чим вище SNR, тим більше бітів на символ ви можете обробити без зайвих помилок.

***********************************************
Приклад розрахунку бюджету лінії зв'язку: ADS-B
***********************************************

Автоматичне залежне спостереження-радіомовне (ADS-B) - це технологія, яка використовується літаками для трансляції сигналів, що повідомляють про своє місцезнаходження та інший свій статус наземним станціям з управління повітряним рухом та іншим повітряним суднам.  ADS-B є автоматичною системою, оскільки не вимагає участі пілота або зовнішнього втручання; вона залежить від даних з навігаційної системи літака та інших комп'ютерів.  Повідомлення не шифруються (ура!).  Наразі обладнання ADS-B є обов'язковим у частині повітряного простору Австралії, в той час як США вимагають оснащення цим обладнанням літаків, залежно від їхнього розміру.

.. image:: ../_images/adsb.jpg
   :scale: 120 % 
   :align: center 
   
Фізичний (PHY) рівень ADS-B має наступні характеристики:

- Передається на частоті 1,090 МГц
- Смуга пропускання сигналу близько 2 МГц
- PPM модуляція
- Швидкість передачі даних 1 Мбіт/с, з повідомленнями від 56 до 112 мікросекунд
- Повідомлення містять 15 байт даних кожне, тому для отримання всієї інформації про літак зазвичай потрібно декілька повідомлень
- Множинний доступ досягається шляхом трансляції повідомлень з періодом, який випадковим чином коливається між 0,4 і 0,6 секунди.  Ця рандомізація призначена для того, щоб запобігти накладанню всіх передач літаків одна на одну (деякі все одно можуть змішатись, але це не страшно)
- Антени ADS-B вертикально поляризовані
- Потужність передачі варіюється, але повинна бути в районі 100 Вт (20 дБВт)
- Передавальна антена всеспрямована, але спрямований лише вниз, тому, скажімо коефіцієнт підсилення 3 дБ
- Антена приймача ADS-B також всеспрямована, і тому коефіцієнт підсилення антени приймемо за 0 дБ

Втрати на шляху розповсюдження залежать від того, як далеко знаходиться літак від нашого приймача.  Наприклад, між Університетом Меріленда (де читався курс, на якому ґрунтується зміст цього підручника) і аеропортом BWI близько 30 км.  Давайте розрахуємо FSPL для цієї відстані і частоти 1090 МГц:

.. math::
    \mathrm{FSPL}_{dB} = 20 \log_{10} d + 20 \log_{10} f - 147.55 \left[ \mathrm{dB} \right]
    
    \mathrm{FSPL}_{dB} = 20 \log_{10} 30e3 + 20 \log_{10} 1090e6 - 147.55 \left[ \mathrm{dB} \right]

    \mathrm{FSPL}_{dB} = 122.7 \left[ \mathrm{dB} \right]

Інший підхід - залишити :math:`d` як змінну у формулі розрахунку бюджету каналу і з'ясувати, на якій відстані ми зможемо чути сигнали, виходячи з необхідного значення с\ш (SNR). 

Тепер, оскільки у нас точно нема розповсюдження у вільному просторі, давайте додамо ще 3 дБ до дадоткових втрат.  Приймемо загальні втрати рівними 6 дБ, щоб врахувати погане узгодження нашої антени і втрати в кабелі/конекторі.  Враховуючи всі ці критерії, наш бюджет лінії зв'язку виглядає наступним чином:

.. list-table::
   :widths: 15 10
   :header-rows: 0
   
   * - Pt
     - 20 dBW
   * - Gt
     - 3 dB
   * - Gr
     - 0 dB
   * - Lp
     - -122.7 dB
   * - Lmisc
     - -6 dB
   * - **Pr**
     - **-105.7 dBW**

Для нашого розрахунку бюджету шуму:

- B = 2 МГц = 2e6 = 63 дБГц
- T ми повинні взяти приблизно, скажімо, припустимо що це значення 300 К, що становить 24,8 дБК. Це значення залежить від якості приймача
- k завжди дорівнює -228,6 дБВт/К/Гц 

.. math::
 P_{noise} = k + T + B = -140.8 \quad \mathrm{dBW}
 
Отже, наш с\ш (SNR) становить -105.7 - (-140.8) = **35.1 дБ**.  Не дивуйтесь цьому величезному числу, тому що ми вважаємо, що знаходимося лише на відстані 30 км від літака у вільному просторі.  Якби сигнали ADS-B не могли розповсюджуватись на 30 км, то ADS-B не була б дуже ефективна - літаки "чули" би один одного тільки б з дуже близької відстані.  Для цього прикладу ми можемо легко декодувати сигнали; імпульсно-позиційна модуляція (ІПМ) є досить надійною і не вимагає такого високого SNR. Складність прийому полягає в тому, що ми намагаємось прийняти ADS-B, перебуваючи в кімнаті, з антеною, яка дуже погано узгоджена, і наприклад сигналами потужних FM-радіостанцією поруч, які створюють перешкоди.  Ці фактори можуть легко призвести до втрат рівних 20-30 дБ.

Цей приклад насправді був лише приблизним розрахунком, але він демонструє основи розрахунку бюджету каналу зв'язку та розуміння важливих параметрів що впливають на канал зв'язку.
