# Pompe DanaRS

*Ces instructions décrivent la configuration de l’application et de votre pompe si vous avez une DanaRS commercialisée depuis 2017. Visitez la [pompe à insuline Dana R](./DanaR-Insulin-Pump) si vous avez plutôt la pompe initiale DanaR.*

**DanaRS with new firmware v3 cannot be used with AndroidAPS!**

* Sur la pompe DanaRS, pompe « BASAL A » est utilisé par l'application. Les données existantes se font écrasé.

* Dans AndroidAPS, allez dans Générateur de configuration et sélectionnez « DanaRS »

* Sélectionnez le Menu en appuyant sur les 3 points en haut à droite. Sélectionnez le menu Préférences.

* Sélectionnez Appairage sur la nouvelle pompe DanaRS, puis cliquez sur le numéro de série de votre DanaRS.
  
      ![AAPS pairing Dana RS](../images/AAPS_DanaRSPairing.png)
      

* Sélectionnez Mot de passe de la pompe et saisissez votre mot de passe. (Le mot de passe par défaut est 1234)   
  ** Vous devez confirmer l'appairage sur la pompe ! ** C'est juste la façon dont vous êtes habitués à faire d'autres appairages bluetooth (par ex. le smartphone et l'audio de la voiture).
  
      ![DanaRS confirm pairing](../images/DanaRS_Pairing.png)
      

* Sélectionner la vitesse de Bolus pour changer la vitesse de Bolus par défaut souhaitée (12 sec par 1 U, 30 sec par 1 U ou 60 sec par 1 U).

* Redémarrez votre téléphone.

* Régler l'incrément Basale sur pompe à 0,01 U/h en utilisant le menu de Médecins (voir le guide de l’utilisateur de la pompe)

* Activez les Bolus Étendus sur la pompe

## Erreurs spécifiques à DanaRS

### Erreur lors de la distribution de l'insuline

In case the connection between AAPS and Dana RS is lost during bolus insulin delivery (i.e. you walk away from phone while Dana RS is pumping insulin) you will see the following message and hear an alarm sound.

![Alarm insulin delivery](../images/DanaRS_Error_bolus.png)

* Dans la plupart des cas c'est juste un problème de communication et la quantité d'insuline délivrée est correcte.
* Vérifiez dans l'historique de la pompe (à la pompe ou à l'aide de l'onglet Dana > historique de la pompe > bolus) si le bolus est correct.
* Supprimez l'entrée erreur dans l'onglet CP si vous le souhaitez.
* Le montant réel est lu et enregistré lors de la prochaine connexion. Pour forcer cette mise à jour, appuyez sur l'icône BT dans l'onglet dana ou attendez juste la prochaine connexion.

## Remarque spéciale lors du changement de téléphone

When switching to a new phone the following steps are neccessary:

* **Exportez les paramètres** sur votre ancien téléphone
  
  * Menu Hamburger (coin supérieur gauche de l'écran)
  * Maintenance
  * Exporter les paramètres
    
    ![Export des paramètres AAPS](../images/AAPS_ExportSettings.png)

* **Transférez** les paramètres de l'ancien au nouveau téléphone

* **Appairez manuellement** DanaRS avec le nouveau téléphone 
  * Comme les paramètres de connexion de la pompe sont également importés dans AAPS sur votre nouveau téléphone, il va déjà "connaître" la pompe et donc ne démarrera pas une analyse bluetooth. Par conséquent, le nouveau téléphone et la pompe doivent être appairés manuellement.
* **Installez AndroidAPS** sur le nouveau téléphone.
* **Importez les paramètres** Sur votre nouveau téléphone 
  * Menu Hamburger (coin supérieur gauche de l'écran)
  * Maintenance
  * Importer les paramètres

## Voyager avec différents fuseaux horaires avec la pompe DanaR

Pour plus d'informations sur les voyages dans différents fuseaux horaires, voir la section [Voyager avec différents fuseaux horaires avec une pompe](../Usage/Timezone-traveling#danarv2-danars).