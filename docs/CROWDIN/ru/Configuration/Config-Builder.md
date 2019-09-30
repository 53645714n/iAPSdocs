# Конфигуратор

В зависимости от настроек, конфигуратор можно открыть с помощью вкладки в верхней части экрана или через сэндвич-меню.

![Open config builder](../images/ConfBuild_Open.png)

Конфигуратор (Конф) - это вкладка, на которой можно подключать и отключать модули программы. Ячейки с левой стороны (A) позволяют выбрать, какими модулями программы вы будете пользоваться, ячейки справа (C) позволяют представить эти модули в виде вкладок (E) в AndroidAPS. Если правая ячейка не активирована, доступ к функциям можно получить из выпадающего меню (D) в левом верхнем углу экрана.

Там, где в пределах модуля доступны дополнительные параметры, можно нажать на шестеренку (B), которая их откроет.

**Первая конфигурация:** Начиная с версии 2.0 AAPS процесс настройки AndroidAPS контролируется Мастером установки. Для его запуска нажмите на меню под тремя точками в правом верхнем углу экрана меню (F) и выберите «Мастер установки».

![Config Builder boxes and cog wheel](../images/ConfBuild_ConfigBuilder.png)

## Вкладка или сэндвич-меню

С помощью переключателя под значком глаза вы можете решить, как открыть соответствующий раздел программы.

![Вкладка или сэндвич-меню](../images/ConfBuild_TabOrHH.png)

## Профиль

Выберите нужный базальной профиль См. страницу [Профили](../Usage/Profiles.md) для дополнительной информации.

### Локальный профиль (рекомендуется)

Локальный профиль использует базальной профиль, введенный вручную в телефоне. Как только он выбран, появляется новая вкладка, где можно при необходимости изменить данные профиля, считываемые с помпы. При следующем переключении профиля они записываются на помпу в профиль 1. Мы рекомендуем этот профиль, поскольку он не зависит от интернет-соединения.

Преимущества:

* не требуется подключение к интернету для изменения настроек профиля
* изменения профиля могут быть сделаны непосредственно на телефоне

Недостатки:

* только один профиль

### Профиль Nightscout (NS)

