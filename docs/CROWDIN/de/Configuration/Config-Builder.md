# Konfigurations-Generator

Abhängig von Deinen Einstellungen kannst Du den Konfigurationsgenerator über eine Registerkarte am oberen Bildschirmrand oder über das Hamburger-Menü öffnen.

![Konfigurations-Generator öffnen](../images/ConfBuild_Open.png)

Im Reiter “Konfigurations-Generator” (KONF) kannst du fast alle AAPS-Funktionen konfigurieren. Die Auswahlfelder links (A) aktivieren die gewählte Funktion, die Auswahlfelder rechts (C) legen fest, ob die Funktion als Tab (E) angezeigt wird oder nicht. Falls die rechte Box nicht aktiviert ist, sind die Funktionen über das Hamburger-Menü (D) oben links am Bildschirm erreichbar.

Falls zusätzliche Einstellungen innerhalb der Funktion möglich sind, können sie über das Zahnrad (B) aufgerufen werden.

**Erste Konfiguration:** Seit AAPS 2.0 führt dich ein Einrichtungsassistent durch die Einrichtung von AndroidAPS. Drücke das 3-Punkte-Menü (F) oben rechts am Bildschirm und wähle "Einrichtungsassistent", um diesen zu starten.

![Konfigurations-Generator - Checkboxen und Zahnrad](../images/ConfBuild_ConfigBuilder.png)

## Registerkarte (Tab) oder Hamburger-Menü

Mit der Checkbox unter dem Augensymbol entscheidest Du, wie Du den entsprechenden Programmabschnitt öffnest.

![Registerkarte (Tab) oder Hamburger-Menü](../images/ConfBuild_TabOrHH.png)

## Profile

Wähle das Basal-Profil aus, das du benutzen möchtest. Unter [Profile](../Usage/Profiles.md) findest du weitere Informationen zu den Einstellungen.

### Lokales Profil (empfohlen)

Das lokale Profil nutzt das Profil, das in der Pumpe manuell erfasst wurde. Sobald "Lokales Profil" ausgewählt ist, erscheint ein weiterer Tab, in dem die aus der Pumpe ausgelesenen Profildaten bei Bedarf angepasst werden können. Beim nächsten Profil Wechsel werden sie an die Pumpe übertragen und in deren Profil 1 gespeichert. Diese Einstellung wird empfohlen, da keine Internetverbindung erforderlich ist.

Vorteile:

* Keine Internetverbindung erforderlich, um die Profileinstellungen zu ändern.
* Profilwechsel können direkt auf dem Smartphone vorgenommen werden.

Nachteile:

* nur ein Profil

### Nightscout-Profil

