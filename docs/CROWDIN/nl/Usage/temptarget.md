# Tijdelijk streefdoel

## Wat is een Tijdelijk streefdoel en hoe kan ik dat instellen?

Met een Tijdelijk streefdoel ("Temp-Target” of TT in het Engels), kun je het streefdoel wijzigen voor jouw bloedglucose gedurende een zelfgekozen periode. Dit is vooral handig in bepaalde situaties: bij fysieke activiteit, tijdens een hypo (waarbij je koolhydraten nodig hebt) of wanneer je binnenkort gaat eten. Voor deze situaties heeft AAPS standaardinstellingen, die je zelf kunt kiezen. Tik hiervoor op de 3 puntjes in de rechter bovenhoek en kies Instellingen -> Overig -> Standaardwaardes tijdelijke streefdoelen. Hier heb je de mogelijkheid om de standaardinstellingen van AAPS te wijzigen.

![Standaard Tijdelijke streefdoelen instellen](../images/TempTarget_Default.png)

Om vervolgens een Tijdelijk streefdoel te gebruiken, zijn er verschillende manieren. Druk op het Overzicht-scherm op het vlak rechtsboven met jouw streefdoel. Of druk op het Overzicht-scherm op de oranje 'Koolhydraten' knop of op de blauwe 'Insuline' knop onderin beeld. To manually set a [“Custom Temp-Target”](../Usage/temptarget.md#custom-temp-target) (BG value and/or duration), short click on your target in the top right corner or use the “Temporary Target“ button in the [actions tab / menu](../Configuration/Config-Builder#actions).

![Start Tijdelijk streefdoel](../images/TempTarget_Set2.png)

- Als je de waarden van een standaard tijdelijk streefdoel iets wilt aanpassen, kun je de Eet Binnenkort, Activiteit of Hypo-knop lang indrukken en vervolgens de waarden in de velden Doel of Duur bewerken.
- Als een tijdelijk streefdoel actief is, wordt er een extra "Annuleren" knop weergegeven in het dialoogvenster om het te annuleren

## Hypo Tijdelijk streefdoel

Dit kan worden beschouwd als het belangrijkste Tijdelijke streefdoel. Er zijn verschillende redenen om deze te gebruiken:

1. Je realiseren dat je op een hypo afstevent; meestal ziet de Loop dit al aankomen en voorkomt hij dat je te laag gaat zitten, maar in sommige gevallen kun jij dit zelf beter zien aankomen. In dat geval stel je een Hypo Tijdelijk streefdoel in, omdat de Loop sneller zal stoppen/minderen met insuline afgeven wanneer een hogere streefwaarde is ingesteld.
2. Wanneer je koolhydraten eet om een hypo te behandelen; je bloedglucose zal in zo'n situatie snel stijgen. De Loop zal proberen om voor deze stijging te corrigeren door een hoge tijdelijke basaalstand of zelfs een SMB te geven. Een Hypo Tijdelijk streefdoel kan dat voorkomen. 
3. (advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb)): You can enable “High Temp-Targets raises sensitivity” for Temp-Targets of 100mg/dl or 5.5mmol/l or higher in OpenAPS SMB, so AndroidAPS is more sensitive.
4. (advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb)): You can deactivate “SMB with high temp target”, so that even if you have COB > 0, "SMB with Temp-Target" or "SMB always" enabled and OpenAPS SMB active, AndroidAPS won’t give SMBs while high temp targets are active.

Opmerking: als jouw bloedglucose lager dan 72mg/dl of 4mmol/l is, en je voert koolhydraten in via de oranje 'Koolhydraten' knop op het Overzicht-scherm, dan wordt er automatisch een Hypo Tijdelijk streefdoel ingeschakeld. Wel zo handig!

## Activiteit Tijdelijk streefdoel

Voor en tijdens fysieke activiteit wil je misschien een hoger streefdoel instellen om te voorkomen dat je te laag komt te zitten. De makkelijkste manier om dat te doen, is via de standaardinstelling "Activiteit Tijdelijk streefdoel". Hoelang en op welke waarde je het Tijdelijk streefdoel instelt, kies je op basis van DIA, IOB en jouw eigen ervaring. See also [sports section in FAQ](../Getting-Started/FAQ.md#sports).

Advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb): The advantages about “Activity Temp-Target”, is that you can enable “High Temp-Targets raises sensitivity” for Temp-Targets higher or equal 100mg/dl or 5.5mmol/L in OpenAPS SMB. AndroidAPS is dan gevoeliger. Sommige mensen gebruiken in plaats van die optie een Profiel wissel voordat/terwijl ze een Activiteit Tijdelijk streefdoel instellen, dat kan ook. Iedereen is anders en je moet uitproberen wat voor jou werkt. Als “Gebruik SMB met hoog tijdelijk doel” is gedeactiveerd, zal AndroidAPS geen SMBs gebruiken, zelfs niet wanneer COB > 0, "Gebruik SMB met Tijdelijke doelen" of "Activeer SMB altijd" zijn ingeschakeld.

## Eet binnenkort Tijdelijk streefdoel

Als u weet dat je strakjes iets gaat eten, dan kun je dit Tijdelijke streefdoel inschakelen, zodat je al meer insuline aan boord (IOB) hebt voordat je iets eet. Vooral voor degenen die geen pre-bolus gebruiken (pre-bolus is alvast bolussen, en dan even wachten met eten), is dit een goed alternatief. Je kunt meer lezen over de mogelijkheden van Eet binnenkort ("Eating soon") in het Engelstalige artikel ['How to do "eating soon" mode'](https://diyps.org/2015/03/26/how-to-do-eating-soon-mode-diyps-lessons-learned/) of ga naar [deze site](https://diyps.org/tag/eating-soon-mode/).

Advanced, [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb): If you use OpenAPS SMB and have “Low temptarget lowers sensitivity”, AndroidAPS works a little bit more aggressive. Voor deze optie geldt dat je Tijdelijke streefdoel lager dan 100 mg/dl of 5,5mmol/l moet zijn.

## Aangepast Tijdelijk streefdoel

Soms wil je gewoon een Tijdelijk streefdoel hebben dat anders is dan de standaard ingestelde Tijdelijke streefdoelen. Je kunt er één instellen door kort te drukken op het doel (bereik) in de rechterbovenhoek in het Overzichtscherm of in het tabblad "Acties".

![Tijdelijk streefdoel instellen via Actie tabblad](../images/TempTarget_ActionTab.png)