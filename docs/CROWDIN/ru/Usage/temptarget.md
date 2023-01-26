# Временные цели

## Что такое временные цели и где можно задать и сконфигурировать их?

С помощью "Временной цели" (TT) можно изменить целевое значение уровня глюкозы в крови на определенный период времени. Так как временные цели в основном нужны при нагрузке, гипогликемии (углеводы на купирование) или приближающемся приеме пищи, можно установить некоторые из них по умолчанию. Чтобы их сконфигурировать, перейдите в меню в правом углу сверху и выберите Настройки-> Другое-> Временные цели по умолчанию.

![Задать временные цели по умолчанию](../images/TempTarget_Default.png)

Чтобы активировать одну из "Предустановленных временных целей TT", следует долго нажать на кнопку целевых значений в правом углу главного окна и выбрать Ожидаемый прием пищи, Нагрузка или Гипо или использовать соответствующие ярлыки в оранжевой кнопке "Углеводы". To manually set a [“Custom Temp-Target”](../Usage/temptarget.md#custom-temp-target) (BG value and/or duration), short click on your target in the top right corner or use the “Temporary Target“ button in the [actions tab / menu](../Configuration/Config-Builder#actions).

![Начать врем цель](../images/TempTarget_Set2.png)

- Если вы хотите немного отрегулировать значения временной цели по умолчанию, вы можете долго нажать на кнопку Ожидаемый прием пищи, Действия или Hypo и затем отредактировать значения в полях Цель или Продолжительность.
- Если запущена временная цель, в диалоговом окне появится дополнительная кнопка "Отмена", чтобы отменить ее

## Временная цель Гипо 

Можно считать ее наиболее важной временной целью. На это есть несколько причин:

1. Когда гликемия чрезмерно понижается: Обычно, алгоритм AAPS должен сам справиться с этим, но иногда вам виднее, а цикл ИПЖ будет реагировать быстрее, если он нацелен на более высокое значение глюкозы в крови.
2. Когда вы принимаете углеводы для купирования гипогликемии, уровень глюкозы в крови будет расти очень быстро. Алгоритм AAPS будет стремиться устранить подъем или давать микроболюсы SMB (если активированы). Временная цель Гипо может корректировать ситуацию. 
3. (advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb)): You can enable “High Temp-Targets raises sensitivity” for Temp-Targets of 100mg/dl or 5.5mmol/l or higher in OpenAPS SMB, so AndroidAPS is more sensitive.
4. (advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb)): You can deactivate “SMB with high temp target”, so that even if you have COB > 0, "SMB with Temp-Target" or "SMB always" enabled and OpenAPS SMB active, AndroidAPS won’t give SMBs while high temp targets are active.

Примечание: если вы вводите углеводы с помощью кнопки углеводы, а уровень глюкозы в крови меньше 72мг/дл или 4ммоль/л, то автоматически включается временная цель Гипо.

## Временная цель Нагрузка

До и во время нагрузки, можно установить более высокую цель, чтобы предотвратить гипогликемию. Чтобы упростить настройку временной цели, можно сконфигурировать значение временной цели "Нагрузка (Activity)" по умолчанию. На основе DIA, IOB и вашего опыта можно задать TT перед нагрузкой. See also [sports section in FAQ](../Getting-Started/FAQ.md#sports).

Advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb): The advantages about “Activity Temp-Target”, is that you can enable “High Temp-Targets raises sensitivity” for Temp-Targets higher or equal 100mg/dl or 5.5mmol/L in OpenAPS SMB. В этом случае чувствительность AndroidAPS повышается. Некоторые пользователи вместо этого переключают профиль до/во время временной цели Нагрузка, но у всех все по-разному. Если "микроболюсы SMB деактивированы при высоких временных целях TT" AndroidAPS не будет выполнять SMB, даже с активными углеводами COB > 0, включенными "SMB при временных целях", "SMB всегда " и активированными микроболюсами OpenAPS SMB.

## Временная цель Ожидаемый прием пищи

Если вы знаете, что в ближайшее время вас ожидает прием пищи, можно включить эту временную цель, чтобы активный инсулин IOB уже начал работать перед едой. Особенно для тех, кто не ставит преболюсы, такая установка позволит привести глюкозу крови к более низкому значению. Подробнее об "Ожидаемом приеме пищи" можно прочитать в статье [ How to do "eating soon" mode ' ](https://diyps.org/2015/03/26/how-to-do-eating-soon-mode-diyps-lessons-learned/) или [ здесь ](https://diyps.org/tag/eating-soon-mode/).

Advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb): If you use OpenAPS SMB and have “Low temptarget lowers sensitivity”, AndroidAPS works a little bit more aggressive. Для этой опции требуется значение временной цели TT менее 100мг/дл или 5,5 ммоль/л.

## Настраиваемая временная цель

Иногда требуется временная цель, отличная от дефолтных. Ее можно задать, нажав на целевой диапазон в правом углу главного экрана или на вкладке "Действия".

![Установить временные цели через вкладку Действия](../images/TempTarget_ActionTab.png)