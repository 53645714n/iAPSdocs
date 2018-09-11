# AndroidAPS와 호환되는 펌프

AndroidAPS는 현재 다나R, 다나RS 그리고 Combo 펌프에서 동작합니다. 다나R과 Combo 펌프는 출시된 국가에서 구할 수 있고 이미 많은 사람들이 이것들을 사용하고 있으며 다나RS 펌프는 다나R이 업그레이드된 펌프로써 APS를 연동을 위해 좀더 일반적으로 선택되어지고 있습니다. 만약 당신이 업그레이드된 펌프를 선택할 생각이거나 많은 사람들이 선택하는 펌프를 선택하고 싶다면 다나RS 펌프를 선택하면 됩니다. 다양한 판매자의 세부정보는 [이 스프레드시트](https://drive.google.com/open?id=1CRfmmjA-0h_9nkRViP3J9FyflT9eu-a8HeMrhrKzKz0)에 있고 만약 리스트에 없는 정보를 당신이 알고 있다면 공유해 주시기 바랍니다.

Combo 펌프는 연동하기 쉽지는 않지만 loop는 가능합니다.

다나RS 펌프를 선택하면 아래와 같은 장점이 있습니다.

* 수일개발에서 (특정적으로 Loop 사용을 명시하진 않았지만) 스마트폰으로 펌프를 제어해도 보증이 무효화되지는 않는다고 언급했습니다. IME-DC은 보증이 필요할 경우 대체품으로 단지 교환해줄 뿐이고, 문제가 발생한 펌프는 수일개발로 바로 보낸다고 언급했습니다. 따라서 그들은 당신의 Loop 사용여부를 알지도 못합니다. 따라서 현재 다나R과 다나RS는 DIY Loop를 사용하면서도 보증을 받을 수 있는 유일한 펌프입니다. (Roche는 매뉴얼에 언급되지 않은 내용에 대해서는 사용을 제한하고 있습니다.)

* 다나*R/RS 펌프는 Android 5.1 이상의 대부분에 폰에서 연결이 됩니다. 만약 당신의 폰이 고장났다면 다나*R/RS와 연동되는 교체 폰은 쉽게 찾을 수 있습니다. Combo와 연동되는 폰을 찾기는 쉽지 않습니다. (Android 8.1 이상의 폰이 좀 더 대중화되면 바뀔 수도 있습니다)

* Initial pairing is simpler with the Dana* RS. 그러나 일반적으로 이 작업은 한 번만 수행되므로 다른 펌프로 새 기능을 테스트하려는 경우에만 영향을줍니다.

* 지금까지 Combo는 screen parsing으로 동작합니다. 일반적으로 잘 동작하지만 아주 느립니다. Loop를 실행하기 위해서는 백그라운드에서 작업이 수행되는 것이 훨씬 많으므로 이것은 문제가 되지 않습니다. 그렇지만 여전히 블루투스 연결이 끊기거나 했을 때 좀더 많은 시간이 필요하고 bolusing & cooking 등을 할 때 당신이 폰으로 부터 떨어져 있는 경우 쉽지 않은 일입니다.

* Combo는 TBRs의 마지막에 진동이 울리고 다나R은 SMB 상태에서 진동 또는 경고음이 울립니다. 야간에는 SMB보다는 TBRs를 더 많이 사용할 것입니다. 다나RS는 경고음이나 진동 모두 울리지 않게 구성할 수 있습니다.

* RS는 오프라인 상태에서도 몇초 이내에 탄수화물을 비롯한 펌프 이력을 읽은 내용이 폰으로 스위치 가능하고 CGM 값이 들어오자 마자 loop는 진행됩니다.

* AndroidAPS의 모든 펌프들은 주입 중 방수가 된다고 말하고 있습니다. Only the Dana pumps are also "waterproof by warranty" due to the sealed battery compartment and reservoir filling system.

The Combo of course is a very good pump, and loopable. It also has the advantage of many more infusion set types to choose from as it has a standard luer lock. And the battery is a default one you can buy at any gas station, 24 hour convenience store and if you really need one, you can steal/borrow it from the remote control in the hotel room ;-)

Details of the status of other pumps that may have the potential to work with AndroidAPS are listed on the [Future (possible) Pumps](Future-possible-Pump-Drivers.md) page.