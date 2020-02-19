Objectifs
**************************************************

AndroidAPS a une série d'objectifs qui doivent être complétés pour vous guider à travers les fonctionnalités et les paramètres de la boucle sécurisée.  Ils s'assurent que vous avez correctement configuré tout ce qui est détaillé dans les sections ci-dessus, et que vous comprenez ce que votre système fait et pourquoi vous pouvez lui faire confiance.

Si vous **mettez à jour les téléphones** alors vous pouvez `exporter vos paramètres <../Usage/ExportImportSettings.html>`_ pour garder votre progression à travers les objectifs. Non seulement vos progrès à travers les objectifs de l'être sauvés, mais également vos paramètres de sécurité, tels que max bolus etc.  Si vous n'exportez pas et n'importez pas vos paramètres, vous devrez recommencer les objectifs depuis le début.  C'est une bonne idée de `sauvegarder vos paramètres <../Usage/ExportImportSettings.html>`_ souvent juste au cas où.
 
Objectif 1 : Paramétrage de la visualisation et la surveillance des données, analyse des débits Basal et des ratios
====================================================================================================
* Sélectionnez la source de glycémie adaptée à votre configuration.  Voir `Source GLY <../Configuration/BG-Source.html>`_ pour plus d'informations.
* Sélectionnez la bonne pompe dans le générateur de configuration (sélectionnez la Pompe virtuelle si vous utilisez un modèle de pompe sans pilote AndroidAPS pour le bouclage) afin de vous assurer que votre pompe peut communiquer avec AndroidAPS.  
* Si vous utilisez la pompe DanaR, assurez-vous d'avoir suivi les instructions `Pompe à insuline DanaR <../Configuration/DanaR-Insulin-Pump.html>`_ pour assurer le lien entre la pompe et AndroidAPS.
* Suivez les instructions de la page `Nightscout <../Installing-AndroidAPS/Nightscout.html>`_ pour s'assurer que Nightscout peut recevoir et afficher ces données.
* Notez que l'URL dans NSClient doit être **SANS /api/v1/** à la fin - voir les `paramètres NSClient dans les Préférences <../Configuration/Preferences.html#ns-client>`_.

*Vous devrez peut-être attendre la prochaine lecture de glycémie avant qu'AndroidAPS ne la reconnaisse.*

Objectif 2 : Apprendre comment contrôler AndroidAPS
==================================================
* Exécutez différentes actions dans AndroidAPS tel que décrit dans cet objectif.
* Cliquez sur le texte orange "Pas encore terminé" pour accéder à la liste des tâches.
* Des liens seront fournis pour vous guider si vous n'êtes pas encore familiarisé avec une action spécifique.

   .. image:: ../images/Objective2_V2_5.png
     :alt: Screenshot objective 2

Objectif 3 : Prouver ses connaissances
==================================================
* Passez un examen à choix multiples pour tester vos connaissances d'AndroidAPS.
* Cliquez sur le texte orange "Pas encore terminé" pour accéder à la page avec la question et répondre aux options.

   .. image:: ../images/Objective3_V2_5.png
     :alt: Screenshot objective 3

* Des liens sont fournis pour vous guider si vous n'êtes pas certain d'avoir les bonnes réponses.

Ignorer les objectifs
--------------------------------------------------
* Uniquement si vous avez utilisez une boucle fermée sur un autre système (par ex. OpenAPS, iOS Loop) auparavant et que vous pouvez le prouver (par ex. avec au moins 3 mois de données de bouclage dans Nightscout), vous pouvez envoyer un email à `objectives@androidaps.org <mailto:objectives@androidaps.org>`_ avec votre adresse NS et demander un code pour contourner le reste des objectifs.
* Veuillez noter qu'aucun support n'est fourni via ce compte de messagerie. Reportez-vous aux `ressources de support <../Where-To-Go-For-Help/Connect-with-other-users.html>`_ mentionnés dans cette documentation.

