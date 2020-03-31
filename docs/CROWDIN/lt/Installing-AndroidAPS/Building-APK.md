# Android programos (APK) kūrimas

## Kurti sau, o ne parsisiųsti

**Dėl reikalavimų medicininiams įrenginiams, nėra galimybės tiesiog parsisiųsti AndroidAPS programą. Programos kūrimas savo reikmėms yra visiškai teisėtas, tačiau jums neleidžiama perduoti jos kopijos kitiems! Žr. [DUK](../Getting-Started/FAQ.md) dėl išsamesnės informacijos.**

## ## Svarbios pastabos

* Norėdami sukurti APK failą, naudokite **[Android Studio 3.6.1 arba naujesnę versiją](https://developer.android.com/studio/)**.
* [Windows 10 32-bitų sistemos](../Installing-AndroidAPS/troubleshooting_androidstudio#unable-to-start-daemon-process) nėra palaikomos Android Studio 3.6.1.

**Konfigūracija pagal pareikalavimą** nepalaikoma dabartinėje Android Gradle modulio versijoje!

Jei sukurti APK nepavyko dėl pasirinktinės konfigūracijos klaidos, galite atlikti šiuos veiksmus:

* Atidarykite nustatymų langą spustelėdami File > Settings (Mac kompiuteryje Android Studio > Preferences).
* Kairiojoje srityje spustelėkite Build, Execution, Deployment > Compiler.
* Panaikinkite langelio „Configure on demand“ žymėjimą.
* Spustelėkite Apply arba OK.

* * *

### Šis straipsnis yra padalintas į dvi dalis.

* Apžvalgos skyriuje paaiškinta, kokių veiksmų reikia norint sukurti APK failą.
* Žingsnis po žingsnio instrukcijose rasite konkretaus diegimo ekrano kopijas. Kadangi Android Studio versijos - programinės įrangos kūrimo aplinka, kurioje sukursime APK - keičiasi labai greitai, tikslios atitikties su savo kūrimu nepamatysite, tačiau susidarysite bendrą įspūdį, kaip tai daroma. Android Studio veikia Windows, Mac OS X ir Linux ir kiekvienoje platformoje gali būti nedidelių skirtumų. Jei pastebite, kad kažkas svarbaus neveikia tinkamai arba jo trūksta, praneškite Facebook grupėje "AndroidAPS users" arba Gitter kanale [Android APS](https://gitter.im/MilosKozak/AndroidAPS) arba [AndroidAPSwiki](https://gitter.im/AndroidAPSwiki/Lobby), kad galėtumėme išspręsti problemą.

## Apžvalga

APK failui sukurti reikalingi šie veiksmai:

1. [Git diegimas](../Installing-AndroidAPS/git-install.rst)
2. [Android Studio įdiegimas](../Installing-AndroidAPS/Building-APK#install-android-studio)
3. [Nustatyti git kelią Android Studio parametruose](../Installing-AndroidAPS/Building-APK#set-git-path-in-preferences)
4. [Atsisiųsti AndroidAPS kodą](../Installing-AndroidAPS/Building-APK#download-androidaps-code)
5. [Atsisiųskite AndroidAPS SDK](../Installing-AndroidAPS/Building-APK#download-android-sdk)
6. [Sukurti programą](../Installing-AndroidAPS/Building-APK#generate-signed-apk) (generuoti pasirašomą apk)
7. [Perkelti apk failą į telefoną](../Installing-AndroidAPS/Building-APK#transfer-apk-to-smartphone)
8. [Identifikuoti gavėją, jei naudojate xDrip+](../Installing-AndroidAPS/Building-APK#identify-receiver-if-using-xdrip)

## Žingsnis po žingsnio instrukcija

Detalus veiksmų, reikalingų sukurti APK failą, aprašymas.

## Install git (if you don't have it)

Follow the manual on the [git installation page](../Installing-AndroidAPS/git-install.rst).

## Android Studio įdiegimas

Šios ekrano kopijos yra iš Android Studio 3.6.1 versijos. Priklausomai nuo Android Studio versijos, jūsų ekranas gali atrodyti šiek tiek kitaip. Bet jūs vis tiek turėtumėte sugebėti susitvarkyti. Čia galite rasti [bendruomenės pagalbą](../Where-To-Go-For-Help/Connect-with-other-users.md).

Vienas iš svarbiausių aspektų diegiant Android Studio yra: **Būkite kantrūs!** Diegiant ir nustatant Android Studio yra įkeliama daug duomenų ir tai užima daug laiko.

Įdiekite [Android Studio](https://developer.android.com/studio/install.html) ir nustatykite jį pirmojo paleidimo metu.

Pasirinkite „Do not import settings“, nes iki šiol nebuvo atlikta jokių nustatymų.

![Neimportuoti nustatymų](../images/AndroidStudio361_01.png)

Nuspręsti, ar norite bendrinti duomenis su Google, ar ne.

![Dalintis duomenimis su Google](../images/AndroidStudio361_02.png)

Kitame ekrane spustelėkite "Next" (kitas).

![Pasisveikinimo ekranas](../images/AndroidStudio361_03.png)

Pasirinkite "Standart" instaliavimą ir spauskite "Next".

![Standartinis instaliavimas](../images/AndroidStudio361_04.png)

Pasirinkite sąsajos dizainą, kuris jums labiausiai patinka. (Šiame vadove mes naudojamas "Light".) Tada spustelėkite "Next" (kitas). Tai tik spalvų schema. Galite pasirinkti bet kurią norite (pvz., "Darcula" tamsiam režimui). Šis pasirinkimas neturi įtakos APK kūrimui.

![UI Spalvų schema](../images/AndroidStudio361_05.png)

"Verify Settings" (patvirtinti nustatymus) lange spustelėkite "Next".

![Patvirtinti nustatymus](../images/AndroidStudio361_06.png)

Palaukite, kol Android Studio siunčiasi papildomus komponentus ir būkite kantrūs. Kai viskas atsisiųs, mygtukas "Finish" (baigti) pamėlynuos. Spustelėkite mygtuką dabar.

![Downloading components](../images/AndroidStudio361_07.png)

## Android Studio nustatymuose įveskite git kelią

Įsitikinkite, kad [git yra įdiegta](../Installing-AndroidAPS/git-install.rst) kompiuteryje.

Android Studio pasisveikinimo ekrane spustelėkite mažą trikampį (1. kitame paveikslėlį) ir pasirinkite "Settings" (Nustatymai) (2.).

![Android Studio nustatymai pasisveikinimo ekrane](../images/AndroidStudio361_08.png)

### Windows

* Spustelėkite mažą trikampį šalia "Version Control" (1.) norėdami atidaryti sub-meniu.
* Spustelėkite Git (2.).
* Įsitikinkite, kad atnaujinimo metodas "Merge" (3.) yra pasirinktas.
* Patikrinkite, ar Android Studio automatiškai randa kelią į git.exe, paspaudus mygtuką "Test" (4.)

![Android Studio settings](../images/AndroidStudio361_09.png)

* Jei automatinis nustatymas sėkmingas, git versija bus rodoma.
* Spauskite "OK" dialogo lange (1.) ir "OK" nustatymų lange (2.).

![Automatinis git instaliavimas pavyko](../images/AndroidStudio361_10.png)

* Jei failas git.exe negali būti rastas, spustelėkite "OK" dialogo lange (1.) ir tada mygtuką su trimis taškais (2.).
* Naudokite [paieškos funkcija](https://www.tenforums.com/tutorials/94452-search-file-explorer-windows-10-a.html) "Windows explorer" rasti "git.exe" jei jūs nežinote, kur jį galima rasti. Jūs ieškote git.exe, esančiame \bin\ aplanke.
* Pasirinkite kelią į git.exe ir įsitikinkite, kad jūs pasirinkote vieną iš ** \bin\ ** aplankų (3.) ir spustelėkite "OK" (4.).
* Uždarykite nustatymų langą, paspausdami "OK" mygtuką (5.).

![Automatinis git instaliavimas nepavyko](../images/AndroidStudio361_11.png)

* **Perkraukite kompiuterį, kad atsinaujintų sistemos aplinka.**

### Mac

* Bet kuri git versija turėtų veikti. Pvz., <https://git-scm.com/download/mac>.
* Naudoti homebrew įdiegti git: ```$ brew install git```.
* Daugiau informacijos, kaip įdiegti git, žr. [oficialioji git dokumentacijoje](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* Jei įdiegiate git per homebrew, nereikia keisti jokių nuostatų. Just in case: They can be found here: Android Studio - Preferences.

## Atsisiųsti AndroidAPS kodą

* **Jei dar neperkrovėte kompiuterio iš naujo, po git.exe kelio nustatymų, padarykite tai dabar. Sistemos aplinka turi būti atnaujinta.**
* Android Studio pasisveikinimo ekrane spustelėkite mažas trikampį dešinėje "Check out project from version control" (1.).
* Pasirinkite "Git" (2.).

![Check out project from version control from welcome screen](../images/AndroidStudio361_12.png)

* Jei jau atidarėte Android Studio ir nematote pasisveikinimo ekrano, pasirinkite File (1.) > New (2.) > Project from Version Control... (3.) > Git (4.).

![Patikrinti projektą iš Versijos kontrolės Android Studio](../images/AndroidStudio361_13.png)

* Įveskite pagrindinio AndroidAPS saugyklos puslapio URL (nuorodą_ ("https://github.com/MilosKozak/AndroidAPS") (1.).
* Pasirinkite katalogą, kuriame norite išsaugoti klonuotą kodą.
* Spustelėkite mygtuką "Test" (2.).
* Jei testas negali būti baigtas sėkmingai, patikrinkite URL (nuorodą), pataisykite, jei reikia, ir spauskite "Test" dar kartą.
* Jei URL yra įvestas teisingai, bus rodomas "Connection successful" (3.).
* Spustelėkite mygtuką "Clone" (4.).

![Clone repository](../images/AndroidStudio361_14.png)

* Nespauskite "Background" (vykdyti fone), o kol duomenų saugykla yra klonuojama!

![Klonuoti saugyklą - jokių foninių veiksmų](../images/AndroidStudio361_15.png)

* After repository is cloned successfully open your local copy by clicking "Yes".

![Open repository](../images/AndroidStudio361_16.png)

* In the lower right corner you will see the information that Android Studio is running background tasks.

![Background tasks](../images/AndroidStudio361_17.png)

* Grant access if your firewall is asking for permission.

![Firewall permission java](../images/AndroidStudio361_18.png)

* Once the background tasks are finished you will probably see the following error message:

![SDK licence](../images/AndroidStudio361_19.png)

## Atsisiųskite AndroidAPS SDK

* Click File > Settings.

![Open settings](../images/AndroidStudio361_20.png)

* Click the small triangle next to Appearance & Behaviour (1.).
* Click the small triangle next to System Settings (2.) and select Android SDK (3.)
* Check the box left of "Android 9.0 (Pie)" (4.) (API Level 28).

![SDK settings](../images/AndroidStudio361_21.png)

* Confirm changes by clicking OK.

![Confirm SDK changes](../images/AndroidStudio361_22.png)

* Accept licence agreement (1.) and click "Next" (2.).

![Accept SDK licence](../images/AndroidStudio361_23.png)

* Wait until installation is finished.

![Wait during SDK installation](../images/AndroidStudio361_24.png)

* When SDK installation is completed the "Finish" button will turn blue. Click this button.

![Finish SDK installation](../images/AndroidStudio361_25.png)

* Android Studio might recommend to update the gradle system. **Niekada neatnaujinkite gradle!** Tai gali sukelti problemų!
* If you see an information on the lower right side of your Android Studio window that Android Gradle Plugin is ready to update click on the text "update" (1.) and in the dialog box on "Don't remind me again for this project" (2.).

![No cradle update](../images/AndroidStudio361_26.png)

## Generuoti pasirašytą APK (Generate signed APK)

Signing means that you indicate your app to be your own creation but in a digital way as a kind of digital fingerprint within the app itself. Programą būtina pasirašyti skaitmeniniu būdu, nes Android saugumo sumetimais priima tik pasirašytą kodą. For more information on this topic, follow [this link](https://developer.android.com/studio/publish/app-signing.html#generate-key).

* Click "Build" in the menu bar and select "Generate Signed Bundle / APK...".

![Build apk](../images/AndroidStudio361_27.png)

* Select "APK" (1.) instead of "Android App Bundle" and click "Next" (2.).

![APK instead of bundle](../images/AndroidStudio361_28.png)

* Make sure that module is set to "app" (1.).
* Click "Create new..." (2.) to start creating your key store.
    
    A key store in this case is nothing more than a file in which the information for signing is stored. Ji šifruojama, ir informacija apsaugota slaptažodžiais.

![Create key store](../images/AndroidStudio361_29.png)

* Click the folder symbol (1.) to select your key store path. 
* Select the path where your key store shall be saved (2.). **Do not save in same folder as project. You must use a different directory!** One option might be your home folder.
* Type a file name for your key store (3.).
* Click "OK" (4.).
* Passwords for key store and key do not have to be very sophisticated. Make sure to remember those or make a note in a safe place. In case you will not remember your passwords in the future you see [troubleshooting for lost key store](../Installing-AndroidAPS/troubleshooting_androidstudio#lost-keystore).
* Enter (5.) and confirm (6.) the password for your key store.
* Do the same for your key (7. + 8.).
* Validity (9.) is 25 years by default. You do not have to change the default value.
* First and last name must be entered (10.). All other information is optional.
* Click "OK" (11.) when you are done.

![Key store path](../images/AndroidStudio361_30.png)

* Make sure the box to remember passwords is checked (1.). So you don't have to enter them again next time you build the apk (i.e. when updating to a new AndroidAPS version).
* Click "Next" (2.).

![Remember passwords](../images/AndroidStudio361_31.png)

* Select build variant "fullRelease" (1.). 
* Check boxes V1 and V2 for signature versions (2.).
* Click "Finish". (3.)

![Finish build](../images/AndroidStudio361_32.png)

* Android Studio will display the information "APK(s) generated successfully..." after build is finished.
* In case build was not successful refer to the [troubleshooting section](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).
* Easiest way to find the apk is to click on "Event log".

![Build successfully - event log](../images/AndroidStudio361_33.png)

* In the event log section click "locate".

![Event log - locate apk](../images/AndroidStudio361_34.png)

* app-full-release.apk is the file you are looking for.

![File location apk](../images/AndroidStudio361_35.png)

## Perkelkite APK į išmanųjį telefoną

Easiest way to transfer app-full-release.apk to your phone is via [USB cable or Google Drive](https://support.google.com/android/answer/9064445?hl=en). Please note that transfer by mail might cause difficulties and is not the preferred way.

On your phone you have to allow installation from unknown sources. Manuals how to do this can be found on the internet (i.e. [here](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) or [here](https://www.androidcentral.com/unknown-sources)).

## Identifikuoti gavėją, jei naudojate xDrip+

[See xDrip+ page](../Configuration/xdrip#identify-receiver)

## Trikčių šalinimas

See separate page [troubleshooting Android Studio](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).