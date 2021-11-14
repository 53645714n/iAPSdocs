# DanaRS and Dana-i Pump

*다음은 2017년 이후의 다나 RS 펌프를 사용하는 경우에서 앱과 펌프를 설정하기 위한 안내입니다. 만약 오리지널 다나 R 펌프를 사용하는 경우에는 [DanaR Insulin Pump](./DanaR-Insulin-Pump)를 확인하십시오.*

**New Dana RS firmware v3 can be used from AndroidAPS version 2.7 onwards.**

**New Dana-i can be used from AndroidAPS version 3.0 onwards.**

* In DanaRS/i pump "BASAL A" is used by the app. Existing data gets overwritten.

## Pairing pump

* In AndroidAPS go to Config Builder and select 'DanaRS'

* 오른쪽 상단에 있는 점 3개를 눌러 메뉴를 선택하세요. 설정을 선택하세요.

* Click on "Selected pump".
  
  ![AAPS pair Dana RS](../images/AAPS_DanaRSPairing.png)

* **You have to confirm the pairing on the pump!** That's just the way you are used to from other bluetooth pairings (i.e. smartphone and car audio).
  
  ![Dana RS confirmation pairing](../images/DanaRS_Pairing.png)

* -> For DanaRS v1 select Pump password in preferences and set your password

* -> For DanaRS v3 you have to type 2 sequences of numbers and letters displayed on pump to AndroidAPS pairing dialog
* -> For Dana-i standard Android pairing dialog appear and you have to enter 6-digit number displayed on pump

* Select Bolus Speed to change the default bolus speed used (12sec per 1u, 30sec per 1u or 60sec per 1u).

* Set basal step on pump to 0.01 U/h using Doctors menu (see pump user guide)
* Set bolus step on pump to 0.1 U/h using Doctors menu (see pump user guide)
* 펌프에서 확장Bolus를 활성화하세요.

### Default password

* For DanaRS with firmware v1 and v2 the default password is 1234.
* For DanaRS with firmware v3 or Dana-i the default password is a combination of production month and production date (i.e. month 01 and day 24). Open main menu on pump > review > information. Number 3 is production date. For v3/i this password is used only for locking menu on pump. It's not used for communication and it's not necessary to enter it in AndroidAPS.

## Change password on pump

* Press OK button on pump
* In main menu select "OPTION" (move right by pressing arrow button several times)
  
  ![DanaRS Main Menu](../images/DanaRSPW_01_MainMenu.png)

* In options menu select "USER OPTION"
  
  ![DanaRS Option Menu](../images/DanaRSPW_02_OptionMenu.png)

* Use arrow button to scroll down to "11. password"
  
  ![DanaRS 11. Password](../images/DanaRSPW_03_11PW.png)

* Press OK to enter old password.

* Enter **old password** (Default password see [above](#default-password)) and press OK
  
  ![DanaRS Enter old password](../images/DanaRSPW_04_11PWenter.png)

* If wrong password is entered here there will be no message indicating failure!

* Set **new password** (Change numbers with + & - buttons / Move right with arrow button).
  
  ![DanaRS New password](../images/DanaRSPW_05_PWnew.png)

* Confirm with OK button.

* Save by pressing OK button again.
  
  ![DanaRS Save new password](../images/DanaRSPW_06_PWnewSave.png)

* Move down to "14. EXIT" and press OK button.
  
  ![DanaRS Exit](../images/DanaRSPW_07_Exit.png)

## Dana RS specific errors

### Error during insulin delivery

In case the connection between AAPS and Dana RS is lost during bolus insulin delivery (i.e. you walk away from phone while Dana RS is pumping insulin) you will see the following message and hear an alarm sound.

![Alarm insulin delivery](../images/DanaRS_Error_bolus.png)

* In most cases this is just a communication issue and the correct amount of insulin is delivered.
* Check in pump history (either on the pump or through Dana tab > pump history > boluses) if correct bolus is given.
* Delete error entry in [treatments tab](../Getting-Started/Screenshots#carb-correction) if you wish.
* Real amount is read and recorded on next connect. To force this press BT icon on dana tab or just wait for next connect.

## Special note when switching phone

When switching to a new phone the following steps are necessary:

* [Export settings](../Usage/ExportImportSettings#export-settings) on your old phone
* Transfer settings from old to new phone

* DanaRS v1
  
  * **Manually pair** Dana RS with the new phone
  * As pump connection settings are also imported AAPS on your new phone will already "know" the pump and therefore not start a bluetooth scan. Therefore new phone and pump must be paired manually.
  * Install AndroidAPS on the new phone.
  * [Import settings](../Usage/ExportImportSettings#import-settings) on your new phone
* DanaRS v3, Dana-i 
  * start pairing procedure like decribed above
  * sometimes may be necessary to clear pairing information in AndroidAPS by long-click BT icon on DanaRS/i tab

## Timezone traveling with Dana RS pump

For information on traveling across time zones see section [Timezone traveling with pumps](../Usage/Timezone-traveling#danarv2-danars).