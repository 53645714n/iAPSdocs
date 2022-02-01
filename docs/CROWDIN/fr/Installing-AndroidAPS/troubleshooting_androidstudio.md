# Dépannage d'Android Studio

## Fichier de clés perdu
Si vous utilisez le même fichier de clés lors de la mise à jour d'AndroidAPS, vous n'avez pas besoin de désinstaller la version précédente sur votre smartphone. C'est pourquoi il est recommandé de stocker le fichier de clés dans un dossier de sauvegarde sûr.

Si vous essayez d'installer l'apk, signé avec un fichier de clés différent de celui d'avant, vous recevrez un message d'erreur indiquant que l'installation a échoué!

Si vous ne trouvez plus votre ancien fichier de clés ou son mot de passe, procédez comme suit :

1. [Exporter les paramètres](../Usage/ExportImportSettings#exporter-les-parametres) sur votre ancien téléphone.
2. Copiez le fichier de configuration de votre téléphone vers un emplacement externe (par ex. votre ordinateur, un service cloud...).
4. Générez l'apk signé de la nouvelle version comme décrit dans le [Guide de mise à jour](../Installing-AndroidAPS/Update-to-new-version) et transférez-le sur votre téléphone.
5. Désinstaller la précédente version de AAPS sur votre téléphone.
6. Installez la nouvelle version de AAPS sur votre téléphone.
7. [Importer les paramètres](../Usage/ExportImportSettings.html#importer-les-parametres) pour restaurer vos objectifs et votre configuration.

   Si vous ne pouvez pas les trouver sur votre téléphone, copiez les depuis le stockage externe vers votre téléphone.
8. Pousuivez la boucle.

## Gradle Sync en échec
Gradle Sync peut échouer pour diverses raisons. Quand vous recevez un message indiquant que la synchronisation gradle a échouée, ouvrez l'onglet "Build" (1) en bas d'Android Studio et vérifiez quel message d'erreur (2) est affiché.

  ![Gradle Failed](../images/studioTroubleshooting/07_GradleSyncFailed2.png)

Ci-dessous les échecs courants de synchronisation de gradle :
* [Uncommitted changes](#Uncommitted-changes)
* [No cached version of ... available](#could-not-resolveno-cached-version)
* [Android Gradle requires Java 11 to run](#Android-Gradle-plugin-requires-Java-11-to-run)

*Important*: Après avoir suivi les instructions pour votre problème spécifique, vous devez déclencher la [Resynchronisation gradle](#resynchronisation-gradle) à nouveau.

### Uncommitted changes

Si vous recevez un message d'erreur comme ceci

![Changements non commités Gradle](../images/studioTroubleshooting/02_GradleUncommitedChanges.png)

#### Étape 1 - Vérifiez l'installation de git
  * Ouvrez l'onglet Terminal (1) en bas d'Android Studio, copiez le texte suivant et collez le dans le terminal.
    ```
    git --version
    ```

    ![Gradle version de Git](../images/studioTroubleshooting/03_GitVersion.png)

    Note : Il y a un espace et deux traits d'union entre git et version !

  * Vous devez recevoir un message indiquant quelle version de git est installée, comme vous pouvez le voir dans la capture d'écran ci-dessus. Dans ce cas, allez à [l'étape 2](#etape-2-verifier-les-modifications-non-commit-es).

  * Dans le cas où vous recevez un message disant
    ```
    Git: command not found
    ```
    votre installation Git n'est pas correcte.

  * [Vérifiez l'installation de git](../Installing-AndroidAPS/git-install#check-git-settings-in-android-studio)

  * Quand vous êtes sur Windows et que git vient juste d'être installé, vous devez redémarrer votre ordinateur pour rendre git disponible après l'installation

  * Si Git est installé, que vous avez redémarré (si sous Windows), et git n'est toujours pas trouvé :

  * Cherchez dans votre ordinateur un fichier "git.exe".

    Notez pour vous, dans quel répertoire il se trouve.

  * Allez dans les variables d'environnement de Windows, sélectionnez la variable "PATH" et cliquez sur Modifier. Ajoutez le répertoire où vous avez trouvé votre installation de git.

  * Sauver et fermer.

  * Redémarrer Android Studio.

#### Étape 2 : Vérifier les modifications non commitées.

  * In Android Studio, oben the "Commit" Tab (1) on the left-hand side. ![Onglet de commit : changements non commités](../images/studioTroubleshooting/04_CommitTabWithChanges.png)
  * You can see either a "Default changeset" (2) or "Unversioned files" (3):

    * For "Default changeset", you probably updated gradle or changed some of the file contents by mistake.

    * Right click on "Default Changeset" and select "Rollback"

      ![Onglet de commit : Restaurer les modifications](../images/studioTroubleshooting/05_CommitTabRollback.png)

    * The files are fetched again from the Git server. If there are no other changes in the commit tab, go to [Step 3](#step-3-resync-gradle-again).

  * If you can see "Unversioned Files", you might have stored files in your sourecode directory which should be better places somewhere else, e.g. your keystore file.

    * Use your regular file explorer on your computer to move or cut and paste that file to a save place.

    * Go back to Android Studio and click the Refresh button (4) within the Commit tab to make sure the file is not stored in the AndroidAPS directory anymore.

      If there are no other changes in the commit tab, go to [Step 3](#step-3-resync-gradle-again).


#### Étape 3 : Resynchroniser Gradle (encore)

Suivez les instructions à [Resynchronisation Gradle](#resynchronisation-gradle).

### Android Gradle requires Java 11 to run

  You might experience this error message:

  ![Android Gradle requires Java 11 to run](../images/studioTroubleshooting/11_GradleJDK.png)

  Click on "Gradle Settings" (1) to go to open the gradle settings.

  ![Configuration de Gradle](../images/studioTroubleshooting/12_GradleSettingsJDK.png)

  Open the options (1) at "Gradle JDK" and selected the "Embedded JDK version" (2)

  Press "OK" to save and close the settings dialog.

  Now you need to trigger a [Gradle Resync](#gradle-resync)

### Could not resolve/No cached version

  You might get this error message:

    ![Could not resolve... No cached version](../images/studioTroubleshooting/08_NoCachedVersion.png)

  * On the right side, open the Gradle tab (1).

    Make sure the button shown at (2) is *NOT* selected.

    ![Gradle mode hors connexion](../images/studioTroubleshooting/10_GradleOfflineMode.png)

  * Now you need to trigger a [Gradle Resync](#gradle-resync)

### Impossible de démarrer le processus daemon

  Si vous voyez un message d'erreur ci-dessous, vous utilisez probablement un système Windows 10 32 bits. This is not supported by Android Studio 3.5.1 and above and unfortunately nothing the AAPS developer can do about.

  If you are using Windows 10 you must use a 64-bit operating system.

  There are a lot of manuals on the internet how to determine wether you have a 32-bit or 64-bit OS - i.e. [this one](https://www.howtogeek.com/howto/21726/how-do-i-know-if-im-running-32-bit-or-64-bit-windows-answers/).

  ![Copie d'écran Impossible de démarrer le processus daemon](../images/AndroidStudioWin10_32bitError.png)

### Resynchronisation Gradle

  If you can still see the message that the gradle sync failed, now select the Link "Try again". ![Gradle Sync en échec](../images/studioTroubleshooting/01_GradleSyncFailed.png)


  If you don't see the a message anymore, you can still trigger this manually:

  * Open the Gradle tab (1) on the right border of Android Studio.

    ![Gradle Rechargement](../images/studioTroubleshooting/06_GradleResyncManually.png)

  * Right-click on AndroidAPS (2)

  * Click on "Reload Gradle Project" (3)

## App was created with compiler/kotlin warnings

If your build completed successfully but you get compiler or kotlin warnings (indicated by a yellow or blue exclamation mark) then you can just ignore these warnings.

 ![Gradle terminé avec des avertissements](../images/studioTroubleshooting/13_BuildWithWarnings.png)

Your app was build successfully and can be transferred to phone!


## La clé a été créée avec des erreurs

Lors de la création d'un fichier de clés pour pouvoir générer un APK signé, sous Windows, le message d'erreur suivant peut apparaître

![La clé a été créée avec des erreurs](../images/AndroidStudio35SigningKeys.png)

Cela semble être un bug avec Android Studio 3.5.1 et son environnement Java livré sous Windows. La clé est créée correctement mais une recommandation est affichée à tort comme une erreur. Cela peut actuellement être ignoré.


## No CGM data is received by AndroidAPS

* Si vous utilisez l'application Dexcom G6 patchée, cette application est obsolète. Use the [BYODA](../Hardware/DexcomG6#if-using-g6-with-build-your-own-dexcom-app) app instead.

* In case you are using xDrip+: Identify receiver as described on [xDrip+ settings page](../Configuration/xdrip#identify-receiver).


## Application non installée.

![note d'application du téléphone installée](../images/Update_AppNotInstalled.png)

* Assurez-vous d'avoir transféré le fichier “app-full-release.apk” sur votre téléphone.
* Si vous avez le message "App non installé" sur votre téléphone, suivez ces étapes :

1. [Exporter les paramètres](../Usage/ExportImportSettings) (dans la version AAPS déjà installée sur votre téléphone)
2. Désinstaller AAPS sur votre téléphone.
3. Activer le mode avion & désactiver bluetooth.
4. Installer la nouvelle version (« app-full-release.apk »)
5. [Importer les paramètres](../Usage/ExportImportSettings)
6. Activer le bluetooth et désactiver le mode avion

## Application installée mais ancienne version

If you built the app successfully, transferred it to your phone and installed it successfully but the version number stays the same then you might have missed to [update your local copy](../Installing-AndroidAPS/Update-to-new-version#update-your-local-copy)

## Rien ci-dessus n'a marché

Si aucun des conseils ci-dessus ne vous a aidé, vous pourriez envisager de repartir de zéro pour reconstruire l'application :

1. [Exporter les paramètres](../Usage/ExportImportSettings) (dans la version AAPS déjà installée sur votre téléphone)

2. Ayez vos mots de passe pour la clé et le fichier de clés sous la main. In case you have forgotten passwords you can try to find them in project files as described [here](https://youtu.be/nS3wxnLgZOo).

    Ou vous pouvez recréer un nouveau fichier de clés.

3. Build app from scratch as described [here](../Installing-AndroidAPS/Building-APK#download-androidaps-code).

4. Quand vous avez construit l'APK avec succès, supprimez l'application existante sur votre téléphone, transférez le nouvel apk sur votre téléphone et installez le.
5. [Import settings](../Usage/ExportImportSettings) again to restore your objectives and settings.

## Pire scénario

Dans le cas où même construire l'application à partir de rien ne résout pas votre problème, vous pouvez essayer de désinstaller complètement Android Studio. Certains utilisateurs ont signalé que cela a résolu leur problème.

**Make sure to uninstall all files associated with Android Studio.** If you do not completely remove Android Studio with all hidden files, uninstalling may cause new problems instead of solving your existing one(s). Les manuels pour une désinstallation complète peuvent être trouvés en ligne, par ex.

[https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10](https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10).

Install Android Studio from scratch as described [here](../Installing-AndroidAPS/Building-APK.html#install-android-studio).
