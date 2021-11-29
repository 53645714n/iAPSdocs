# Обновление до новой версии или ветки

## Постройте сами вместо того, чтобы загружать

**AndroidAPS недоступен для скачивания из-за законодательства, касающегося медицинских устройств. Построить приложение для собственного использования вполне законно, но вам не разрешается передавать копию другим! См. раздел [ FAQ ](../Getting-Started/FAQ.md).**

## Важные Примечания

* Пожалуйста, обновите приложение сразу же после выхода новой версии. Вы получите информацию о новой версии [ на главном экране AndroidAPS ](../Installing-AndroidAPS/Releasenotes#release-notes).
* Начиная с версии 2.3 для обновления требуется использовать git. Обновление с zip-файла больше не работает.
* Начиная с версии 2.7 местоположение репозитория изменено на <https://github.com/nightscout/AndroidAPS>. Если вы не знакомы с Git самый простой способ обновления- удалить каталог с AndroidAPS и [ клонировать заново](../Installing-AndroidAPS/Building-APK.md).
* Используйте [](https://developer.android.com/studio/) Android Studio версии 4.1.1 или новее для построения apk.
* [Windows 10 для 32-разрядных систем](../Installing-AndroidAPS/troubleshooting_androidstudio#unable-to-start-daemon-process) не поддерживается в Android Studio 4.1.1.
* Если вы используете xDrip, [identify the receiver](../Configuration/xdrip#identify-receiver).
* You can also use Dexcom G6 with the ['Build your own Dexcom App'](../Hardware/DexcomG6.html#if-using-g6-with-build-your-own-dexcom-app).

## Пошаговая инструкция для опытных пользователей

Пропустите этот раздел, если обновляете в первый раз. Пошаговая инструкция для опытных пользователей. Следующим шагом будет [ установить git ](../Installing-AndroidAPS/git-install.rst), если у вас его еще нет.

Если вы уже обновили AAPS в предыдущих версиях и используете Windows PC, то можете обновить приложение в четыре простых шага:

1. [ Экспортируйте параметры ](../Usage/ExportImportSettings#export-settings) из существующей версии AAPS на вашем телефоне, чтобы обезопасить себя
2. [ Обновите локальную копию ](../Installing-AndroidAPS/Update-to-new-version#update-your-local-copy) (VCS-> Git-> Pull)
3. [ Создайте подписанное APK ](../Installing-AndroidAPS/Update-to-new-version#generate-signed-apk) (Выберите 'app', а не 'wear' на своем пути!)
4. Depending on your [BG source](../Configuration/BG-Source.rst) make sure to [identify receiver](../Configuration/xdrip#identify-receiver) in xDrip or use the ['Build your own Dexcom App'](../Hardware/DexcomG6.html#if-using-g6-with-build-your-own-dexcom-app).

## Установите git (если у вас его нет)

Следуйте инструкциям на странице установки [git](../Installing-AndroidAPS/git-install.rst).

## Обновите свою локальную копию

* Начиная с версии 2.7 местоположение репозитория изменено на <https://github.com/nightscout/AndroidAPS>. Если вы не знакомы с Git самый простой способ обновления- удалить каталог с AndroidAPS и [ клонировать заново](../Installing-AndroidAPS/Building-APK.md).
* Выберите: VCS-> Git-> Pull
    
    ![Android Studio-GIT-Pull](../images/AndroidStudio361_Update01.png)

* Нажмите кнопку Pull (без изменений в диалоговом окне)
    
    ![Android Studio-GIT-Pull 2](../images/AndroidStudio361_Update02a.png)

* Подождите, пока выполняется загрузка.
    
    ![Android Studio-извлечение выполняется](../images/AndroidStudio361_Update03.png)

* По завершении Android Studio сообщит вам, что "все файлы актуальны".
    
    ![Все файлы в актуальном состоянии](../images/AndroidStudio361_Update04.png)

## Создание подписанного APK

<!--- Text is maintained in page building-apk.md --->

* Нажмите "Build" в строке меню и выберите "Generate Signed Bundle / APK...".

![Построение apk](изображение::../images/AndroidStudio361_27.png)

* Выберите "APK" (1.) вместо "Android App Bundle" и нажмите кнопку "Далее" (2.).

![Apk вместо пакета](изображение::../images/AndroidStudio361_28.png)

* Убедитесь, что модуль имеет значение "app".
* Выберите путь к хранилищу ключей, нажав кнопку "Выбрать существующую...".
* Введите пароли для хранилища ключей и ключа.
* Если установлен флажок запомнить пароли, вам не придется их вводить. В том случае, если этот переключатель не был включен во время последней компоновки, и вы не можете запомнить эти пароли, обратитесь к разделу [ Устранение неполадок ](../Installing-AndroidAPS/troubleshooting_androidstudio#lost-keystore).
* Нажмите "Далее".

![Хранилище ключей](../images/AndroidStudio361_Update05.png)

* Выберите вариант компоновки "fullRelease" (1.). 
* Отметьте флажки V1 и V2 для подписи версий (2.).
* Нажмите ``Finish``. (3.)

![Завершение сборки](изображение::../images/AndroidStudio361_32.png)

* После завершения сборки Android Studio покажет информацию "APK (s) сгенерировано успешно ...".
* В случае, если сборка не удалась, обратитесь к разделу [поиск и устранение неисправностей ](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).
* Самый простой способ найти apk это нажать на кнопку "журнал событий".

![Построено успешно - журнал событий](изображение::../images/AndroidStudio361_33.png)

* В секции журнала событий нажмите «locate».

![Журнал событий - обнаружить apk](изображение::../images/AndroidStudio361_34.png)

* app-full-release.apk это файл, который вы ищете.

![Расположение файла apk](изображение::../images/AndroidStudio361_35.png)

## Перенос приложения на смартфон

Самый простой способ перенести приложение на ваш телефон - [через кабель USB или Google Drive](https://support.google.com/android/answer/9064445?hl=en). Обратите внимание, что передача по почте может вызвать трудности и не является предпочтительным способом.

На вашем телефоне необходимо разрешить установку из неизвестных источников. Инструкции, как это сделать, можно найти в интернете (например [здесь](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) или [здесь](https://www.androidcentral.com/unknown-sources)).

## Проверить версию AAPS на телефоне

Вы можете проверить версию AAPS на вашем телефоне, нажав на меню трех точек сверху справа "о приложении".

![Версия AAPS установлена](../images/Update_VersionCheck.p)

## Устранение неполадок

См. отдельную страницу [ устранение неполадок Android Studio ](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).