# Freestyle Libre 1

Чтобы использовать Libre в качестве постоянного мониторинга, который получает новые значения гликемии каждые 5 минут, нужно сначала приобрести один из адаптеров NFC - Bluetooth:

- MiaoMiao Reader (версия 1 или 2) [https://www.miaomiao.cool/](https://www.miaomiao.cool/)
- Blucon Nightrider [https://www.ambrosiasys.com/our-products/blucon/](https://www.ambrosiasys.com/our-products/blucon/)
- Bubble [https://bubbleshop.eu/](https://bubbleshop.eu/)  или для русских пользователей  [https://vk.com/saharmonitor/](https://vk.com/saharmonitor/)

Кроме того, можно использовать специальные часы, Sony Smartwatch 3, имеющие чип NFC, который можно включить и использовать как коллектор NFC. Однако перечисленные выше пользовательские NFC адаптеры Bluetooth предлагают менее сложное решение и будут использоваться большинством желающих использовать свой Libre 1 в качестве CGM.

- Sony Smartwatch 3 (SWR50) [https://github.com/pimpimmi/LibreAlarm/wiki/](https://github.com/pimpimmi/LibreAlarm/wiki/)

В настоящее время, если Libre 1 используется в качестве источника ГК, в рамках SMB алгоритма невозможно активировать «Включать SMB всегда» и «Включить SMB после приема углеводов». Значения BG Libre 1 недостаточно ровные, чтобы использовать их безопасно. Подробнее см. в `Выравнивание данных мониторинга <../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md>`.

## При использовании xdrip+

- Если это еще не сделано, скачайте xdrip+ и следуйте инструкциям [LimiTTEer](https://github.com/JoernL/LimiTTer) или  [Libre Alarm](https://github.com/pimpimmi/LibreAlarm/wiki).

В xdrip перейдите в настройки > совместимость программ >локальная трансляция данных и выберите Включить (ON).
В xdrip+ перейдите в настройки > совместимость программ > принимать назначения (Accept treatments) и выберите ВЫКЛ (OFF).
Если хотите, чтобы AndroidAPS мог калибровать показания гликемии, в xdrip + перейдите в настройки > совместимость приложений > принимать калибровки (Accept calibrations) и выберите ВКЛ (ON).  Возможно вы также захотите рассмотреть варианты калибровки в настройках > менее распространенные параметры > дополнительные параметры калибровки.
В конфигуратоге (настройки AndroidAPS) выберите xdrip+.
\* Настройте параметры в xDrip+ в соответствии со страницей настроек [xDrip+ со снимками экрана](../Configuration/xdrip.md). Существует раздел базовых настроек xDrip+ и для параметров Freestyle Libre xDrip+.
Если AAPS не получает значения ГК, когда телефон находится в режиме авиаперелета пользуйтесь функцией "Идентифицировать приемник" в соответствии с описанием на странице настроек [xDrip+](../Configuration/xdrip.md).

## При использовании Glimp

- Вам понадобится Glimp версии 4.15.57 или выше. Более старые версии не поддерживаются.
- Если это еще не сделано, скачайте Glimp и следуйте инструкциям \<<https://nightscout.github.io/uploader/setup/#glimp>>Nightscout\`\_.

В конфигураторе (настройки AndroidAPS) выберите Glimp.
