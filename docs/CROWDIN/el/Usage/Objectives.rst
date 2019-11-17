Στόχοι
**********

Το AndroidAPS διαθέτει μια σειρά στόχων που πρέπει να ολοκληρωθούν για να σας καθοδηγήσουν στα χαρακτηριστικά και τις ρυθμίσεις του ασφαλούς κυκλώματος.  Εξασφαλίζουν ότι έχετε ρυθμίσει σωστά όλες τις λεπτομέριες στις παραπάνω ενότητες και ότι καταλαβαίνετε τι κάνει το σύστημά και γιατί μπορείτε να το εμπιστευτείτε.

If you are **upgrading phones** then you can `export your settings <../Usage/ExportImportSettings.html>`_ to keep your progress through the objectives. Όχι μόνο θα αποθηκευτεί η πρόοδός σας μέσω των στόχων, αλλά και οι ρυθμίσεις ασφαλείας σας όπως το μέγιστο bolus κ. λπ.  Αν δεν εξάγετε και δεν εισάγετε τις ρυθμίσεις σας, θα χρειαστεί να ξεκινήσετε πάλι τους στόχους από την αρχή.  It is a good idea to `backup your settings <../Usage/ExportImportSettings.html>`_ frequently just in case.
 
Στόχος 1: Δημιουργία οπτικοποίησης και παρακολούθησης, ανάλυση βασικού δεδομένων και αναλογιών
=================================================================================
* Select the right blood glucose source for your setup.  See `BG Source <../Configuration/BG-Source.html>`_ for more information.
* Select the right Pump in ConfigBuilder (select Virtual Pump if you are using a pump model with no AndroidAPS driver for looping) to ensure your pump status can communicate with AndroidAPS.  
* If using DanaR pump then ensure you have followed `DanaR Insulin Pump <../Configuration/DanaR-Insulin-Pump.html>`_ instructions to ensure the link between pump and AndroidAPS.
* Follow instructions in `Nightscout <../Installing-AndroidAPS/Nightscout.html>`_ page to ensure Nightscout can receive and display this data.
* Note that URL in NSClient must be **WITHOUT /api/v1/** at the end - see `NSClient settings in Preferences <../Configuration/Preferences.html#ns-client>`_.

*You may need to wait for the next blood glucose reading to arrive before AndroidAPS will recognise it.*

Objective 2: Learn how to control AndroidAPS
============================
* Perform several actions in AndroidAPS as described in this objective.
* Click on the orange text "Not completed yet" to access the to-dos.
* Links will be provided to guide you in case you are not familiar with a specific action yet.

   .. image:: ../images/Objective2_V2_5.png
     :alt: Screenshot objective 2

Objective 3: Prove your knowledge
=================================
* Pass a multiple-choice exam testing your AndroidAPS knowledge.
* Click on the orange text "Not completed yet" to access the page with the question and answering options.

   .. image:: ../images/Objective3_V2_5.png
     :alt: Screenshot objective 3

* Links will be provided to guide you in case you are unsure about the correct answers yet.
* Only if you have been closed looping with another system (i.e. OpenAPS, iOS Loop) before and can proof this (i.e. at least 3 months of looping data in Nightscout), you can send an email to `objectives@androidaps.org <mailto:objectives@androidaps.org>`_ with your NS address and request code to bypass the rest of objectives.

Objective 4: Starting on an open loop
=====================================
* Select Open Loop either from Preferences, or by pressing and holding the Loop button in top left of the home screen.
* Work through the `Preferences <../Configuration/Preferences.html>`_ to set up for you.
* Manually enact at least 20 of the temporary basal rate suggestions over a period of 7 days; input them to your pump and confirm in AndroidAPS that you have accepted them.  Βεβαιωθείτε ότι τα δεδομένα αυτά εμφανίζονται σε AndroidAPS και Nightscout.
* Enable `temp targets <../Usage/temptarget.html>`_ if necessary. Χρησιμοποιήστε στόχους υπογλυκαιμίας για να αποφύγετε ότι το σύστημα θα διορθώσει πολύ έντονα λόγω αύξησης της γλυκόζης αίματος μετά από υπογλυκαιμία. 

Objective 5: Understanding your open loop, including its temp basal recommendations
===================================================================================
* Start to understand the thinking behind the temp basal recommendations by looking at the `determine basal logic <https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/Understand-determine-basal.html>`_ and both the `forecast line in AndroidAPS homescreen <../Getting-Started/Screenshots.html#section-e>`_/Nightscout and the summary of outputs from the calculations in your OpenAPS tab.
 
Θα θελήσετε να ορίσετε το στόχο σας υψηλότερο από το συνηθισμένο έως ότου είστε σίγουροι για τους υπολογισμούς και τις ρυθμίσεις.  System allows

* a low target to be a minimum of 4 mmol (72 mg/dl) or maximum of 10 mmol (180 mg/dl) 
* a high target to be a minimum of 5 mmol (90 mg/dl) and maximum of 15 mmol (225 mg/dl)
* a temporary target as a single value can be anywhere in the range of 4 mmol to 15 mmol (72 mg/dl to 225 mg/dl)

Ο στόχος είναι η τιμή στην οποία βασίζονται οι υπολογισμοί και όχι η ίδια με εκείνη που στοχεύετε να διατηρείτε τις τιμές γλυκόζης στο αίμα σας μέσα.  If your target is very wide (say, 3 or more mmol [50 mg/dl or more] wide), you will often find little AAPS action. This is because blood glucose is eventually predicted to be somewhere in that wide range and therefore not many fluctuating temporary basal rates are suggested. 

You may want to experiment with adjusting your targets to be a closer together range (say, 1 or less mmol [20 mg/dl or less] wide), and observe how the behavior of your system changes as a result.  

You can view a wider range (green lines) on the graph for the values you aim to keep your blood glucose within by entering different values in `Preferences <../Configuration/Preferences.html>`_ > Range for Visualisation.
 
.. image:: ../images/sign_stop.png
  :alt: Stop sign

Σταματήστε εδώ αν είστε σε ανοιχτό κύκλωμα με μια εικονική αντλία - μην κάνετε κλικ στην επιλογή Επαλήθευση στο τέλος αυτού του στόχου.
--------------------------

.. image:: ./images/blank.png
  :alt: blank

Objective 6: Starting to close the loop with Low Glucose Suspend
================================================================
.. image:: ../images/sign_warning.png
  :alt: Warning sign
  
Closed loop will not correct high bg values in objective 6 as it is limited to low glucose suspend. Οι υψηλές τιμές BG πρέπει να διορθωθούν χειροκίνητα από εσάς!
---------------------------

* Select Closed Loop either from `Preferences <../Configuration/Preferences.html>`_ or by pressing and holding the Open Loop button in the top left of the home screen.
* Set your target range slightly higher than you usually aim for, just to be safe.
* Watch  how temporary basals are active by viewing the blue basal text on the homescreen or the blue basal render on the homescreen graph.
* Ensure your settings have supported AndroidAPS to avoid having to treat a low glucose over a period of 5 days.  Εάν εξακολουθείτε να εμφανίζετε συχνά ή σοβαρά επεισόδια χαμηλής γλυκόζης, εξετάστε το ενδεχόμενο αλλαγής των αναλογιών DIA, βασικών, ISF και υδατανθράκων.

*The system will override your maxIOB settings to zero, which means if blood glucose is dropping it can reduce basal for you, but if blood glucose is rising then it will only increase basal if the IOB is negative (from a previous Low Glucose Suspend), otherwise basal rates will remain the same as your selected profile.  You may temporarily experience spikes following treated hypos without the ability to increase basal on the rebound.*

Objective 7: Tuning the closed loop, raising max IOB above 0 and gradually lowering BG targets
=========================================================
* Raise your 'Maximum total IOB OpenAPS can’t go over' (in OpenAPS called 'max-iob') above 0 over a period of 1 day, the default recommendation is "average mealbolus + 3x max daily basal"(for SMB algorithm) or "3x max daily basal" (for older AMA algorithm) but you should slowly work up to this until you know your settings work for you (max daily basal = the maximum hourly value in any time segment of the day).

  Αυτή η σύσταση πρέπει να θεωρηθεί ως σημείο εκκίνησης. Εάν ρυθμίσετε στο 3x και βλέπετε κινήσεις που σας ωθούν έντονα και γρήγορα τότε μειώστε τον αριθμό. Εάν είστε πολύ ανθεκτικοί, αυξήστε το πολύ λίγο τη φορά.

   .. image:: ../images/MaxDailyBasal2.png
     :alt: max daily basal

* Once confident on how much IOB suits your looping patterns then reduce your targets to your desired level.


Objective 8: Adjust basals and ratios if needed, and then enable autosens
=============================================
* You can use `autotune <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html>`_ as a one off to check your basals remain accurate, or do a traditional basal test.
* Enable `autosens <../Usage/Open-APS-features.html>`_ over a period of 7 days and watch the white line on the homescreen graph show how your sensitivity to insulin may be rising or falling as a result of exercise or hormones etc, and keep an eye in the OpenAPS report tab how AndroidAPS is adjusting the basals and/or targets accordingly.

*Don’t forget to record your looping in `this form <http://bit.ly/nowlooping>`_ logging AndroidAPS as your type of DIY loop software, if you have not already done so.*


Objective 9: Enabling additional oref0 features for daytime use, such as advanced meal assist (AMA)
==============================================
* Now you should feel confident with how AndroidAPS works and what settings reflect your diabetes best
* Then over a period of 28 days you can try additional features that automate even more of the work for you such as the `advanced meal assist <../Usage/Open-APS-features.html#advanced-meal-assist-ama>`_


Objective 10: Enabling additional oref1 features for daytime use, such as super micro bolus (SMB)
===============================================
* You must read the `SMB chapter in this wiki <../Usage/Open-APS-features.html#super-micro-bolus-smb>`_ and `chapter oref1 in openAPSdocs <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html>`_ to understand how SMB works, especially what's the idea behind zero-temping.
* Then you ought to `rise maxIOB <../Usage/Open-APS-features.html#maximum-total-iob-openaps-cant-go-over-openaps-max-iob>`_ to get SMBs working fine. η μέγιστη IOB περιλαμβάνει τώρα όλα τα IOB, όχι μόνο βασικά. That is, if given a bolus of 8 U for a meal and maxIOB is 7 U, no SMBs will be delivered until IOB drops below 7 U. A good start is maxIOB = average mealbolus + 3x max daily basal (max daily basal = the maximum hourly value in any time segment of the day - see `objective 7 <../Usage/Objectives.html#objective-7-tuning-the-closed-loop-raising-max-iob-above-0-and-gradually-lowering-bg-targets>`_ for an illustration)
* min_5m_carbimpact default in absorption settings has changed from 3 to 8 going from AMA to SMB. Εάν κάνετε αναβάθμιση από AMA σε SMB, πρέπει να το αλλάξετε χειροκίνητα
