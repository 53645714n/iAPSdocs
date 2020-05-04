# Pumpa Accu-Chek Insight

**Tento software je součástí DIY řešení umělé slinivky, nejedná se o výrobek. Před jeho používáním je důležité, abyste prostudovali a pochopili celý systém, včetně toho jak ho používat. Není to něco, co za Vás udělá veškerý management diabetu. Pokud do toho investujete potřebný čas, pomůže Vám dojít k lepším výsledkům při léčbě Vaší cukrovky, a tím zlepšit i kvalitu Vašeho života. Zbytečně nespěchejte, a vytvořte si čas pro učení. Pouze Vy jste zodpovědní za ovládání Vašeho systému.**

* * *

## ***UPOZORNĚNÍ:** Pokud jste v minulosti používali Insight se **SightRemote**, prosím **aktualizujte na nejnovější verzi AAPS** a **odinstalujte SightRemote**.*

## Hardwarové a softwarové požadavky

* Roche Accu-Chek Insight (kterýkoli firmware, funguje se všemi)
    
    Poznámka: AAPS vždy zapíše data do **prvního bazálního profilu v pumpě**.

* Telefon s Androidem (v podstatě všechny verze Androidu budou fungovat, ale AndroidAPS sám o sobě vyžaduje alespoň Android 5 (Lollipop)).

* Aplikace AndroidAPS instalovaná ve vašem telefonu

## Nastavení

* Pumpa Insight by měla být připojena současně pouze k jednomu zařízení. Pokud jsme v minulosti používali dálkové ovládání pro Insight (glukometr), musíte zařízení odstranit ze seznamu spárovaných zařízení ve své pumpě: Menu > Nastavení > Komunikace > Odebrat zařízení
    
    ![Screenshot odebrání glukometru z Insight](../images/Insight_RemoveMeter.png)

* V nabídce [Konfigurace](../Configuration/Config-Builder) aplikace AndroidAPS vyberte v sekci Pumpa možnost Accu-Chek Insight
    
    ![Screenshot nastavení pumpy Insight](../images/Insight_ConfigBuilder.png)

* Chcete-li otevřít nabídku nastavení, klikněte na ozubené kolečko.

* V nastavení klikněte na tlačítko „Insight párování“ v horní části obrazovky. Měli byste vidět seznam bluetooth zařízení v dosahu (níže vlevo).
* V pumpě Insight jděte do Menu > Nastavení > Komunikace > Přidat zařízení. Pumpa zobrazí následující obrazovku (vpravo níže) zobrazující seriové číslo pumpy.
    
    ![Screenshot párování Insight 1](../images/Insight_Pairing1.png)

* Vezměte telefon a klikněte na sériové číslo pumpy v seznamu bluetooth zařízení v telefonu. Potvrďte kliknutím na Párování.
    
    ![Screenshot párování Insight 2](../images/Insight_Pairing2.png)

* Pumpa i telefon poté zobrazí na displeji kód. Zkontrolujte, jestli je na obou zařízeních shodný kód a potvrďte jej jak v pumpě, tak v telefonu.
    
    ![Screenshot párování Insight 3](../images/Insight_Pairing3.png)

* Úspěch! Můžete si poblahopřát, úspěšně jste spárovali pumpu s AndroidAPS.
    
    ![Screenshot párování Insight 4](../images/Insight_Pairing4.png)

* Chcete-li zkontrolovat, jestli je vše správně, jděte zpět do nabídky Konfigurace v AndroidAPS a klikněte na ozubené kolečko v nabídce Pumpa - Accu Chek Insight. Klikněte na Insight párování, kde uvidíte informace o pumpě:
    
    ![Screenshot informací o spárování Insight](../images/Insight_PairingInformation.png)

Poznámka: Spojení mezi pumpou a telefonem není permanentní. Spojení bude navázáno pouze tehdy, je-li to nezbytné (např. při nastavování dočasného bazálu, posílání bolusu, čtení historie z pumpy apod.). V opačném případě by se baterie v pumpě i mobilu velmi rychle vybila.

## Nastavení v AAPS

Při používání pumpy Insight **nesmí být nastaveno 'Vždy použít absolutní hodnoty bazálu'**. V AAPS přejděte do nastavení > NSClient > Rozšířené nastavení a ujistěte se, že možnost 'Vždy použít bazální absolutní hodnoty' je vypnuta. Toto nastavení způsobuje problémy při nastavování dočasných bazálů.

Jestliže potřebujete používat Autotune, jediným řešením v tuto chvíli je **zakázat synchronizaci** s Nightscoutem (pouze nahrávání). V AAPS přejděte do nastavení > NSClient > Pokročilá nastavení a povolte ‘Pouze nahrávání do NS (zakázat synchronizaci)‘.

![Screenshot nastavení Insight](../images/Insight_pairing_V2_5.png)

V Insight nastavení v AndroidAPS můžete upravit následující možnosti:

