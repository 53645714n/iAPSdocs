# FAQ for loopers

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

So a basal rate too high will create low BGs both with the default rate, but also some hours hence as AAPS corrects to target.

Conversely a basal rate too low can lead to high BGs, and a failure to bring levels down to target.

## Insulin sensitivity factor (ISF) (mmol/l/U or mg/dl/U)

### Описание & тестирование

The drop in BG expected from dosing 1U of insulin.

Assuming correct basal, you can test this by suspending loop, checking IOB is zero, and taking a few glucose tablets to get to a stable ‘high’ level.

Then take an estimated amount of insulin (as per current 1/ISF) to get to your target BG.

Be careful as this is quite often set too low. Too low means 1 U will drop BG faster than expected.

### Эффект

**Lower ISF** = a smaller drop in BGs for each unit of insulin (also can be called ‘more severe / aggressive’ or ‘stronger’). If too low, this can lead to low BGs.

**Higher ISF** = a bigger drop in BGs for each unit of insulin (also can be called ‘less severe / aggressive’ or ‘weaker’). If too high, this can lead to high BGs.

An ISF that is too low (not uncommon) can result in ‘over corrections’, because AAPS thinks it needs more insulin to correct a high BG than it actually does. This can lead to ‘roller coaster’ BGs (esp when fasting). In this circumstance you need to increase your ISF. This will mean AAPS gives smaller correction doses, and this will avoid over-correcting a high BG resulting in a low BG.

Conversely, an ISF set too high can result in under-corrections, meaning your BG remains above target – particularly noticeable overnight.

## Carbohydrate to insulin ratio (CR) (g/U)

### Описание & тестирование

The grams of carbohydrate for each unit of insulin.

Assuming correct basal, you can test by checking IOB is zero and that you are in-range, eating exactly known carbs, and take an estimated amount of insulin based on current 1/CR. Best is to eat food your normally eat at that time of day and count its carbs precicely.

### Эффект

**Lower CR** = less food per unit, ie you are getting more insulin for a fixed amount of carbs. Can also be called ‘more aggressive’.

**Higher CR** = more food per unit, ie you are getting less insulin for a fixed amount of carbs. Can also be called ‘less aggressive’.

If after meal has digested and IOB has returned to zero, your BG remains higher than before food, chances are CR is too large. Conversely if your BG is lower than before food, CR is too small.

# APS algorithm

## Why does it show "dia:3" in the "OPENAPS AMA"-tab even though I have a different DIA in my profile?

![AMA 3h](../images/Screenshot_AMA3h.png)

In AMA, DIA actually doesn't mean the 'duration of insulin acting'. It is a parameter, which used to connected to the DIA. Now, it means, 'in whích time should the correction be finished'. It has nothing to do with the calculation of the IOB. In OpenAPS SMB, there is no need for this parameter anymore.

## Профиль

### Why using min. 5h DIA (insulin end time) instead of 2-3h?

