# Примечания к изменениям в версиях

Следуйте инструкциям [ в руководстве по обновлению](../Installing-AndroidAPS/Update-to-new-version.md). На ее страницах решаются наиболее распространенные проблемы связанные с обновлениями.

Начиная с версии 2.3 установлена новая процедура обновления. Как только будет доступно новое обновление вы получите следующую информацию:

![Информация об обновлении](../images/AAPS_LoopDisable90days.png)

У вас есть 60 дней для обновления. Если вы не обновитесь в течение 60 дней AAPS войдет в режим LGS (приостановка на низких ГК - см. [глоссарий](../Getting-Started/Glossary.md)), [цель 4](../Usage/Objectives.md).

Если вы не обновитесь еще 30 дней (90 дней с новой даты выпуска) AAPS переключится в режим открытого цикла.

Имейте в виду, что это изменение не предназначено для того, чтобы действовать вам на нервы, а существует по соображениям безопасности. Новые версии AndroidAPS не только обеспечивают новые возможности, но и содержат исправления безопасности. Поэтому необходимо, чтобы каждый пользователь обновлял приложение как можно чаще. К сожалению, все еще поступают сообщения об ошибках из очень старых версий, поэтому это попытка повысить безопасность каждого пользователя и всего сообщества. Благодарим за понимание!

## Version 2.4

Release date: 26-10-2019

### Is this update for me? Currently is NOT supported

* Android 5
* Poctech, 600SeriesUploader, Glimp, Patched Dexcom from 2.3 directory

### Новые возможности

* Internal change of targetSDK to 28 (Android 9), jetpack support
* RxJava2, Okhttp3, Retrofit support
* Old Medtronic pumps support (RileyLink need)
* New Automation plugin
* Allow to bulus only part from bolus wizard calculation
* Rendering insulin activity
* Adjusting IOB predictions by autosense result
* New support for patched Dexcom apks (2.4 folder)
* Signature verifier
* Allow to bypass objectives for OpenAPS users
* New objectives - exam, application handling
* Fixed bug in Dana* drivers where false time difference was reported

## Version 2.3

Release date: 25-04-2019

### Новые возможности

* Important safety fix for Insight (really important if you use Insight!)
* Fix History-Browser
* Fix delta calculations
* Language updates
* Check for GIT and warn on gradle upgrade
* More automatic testing
* Fixing potential crash in AlarmSound Service (thanks @lee-b !)
* Fix broadcast of BG data (works independently of SMS permission now!)
* New Version-Checker

## Version 2.2.2

Release date: 07-04-2019

### Новые возможности

* Autosens fix: deactivate TT raises/lowers target
* New translations
* Insight driver fixes
* SMS plugin fix

## Version 2.2

Release date: 29-03-2019

### Новые возможности

* [DST fix](../Usage/Timezone-traveling#time-adjustment-daylight-savings-time-dst)
* Wear Update
* [SMS plugin](../Usage/SMS-Commands.md) update
* Go back in objectives.
* Stop loop if phone disk is full

## Version 2.1

Release date: 03-03-2019

### Новые возможности

* Accu-Chek [Insight](../Configuration/Accu-Chek-Insight-Pump.md) support (by Tebbe Ubben and JamOrHam)
* Status lights on main screen (Nico Schmitz)
* Daylight saving time helper (Roumen Georgiev)
* Fix processing profile names comming from NS (Johannes Mockenhaupt)
* Fix UI blocking (Johannes Mockenhaupt)
* Support for updated G5 app (Tebbe Ubben and Milos Kozak)
* G6, Poctech, Tomato, Eversense BG source support (Tebbe Ubben and Milos Kozak)
* Fixed disabling SMB from preferences (Johannes Mockenhaupt)

### Misc

* If you are using non default `smbmaxminutes` value you have to setup this value again

## Version 2.0

Release date: 03-11-2018

### Новые возможности

* oref1/SMB support ([oref1 documentation](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html)) Be sure to read the documentation to know what to expect of SMB, how it will behave, what it can achive and how to use it so it can operate smoothly.
* Accu-check Combo pump support ([setup instructions](../Configuration/Accu-Chek-Combo-Pump.md))
* Setup wizard: guides you through the process of setting up AndroidAPS

### Settings to adjust when switching from AMA to SMB

* Objective 8 must be started for SMBs to be enabled (SMB tab generally shows what restrictions apply)
* maxIOB now includes *all* IOB, not just added basal. That is, if given a bolus of 8 U for a meal and maxIOB is 7 U, no SMBs will be delivered until IOB drops below 7 U.
* min_5m_carbimpact default has changed from 3 to 8 going from AMA to SMB. Если вы переходите с AMA на SMB, то вам нужно изменить его вручную
* Note when building AndroidAPS 2.0 apk: Configuration on demand is not supported by the current version of the Android Gradle plugin! Если сборка выполнена с ошибкой, относящейся к "выборочной конфигурации", можно сделать следующее:
  
  * Откройте окно настроек, нажав Файл > Настройки (на Mac, Android Studio > Настройки).
  * В левой панели нажмите Сборка, Выполнение, Развертывание > Компилятор.
  * Снимите флажок с ячейки "выборочная конфигурация".
  * Нажмите Применить или OK.

### Overview tab

* Top ribbon gives access to suspend/disable loop, view/adjust profile and to start/stop temporary targets (TTs). TTs use defaults set in preferences. The new Hypo TT option is a high temp TT to prevent the loop from too aggressively overcorrection rescue carbs.
* Treatment buttons: old treatment button still available, but hidden by default. Visibility of buttons can now be configured. New insulin button, new carbs button (including [eCarbs/extended carbs](../Usage/Extended-Carbs.md))
* Colored prediction lines: 
  * Orange: COB (colour is used generally to represent COB and carbs)
  * Dark blue: IOB (colour is used generally to represent IOB and insulin)
  * Light blue: zero-temp
  * Dark yellow: UAM
* Option to show a notes field in insulin/carbs/calculator/prime+fill dialogs, which are uploaded to NS
* Updated prime/fill dialog allows priming and creating careportal entries for site change and cartridge change

### Watch

* Separate build variant dropped, included in regular full build now. To use bolus controls from watch, enable this setting on the phone
* Wizard now only asks for carbs (and percentage if enabled in watch settings). Which parameters are included in the calculation can be configured in the settings on the phone
* confirmations and info dialogs now work on wear 2.0 as well
* Added eCarbs menu entry

### New plugins

* PocTech app as BG source
* Dexcom patched app as BG source
* oref1 sensitivity plugin

### Misc

* App now uses drawer to show all plugins; plugins selected as visible in config builder are shown as tabs on top (favourites)
* Overhaul for config builder and objectives tabs, adding descriptions
* New app icon
* Lots of improvements and bugfixes
* Nightscout-independant alerts if pump is unreachable for a longer time (e.g. depleted pump battery) and missed BG readings (see *Local alerts* in settings)
* Option to keep screen on
* Option to show notification as Android notification
* Advanced filtering (allowing to always enable SMB and 6h after meals) supported with patched Dexcom app or xDrip with G5 native mode as BG source.