* „Zaznamenat výměnu zásobníku“: při spuštění programu „naplnit kanylu“ dojde automaticky k zaznamenání výměny inzulínu.
* „Zaznamenat výměnu hadičky“: Automaticky provede záznam v databázi AndroidAPS, když v pumpě provedete „Naplnit hadičku“.
* „Zaznamenat výměnu kanyly“: Tato volba přidá do databáze AndroidAPS záznam při spuštění programu „naplnit kanylu“. ** Poznámka: Výměna kanyly také resetuje Autosens. **
* „Zaznamenat výměnu baterie“: Automaticky provede záznam o výměně baterie, pokud vložíte do pumpy novou baterii.
* „Zaznamenat změnu režimu provozu“: Automaticky provede záznam v databázi AndroidAPS, kdykoliv spustíte/zastavíte pumpu.
* „Zaznamenat výstrahy“: Automaticky provede záznam v databázi AndroidAPS, kdykoliv pumpa zahlásí alarm (s výjimkou upomínek, bolusů a konce dočasných bazálů (TBR) – ty zaznamenány nejsou).
* „Povolit emulaci dočasných bazálů“: pumpa Insight umožňuje hodnotu maximálního dočasného bazálu (TBR) do výše 250 %. Pumpa má nastaveno omezení dočasného bazálu na 250 %. Pokud je požadavek na dočasný bazál vyšší než 250 %, bude provedena jeho emulace zadáním rozloženého bolusu.
    
    **Pozn.: Nastavte najednou jeden rozložený bolus. Používání více rozložených bolusů současně může způsobit chyby.**

* „Doba čekání na obnovení spojení“: Definuje, jak dlouho bude AndroidAPS čekat před opětovným pokusem po neúspěšném pokusu o připojení. Můžete vybrat 0 až 20 sekund. Pokud máte problémy s připojením, vyberte delší dobu čekání.   
      
    Příklad pro min. dobu trvání zotavení = 5 a max. dobu zotavení = 20   
      
    žádné spojení -> čekej **5** s   
    znovu -> žádné spojení -> čekej **6** s   
    znovu -> žádné spojení -> čekej **7** s   
    znovu -> žádné spojení -> čekej **8** s   
    ...   
    znovu -> žádné spojení -> čekej **20** s   
    znovu -> žádné spojení -> čekej **20** s   
    ...

* „Limit pro odpojení“: Definuje, jak dlouho (v sekundách) bude AndroidAPS čekat s odpojením od pumpy po dokončení úlohy. Výchozí hodnota je 5 sekund.

Po dobu, kdy byla pumpa zastavena, AAPS zobrazí záznam s dočasnou bazální hodnotou 0 %.

V AndroidAPS v záložce Accu-Chek Insight se zobrazuje aktuální stav pumpy a dvě tlačítka:

* „Obnovit“: Opětovné načtení statusu z pumpy
* „Povolit oznamování konce dočasného bazálu“: Standardně pumpa Insight spouští zvukový signál, když je TBR dokončen. Toto tlačítko vám umožňuje povolit nebo zakázat tento alarm, aniž byste museli použít software pro konfiguraci pumpy.
    
    ![Screenshot stavu Insight](../images/Insight_Status2.png)

## Nastavení v pumpě

Nastavení alarmů v pumpě:

* Menu > Nastavení > Nastavení zařízení > Nastavení režimu > Tichý > Signál > Zvuk
* Menu > Nastavení > Nastavení zařízení > Nastavení režimu > Tichý > Hlasitost > 0 (odeberte všechny sloupečky)
* Menu > Režimy > Režim signalizace > Tichý

To ztlumí všechny alarmy z pumpy, což umožní systému AndroidAPS rozhodnout, zda je pro vás alarm relevantní. Pokud alarm AndroidAPS nebude potvrzen, hlasitost alarmu se bude zvyšovat (nejprvé pípnutí, potom vibrace).

### Vibration

Depending on pump firmware Insight pump will vibrate briefly every time a bolus is delivered (for example, when AndroidAPS issues an SMB or TBR emulation delivers an extended bolus).

* Firmware 1.x: No vibration by design.
* Firmware 2.x: Vibration cannot be disabled.
* Firmware 3.x: Vibration can be diabled in AAPS (minimum [version 2.6.1.3](../Installing-AndroidAPS/Releasenotes#version-2-6-1-3))

Firmware version can be found in the menu.

## Výměna baterie

Battery life for Insight when looping range from 10 to 14 days, max. 20 days. The user reporting this is using Energizer lithium batteries.

The Insight pump has a small internal battery to keep essential functions like the clock running while you are changing the removable battery. If changing the battery takes too long, this internal battery may run out of power, the clock will reset, and you will be asked to enter a new time and date after inserting a new battery. If this happens, all entries in AndroidAPS prior to the battery change will no longer be included in calculations as the correct time cannot be identified properly.

## Specifické chyba Insight

### Prodloužený bolus

Just use one extended bolus at a time as multiple extended boluses at the same time might cause errors.

### Time out

Sometimes it might happen that the Insight pump does not answer during connection setup. In this case AAPS will display the following message: "Timeout during handshake - reset bluetooth".

![Insight Reset Bluetooth](../images/Insight_ResetBT.png)

In this case turn off bluetooth on pump AND smartphone for about 10 seconds and then turn it back on.

## Změna časových pásem s pumpou Insight

For information on traveling across time zones see section [Timezone traveling with pumps](../Usage/Timezone-traveling#insight).