Well explained in [this article](http://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/). Don't forget to `ACTIVATE PROFILE` after changing your DIA.

### What causes the loop to frequently lower my BG to hypoglycemic values without COB?

First of all, check your basal rate and make a no-carb basal rate test. If it is correct, this behaviour is typically caused by a too low ISF. A too low ISF looks typically like this:

![ISF too low](../images/isf.jpg)

### What causes high postprandial preaks in closed loop?

First of all, check your basal rate and make a no-carb basal rate test. If it is correct and your BG is falling to your target after carbs are fully absorbed, try to set an 'eating soon' temp target in AndroidAPS some time before the meal or think about an appropriate prebolus time with your endocrinologist. If your BG is too high after the meal and still too high after carbs are fully absorbed, think about decreasing your IC with your endocrinologist. If your BG is too high while COB and too low after carbs are fully absorbed, think about increasing your IC and an appropriate prebolus time with your endocrinologist.

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

* уменьшить длительность работы экрана LCD (в меню настроек помпы)
* уменьшить длительность работы подсветки (в меню настроек помпы)
* выберите уведомления в виде звукового сигнала а не вибрации (в меню настроек помпы)
* Нажимайте кнопки помпы только для перезагрузки; для просмотра журналов, уровня батареи и объема резервуара помпы пользуйтесь смартфоном с AndroidAPS.
* На некоторых телефонах AndroidAPS периодически закрывается для экономии энергии или высвобождения оперативной памяти. Когда AndroidAPS вновь инициализируется, то каждом старте устанавливает соединение Bluetooth с помпой и перечитывает текущую базальную скорость и журнал болюсов. Это расходует батарею. Чтобы увидеть, происходит ли это, перейдите в Настройки > NSClient и включите 'Отправлять запуски приложения в NS'. Nightscout будет получать данные о событии при каждом перезапуске AndroidAPS, что облегчит отслеживание проблемы. Чтобы уменьшить расход батареи при таких событиях, в настройках батареи телефона включите AndroidAPS в список разрешенных приложений и тогда монитор расхода энергии перестанет закрывать AAPS.
* протирайте контакты батареи спиртовыми салфетками, чтобы на ней не оставались следы заводской смазки.
* в помпах DanaR/RS процедура запуска батареи отправляет импульс высокого напряжения для устранения заводской пленки (которая предотвращает потерю энергии при хранении), но это не всегда срабатывает на 100%. Либо удалите и заново вставьте батарею 2-3 раза до тех пор, пока на экране помпы заряд батареи не покажет 100%, либо замкните контакты батареи на долю секунды при помощи ключа батареи, чтобы удалить этот налет.
* см. также еще советы для [конкретных типов батареи](../Usage/Accu-Chek-Combo-Tips-for-Basic-usage#battery-type-and-causes-of-short-battery-life) для помпы Combo

### Changing reservoirs and canulas

The change of cartridge can not be done via AndroidAPS, but must be carried out as before directly via the pump.

* Произведите долгое нажатие на кнопку "Открытый цикл"/"Замкнутый цикл" на вкладке "Домашний экран" AndroidAAPS и выберите "Приостановка цикла на 1ч'
* Отключите помпу и замените резервуар в соответствии с инструкцией помпы.
* После переподключения помпы запустите цикл долгим нажатием на 'Приостановлено (X мин.)'.

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

* Деактивировать режим замкнутого цикла и разбираться с диабетом вручную или
* устанавливать высокие временные цели и отключать незапланированный прием пищи UAM, чтобы избежать увеличения активного инсулина IOB из-за непредусмотренной еды или
* переключить профиль на величину, заметно менее 100% 

When drinking alcohol you always have to have an eye on your CGM to manually avoid a hypoglycemia by eating carbs.

### Sleeping

#### How can I loop during the night without mobile and WIFI radiation?

Many users turn the phone into airplane mode at night. If you want the loop to support you when you are sleeping, proceed as follows (this will only work with a local BG-source such as xDrip+ or patched Dexcom app, it will NOT work if you get the BG-readings via nightscout):

1. Включите режим авиаперелета на вашем мобильном устройстве.
2. Подождите, пока режим авиаперелета не будет активирован.
3. Включите Блутус.

You are not receiving calls now, nor are you connected to the internet. But the loop is still running.

### Travelling

#### How to deal with timezone changes?

With DanaR and DanaR Korean you don't have to do anything. For other pumps see [timezone travelling](../Usage/Timezone-traveling.md) page for more details.

## Medical topics

### Hospitalization

If you want to share some information about AndroidAPS and DIY looping with your clinicians, you can print out the [guide to AndroidAPS for clinicians](../Resources/clinician-guide-to-AndroidAPS.md).

### Medical appointment with your endocrinologist

#### Reporting

You can either show your nightscout reports (https://YOUR-NS-SITE.com/report) or check [Nightscout Reporter](https://nightscout-reporter.zreptil.de/)