Профиль NS использует профили, которые вы сохранили на сайте Nightscout (https://[адрес вашего сайта]/profile). Вы можете воспользоваться [Переключателем профиля](../Usage/Profiles.md) для изменения активного профиля, это действие записывает данные профиля в помпу на случай отказа AndroidAPS. Это позволяет легко создавать несколько профилей в Nightscout (например.. работа, дом, спорт, отдых и т. п.). Вскоре после нажатия кнопки «Сохранить» они будут переданы в AAPS если ваш смартфон подключен к интернету. Даже без подключения к Интернету или без подключения к Nightscout профили Nightscout доступны в AAPS после синхронизации.

Выполните ** переключение профиля** для активации профиля из Nightscout. Нажмите и удерживайте поле текущего профиля в верхнем углу (серое поле между светло синим полем «Открытый/замкнутый цикл» и темно синим полем области целевых значений) > переключатель профиля > выбрать профиль > ОК. AAPS также прописывает выбранный профиль в помпу, так что он будет доступен и выполняться без AAPS при непредвиденных ситуациях.

Преимущества:

* множественные профили
* легко редактировать с помощью ПК или планшета

Недостатки:

* невозможность локальных изменений в настройках профиля
* профиль не может быть изменен непосредственно на телефоне

### Простой профиль

Простой профиль с одним блоком времени для продолжительности действия инсулина DIA, углеводного коэффициента IC, чувствительности к инсулину ISF, скорости базала и целевым диапазоном (напр. если скорость базала не изменяется в течение дня). Вероятнее всего, будет использоваться для тестирования, если только у вас не одни и те же коэффициенты 24 часа в сутки. После выбора «Простого профиля», в AAPS появится новая вкладка, куда можно ввести данные профиля.

## Инсулин

Выберите кривую, соответствующую типу вашего инсулина. Варианты 'Быстродействующий Oref', Сверхбыстрый Oref' и 'Безпиковый Oref' имеют вид экспоненты. Более подробно см. в [Документах OpenAPS](http://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/understanding-insulin-on-board-calculations.html#understanding-the-new-iob-curves-based-on-exponential-activity-curves), кривые различаются на основе длительности действия инсулина DIA и времени пика. Длительность действия инсулина DIA всегда должна быть не менее 5 часов, подробнее в разделе Профиль инсулина [на этой странице](../Getting-Started/Screenshots.md). Для быстродействующих и сверхбыстрых инсулинов, длительность действия инсулина DIA является единственной переменной, которую можно настроить самостоятельно, время пика фиксированное. Безпиковый позволяет настроить как DIA, так и время пика, эта опция для опытных пользователей, которые знают последствия таких параметров. График инсулина позволяет понять поведение других кривых. Его можно увидеть на вкладке, если отметить галочкой в конфигураторе или выбрать из выпадающего меню слева.

### Быстродействующий Oref

* рекомендуется для Humalog, Novolog и Novorapid
* DIA (длительность действия инсулина) = по крайней мере 5.0 часов
* Макс. пик = 75 минут после инъекции

### Сверхбыстрый Oref

* рекомендуется для FIASP
* DIA (длительность действия инсулина) = по крайней мере 5.0 часов
* Макс. пик = 55 минут после инъекции

Для многих людей действие FIASP практически незаметно спустя 3-4 часа, даже если, как правило, еще остается 0.0xx ед. Это остаточное количество может быть ощутимо во время занятий спортом, например. Поэтому AndroidAPS использует как минимум 5 часов в качестве DIA.

![Config Builder Ultra-Rapid Oref](../images/ConfBuild_UltraRapidOref.png)

### Безпиковый Oref

На профиле «Безпиковый 0ref» можно самостоятельно ввести пиковое время. Если в профиле не определено более высокое значение, DIA автоматически устанавливается на 5 часов.

Этот инсулиновый профиль рекомендуется если используется неподдерживаемый тип инсулина или смесь различных инсулинов.

## Источник данных гликемии

Выберите источник данных ГК - см. страничку [Источник ГК](BG-Source.rst) для получения дополнительной информации по настройкам.

* [xDrip +](https://xdrip-plus-updates.appspot.com/stable/xdrip-plus-latest.apk)
* ГК с клиента Nightscout
* [MM640g](https://github.com/pazaan/600SeriesAndroidUploader/releases)
* [Glimp](https://play.google.com/store/apps/details?id=it.ct.glicemia&hl=de)
* Модифицированное приложение [Dexcom G5](https://github.com/dexcomapp/dexcomapp/) - выберите «Отправлять данные ГК на xDrip +», если хотите получать оповещения от xDrip +. ![Источник ГК в конфигураторе](../images/ConfBuild_BGSource.png)
* [Poctech](http://www.poctechcorp.com/en/contents/268/5682.html)

## Помпа

Выберите помпу, которой пользуетесь.

* [Dana R](DanaR-Insulin-Pump.md)
* DanaR Корея (DanaR для корейского рынка)
* DanaRv2 (DanaR с обновленной прошивкой)
* [Dana RS](DanaRS-Insulin-Pump.md)
* [Accu-Chek Combo](Accu-Chek-Combo-Pump.md) (требует установки утилиты ruffy)
* MDI инъекции инсулина шприцем/шприц-ручкой (на основе предложений от AAPS по ведению терапии)
* Виртуальная помпа (открытый цикл для помпы, не имеющей драйверов - только предложения по ведению терапии от AAPS)

Для активации сторожа BT, BT watchdog, пользуйтесь **Дополнительными параметрами**. Он отключает bluetooth на одну секунду, если подключение к помпе невозможно. Это помогает на некоторых телефонах, где зависает стек bluetooth.

## Определение чувствительности

Выберите тип анализа чувствительности. Алгоритм будет анализировать историю данных и вносить коррективы, если признает, что вы реагируете более чутко (или, наоборот, более резистентно) на инсулин, чем обычно. Подробнее об алгоритме чувствительность Oref0 можно прочитать в [документации OpenAPS](http://openaps.readthedocs.io/en/latest/docs/walkthrough/phase-4/advanced-features.html#auto-sensitivity-mode).

Вы можете вывести график чувствительности на экран, отметив галочкой соответствующий пункт из выпадающего меню графиков. Он изображается в виде белой линии. Для применения авточувствительности вы должны находиться на шестом этапе [целей](../Usage/Objectives).

### Настройки усваиваемости

Если вы используете Oref1 с микроболюсами SMB, следует заменить минимальное время действия углеводов**min_5m_carbimpact** на 8. Это значение используется только во время пробелов в мониторинге или когда физическая нагрузка "съедает" весь подъем гликемии, которая в ином случае заставила бы алгоритм AAPS компенсировать активные углеводы COB организма. В те времена когда поглощение углеводов не может быть рассчитано динамически на основе реакции крови, он по умолчанию применяет эту скорость распада. Этот параметр не приводит к отказам.

## Система ИПЖ

Выберите нужный алгоритм APS для ведения терапии. Подробности выбранного алгоритма можно просмотреть на вкладке OpenAPS(OAPS).

* Помощник болюса OpenAPS MA (по состоянию алгоритма на 2016г.)
* Помощник болюса OpenAPS AMA (расширенный помощник болюса, состояние алгоритма на 2016г.).  
    Подробнее об OpenAPS AMA в [документации OpenAPS](http://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autosens.html#advanced-meal-assist-or-ama). Говоря просто, его преимущество в том, что после болюса на еду система быстрее определит верхнюю временную цель если углеводы введены верно.  
    Обратите внимание, что для пользования алгоритмом следует дойти до [Цели 7](../Usage/Objectives.md).
* [OpenAPS SMB](../Usage/Open-APS-features.md) (супер микро болюс, новый алгоритм для опытных пользователей)   
    ; обратите внимание, работа OpenAPS SMB требует достижения [цели 8](../Usage/Objectives.md), а в конфигураторе минимальное 5-мин действие углеводов должно быть установлено как 8: конфигуратор> чувствительность >параметр чувствительности Oref1.

## Замкнутый цикл

Определите, хотите ли вы доверить AAPS автоматическое управление.

### Открытый цикл

AAPS continuously evaluates all available data (IOB, COB, BG...) and makes treatment suggestions on how to adjust your therapy if necessary. The suggestions will not be executed automatically (as in closed loop) have to be entered manually into the pump or by using a button in case you are using a compatible pump (Dana R/RS or Accu Chek Combo). This option is for getting to know how AndroidAPS works or if you are using an unsupported pump.

### Замкнутый цикл

AAPS continuously evaluates all available data (IOB, COB, BG...) and automatically adjusts the treatment if necessary (i.e. without further intervention by you) to reach the set target range or value (bolus delivery, temporary basal rate, insulin switch-off to avoid hypo etc.). The Closed Loop works within numerous safety limits, which you can be set individually. Closed Loop is only possible if you are in [Objective 4](../Usage/Objectives.md) or higher and use a supported pump.

## Objectives (learning program)

AndroidAPS has a number of objectives that you have to fulfill step by step. This should guide you safely through setting up a closed loop system. It guarantees that you have set everything up correctly and understand what the system does exactly. This is the only way you can trust the system.

You should export your settings (including progress of the objectives) on a regularly basis. In case you have to replace your smartphone later (new purchase, display damage etc.) you can simply import those settings.

See [Objectives](../Usage/Objectives.md) page for more information.

## Терапия

If you view the Treatments (Treat) tab, you can see the treatments that have been uploaded to nightscout. Should you wish to edit or delete an entry (e.g. you ate less carbs than you expected) then select 'Remove' and enter the new value (change the time if necessary) through the Careportal (CP) tab.

## Общие настройки

### Главный экран

Displays the current state of your loop and buttons for most common actions (see [section The Homescreen](../Getting-Started/Screenshots.md) for details). Settings can be accessed by clicking the cog wheel.

#### Не отключать экран

Option 'Keep screen on' will force Android to keep the screen on at all times. This is useful for presentations etc. But it consumes a lot of battery power. Therefore, it is recommended to connect the smartphone to a charger cable.

#### Кнопки

Define which Buttons are shown on the home screen.

* Терапия
* Калькулятор
* Инсулин
* Углеводы
* Мониторинг (открывает xDrip +)
* Калибровка

Furthermore, you can set shortcuts for insulin and carb increments and decide whether the notes field should be shown in treatment dialogues.

#### Быстрый болюс

Create a button for a certain standard meal (carbs and calculation method for the bolus) which will be displayed on the home screen. Use for standard meals frequently eaten. If different times are specified for the different meals you will always have the appropriate standard meal button on the home screen, depending on the time of day.

Note: Button will not be visible if outside the specified time range or if you have enough IOB to cover the carbs defined in the QuickWizard button.

![QuickWizard button](../images/ConfBuild_QuickWizard.png)

#### Расширенные настройки

Enable super bolus functionality in wizard. Use with caution and do not enable until you learn what it really does. Basically, the basal for the next two hours is added to the bolus and a two hour zero-temp activated. **AAPS looping functions will be disabled - so use with care! If you use SMB AAPS looping functions will be disabled according to your settings in ["Max minutes of basal to limit SMB to"](../Usage/Open-APS-features#max-minutes-of-basal-to-limit-smb-to), if you do not use SMB looping functions will be disabled for two hours.** Details on super bolus can be found [here](https://www.diabetesnet.com/diabetes-technology/blue-skying/super-bolus).

### Действия

Some buttons to quickly access common features:

* Переключатель профилей (см. [страницу профилей](../Usage/Profiles.md) для дополнительной информации по настройке)
* Временные цели
* Задать / отменить врем. скорость базала
* Пролонгированный болюс (только для DanaR/RS или Combo)
* Первичное заполнение / заправка картриджа (только для DanaR/RS или Combo)
* Журнал
* TDD (Общая суточная доза = болюс + базал за день)

Some doctors use - especially for new pumpers - a basal-bolus-ratio of 50:50. Therefore ratio is calculated as TDD / 2 * TBB (Total base basal = sum of basal rate within 24 hours). Others prefer range of 32% to 37% of TDD for TBB. Like most of these rules-of-thumb it is of limited real validity. Note: Your diabetes may vary!

![Actions tab](../images/ConfBuild_ConfBuild_Actions.png)

### Портал назначений/терапии

Allows you to record any specific care entries and view the current sensor, insulin, canula and pump battery ages in the Careportal (CP) tab.

Note: **No insulin** will be given if entered via careportal (i.e. meal bolus, correction bolus...)

Carbs entered in the careportal (i.e. correction carbs) will be used for COB calculation.

![Careportal tab](../images/ConfBuild_CarePortal.png)

### SMS коммуникатор

Allows remote caregivers to control some AndroidAPS features via SMS, see [SMS Commands](../Usage/SMS-Commands.md) for more setup information.

### Еда

Displays the food presets defined in the Nightscout food database, see [Nightscout Readme](https://github.com/nightscout/cgm-remote-monitor#food-custom-foods) for more setup information.

Note: Entries cannot be used in the AndroidAPS calculator. (View only)

### Смарт-часы Wear

Monitor and control AAPS using your Android Wear watch (see [page Watchfaces](../Configuration/Watchfaces.md)). Use settings (cog wheel) to define which variables should be considered when calculating bolus given though your watch (i.e. 15min trend, COB...).

If you want to bolus etc. from the watch then within "Wear settings" you need to enable "Controls from Watch".

![Wear settings](../images/ConfBuild_Wear.png)

Through Wear tab or hamburger menu (top left of screen, if tab is not displayed) you can

* Повторить отправку всех данных. Может быть полезно, если некоторое время часы не были подключены и вы хотите передать на них данные.
* Открыть настройки на часах прямо с телефона.

### Cтрока состояния xDrip (часы)

Display loop information on your xDrip+ watchface (if you are not using AAPS/[AAPSv2 watchface](../Configuration/Watchfaces.md)

### Текущее состояние приложения

Displays a summary of current BG, delta, active TBR%, active basal u/h and profile, IOB and split into bolus IOB and basal IOB on the phones's dropdown screen and phone's lock screen.

![AAPS widget](../images/ConfBuild_Widget.png)

### Клиент Nightscout

Setup sync of your AndroidAPS data with Nightscout.

If **Log app start to NS** is activated each AndroidAPS will be visible in Nightscout. Might be useful to detect problems with the app (i.e. battery optimization not disabled for AAPS) but can flood the Nightscout graph with entries.

#### Опции оповещения

Activate/deactivate AndroidAPS alarms

![Опции оповещения](../images/ConfBuild_NSClient_Alarms.png)

#### Настройки подключения

Offline looping, disable roaming...

If you want to use only a specific WiFi network you can enter its **WiFi SSID **. Several SSIDs can be separated by semicolon. To delete all SSIDs enter a blank space in the field.

![Nightscout connection settings](../images/ConfBuild_ConnectionSettings.png)

#### Расширенные настройки

* Заполнять пропущенные значения ГК данными из Nightscout
* Create announcement from errors Create Nightscout announcement for error dialogs and local alerts (also viewable in careportal in treatments section)
* Активировать местную трансляцию на другие приложения (напр. xDrip+)
* Только отправлять на NS (Синхронизация отключена)
* Не отправлять в NS
* Всегда использовать абсолютные значения базала -> должно быть активировано, если вы хотите правильно применять [Autotune](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html).

![Nightscout advanced settings](../images/ConfBuild_NSClient_Advanced.png)

### Тех. обслуживание

Email and number of logs to be send. Normally no change necessary.

### Конфигуратор

Use tab for config builder instead of hamburger menu.