Das NS-Profil verwendet das von dir auf deiner Nightscout Seite gespeicherte Profil (https://[yournightscoutsiteaddress]/profile). Mache einen [Profil Wechsel](../Usage/Profiles.md), um zu bestimmen, welches Profil aktiv sein soll. Dieses Profil wird auch in die Pumpe gespeichert für den Fall, dass AndroidAPS ausfallen sollte. So kannst du ganz einfach verschiedene Basalprofile in Nightscout hinterlegen (z.B. Arbeit, zu Hause, Sport, Urlaub usw.). Kurz nachdem du das Profil auf deiner Nightscout Seite gespeichert hast, wird es an AAPS übertragen - sofern dein Smartphone online ist. Selbst ohne Internetverbindung oder wenn eine Verbindung zu Nightscout nicht möglich ist sind die verschiedenen Profile in AAPS verfügbar, wenn sie einmal synchronisiert wurden.

Du musst einen **Profil Wechsel** machen, um ein anderes Profil von deiner Nightscout-Seite zu aktivieren. Drücke und halte die Bezeichnung für dein aktuelles Profil auf dem AAPS Startbildschirm (graues Feld zwischen dem hellblauen "Open/Closed Loop" Feld und dem dunkelblauen Bereich mit deinem Zielbereich) > Profil Wechsel > gewünschtes Profil auswählen > OK. AAPS überträgt das gewählte Profil dann an die Pumpe, wo es gespeichert wird. Somit steht das Basalprofil unabhängig von AAPS zur Verfügung und läuft wie programmiert weiter, auch wenn AAPS einmal keine Verbindung mit Deiner Pumpe herstellen kann.

Vorteile:

* Mehrere Profile
* einfach per PC oder Tablet zu bearbeiten

Nachteile:

* Keine lokalen Änderungen an den Profileinstellungen möglich.
* Profilwechsel nicht direkt auf dem Smartphone möglich.

### Einfaches Profil

Einfaches Profil mit nur einem Zeitblock für DIA, IC, ISF, Basalrate und Zielbereich (z.B. keine Basalratenänderung im Laufe des Tages). Eher für Testzwecke geeignet, außer du verwendest über 24 Stunden dieselben Faktoren. Sobald "Einfaches Profil" ausgewählt ist erscheint ein weiterer Tab, in dem die Profildaten eingetragen werden können.

## Insulin

Wähle die Art der Insulinkurve, die du verwendest. Die Oref Optionen 'Rapid-Acting Oref', Ultra-Rapid Oref' und 'Free-Peak Oref' sind exponentiell. Mehr Informationen dazu finden sich in den [OpenAPS docs](http://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/understanding-insulin-on-board-calculations.html#understanding-the-new-iob-curves-based-on-exponential-activity-curves). Diese Kurven variieren basierend auf der DIA und dem zeitlichen Abstand zum Wirkmaximum.

Die Insulinwirkdauer (DIA) ist nicht für jeden gleich. Daher musst Du es selbst für Dich austesten. Unter fünf Stunden darf der Wert aber nicht liegen. Im Abschnitt zu den Insulinprofilen auf [dieser Seite](../Getting-Started/Screenshots#insulin-profile) findest Du weitere Informationen dazu.

Bei den Profilen Rapid-Acting und Ultra-Rapid kannst Du nur die Insulinwirkdauer (DIA) anpassen. Der Zeitpunkt der maximalen Insulinwirkung ist fix vorgegeben. Das Profil Free-Peak erlaubt, nicht nur die Insulinwirkdauer (DIA), sondern auch den Zeitpunkt der maximalen Insulinwirkung individuell festzulegen. Es sollte nur von erfahrenen Anwendern genutzt werden, die die Auswirkungen dieser Einstellungen kennen.

Das [Kurvendiagramm](../Getting-Started/Screenshots#insulin-profile) unterstützt Dich dabei, die verschiedenen Kurven zu verstehen. Wenn Du die Checkbox akivierst, wird das Diagramm als eigener Tab angezeigt, sonst ist es über das Hamburger-Menü links oben erreichbar.

### Rapid-Acting Oref

* empfohlen für Humalog, Novolog und Novorapid
* DIA = mindestens 5 Stunden
* Wirkdauermaximum = 75 Minuten nach Insulingabe (fest eingestellt, nicht anpassbar)

### Ultra-Rapid Oref

* empfohlen für FIASP
* DIA = mindestens 5 Stunden
* Wirkdauermaximum = 55 Minuten nach Insulingabe (fest eingestellt, nicht anpassbar)

Für viele Menschen mit Diabetes gibt es 3 - 4 Stunden nach der Insulingabe nahezu keinen spürbaren Effekt von FIASP mehr, auch wenn dann rechnerisch noch 0.0xx Einheiten vorhanden sind. Die verbleibende Menge kann aber bei Sport und anderen Aktivitäten doch noch einen Einfluss haben. Daher nutzt AAPS eine minimale Wirkdauer von 5 Stunden.

![Konfigurations-Generator - Ultra-Rapid Oref](../images/ConfBuild_UltraRapidOref.png)

### Free Peak Oref

Erlaubt das Wirkmaximum der Insulinaktivität individuell zu definieren. DIA wird automatisch auf 5 Stunden gesetzt, sofern von Dir im Profil nichts anderes definiert wird.

Dieses Profil wird dann empfohlen, wenn dein Insulintyp von den anderen Profilen nicht abgedeckt werden kann oder wenn eine Mischung verschiedener Insuline verwendet wird.

## BZ-Quelle

Hier kannst du auswählen, aus welcher Quelle AAPS die BZ-Werte empfangen soll. Weitere Informationen findest du auf der Seite [BZ-Quelle](BG-Source.rst).

* [xDrip+](https://xdrip-plus-updates.appspot.com/stable/xdrip-plus-latest.apk)
* Nightscout-Client BZ
* [MM640g](https://github.com/pazaan/600SeriesAndroidUploader/releases)
* [Glimp](https://play.google.com/store/apps/details?id=it.ct.glicemia&hl=de) - nur Version 4.15.57 und neuer werden unterstützt
* [gepatchte Dexcom App](https://github.com/dexcomapp/dexcomapp/) - Wähle zusätzlich in den Einstellungen "Sende BZ-Werte zu xDrip+", wenn du die xDrip+ Alarme nutzen willst. 
    
    ![Konfigurations-Generator - BZ-Quelle](../images/ConfBuild_BGSource.png)

* [Poctech](http://www.poctechcorp.com/en/contents/268/5682.html)

## Pumpe

Wähle die von Dir genutzte Pumpe.

* [Dana R](DanaR-Insulin-Pump.md)
* DanaR Korean (koreanische Version der DanaR)
* DanaRv2 (DanaR mit Firmware Upgrade)
* [Dana RS](DanaRS-Insulin-Pump.md)
* [Accu Chek Combo ](Accu-Chek-Combo-Pump.md) (erfordert Installation von Ruffy)
* ICT (für OpenLoop mit ICT, AAPS macht nur Behandlungsvorschläge, die du dann selbst mit dem Pen umsetzen musst)
* Virtuelle Pumpe (für OpenLoop mit nicht unterstützten Pumpen, AAPS macht nur Behandlungsvorschläge, die du dann selbst in deiner Pumpe umsetzen musst)

Wenn Du eine Dana-Pumpe nutzt, kannst Du in den **erweiterten Einstellungen** den Bluetooth Watchdog aktivieren, falls dies notwendig sein sollte. Er deaktiviert Bluetooth für eine Sekunde, falls keine Verbindung zur Pumpe möglich ist. Dies kann helfen, falls bei deinem Smartphone Probleme mit der Bluetooth-Verbindung auftreten.

## Empfindlichkeitserkennung

Hier kannst du auswählen, nach welchem Algorythmus AAPS die Insulinempfindlichkeit berechnen soll. Bei der Empfindlichkeitserkennung werden historische Daten "on the go" analysiert und Anpassungen vorgenommen, falls der Algorithmus feststellt, dass du sensibler oder weniger empfindlich auf das Insulin reagierst als üblich. Details zum Sensitivity Oref0 Algorithmus findest du in den [OpenAPS docs](http://openaps.readthedocs.io/en/latest/docs/walkthrough/phase-4/advanced-features.html#auto-sensitivity-mode).

Die berechnete Insulinempfindlichkeit kannst du verfolgen, indem du auf der Startseite im Auswahlmenü der angezeigten Kurven “Sensitivität” auswählst. Die weiße Linie zeigt dir das graphisch an. Die Empfindlichkeitserkennung ist erst freigeschaltet, wenn du [Ziel (objective) 8](../Usage/Objectives#objective-8-adjust-basals-and-ratios-if-needed-and-then-enable-autosens) erreicht hast.

### Resorptions-Einstellungen

Wenn Du Oref1 mit SMB musst du **min_5m_carbimpact** auf 8 ändern. Dieser Wert wird nur dann verwendet, wenn keine CGM-Werte empfangen werden oder körperliche Aktivitäten den Blutzuckeranstieg kompensieren, den AAPS normalerweise zur Berechnung des Kohlenhydratabbaus verwendet. So lange der Kohlenhydratabbau nicht dynamisch aus den Veränderungen des BZ ermittelt werden kann, wird ein Standardwert für den Abbau angesetzt. Im Prinzip ist es eine Notlauffunktion.

## APS

Wähle den gewünschten APS-Algorithmus für Therapie-Anpassungen. Die Details zum ausgewählten Algorithmus findest du im Reiter OpenAPS (OPAS).

* OpenAPS MA (meal assist, Algorithmus aus 2016)
* OpenAPS AMA (advanced meal assist, Algorithmus aus 2017)  
    Details zu OpenAPS AMA findest Du in der [OpenAPS Dokumentation](http://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autosens.html#advanced-meal-assist-or-ama). Einfach ausgedrückt profitierst Du von schnelleren AAPS-Korrekturen nach einem Mahlzeitenbolus, wenn du die Menge der Kohlenhydrate korrekt angegeben hast.  
    Hinweis: OpenAPS AMA steht ab dem [9. Ziel](../Usage/Objectives#objective-9-enabling-additional-oref0-features-for-daytime-use-such-as-advanced-meal-assist-ama) (objective 9) zur Verfügung.
* [OpenAPS SMB](../Usage/Open-APS-features.md) (super micro bolus, aktuellster Algorithmus für erfahrene Anwender  
    Hinweis: OpenAPS SMB steht ab dem [10. Ziel](../Usage/Objectives#objective-10-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb) (objective 10) zur Verfügung und min_5m_carbimpact muss auf 8 eingestellt werden (Konfigurations-Generator > Sensitivitätserkennung > Sensitivität Oref1 Einstellungen).

## Loop

Hier kannst du einstellen, ob du AAPS die automatische Steuerung erlauben willst oder nicht.

### Open Loop

AAPS wertet laufend alle verfügbaren Daten (IOB, COB, BZ-Wert) aus und macht dir bei Bedarf Behandlungsvorschläge, wie du deine Therapie anpassen solltest. Die Vorschläge werden nicht automatisch (wie im Closed Loop) ausgeführt, sondern müssen manuell in die Pumpe eingegeben werden. Wenn Du eine kompatible Pumpe (Dana R/RS oder Accu Chek Combo) verwendest, kann dies auch über eine Schaltfläche in AndroidAPS geschehen. Diese Option ist zum Kennenlernen der Funktionsweise gedacht oder falls du eine nicht unterstützte Pumpe verwendest.

### Closed Loop

AAPS wertet laufend alle verfügbaren Daten (IOB, COB, BZ-Wert) aus und passt die Behandlung bei Bedarf automatisch (also ohne weiteren Eingriff durch dich) an, um den eingestellten Zielbereich oder Zielwert zu erreichen (Bolusabgabe, temporäre Basalrate, Insulinabschaltung zur Hypovermeidung etc.). Der Closed Loop arbeitet im Rahmen zahlreicher Sicherheitsgrenzen, die du individuell einstellen kannst. Hinweis: Der Closed Loop steht ab dem [6. Ziel](../Usage/Objectives#objective-6-starting-to-close-the-loop-with-low-glucose-suspend) (objective 6) zur Verfügung und setzt eine unterstütze Pumpe voraus.

## Ziele (objectives - Lernprogramm)

AndroidAPS hat eine Reihe an Zielen (objectives), die du nach und nach erfüllen musst. Dies soll dich sicher durch die Einrichtung eines Closed Loop Systems führen. Das garantiert, dass du alles korrekt eingestellt hast und auch verstehst, was das System genau macht. Nur so kannst du dem System vertrauen.

Du solltest regelmäßig deine Einstellungen (inklusive deiner Fortschritte in den objectives) [exportieren](../Usage/ExportImportSettings.rst). Dann kannst du sie einfach importieren, wenn du später einmal dein Smartphone austauschen musst (neues Gerät, Displayschaden...).

Weitere Informationen findest du auf der Seite [Objectives (Ziele)](../Usage/Objectives.rst).

## Behandlungen

Der Reiter Behandlungen (BEH) zeigt dir die Behandlungen an, die zu Nightscout hochgeladen wurden. Falls du einen Eintrag editieren oder löschen willst (z.B. weil du weniger Kohlenhydrate gegessen hast, als erwartet) - wähle "Löschen" und trage den neuen Wert über den Reiter Careportal (CP) ein. Denke daran, ggf. die Zeit anzupassen.

## Allgemein

### Übersicht

Zeigt den aktuellen Status deines Loops und Schaltflächen für die häufigsten Aktionen an (Details dazu findest du im Bereich [Die Startseite](../Getting-Started/Screenshots.md)). Die Einstellungen erreichst Du über das Zahnradsymbol.

#### Bildschirm aktiv lassen

Die Option "Bildschirm aktiv lassen" hindert Android daran, den Bildschirm abzuschalten. Dies ist z.B. zu Präsentationszwecken hilfreich, es verbraucht aber sehr viel Batterie. Deshalb wird empfohlen, das Smartphone an ein Ladekabel anzuschließen.

#### Schaltflächen

Hier kannst du festlegen, welche Schaltflächen auf der Startseite angezeigt werden.

* Behandlungen
* Bolus-Rechner
* Insulin
* Kohlenhydrate
* CGM (öffnet xDrip+)
* Kalibrierung

Außerdem kannst du feste Werte für die Erhöhung der Insulin- und Kohlenhydratmengen festlegen und entscheiden, ob ein Notizfeld im Behandlungsdialog angezeigt werden soll.

#### QuickWizard-Einstellungen

Hier kannst du eine Schaltfläche für eine bestimmte Standardmahlzeit erstellen (KH und Berechnungsmethode für den Bolus), die dir dann auf dem Startbildschirm angezeigt wird. Dies ist sehr hilfreich, wenn du z.B. morgens häufig dasselbe isst (Button “1 Vollkornbrot”). Wenn du mehrere Standardmahlzeiten anlegst und für sie verschiedene Uhrzeiten angibst, dann hast du je nach Tageszeit auf dem Startbildschirm immer den passenden Standardmahlzeit-Button.

Hinweis: Die Schaltfläche wird außerhalb der eingestellten Zeiträume nicht angezeigt. Gleiches gilt, wenn genug Insulin (IOB) zur Verfügung steht, um die in den Schaltflächeneinstellungen definierte Kohlenhydratmenge abzudecken.

![QuickWizard Schaltfläche](../images/ConfBuild_QuickWizard.png)

#### Erweiterte Einstellungen

Aktiviere den SuperBolus im Wizard. Sei vorsichtig und aktiviere das erst, wenn du weißt, was es wirklich bewirkt. Im Wesentlichen wird das Basalinsulin der nächsten zwei Stunden zum Bolus hinzugefügt und die Basalrate für zwei Stunden auf null gesetzt. **AAPS Loop-Funktionen werden deaktiviert - also mit Vorsicht verwenden! Wenn Du SMB nutzt, werden die AAPS Loop-Funktionen entsprechend Deiner Einstellungen in ["SMB Basal-Limit in Minuten"](../Usage/Open-APS-features#max-minutes-of-basal-to-limit-smb-to) deaktiviert. Wenn Du SMB nicht nutzt, wird für zwei Stunden deaktiviert.** Details zum Superbolus findest Du [hier](https://www.diabetesnet.com/diabetes-technology/blue-skying/super-bolus).

### Aktionen

Einige Schaltflächen, um auf häufig verwendete Funktionen zugreifen zu können.

* Profilwechsel (Profil Switch - weitere Informationen dazu siehe Seite [Profile](../Usage/Profiles.md))
* Temporäres Ziel
* Temporäre Basalrate starten / abbrechen
* Verzögerter Bolus (nur für DanaR/RS und Combo)
* Vorfüllen/Füllen (wenn von der Pumpe unterstützt [aktuell Dana R/RS, Combo und Insight])
* Historie
* TDD (Total daily dose = Bolus + Basal pro Tag)

Einige Ärzte nutzen, gerade für neue Pumpenbenutzer, ein Basal-Bolus-Verhältnis von 50:50. Daher wird das Verhältnis als TDD / 2 * TBB (Total base basal = Summe der Basalrate innerhalb von 24 Stunden) berechnet. Andere bevorzugen einen Anteil von 32% bis 37% des Basalinsulins (TBB) am Gesamtinsulin (TDD). Wie die meisten Faustregeln gilt, dass dies nicht allgemeingültig ist. Hinweis: Bei dir und deinem Diabetes kann es ganz anders sein!

![Aktionen Tab](../images/ConfBuild_ConfBuild_Actions.png)

### Careportal

Im Careportal Tab (CP) können zu verschiedensten Ereignissen deiner Diabetestherapie Tagebucheinträge erstellt werden und es werden dort das Alter des Sensors, des Insulinreservoirs, der Kanüle und der Batterie angezeigt.

Hinweis: Es wird **kein Insulin** abgegeben, wenn du eine der Schaltflächen im Careportal verwendest (z.B. Mahlzeitenbolus, Korrekturbolus...)

Kohlenhydrate hingegen, die im Careportal erfasst werden (z.B. Kohlenhydrat Korrektur), werden in die Berechnung der COB (carbs on board) einbezogen.

![Careportal Tab](../images/ConfBuild_CarePortal.png)

### SMS-Kommunikator

Der SMS-Kommunikator erlaubt die Fernsteuerung einiger AndroidAPS Funktionen via SMS. Weitere Informationen zum Setup findest Du auf der Seite [SMS-Befehle](../Children/SMS-Commands.rst).

### Essen

Zeigt die im Nahrungsmittel-Editor erfassten Einträge an. Weitere Informationen zur Einrichtung der Nahrungsmitteldatenbank findest Du im [Nightscout Readme](https://github.com/nightscout/cgm-remote-monitor#food-custom-foods).

Hinweis: Die Einträge können nicht im AndroidAPS-Rechner verwendet werden. (reine Anzeigefunktion)

### Wear

Auf einer Android Wear Smartwatch können die Daten von AAPS angezeigt und einige Funktionen gesteuert werden (siehe [Seite Watchfaces](../Configuration/Watchfaces.md)). In den Einstellungen (Zahnradsymbol) kannst du die Variablen festlegen, die bei der Berechnung eines über die Uhr gegebenen Bolus berücksichtigt werden sollen (z.B. 15'-Trend, COB...).

Wenn Du Deinen Loop von der Uhr aus steuern willst (z.B. Bolus abgeben), aktiviere "Steuerung durch die Uhr".

![Wear-Einstellungen](../images/ConfBuild_Wear.png)

Über den Wear Tab oder das Hamburger Menü (oben links, falls der Wear Tab nicht angezeigt wird) kannst du

* Alle Daten erneut senden. Dies kann hilfreich sein, wenn die Uhr längere Zeit außer Reichweite war und du die Informationen an die Uhr pushen willst.
* Über das Smartphone die Einstellungen auf der Uhr öffnen.

### xDrip+ Statuszeile (Uhr)

Zeigt Loop Information in deinem xDrip+ Watchface (falls du nicht das AAPS/[AAPSv2 Watchface](../Configuration/Watchfaces.md) nutzt.)

### Dauer-Benachrichtigung

Zeigt im Dropdown- und Sperrbildschirm deines Smartphones eine kurze Übersicht über den aktuellen BZ, eine aktive temporäre Basalrate (%), die Basalrate (I. E./Std.) sowie IOB und COB.

![AAPS Widget](../images/ConfBuild_Widget.png)

### Nightscout-Client

Ns-Client Synchronisierung deiner AndroidAPS-Daten mit Nightscout einrichten.

Falls **Logge App-Start in Nightscout** aktiviert ist, ist jeder AndroidAPS Neustart in Nightscout sichtbar. Dies kann dabei helfen, Probleme mit der App zu erkennen (z.B. Batteriesparmodus für AAPS nicht deaktiviert), aber auch die Kurven in Nightscout mit Einträgen überfrachten.

#### Alarm-Optionen

AndroidAPS Alarme aktivieren/deaktivieren

![Alarm-Optionen](../images/ConfBuild_NSClient_Alarms.png)

#### Verbindungseinstellungen

Offline loopen, Roaming deaktivieren...

Wenn Du nur ein bestimmtes WLAN-Netzwerk verwenden möchtest, kannst du dessen **WiFi SSID** eingeben. Mehrere SSIDs können durch Semikolon (Strichpunkt) getrennt werden. Gib zum Löschen aller SSIDs ein Leerzeichen in das Feld ein.

![Nightscout Verbindungseinstellungen](../images/ConfBuild_ConnectionSettings.png)

#### Erweiterte Einstellungen

* Lade fehlende Blutzuckerwerte automatisch aus Nightscout nach.
* Ankündigungen aus Fehlern generieren Erstelle Nightscout-Einträge für Fehler-Dialoge und lokale Alarme. Sie werden auch im Careportal im Bereich Behandlungen angezeigt,
* Aktiviere Broadcasts für andere Apps (z. B. xDrip+)
* Zu Nightscout nur hochladen (keine Synchronisierung)
* Kein Upload zu Nightscout
* Verwende absolute statt prozentuale Basalraten -> Muss aktiviert sein, wenn du [Autotune](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html) nutzen willst.

![Nightscout erweiterte Einstellungen](../images/ConfBuild_NSClient_Advanced.png)

### Wartung

E-Mail-Adresse und Anzahl der zu sendenden Protokolle. Normalerweise keine Änderung notwendig.

### Konfigurations-Generator

Verwende einen Tab für den Konfigurations-Generator statt des Zugangs über das Hamburger-Menü.