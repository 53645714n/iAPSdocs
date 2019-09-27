# Pompa Dana RS

*Te instrukcje dotyczą konfiguracji aplikacji i pompy, jeśli masz DanaRS wyprodukowaną po 2017 roku. Odwiedź [ Pompa insulinowa DanaR ](./DanaR-Insulin-Pump), jeśli zamiast niej masz oryginalną pompę DanaR.*

* W pompie DanaRS jest używana baza „BASAL A”. Istniejące dane zostaną zastąpione.

* W AndroidAPS przejdź do zakładki Konfiguracja > Pompa i wybierz „DanaRS”

* Wybierz Menu, dotykając 3 kropki w prawym górnym rogu. Wybierz Ustawienia

* Wybierz DanaRS sparuj nową pompę i kliknij swój numer seryjny DanaRS.
  
      ![AAPS pairing Dana RS](../images/AAPS_DanaRSPairing.png)
      

* Wybierz hasło pompy i wprowadź hasło. (Domyślne hasło to 1234)   
  ** Musisz potwierdzić powiązanie w pompie! ** Tak jak podczas parowania innych urządzeń po bluetoth (np. Smartfona i car audio).
  
      ![Dana RS confirm pairing](../images/DanaRS_Pairing.png)
      

* Wybierz Szybkość bolusa, aby zmienić domyślną prędkość bolusa (12 sek na 1u, 30 sek na 1u lub 60 sek na 1u).

* Zrestartuj telefon.

* Ustaw podstawowy krok na pompie na 0,01 U / h za pomocą menu Lekarze (patrz instrukcja obsługi pompy)

* Uaktywnij bolusy przedłużone w pompie

## Dana RS znane problemy

### Błąd podczas podawania insuliny

W przypadku utraty połączenia między AAPS i Dana RS podczas podawania insuliny w bolusie (tzn. Odchodzisz od telefonu, gdy Dana RS pompuje insulinę) zobaczysz następujący komunikat i usłyszysz dźwięk alarmu.

![Alarm podawania insuliny](../images/DanaRS_Error_bolus.png)

* In most cases this is just a communication issue and the correct amount of insulin is delivered.
* Check in pump history (either on the pump or through Dana tab > pump history > boluses) if correct bolus is given.
* Delete error entry in CP tab if you wish.
* Real amount is read and recorded on next connect. To force this press BT icon on dana tab or just wait for next connect.

## Dodatkowe informacje związane z wymianą telefonu

Jeśli chcesz zmienić telefon na nowy, konieczne są następujące kroki:

* ** Eksportuj ustawienia ** na starym telefonie
  
  * Menu "hamburger" (trzy poziome kreski w lewym górnym narożniku ekranu)
  * Konserwacja
  * Eksport ustawień
    
    ![Eksport ustawień AAPS](../images/AAPS_ExportSettings.png)

* **Przenieś** ustawienia ze starego telefonu na nowy, korzystając z lokalizacji pliku wyświetlonej podczas eksportu

* **Ręcznie sparuj** Dana RS z nowym telefonem 
  * Ponieważ importowane są także ustawienia połączenia pompy, AAPS na twoim nowym telefonie będzie już "znał" pompę i dlatego nie rozpocznie skanowania bluetooth. Dlatego nowy telefon i pompa muszą być sparowane ręcznie.
* **Zainstaluj AndroidAPS** na nowym telefonie.
* **Zaimportuj ustawienia** na nowym telefonie 
  * Menu "hamburger" (trzy poziome kreski w lewym górnym narożniku ekranu)
  * Konserwacja
  * Zaimportuj ustawienia

## Strefy czasowe, podróżowanie z pompą Dana RS

Informacje na temat podróżowania w różnych strefach czasowych można znaleźć w sekcji [ Strefa czasowa, podróżując z pompą ](../Usage/Timezone-traveling#danarv2-danars).