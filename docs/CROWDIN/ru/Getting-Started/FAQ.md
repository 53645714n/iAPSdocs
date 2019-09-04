# Часто задаваемые вопросы по работе ИПЖ

Хотите добавить вопросы в ЧаВо? Читайте [инструкции](../make-a-PR.md)

# Общее

## Можно ли скачать установочный файл AndroidAPS?

Нет. Для AndroidAPS не предоставляется загружаемый файл apk. Его надо [скомпилировать](../Installing-AndroidAPS/Building-APK.md) самостоятельно. Причина вот в чем:

AndroidAPS создан для управления помпой и подачи инсулина. В соответствии с действующим Европейским законодательством, все системы, классифицируемые как IIa или IIb, являются медицинскими устройствами, подлежащими обязательной сертификации (получение знака CE), что в свою очередь требует соответствующих исследований и одобрений. Распространение несертифицированных устройств незаконно. Аналогичные законы существуют и в других частях мира.

Это положение не ограничивается торговлей, но относится к любому виду распространения (даже безвозмездному). Создание медицинского устройства для себя является единственным вариантом, не затрагиваемым этими правилами.

Именно поэтому распространение в виде готовых приложений (apk) недоступно.

## С чего начать?

Прежде всего, нужно **подготовить компоненты, которые работают с ипж**:

* Совместимую с AAPS(ИПЖ) инсулиновую помпу 
* Смартфон с Андроидом (Apple iOS не поддерживается AndroidAPS - вместо этого изучите вариант [iOS Loop](https://loopkit.github.io/loopdocs/)) 
* [Система непрерывного мониторинга глюкозы крови (ГК)](../Configuration/BG-Source.rst). 

Во-вторых, вам нужно **настроить ваше оборудование**. Смотрите [пример установки с пошаговым руководством](Sample-Setup.md).

В-третьих, вам нужно **настроить компоненты программного обеспечения**: AndroidAPS и источники мониторинга.

В-четвертых, вам нужно изучить и **понять исходный дизайн OpenAPS для проверки параметров лечения**. Фундаментальный принцип замкнутой петли: скорость подачи вашего базала и соотношение инсулин/углеводы должны быть точно выверены. Все рекомендации, выдаваемые ИПЖ предполагают, что ваши базовые потребности в инсулине удовлетворены и любые пики и провалы характеристики ГК - следствие других факторов, требующих дополнительных одноразовых настроек: упражнения, стресс и пр. В настройках ИПЖ введены ограничения безопасности (см. максимально допустимый базальный уровень в [Архитектуре OpenAPS](https://openaps.org/reference-design/)), которые означают, что вам не придется тратить допустимые дозировки на исправление неправильной базы. Например, если перед едой вы часто ставите временную цель на пониженный уровень ГК, вам, скорее всего, требуется настройка базы. Вы можете использовать [автонастройку](http://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html#phase-c-running-autotune-for-suggested-adjustments-without-an-openaps-rig) для обработки массива ваших данных и определения необходимости коррекции базальной скорости, фактора чувствительности к инсулину ISF и углеводного коэффициента CR. Либо протестировать и определить скорость базала [старым способом](http://integrateddiabetes.com/basal-testing/).

## Важные практические аспекты

* Если вы считаете необходимым исключить несанкционированное изменение настроек ИПЖ, вы можете закрыть паролем настройку, выбрав в меню "Пароль для настроек" и установив пароль на этот раздел. В следующий раз, когда вы войдете в это меню, система запросит пароль и не позволит поменять их без корректного ввода. Если в дальнейшем вы хотите удалить пароль, зайдите в это меню снова и удалите текст.

* Если вы планируете использовать Android Wear для изменения болюса или настроек, вам нужно удостовериться, что сообщения от ИПЖ не блокируются Подтверждения действий приходят через сообщения (уведомления)

* Если вы снимаете помпу для душа/купания/плавания/спорта и пр, нажмите и удержите текст "Открытый/замкнутый цикл на основном экране и выберите "отключить на..", установив, на сколько часов вы хотите отключить помпу. Это установит скорость подачи базы на "0". Минимальное время отключения определяется минимальной длительностью временной скорости базала на помпе, поэтому, если вы хотите отключить AndroidAPS на более короткий период, или подключили помпу ранее, чем ожидали, нажмите и удерживайте текст "Приостановить (на X минут)", по окончании выберите "Возобновить". когда ИПЖ восстановит работу, ваш активный инсулин будет рассчитан точно.

* Для безопасности, рекомендации системы делаются не на одном показании ГК, а на среднем из последних значений (с учетом скользящей дельты) Поэтому, если вы пропустили несколько показаний, понадобится время на то, чтобы AndroidAPS снова начал компенсацию ГК в режиме замкнутого цикла.

* Вот несколько блогов с полезными советами, которые помогут понять практику работы ИПЖ:
  
  * [Подробные Настройки ](http://seemycgm.com/2017/10/29/fine-tuning-settings/) (см.мой мониторинг)
  * [Почему длительность работы инсулина DIA имеет значение](http://seemycgm.com/2017/08/09/why-dia-matters/) (см. мой мониторинг).
  * [Как ограничить пики после питания](https://diyps.org/2016/07/11/picture-this-how-to-do-eating-soon-mode/) #DIYPS
  * [Гормоны и autosens](http://seemycgm.com/2017/06/06/hormones-2/) (см.мой мониторинг)

## Какое запасное оборудование рекомендуется брать с собой?

Прежде всего, вам необходимо иметь стандартный набор для больного диабетом 1го типа. При работе с AndroidAPS настоятельно рекомендуется также иметь:

* запасной аккумулятор для смартфона и (если необходимо) передатчика ГК
* Резервную копию используемых вами приложений: последний APK программного обеспечения AAPS, пароль на хранилище, файл настроек AAPS, файл настроек xDrip и т. д.. Целесообразно использовать для этого облако(DropBox, Yandex. Disk и пр.)...
* Батарейки для помпы

## Как безопасно закрепить трансмиттер ГК/сенсор ГК?

Его можно закрепить при помощи пластыря: В продаже можно найти предварительно прорезанные пластыри для распространенных систем мониторинга (выполните поиск Google или ebay). Некоторые пользователи ИПЖ применяют более дешевые стандартные кинезезиотейпы или лейкопластыри.

Можно его закрепить: В продаже есть готовые эластичные повязки, которыми можно фиксировать сенсор (поищите через Google или ebay).

# Настройки системы AndroidAPS

Этот список поможет оптимизировать настройки. Начните сверху и двигайтесь вниз. Старайтесь выверить одну настройку прежде чем переходить к другой. Двигайтесь небольшими шагами, не вносите большие изменения сразу. Можно использовать автонастройку [Autotune](https://autotuneweb.azurewebsites.net/) которая даст общее направление, но принимайте рекомендации не вслепую и не во всех ситуациях. Обратите внимание, что настройки дополняют друг друга - вы можете иметь "неправильные" настройки, которые в некоторых обстоятельствах работают хорошо (например, если слишком высокий базал установлен одновременно со слишком высоким углеводным коэффициентом CR), но в других не работают. Это означает, что нужно учитывать все настройки и убедиться, что они совместно работают в различных обстоятельствах.

## Продолжительность активности инсулина DIA

### Описание & тестирование

Время, за которое инсулин снижается до нуля.  
Многие устанавливают его слишком непродолжительным. Правильная настройка для большинства - не менее 5 часов, иногда 6 или 7.

### Эффект

Слишком малое значение продолжительности действия инсулина DIA может привести к низкой ГК. И наоборот.

Если DIA слишком короткий, AAPS слишком рано решит, что предыдущий болюс израсходован, и, при все еще высокой ГК, добавит инсулин. (Фактически, алгоритм не выжидает, а продолжает добавлять инсулин, предсказывая, что произойдет). Это, по сути, создает «затоваривание инсулина», о котором AAPS не знает.

Пример слишком короткого DIA - это высокая ГК, за которой следует избыточная коррекция и в результате - низкая ГК.

## График базала (ед/ч)

### Описание & тестирование

Количество инсулина в заданном часовом блоке для поддержания ГК на стабильном уровне.

Проверьте настройки базы, приостановив цикл и пропуская приемы пищи, чтобы контролировать изменения ГК в течение 5 часов после еды. Повторите несколько раз.

Если ГК падает, то уровень базы слишком велик. И наоборот.

### Эффект

Повышенная скорость подачи базала может привести к низкому уровню ГК. И наоборот.

AAPS по умолчанию строит свой алгоритм отталкиваясь от скорости базала. Если базал слишком высокий, то «нулевая временная скорость» будет определяться при большем отрицательном значении активного инсулина IOB, чем нужно. Это приведет к тому, что АААПС будет давать больше коррекций, чем следует, чтобы привести активный инсулин IOB к нулю.

Таким образом, слишком высокая скорость подачи базала создаст низкую ГК как на стандартной базе, так и несколько часов спустя, так как AAPS еще корректирует к цели.

И наоборот, слишком низкий уровень может привести к высоким ГК, и невозможности снизить уровень до целевого.

## Фактор чувствительности к инсулину (ISF) (ммоль/л/ед или мг/дл/ед)

### Описание & тестирование

Ожидаемое снижение ГК после подачи 1ед. инсулина.

Если база рассчитана верно, вы можете определить ISF, приостановив цикл и убедившись что IOB равен нулю, принять несколько таблеток глюкозы, чтобы получить стабильно «высокую» гликемию.

Затем введите предполагаемое количество инсулина (по текущему соотношению 1/ISF), чтобы прийти к целевой ГК.

Будьте осторожны, так как довольно часто величина слишком занижена. Слишком низкая чувствительность означает, что 1 ед опустит ГК быстрее, чем ожидалось.

### Эффект

**Более низкая чувствительность ISF** (например 40 мг/дл/ед вместо 50) = более агрессивный алгоритм, приводящий к большему падению ГК на каждую единицу инсулина. Если она слишком мала, можно получить низкий уровень ГК.

**Более высокая чувствительность ISF** (например 45 мг/дл/ед вместо 35) = менее агрессивный алгоритм, приводящий к меньшему падению ГК на каждую единицу инсулина. Если она слишком велика, можно получить высокий уровень ГК.

**Пример:**

* ГК - 190 мг/дл (10,5 ммол/л), а цель - 100 мг/дл (5,6 ммол/л). 
* Нужно скорректировать 90 мг/дл (= 190 - 100).
* Чувствитльность ISF = 30 -> 90 / 30 = 3 единицы инсулина
* Чувствитльность ISF = 45 -> 90 / 45 = 2 единицы инсулина

Слишком низкая заданная чувствительность (бывает нередко) может привести к "чрезмерной коррекции" ГК, поскольку AAPS будет считать, что ему нужно больше инсулина для корректировки высокой гликемии, чем на самом деле. Это может привести к «американским горкам» (особенно при голодании). В этом случае нужно увеличить ISF. Тогда ААПС уменьшит корректирующие дозы, что позволит избежать чрезмерной коррекции, которая приводит к низкой ГК.

В то же время, задание слишком высокой чувствительности ISF может привести к недостаточной коррекции, когда ГК останется выше цели, это особенно заметно за ночь.

## Углеводный коэффициент - соотношение углеводов и инсулина (CR) (г/ед)

### Описание & тестирование

Углеводы в граммах на каждую единицу инсулина.

Полагая, что база задана верно, можно проверить этот коэффициент, убедившись в отсутствии активного инсулина IOB при нормальной гликемии. Для этого надо съесть известную пищу с известным количеством углеводов и подав на нее расчетное количество инсулина, основываясь на текущем соотношении 1/CR. Лучше всего есть пищу, которую вы обычно едите в это время дня и точно посчитать ее углеводы.

### Эффект

**Более низкий углеводный коэффициент CR** = меньше еды на единицу инсулина, то есть вы получаете больше инсулина на фиксированное количество углеводов. Может также назваться «более агрессивным».

**Более высокий углеводный коэффициент CR** = больше еды на единицу инсулина, то есть вы получаете меньше инсулина на фиксированное количество углеводов. Может также назваться «менее агрессивным».

Если после усваивания пищи и возвращения активного инсулина IOB к нулю, ГК остается выше чем до еды, высока вероятность того, что CR слишком велик. И наоборот, если ГК ниже, чем перед едой, CR слишком мал.

# Алгоритм APS

## Почему на вкладке "помощник болюса OPENAPS AMA" время действия инсулина DIA показано как 3, хотя у меня в профиле другая величина?

![AMA 3h](../images/Screenshot_AMA3h.png)

В помощнике болюса AMA "DIA" не означает "длительность действия инсулина". Это параметр, который раньше был связан с DIA. Теперь же он означает, 'время, за которое нужно завершить коррекцию'. Он не имеет ничего общего с расчетом активного инсулина IOB. В алгоритме OpenAPS SMB в этом параметре больше нет необходимости.

## Профиль

### Почему следует устанавливать минимум продолжительности действия инсулина DIA на 5 часов вместо 2-3 часов?

Хорошо объяснено в [этой статье](http://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/). Не забудьте `АКТИВИРОВАТЬ ПРОФИЛЬ` после изменения продолжительности действия инсулина DIA.

### Что заставляет алгоритм цикла часто понижать ГК до гипогликемических значений в отсутствии углеводов COB в организме?

В первую очередь, проверьте значения скорости подачи базала и проверьте работу базала безуглеводным test'ом. Если все верно, то такое поведение обычно вызвано слишком низким значением чувствительности к инсулину ISF. Слишком низкая чувствительность ISF обычно выглядит так:

![ISF too low](../images/isf.jpg)

### Что вызывает постпрандиальные пики в замкнутом цикле?

В первую очередь, проверьте значения скорости подачи базала и проверьте работу базала безуглеводным test'ом. Если все правильно, и гликемия падает до целевого значения после того, как углеводы полностью усвоены, попробуйте за некоторое время до еды установить временную цель "приближается прием пищи" в AAPS или продумайте подходящее время преболюса с вашим эндокринологом. Если ваша гликемия слишком высока после еды и все еще слишком высока после того, как углеводы полностью усвоены, подумайте о снижении соотношения инсулин/углеводы IC с вашим эндокринологом. Если гликемия слишком высока при усвоении углеводов COB и слишком низка после их полного усвоения, подумайте об увеличении соотношения инсулин/углеводы IC и о надлежащем времени преболюса с эндокринологом.

# Other settings

## Nightscout settings

### AndroidAPS NSClient says 'not allowed' and does not upload data. What can I do?

In NSClient check 'Connection settings'. Maybe you actually are not in an allowed WLAN or you have activated 'Only if charging' and your charging cable is not attached.

## CGM settings

### Why does AndroidAPS say 'BG source doesn't support advanced filtering'?

If you do use another CGM/FGM than Dexcom G5 or G6 in xDrip native mode, you'll get this alert in AndroidAPS openAPS-tab. See [Smoothing blood glucose data](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md) for more details.

## Помпа

### Where to place the pump?

There are innumerable possibilities to place the pump. It does not matter if you are looping or not. If you rather would have a tubeless insulin pump and have a Dana for looping, check the 30cm catheter with the original belly belt.

### Batteries

Looping can reduce the pump battery faster than normal use because the system interacts through bluetooth far more than a manual user does. It is best to change battery at 25% as communication becomes challenging then. You can set warning alarms for pump battery by using the PUMP_WARN_BATT_P variable in your nightscout site. Tricks to increase battery life include:

* reduce the length of time the LCD stays on (within pump settings menu)
* reduce the length of time the backlight stays on (within pump settings menu)
* select notification settings to a beep rather than vibrate (within pump settings menu)
* only press the buttons on the pump to reload, use AndroidAPS to view all history, battery level and reservoir volume.
* AndroidAPS app may often be closed to save energy or free RAM on some phones. When AndroidAPS is reinitialized at each startup it establishes a Bluetooth connection to the pump, and re-reads the current basal rate and bolus history. This consumes battery. To see if this is happening, go to Preferences > NSClient and enable 'Log app start to NS'. Nightscout will receive an event at every restart of AndroidAPS, which makes it easy to track the issue. To reduce this happening, whitelist AndroidAPS app in the phone battery settings to stop the app power monitor closing it down.
* clean battery terminals with alcohol wipe to ensure no manufacturing wax/grease remains.
* for DanaR/RS pumps the startup procedure draws a high current across the battery to purposefully break the passivation film (prevents loss of energy whilst in storage) but it doesn't always work to break it 100%. Either remove and reinsert battery 2-3 times until it does show 100% on screen, or use battery key to briefly short circuit battery before insertion by applying to both terminals for a split second.
* see also more tips for [particular types of battery](../Usage/Accu-Chek-Combo-Tips-for-Basic-usage#battery-type-and-causes-of-short-battery-life)

### Changing reservoirs and canulas

The change of cartridge can not be done via AndroidAPS, but must be carried out as before directly via the pump.

* Long press on "Open Loop"/"Closed Loop" on the Home tab of AndroidAAPS and select 'Suspend Loop for 1h'
* Now disconnect the pump, and change the reservoir as per pump instructions.
* Once reconnected to the pump continue the loop by long pressing on 'Suspended (X m)'.

The change of a canula however does not use the "prime infusion set" function of the pump, but fills the infusion set and/or canula using a bolus which does not appear in the bolus history. This means it does not interrupt a currently running temporary basal rate. On the Actions (Act) tab, use the PRIME/FILL button to set the amount of insulin needed to fill the infusion set and start the priming. If the amount is not enough, repeat filling. You can set default amount buttons in the Preferences > Other > Fill/Prime standard insulin amounts. See the instruction booklet in your canula box for how many units should be primed depending on needle length and tubing length.

## Daily usage

### Hygiene

#### What to do when taking a shower or bath?

You can remove the pump while taking a shower or bath. For this short period of time you'll usually won't need it. But you should tell it to AAPS so that the IOB calculations are right. Push on the light blue field 'Open loop / Closed loop' on top of the homescreen. Select **'Disconnect pump for XY min'** depending on the estimated time. Once you have been reconnected your pump you can select 'Continue' in the same field or just wait until the chosen time of disconnection is over. The loop will continue automatically.

### Work

Depending on the kind of your job, maybe you use different treatment factors on workdays. As a looper you should think of a profile switch for your estimated working day (e.g. more than 100% for 8h when sitting around or less than 100% when you are active), a high or low temporary target or a time shift of your profile when standing up much earlier or later than regular. If you are using Nightscout profiles, you can also create a second profile (e.g. 'home' and 'workday') and do a daily profile switch to the profile you actually need.

## Leisure activities

### Sports

### Sex

You can remove the pump to be 'free', but you should tell it to AAPS so that the IOB calculations are right. Push on the light blue field 'Open loop / Closed loop' on top of the homescreen. Select **'Disconnect pump for XY min'** depending on the estimated time. Once you have been reconnected your pump you can select 'Continue' in the same field or just wait until the chosen time of disconnection is over. The loop will continue automatically.

### Drinking alcohol

Drinking alcohol is risky in closed loop mode as the algorythm cannot predict the alcohol influenced BG correctly. You have to check out your own method for treating this using the following functions in AndroidAPS:

* Deactivating closed loop mode and treating the diabetes manually or
* setting high temp targets and deactivating UAM to avoid the loop increasing IOB due to an unattended meal or
* do a profile switch to noticeably less than 100% 

When drinking alcohol you always have to have an eye on your CGM to manually avoid a hypoglycemia by eating carbs.

### Sleeping

#### How can I loop during the night without mobile and WIFI radiation?

Many users turn the phone into airplane mode at night. If you want the loop to support you when you are sleeping, proceed as follows (this will only work with a local BG-source such as xDrip+ or patched Dexcom app, it will NOT work if you get the BG-readings via nightscout):

1. Включите режим авиаперелета на вашем мобильном устройстве.
2. Подождите, пока режим авиаперелета не будет активирован.
3. Включите Блутус.

You are not receiving calls now, nor are you connected to the internet. But the loop is still running.

У некоторых пользователей обнаружились проблемы с локальной трансляцией (AAPS не получает данные от xDrip+) в режиме авиаперелета. Перейдите в Настройки xdrip+ > Inter-app settings > Identify receiver и введите `info.nightscout.androidaps`.

![xDrip+ Inter-app Settings Identify receiver](../images/xDrip_InterApp_NS.png)

### Travelling

#### How to deal with timezone changes?

With DanaR and DanaR Korean you don't have to do anything. For other pumps see [timezone travelling](../Usage/Timezone-traveling.md) page for more details.

## Medical topics

### Hospitalization

If you want to share some information about AndroidAPS and DIY looping with your clinicians, you can print out the [guide to AndroidAPS for clinicians](../Resources/clinician-guide-to-AndroidAPS.md).

### Medical appointment with your endocrinologist

#### Reporting

You can either show your nightscout reports (https://YOUR-NS-SITE.com/report) or check [Nightscout Reporter](https://nightscout-reporter.zreptil.de/)