# Обзор компонентов 
==============================================
AndroidAPS - это не просто (самостоятельно собранное) приложение, это один из модулей закрытой системы ИПЖ. Прежде чем выбрать компоненты, было неплохо рассмотреть их также в `комплексе компонентов <https://androidaps.readthedocs.io/en/dev/EN/index.html#component-setup>`_.
   
.. изображение:../images/modules.png
  :alt: Обзор компонентов

.. note:: 
   **ВАЖНОЕ ПРЕДОСТЕРЕЖЕНИЕ**

   Функции безопасности AndroidAPS, описываемые в документации, основываются на возможностях оборудования. В системе "замкнутого цикла" с автоматической дозировкой инсулина допускается использовать только испытанные, работоспособные инсулиновые помпы и системы непрерывного мониторинга глюкозы, которые получили соответствующее разрешение таких зарубежных регуляторов как FDA (США) и CE (Европейский союз). Внесение аппаратных или программных технических изменений в это оборудование может стать причиной неконтролируемого введения инсулина, что может повлечь опасные последствия для пациента. *Не используйте* модифицированные, самодельные или дефектные инсулиновые помпы и/или устройства мониторинга для создания системы AndroidAPS.

   Допустимо использовать только оригинальные, сертифицированные производителем расходные материалы, такие как инсулиновые картриджи, инфузионные наборы, пристреливатели к ним и т. п. Использование непроверенных или модифицированных материалов может вызвать неточность мониторинга и ошибки дозировки инсулина. Инсулин опасен при неверной дозировке - не рискуйте жизнью, пользуясь неумело переделанными компонентами.

Необходимые модули
=====================
Хороший индивидуальный алгоритм дозировки для вашей терапии диабета
------------------
Хотя его нельзя сконструировать или купить, это, вероятно, самый недооцениваемый "модуль", существенно важный для системы. Когда алгоритму доверяется управлять диабетом, следует знать правильные настройки, чтобы не допустить серьезных ошибок.
Даже если у вас еще нет других модулей, вы можете в сотрудничестве с вашим эндокринологом проверить и адаптировать свой профиль. 
Большинство пользователей систем ИПЖ используют циркулярные суточные величины скорости базала (BR), гормональную чувствительность к инсулину ISF и соотношение инсулин-углеводы CR.

Профиль включает

* BR (скорость подачи базового инсулина)
* ISF (коэффициент чувствительности к инсулину) определяет вашу величину понижения ГК в результате введения 1 единицы инсулина
* CR (соотношение инсулин-углеводы) это количество граммов углеводов на единицу инсулина
* DIA (продолжительность действия инсулина).

Телефон
-------
Вам нужен смартфон Android с операционной системой Google Android 6.0 или выше. Пользователи создают `список протестированных телефонов и часов <https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit?usp=sharing>`_

Для того, чтобы включить в список телефон, который не занесен в таблицу, заполните форму <https://docs.google.com/forms/d/e/1FAIpQLScvmuqLTZ7MizuFBoTyVCZXuDb__jnQawEvMYtnnT9RGY6QUw/viewform>.

При обнаружении проблем с таблицей пишите на `hardware@androidaps.org <mailto:hardware@androidaps.org>`_, для отправки телефонов/часов на тестирование пишите по адресу `donations@androidaps.org <mailto:hardware@androidaps.org>`_.

Инулиновая помпа
--------
AndroidAPS **на данный момент** работает с 

- `Accu-Chek Combo <../Configuration/Accu-Chek-Combo-Pump.html>`_ (additionally needed: Ruffy app, LineageOS or Android 8.1 on your phone)
- `Accu-Chek Insight <../Configuration/Accu-Chek-Insight-Pump.html>`_ 
- `DanaR <../Configuration/DanaR-Insulin-Pump.html>`_ 
- `DanaRS <../Configuration/DanaRS-Insulin-Pump.html>`_  
- `some old Medtronic pumps <../Configuration/MedtronicPump.html>`_ from upcoming version 2.4 (additionally needed: RileyLink/Gnarl hardware, Android Phone with bluetooth low energy / BLE-chipset)

**Other pumps** that may have the potential to work with AndroidAPS are listed on the `Future (possible) Pumps <../Getting-Started/Future-possible-Pump-Drivers.html>`_ page.

If you need to **privately buy** a pump then you can find various distributors is in `this spreadsheet <https://drive.google.com/open?id=1CRfmmjA-0h_9nkRViP3J9FyflT9eu-a8HeMrhrKzKz0>`_, please share the details of yours if not already listed.

**So what's the best pump for looping with AndroidAPS?**

The Combo, the Insight and the older Medtronics are solid pumps, and loopable. The Combo has the advantage of many more infusion set types to choose from as it has a standard luer lock. And the battery is a default one you can buy at any gas station, 24 hour convenience store and if you really need one, you can steal/borrow it from the remote control in the hotel room ;-).

The advantages of the DanaR/RS vs. the Combo as the pump of choice however are:

- The Dana*R/RS connects to almost any phone with Android >= 5.1 without the need to flash lineage. If your phone breaks you usually can find easily any phone that works with the Dana*R/RS pumps as quick replacement... С Combo не так просто. (Ситуация может измениться, когда Android 8.1 станет более популярным)
- Initial pairing is simpler with the Dana* RS. Но обычно это делается только один раз, так что это свойство важно, если хотите проверить новую функцию на других помпах.
- So far the Combo works with screen parsing. В целом, это неплохо, но такая работа идет медленно. Для цикла ИПЖ это не имеет значения, так как он работает в фоновом режиме. Still there is much more time you need to be connected so more time where the BT connection might break, which isn't so easy if you walk away from your phone whilst bolusing & cooking. 
- The Combo vibrates on the end of TBRs, the Dana* R vibrates (or beeps) on SMB. В ночное время вы, скорее всего, будете использовать TBR а не SMB.  Dana* RS может быть сконфигурирована так, что не будет ни вибрировать ни пищать.
- Reading the history on the RS in a few seconds with carbs makes it possible to switch phones easily while offline and continue looping as soon a soon as some CGM values are in.
- All pumps AndroidAPS can talk with are waterproof on delivery. Но только помпы Dana также "гарантированно водонепроницаемы" благодаря изолированным отсекам батареи и системы наполнения резервуара. 

Источник данных гликемии
------------
This is just a short overview of all compatible CGMs/FGM with AndroidAPS. For further details, look `here <../Configuration/BG-Source.html>`_. Just a short hint: if you can display your glucose data in xDrip+ app or Nightscout website, you can choose xDrip+ (or Nightscout with web connection) as BG source in AAPS.

* Dexcom G4: These sensors are quite old, but you can find instructions on how to use them with xDrip+ app
* Dexcom G5: It works with xDrip+ app or patched Dexcom app
* Dexcom G6: It works with xDrip+ app or patched Dexcom app
* Libre 1: You need a transmitter like Bluecon or MiaoMiao for it (build or buy) and xDrip+ app
* Libre 2: It works with xDrip+ (no transmitter needed), but you have to build your own patched app (see `these instructions <https://github.com/user987654321resu/Libre2-patched-App>`_ for more details)
* Eversense: It works so far only in combination with ESEL app and a patched Eversense-App (works not with Dana RS and LineageOS, but DanaRS and Android or Combo and Lineage OS work fine)
* Enlite: quite complicated with a lot of extra stuff


Nightscout
------------
Nightscout is a open source web application that can log and display your CGM data and AndroidAPS data and creates reports. You can find more information on the `website of the Nightscout project <http://www.nightscout.info/>`_. You can create your own Nightscout website `using Heroko <http://www.nightscout.info/wiki/welcome/set-up-nightscout-using-heroku>`_, use the semi-automated Nightscout setup on `zehn.be <https://ns.10be.de/en/index.html>`_ or host it on your own server (this is for IT experts).

Nightscout is independent of the other modules. You will need it to fulfill Objective 1.

Additional information on how to configure Nightscout for use with AndroidAPS can be found `here <../Installing-AndroidAPS/Nightscout.html>`_.

AAPS-.apk file
---------------
The basic component of the system. Before installing the app, you have to build the apk-file (which is the filename extension for an Android App) first. Instructions are  `here <../Installing-AndroidAPS/Building-APK.html>`_.  

Optional Modules
==================
Смарт часы
---------------
You can choose any smartwatch with Android Wear 1.x and above. Most loopers wear a Sony Smartwatch 3 (SWR50) as it is the only watch that can get readings from Dexcom G5/G5 when phone is out of range. Some other watches can be patched to work as a standalone receiver as well (see `this documentation <https://github.com/NightscoutFoundation/xDrip/wiki/Patching-Android-Wear-devices-for-use-with-the-G5>`_ for more details).

Users are creating a `list of tested phones and watches <https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit?usp=sharing>`_. There are different watchfaces for use with AndroidAPS, which you can find `here <../Configuration/Watchfaces.html>`_.

Для того, чтобы включить в список телефон, который не занесен в таблицу, заполните форму <https://docs.google.com/forms/d/e/1FAIpQLScvmuqLTZ7MizuFBoTyVCZXuDb__jnQawEvMYtnnT9RGY6QUw/viewform>.

При обнаружении проблем с таблицей пишите на `hardware@androidaps.org <mailto:hardware@androidaps.org>`_, для отправки телефонов/часов на тестирование пишите по адресу `donations@androidaps.org <mailto:hardware@androidaps.org>`_.

xDrip +
-------
Even if you don't need to have the xDrip+ App as BG Source, you can still use it for i.e. alarms or a good blood glucose display. You can have as many as alarms as you want, specify the time when the alarm should be active, if it can override silent mode, etc. Some xDrip+ information can be found `here <../Configuration/xdrip.html>`_. Please be aware that the documentations to this app are not always up to date as its progress is quite fast.

Пример настройки
============
If you want to get a step by step example, you might want to look at a sample setup. The first sample setup is quite old, but should be still up-to-date.

.. toctree::
   :maxdepth: 1
   :glob:
   
   Sample Setup <../Getting-Started/Sample-Setup.html>
 
  
What to do while waiting for modules
============================================
It sometimes takes a while to get all modules for closing the loop. But no worries, there are a lot of things you can do while waiting. It is NECESSARY to check and (where approporiate) adapt basal rates (BR), insulin-carbration (IC), insulin-sensitivity-factors (ISF) etc. And maybe open loop can be a good way to test the system and get familiar with AndroidAPS. Using this mode, AndroidAPS gives treatment advices you can manually execute.

You can keep on reading through the docs here, get in touch with other loopers online or offline, `read <https://androidaps.readthedocs.io/en/dev/EN/Where-To-Go-For-Help/Background-reading.html>`_ documentations or what other loopers write (even if you have to be careful, not everything is correct or good for you to reproduce).

**Done?**
If you have your AAPS components all together (congrats!) or at least enough to start in open loop mode, you should first read through the `Objective description <../Usage/Objectives.html>`_ before each new Objective and setup up your `hardware <../index.html#component-setup>`_.