Objectif 4 : Démarrage de la boucle ouverte
==================================================
* Sélectionnez la Boucle Ouverte soit à partir des Préférences, soit en faisant un appui long sur le bouton de boucle en haut à gauche de l'écran d'accueil.
* Travaillez dans les `Préférences <../Configuration/Preferences.html>`_ pour la configurer pour vous.
* Adoptez manuellement au moins 20 suggestions de débits de base temporaires sur une période de 7 jours; saisissez-les sur votre pompe et confirmez dans AndroidAPS que vous les avez acceptés.  Assurez-vous que ces données apparaissent bien dans AndroidAPS et dans Nightscout.
* Activez des `Cibles temporaires <../Usage/temptarget.html>`_, si nécessaire. Utilisez des cibles temp. hypo temp pour éviter que le système ne corrige trop fortement une augmentation de la glycémie après une hypo. 

Réduire le nombre de notifications
--------------------------------------------------
* Pour réduire le nombre de décisions à prendre en mode Boucle Ouverte, définissez une large plage cible comme 90 - 150 mg/dl ou 5,0 - 8,5 mmol/l. * Vous pouvez même augmenter encore la limite supérieure (ou désactiver la Boucle ouverte) pendant la nuit. 
* Dans les Préférences, vous pouvez définir un pourcentage minimum pour suggérer un changement de débit de basal.

   .. image:: ../images/OpenLoop_MinimalRequestChange2.png
     :alt: Boucle ouverte Changement minimum
     
* De plus, vous n'avez pas besoin d'agir toutes les 5 minutes sur toutes les suggestions...

Objectif 5 : Compréhension de la Boucle Ouverte, y compris les propositions de débits Basal temporaires
====================================================================================================
* Commencez à comprendre le raisonnement qu'il y a derrière chaque recommandation de basal temporaire en regardant `Comprendre la logique de détermination basale <https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/Understand-determine-basal.html>`_ ainsi que les `lignes de prédiction dans l'écran d'accueil AndroidAPS <../Getting-Started/Screenshots.html#section-e>`_/Nightscout et le résumé des résultats des calculs dans votre onglet OpenAPS.
 
Vous voudrez définir votre objectif plus haut que d'habitude jusqu'à ce que vous ayez confiance dans les calculs et les paramètres.  Le système permet

* une cible basse au minimum de 72 mg/dl (4 mmol/l) ou un maximum de 180 mg/dl (10 mmol/l) 
* une cible haute au minimum de 90 mg/dl (5 mmol/l) et au maximum de 225 mg/dl (15 mmol/l)
* une cible temporaire en tant que simple valeur peut être n'importe où entre 72 mg/dl et 225 mg/dl (4 mmol/l et 15 mmol/l)

La cible est la valeur sur laquelle les calculs sont basés, et n'est pas la même que la page dans laquelle vous souhaitez avoir vos glycémies.  Si votre cible est très large (disons 50 mg/dl [3 mmol/l] ou plus de large), vous aurez souvent peu d'action de AAPS. C'est dû au fait que la glycémie devrait finalement se situer quelque part dans cette large plage, et par conséquent, peu de débits de base temporaires sont suggérés. 

You may want to experiment with adjusting your targets to be a closer together range (say, 1 or less mmol [20 mg/dl or less] wide) and observe how the behavior of your system changes as a result.  

You can view a wider range (green lines) on the graph for the values you aim to keep your blood glucose within by entering different values in `Preferences <../Configuration/Preferences.html>`_ > Range for Visualisation.
 
.. image:: ../images/sign_stop.png
  :alt: Stop sign

Stop here if you are open looping with a virtual pump - do not click Verify at the end of this objective.
------------------------------------------------------------------------------------------------------------------------------------------------------

.. image:: ./images/blank.png
  :alt: blank

Objectif 6 : Démarrage de la boucle fermée avec le système AGB ( Arrêt pour Glycémie Basse )
====================================================================================================
.. image:: ../images/sign_warning.png
  :alt: Warning sign
  
