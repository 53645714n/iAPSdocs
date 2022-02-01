# Construire l'APK

## Construire vous-même au lieu de télécharger

**AndroidAPS is not available as download due to regulation for medical devices. It is legal to build the app for your own use, but you must not give a copy to others! Voir la [page FAQ](../Getting-Started/FAQ.md) pour plus de détails.**

## Remarques importantes

* Utilisez **[Android Studio Version 2020.3.1](https://developer.android.com/studio/)** ou une version plus récente pour construire l'apk.
* [Les systèmes d'exploitation Windows 10 32 bits](../Installing-AndroidAPS/troubleshooting_androidstudio#unable-to-start-daemon-process) ne sont pas pris en charge par Android Studio 2020.3.1

## Configuration recommandée de l'ordinateur pour construire un fichier apk

<table class="tg">
  
<thead>
  <tr>
    <th class="tg-baqh">OS (Only 64 bit)</th>
    <th class="tg-baqh">Windows 8 ou supérieur</th>
    <th class="tg-baqh">Mac OS 10.14 ou supérieur</th>
    <th class="tg-baqh">N'importe quel Linux prend en charge Gnome, KDE, ou Unity DE;&nbsp;&nbsp;GNU C Library 2.31 ou ultérieure</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-baqh"><p align="center">CPU (Only 64 bit)</td>
    <td class="tg-baqh">architecture processeur x86_64 ; Core Intel de 2ème génération ou plus récente, ou processeur AMD prenant en charge un <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-windows" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Hypervisor Windows</span></a></td>
    <td class="tg-baqh">Intel Core de 2ème génération ou plus récente, ou processeur AMD prenant en charge un <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-mac" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Hypervisor.Framework</span></a></td>
    <td class="tg-baqh">architecture du processeur x86_64, Intel Core de 2ème génération ou plus récent ou processeur AMD avec support pour la virtualisation AMD (AMD-V) et SSSE3</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">RAM</td>
    <td class="tg-baqh" colspan="3"><p align="center">8GB or more</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Disque</td>
    <td class="tg-baqh" colspan="3"><p align="center">Au moins 30 Go d'espace libre. Un SSD est recommandé.</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Résolution</td>
    <td class="tg-baqh" colspan="3"><p align="center">Minimum 1280 x 800 <br></td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Internet</td>
    <td class="tg-baqh" colspan="3"><p align="center">Haut débit</td>
  </tr>
</tbody>
</table>

Please be in mind that both **64 bit CPU and 64 bit OS are mandatory condition.** If your system DOES NOT meet this condition, you have to change affected hardware or software or the whole system. **It is strongly recommended to use SSD (Solid State Disk) instead of HDD (Hard Disk Drive) because it will take less time when you are building the APS installation apk file.** Recommended is just recommended and it is not a mandatory. However, you may still use a HDD when you are building apk file but note that the building process can take a long time to complete, although once started, you can leave it running unattended.

* * *

### Cet article est divisé en deux parties.

* In the overview part there is an explanation on what steps are necessary to build the APK file.
* In the step by step walkthrough part you will find the screenshots of a concrete installation. Because the versions of Android Studio - the software development environment which we will use to build the APK - will change very quickly this will be not identical to your installation but it should give you a good starting point. Android Studio also runs on Windows, Mac OS X and Linux and there might be small differences in some aspects between each platform. If you find that something important is wrong or missing, please inform the facebook group "AndroidAPS users" or in the Discord chat [Android APS](https://discord.gg/4fQUWHZ4Mw) so that we can have a look at this.

## Aperçu

In general, the steps necessary to build the APK file:

1. [Installer Git](../Installing-AndroidAPS/git-install.rst)
2. [Installer Android Studio](../Installing-AndroidAPS/Building-APK#installez-android-studio)
3. [Définir le chemin d’accès git dans Android Studio](../Installing-AndroidAPS/Building-APK#definir-le-chemin-de-git-dans-les-preferences)
4. [Télécharger le code AndroidAPS](../Installing-AndroidAPS/Building-APK#telecharger-le-code-androidaps)
5. [Télécharger Android SDK](../Installing-AndroidAPS/Building-APK#telecharger-android-sdk)
6. [Générer l'application](../Installing-AndroidAPS/Building-APK#generer-un-apk-signe) (générer un fichier apk signé)
7. [Transférer le fichier apk sur votre téléphone](../Installing-AndroidAPS/Building-APK#transferer-le-fichier-apk-sur-le-smartphone)
8. [Identifier le récepteur si vous utilisez xDrip+](..//Configuration/xdrip#identify-receiver-if-using-xdrip)

## Démarche pas à pas

Detailed description of the steps necessary to build the APK file.

## Installer git (si vous ne l'avez pas)

Suivez le manuel sur la [page d'installation de git](../Installing-AndroidAPS/git-install.rst).

## Installer Android Studio

The following screenshots have been taken from Android Studio Version Arctic Fox | 2020.3.1. Screens can change in future versions of Android Studio. But you should be able to find your way through. [Help from the community](../Where-To-Go-For-Help/Connect-with-other-users.md) is provided.

One of the most important things when installing Android Studio: **Be patient!** During installation and setup Android Studio is downloading a lot of stuff which will take its time.

Download [Android Studio from here](https://developer.android.com/studio/install.html) and install it on your computer.

On first start you will find the setup wizard:

Select "Do not import settings" as you have not used it before.

![Do not import settings](../images/studioSetup/01_ImportSettings.png)

Décidez si vous voulez partager les données avec Google ou non.

![Partager des données avec Google](../images/studioSetup/02_DataSharing.png)

Dans l'écran suivant, cliquez sur "Next".

![Écran d'accueil](../images/studioSetup/03_Welcome.png)

Sélectionnez l'installation "Standard" et cliquez sur "Next".

![Installation standard](../images/studioSetup/04_InstallType.png)

Sélectionnez le thème de l'interface utilisateur que vous souhaitez (dans ce manuel, nous avons utilisé "Light"). Cliquez ensuite sur "Next".

> ***Note:*** This is just the color scheme. You can select whatever you like (i.e. "Darcula" for dark mode). This selection has no influence on building the APK but the following screenshots might look different.

![Couleur de l'interface](../images/studioSetup/05_UITheme.png)

Cliquez sur "Finish" dans la boite de dialogue "Verify Settings".

![Vérifiez les paramètres](../images/studioSetup/06_Verify.png)

Attendez qu'Android Studio télécharge des composants supplémentaires et soyez patient. Une fois que tout est téléchargé, le bouton "Finish" devient bleu. Cliquez sur le bouton maintenant.

![Téléchargement des composants](../images/studioSetup/07_Downloading.png)

## Définir le chemin de git dans les préférences

Make sure [git is installed](../Installing-AndroidAPS/git-install.rst) on your computer and you have restarted your computer after installing.

On the Android Studio welcome screen click "Customize" (1) on the left and then select the link "All settings..." (2):

![Paramètres Android Studio à partir de l'écran d'accueil](../images/studioSetup/10_WizardSettings.png)

### Windows

* As windows user, make sure you have restarted your computer after [installing Git](../Installing-AndroidAPS/git-install.rst).

* Double-click "Version Control" (1) to open the sub-menu.

* Cliquez sur Git (2).
* Make sure update method "Merge" (3) is selected.
* Vérifiez si Android Studio peut localiser le chemin d'accès à git.exe automatiquement en cliquant sur le bouton "Test" (4).
    
    ![Paramètres Android Studio](../images/studioSetup/11_GitPath.png)

* If automatic setting is successful git version will be displayed next to the path.
    
    ![Git version displayed](../images/studioSetup/12_GitVersion.png)

* Eventually git.exe cannot be found automatically or the Test will result in an error (1):
    
    ![Git not found](../images/studioSetup/13_GitVersionError.png)
    
    In this case click on the folder icon (2).

* Use [search function](https://www.tenforums.com/tutorials/94452-search-file-explorer-windows-10-a.html) in windows explorer to find "git.exe" if you are unsure where git has been installed. You are looking for a file named "git.exe", located in **\bin** folder.

* Select path to git.exe and make sure you selected the one in ** \bin\ ** folder (3) and click "OK" (4).
    
    ![Select git manually](../images/studioSetup/14_GitManualSelection.png)

* Check your selected git path again with the "Test" button as described above.

* When the git version is displayed next to the path (see screenshot above), close settings window by clicking "OK" button (5).

### Mac

* N’importe quelle version de git devrait fonctionner. Par exemple <https://git-scm.com/download/mac>.
* Utilisez homebrew pour installer git: ```$ brew install git```.
* Pour plus de détails sur l'installation de git, voir la [documentation officielle](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* Si vous installez git via homebrew, il n'est pas nécessaire de modifier les préférences. Juste au cas où : on peut y accéder ici : Android Studio - Preferences.

## Télécharger le code AndroidAPS

* On the Android Studio welcome screen select "Projects" (1) on the left and then "Get from VCS" (2).
    
    ![Android Studio wizard](../images/studioSetup/20_ProjectVCS.png)
    
    * If you already opened Android Studio and do not see the welcome screen anymore select File (1) > New (2) > Project from Version Control... (3)
        
        ![Charger le projet à partir du contrôle de version dans Android Studio](../images/AndroidStudio_FileNew.PNG)
    
    * We will now tell Android Studio were to get the code from:
    
    * Make sure you have selected "Repository URL" on the left (1).
    
    * Check if "Git" is selected as version control (2).
    * Copy and paste the URL ```https://github.com/nightscout/AndroidAPS``` to the main AndroidAPS repository into the URL textbox (3).
    * Choose the directory where you want to save the cloned code (4).
        
        ![Clone Git](../images/studioSetup/21_CloneURL.png)

* Cliquez sur le bouton "Clone" (5).
    
    ![Cloner le répertoire](../images/studioSetup/22_Cloning.png)

* Ne cliquez pas sur "Background" pendant que le répertoire est cloné !

* After the repository is cloned successfully, Android Studio will open the cloned project.

* You will be asked whether you want to trust the project. Click on "Trust project"!
    
    ![Trust project](../images/studioSetup/23_TrustProject.png)

* In the status bar at the bottom you will see the information that Android Studio is running background tasks.
    
    ![Tâches d'arrière-plan](../images/studioSetup/24_GradleSyncRunning.png)

* Accorder l'accès si votre pare-feu demande l'autorisation.
    
    ![Autorisation java dans le pare-feu](../images/AndroidStudio361_18.png)

* Once the background tasks are finished you will probably see an error saying that errors occurred (1) or (2) or (3).
    
    ![Licence SDK](../images/studioSetup/25_SyncFailed.png)
    
    Don't worry, this will be solved soon!

## Télécharger Android SDK

* In the menu, go to File (1) > Settings (2).
    
    ![Ouvrir les paramètres](../images/studioSetup/30_Settings.png)

* Double-click on Appearance & Behaviour to open its submenu (1).

* Double-click on System Settings (2) and select Android SDK (3).
* Tick the box left of "Android 9.0 (Pie)" (4) (API Level 28).
    
    ![Paramètres SDK](../images/studioSetup/31_AndroidSDK.png)

* Confirmez les modifications en cliquant sur OK.
    
    ![Confirmer les modifications SDK](../images/studioSetup/32_ConfirmSDK.png)

* Accept licence agreement (1) and click "Next" (2).
    
    ![Accepter la licence SDK](../images/studioSetup/33_ConfirmLicense.png)

* Wait until the SDK download and installation is finished.
    
    ![Attendre lors de l'installation du SDK](../images/studioSetup/34_DownloadSDK.png)

* Lorsque l'installation du SDK est terminée, le bouton "Finish" devient bleu. Cliquez sur ce bouton.
    
    ![Terminer l'installation du SDK](../images/studioSetup/35_DownloadSDKfinished.png)

* Android Studio recommande de mettre à jour le "gradle system". **Never update gradle!** This will lead to difficulties!

* If you see an information on the lower right side of your Android Studio window that Android Gradle Plugin is ready to update click on the text "update" (1).
    
    ![No gradle update](../images/studioSetup/36_GradleUpdateRequest.png)

* In the dialog box the select "Don't remind me again for this project" (2).
    
    ![No gradle update](../images/studioSetup/37_GradleUpdateDeny.png)

* Restart Android Studio before you continue.

## Générer un APK signé

Signer signifie que vous signez votre application générée mais d'une façon numérique comme une sorte d'empreinte digitale intégrée dans l'application elle-même. C'est nécessaire car Android a une règle qui impose de n'accepter que du code signé pour des raisons de sécurité. Pour plus d'informations sur ce sujet, suivez [ce lien](https://developer.android.com/studio/publish/app-signing.html#generate-key).

* After Android Studio is started, wait until all background tasks are finished.
    
    ![Wait for background tasks](../images/studioSetup/40_BackgroundTasks.png)
    
    * ***Warning:*** If errors occur, do not continue with the following steps. \ Consult the [troubleshooting section](../Installing-AndroidAPS/troubleshooting_androidstudio.rst) for known problems!
    
    ![Gradle Sync Error](../images/studioSetup/41_GradleSyncError.png)

* Click "Build" (1) in the menu bar and select "Generate Signed Bundle / APK..." (2).
    
    ![Génération de l'apk](../images/studioSetup/42_MenuBuild.png)

* Select "APK" (1) instead of "Android App Bundle" and click "Next" (2).
    
    ![APK au lieu du bundle](../images/studioSetup/43_Apk.png)

* Make sure that module is set to "AndroidAPS.app" (1).

* Click "Create new..." (2) to start creating your key store.
    
    ***Note:*** A key store in this case is nothing more than a file in which the information for signing is stored. Il est crypté et les informations sont sécurisées avec des mots de passe.
    
    ![Créer le fichier de clés](../images/studioSetup/44_KeystoreNew.png)

* Click the folder symbol to select a path on your computer for your key store.
    
    ![Créer le fichier de clés](../images/studioSetup/45_KeystoreDialog.png)

* Sélectionnez le répertoire dans lequel votre fichier de clés doit être sauvé (1).
    
    ![Créer le fichier de clés](../images/studioSetup/46_KeystorePath.png)
    
    ***Warning: Do not save in same folder as project. You must use a different directory!*** A good location would be your home folder.

* Type a file name for your key store (2) and confirm with "OK" (3).

* Enter (2) and confirm (3) the password for your key store. ![Select key store path](../images/studioSetup/47_KeystoreDialog.png)
    
    ***Note:*** Passwords for key store and key do not have to be very sophisticated. Make sure to remember those or make a note in a safe place. In case you will not remember your passwords in the future, see [troubleshooting for lost key store](../Installing-AndroidAPS/troubleshooting_androidstudio#lost-keystore).

* Enter an alias (4) for your key. Choose whatever you like.

* Enter (5) and confirm (6) the password for your key

* Validity (7) is 25 years by default. You do not have to change the default value.

* First and last name must be entered (8). All other information is optional.

* Click "OK" (9) when you are done.

* Make sure the box to remember passwords is checked (1). So you don't have to enter them again next time you build the apk (i.e. when updating to a new AndroidAPS version).

* Click "Next" (2).
    
    ![Remember passwords](../images/studioSetup/48_KeystoreSave.png)

* Select build variant "fullRelease" (1) and press "Finish".
    
    ![Select build variant](../images/studioSetup/49_BuildVariant.png)

* Android Studio will show "Gradle Build running" at the bottom. This takes some time, depending on your computer and internet connection. **Be patient!**
    
    ![Gradle Running](../images/studioSetup/50_GradleRunning.png)

* Android Studio will display the information "Generate Signed APK" after build is finished.
    
    ![Build finished](../images/studioSetup/51_BuildFinished.png)

* Dans le cas ou la génération n'a pas réussie, référez vous à la [section dépannage](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).

* Click on the notification to expand it.

* Click on the link "locate".
    
    ![Locate build](../images/studioSetup/52_BuildLocate.png)
    
    * If the notification is gone, you can always open the "Event log" and select the same link there. ![Génération réussie - journal des événements](../images/studioSetup/53_EventLog.png)

* Your file manager/explorer will open. Navigate to the directory "full" (1) > "release" (2).
    
    ![Emplacement du fichier apk](../images/studioSetup/54_APKlocation.png)

* "app-full-release.apk" (3) is the file you are looking for!

## Transférer le fichier APK sur le smartphone

La façon la plus facile de transférer le fichier app-full-release.apk dans votre téléphone est via [un câble USB ou Google Drive](https://support.google.com/android/answer/9064445?hl=fr). Veuilez noter que le transfert par email peut entraîner des difficultés et n'est pas la méthode conseillée.

Sur votre téléphone, vous devez autoriser l'installation à partir de sources inconnues. Les explications peuvent être trouvées sur internet (par ex. [ici](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) ou [ici](https://www.androidcentral.com/unknown-sources)).

## Résolution de problèmes

Voir la page spécifique [dépannage Android Studio](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).