Closed loop will not correct high bg values in objective 6 as it is limited to low glucose suspend. High bg values have to be corrected manually by you!
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Select Closed Loop either from `Preferences <../Configuration/Preferences.html>`_ or by pressing and holding the Open Loop button in the top left of the home screen.
* Set your target range slightly higher than you usually aim for, just to be safe.
* Watch  how temporary basals are active by viewing the blue basal text on the homescreen or the blue basal render on the homescreen graph.
* Ensure your settings have supported AndroidAPS to avoid having to treat a low glucose over a period of 5 days.  If you are still having frequent or severe low glucose episodes then consider refining your DIA, basal, ISF and carb ratios.
* You don't have to change your settings. During objective 6 maxIOB setting is internally set to zero automatically. This override will be reversed when moving to objective 7.

*The system will override your maxIOB settings to zero, which means if blood glucose is dropping it can reduce basal for you, but if blood glucose is rising then it will only increase basal if the IOB is negative (from a previous Low Glucose Suspend), otherwise basal rates will remain the same as your selected profile.  Vous pouvez subir temporairement des pics de glycémie à la suite d'hypos sans pouvoir augmenter le débit de base sur le rebond.*

Objectif 7 : Réglage de la Boucle Fermée, augmentation de l'IA (Insuline Active) maximale au dessus de 0 et abaissement progressif des cibles glycémiques
====================================================================================================
* Raise your 'Maximum total IOB OpenAPS can’t go over' (in OpenAPS called 'max-iob') above 0 over a period of 1 day, the default recommendation is "average mealbolus + 3x max daily basal"(for SMB algorithm) or "3x max daily basal" (for older AMA algorithm) but you should slowly work up to this until you know your settings work for you (max daily basal = the maximum hourly value in any time segment of the day).

  This recommendation should be seen as a starting point. If you set to the 3x and you are seeing moves that push you to hard and fast then lower that number. If you are very resistant raise it a very little at a time.

   .. image:: ../images/MaxDailyBasal2.png
     :alt: max daily basal

* Once confident on how much IOB suits your looping patterns then reduce your targets to your desired level.


Objectif 8 : Ajustement des débits Basal et des ratios si nécessaire, puis activation de la fonction auto-sens
====================================================================================================
* You can use `autotune <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html>`_ as a one off to check your basals remain accurate or do a traditional basal test.
* Enable `autosens <../Usage/Open-APS-features.html>`_ over a period of 7 days and watch the white line on the homescreen graph show how your sensitivity to insulin may be rising or falling as a result of exercise or hormones etc. and keep an eye in the OpenAPS report tab how AndroidAPS is adjusting the basals and/or targets accordingly.

*Don’t forget to record your looping in `this form <http://bit.ly/nowlooping>`_ logging AndroidAPS as your type of DIY loop software, if you have not already done so.*


Objectif 9 : Activation de fonctionnalités supplémentaires en journée, comme l'Aide au Repas Améliorée ARA (AMA)
====================================================================================================
* Now you should feel confident with how AndroidAPS works and what settings reflect your diabetes best
* Then over a period of 28 days you can try additional features that automate even more of the work for you such as the `advanced meal assist <../Usage/Open-APS-features.html#advanced-meal-assist-ama>`_


Objectif 10 : Activation de fonctionnalités supplémentaires pour l'utilisation en journée, telles que la fonction SMB
====================================================================================================
* You must read the `SMB chapter in this wiki <../Usage/Open-APS-features.html#super-micro-bolus-smb>`_ and `chapter oref1 in openAPSdocs <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html>`_ to understand how SMB works, especially what's the idea behind zero-temping.
* Then you ought to `rise maxIOB <../Usage/Open-APS-features.html#maximum-total-iob-openaps-cant-go-over-openaps-max-iob>`_ to get SMBs working fine. maxIOB now includes all IOB, not just added basal. That is, if given a bolus of 8 U for a meal and maxIOB is 7 U, no SMBs will be delivered until IOB drops below 7 U. A good start is maxIOB = average mealbolus + 3x max daily basal (max daily basal = the maximum hourly value in any time segment of the day - see `objective 7 <../Usage/Objectives.html#objective-7-tuning-the-closed-loop-raising-max-iob-above-0-and-gradually-lowering-bg-targets>`_ for an illustration)
* min_5m_carbimpact default in absorption settings has changed from 3 to 8 going from AMA to SMB. If you are upgrading from AMA to SMB, you have to change it manually.
