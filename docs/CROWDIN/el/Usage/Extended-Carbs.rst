Εκτεταμένοι υδατάνθρακες / "eCarbs"
=====
Με μια τακτική θεραπεία αντλίας, τα εκτεταμένα bolus είναι ένας καλός τρόπος αντιμετώπισης λιπαρών ή άλλως αργά απορροφούμενων γευμάτων που αυξάνουν τη γλυκόζη του αίματος για εκτεταμένη διάρκεια περισσότερο από την διάρκεια ζωής της ινσουλίνη στον οργανισμό. Σε ένα πλαίσιο κυκλώματος, ωστόσο, τα εκτεταμένα bolus δεν έχουν τόσο νόημα (και δημιουργούν τεχνικές δυσκολίες), επειδή είναι βασικά ένας σταθερός υψηλός προσωρινός βασικός ρυθμός, το οποίο αντίκειται στον τρόπο λειτουργίας του κυκλώματος, ο οποίος ρυθμίζει δυναμικά το βασικό ρυθμό. For details see `extended bolus <../Usage/Extended-Carbs.html#extended-bolus>`_ below.

Ωστόσο, η ανάγκη αντιμετώπισης τέτοιων γευμάτων εξακολουθεί να υπάρχει. Για το λόγο αυτό το AndroidAPS από την έκδοση 2.0 υποστηρίζει τους λεγόμενους εκτεταμένους υδατάνθρακες ή eCarbs.

τα eCarbs είναι υδατάνθρακες που διασπούντε σε αρκετές ώρες. Για τα συνηθισμένα γεύματα με περισσότερους υδατάνθρακες από ότι λίπος / πρωτεΐνη, η εισαγωγή των υδατανθράκων από πριν (και η μείωση του αρχικού bolus, αν χρειαστεί) είναι συνήθως αρκετή για να αποτρέψει την πρόωρη χορήγηση ινσουλίνης.  Αλλά για βραδέως απορροφησήμα γεύματα, όπου η πλήρης εισαγωγή υδατανθράκων από πριν οδηγεί σε υπερβολικά μεγάλο IOB από SMB, τα eCarbs μπορούν να χρησιμοποιηθούν για να προσομοιώσουν με μεγαλύτερη ακρίβεια πώς οι υδατάνθρακες (και τα ισοδύναμα υδατανθράκων που εισάγετε για άλλα μακροθρεπτικά συστατικά) απορροφώνται και επηρεάζουν τη γλυκόζη του αίματος. Με αυτές τις πληροφορίες, το κύκλωμα μπορεί να διαχειριστεί τις SMBs πιο σταδιακά για να αντιμετωπίσει αυτούς τους υδατάνθρακες, πράγμα που μπορεί να θεωρηθεί ως ένα δυναμικό εκτεταμένο bolus (αυτό θα πρέπει επίσης να λειτουργεί χωρίς SMBs, αλλά είναι πιθανώς λιγότερο αποτελεσματικό).

eCarbs aren't limited to fatty / protein heavy meals: they can be also be used to help in any situation where there are influences that increase the blood sugar, e.g. other medication like corticosteroids.

To enter eCarbs, set a duration in the _Carbs_ dialog on the overview tab, the total carbs and optionally a time shift:

.. image:: ../images/eCarbs_Dialog.png
  :alt: Enter carbs

Τα eCarbs στην καρτέλα "Επισκόπηση", σημειώστε τους υδατάνθρακες σε παρένθεση στο πεδίο COB, στο οποίο εμφανίζονται οι υδατάνθρακες στο μέλλον:

.. image:: ../images/eCarbs_Graph.png
  :alt: eCarbs in graph

Οι καταχωρίσεις υδατανθράκων που στο μέλλον θα είναι χρωματισμένες σε σκούρο πορτοκαλί στην καρτέλα θεραπείας:

.. image:: ../images/eCarbs_Treatment.png
  :alt: eCarbs in future in treatment tab


-----

A way to handle fat and protein with that feature is described here: `https://adriansloop.blogspot.co.at/2018/04/page-margin-0.html <https://adriansloop.blogspot.co.at/2018/04/page-margin-0.html>`_

-----

The recommended setup is to use the OpenAPS SMB APS plugin, with SMBs enabled as well as the _Enable SMB with COB_ preference being enabled.

A scenario e.g. for a Pizza might be to give a (partial) bolus up front via the _calculator_ and then use the _carbs_ button to enter the remaining carbs for a duration of 4-6 hours, starting after 1 or 2 hours. Θα πρέπει να δοκιμάσετε και να δείτε ποιες συγκεκριμένες αξίες λειτουργούν φυσικά για εσάς. You might also carefully adjust the setting _max minutes of basal to limit SMB to_ to make the algorithm more or less aggressive.
Με γεύματα χαμηλών υδατανθράκων, υψηλών λιπαρών / πρωτεϊνών μπορεί να αρκεί να χρησιμοποιείτε μόνο τα eCarbs χωρίς χειροκίνητα bolus (βλ. Την ανάρτηση του ιστολογίου παραπάνω).

Όταν δημιουργούνται τα eCarbs, δημιουργείται επίσης μια Σημείωση Careport για την τεκμηρίωση όλων των εισροών, για να διευκολυνθεί η επανάληψη και η βελτίωση των εισροών.

Εκτεταμένο bolus
=====
As mentioned above extended or multiwave boluses do not really work in a closed loop environment. Therefore there is no option to issue an extended bolus in AndroidAPS. Here's why:

1. The loop determines that now 1.55U/h is to be delivered. Whether this is delivered as an extended bolus or TBR does not matter to the algorithm. In fact, some of the pumps use the extended bolus. What should happen then? Most pump drivers then stop the extended bolus -> You didn't even need to start it.
2. If you had the extended bolus as input, what should happen in the model?

   1. Should it be considered neutral together with the BR and looped on it? Then the loop should also be able to reduce the bolus if, for example, you get too low and all the "neutral" insulin is taken away?
   2. Should the extended bolus simply be added? So the loop should simply be allowed to continue? Even in the worst hypo? I don't think this is so good: A hypo is foreseen but it must not be prevented?
   
3. The IOB that the extended bolus builds up materializes after 5 minutes at the next run. Accordingly, the loop would give less basal. So not much changes... except that the possibility of hypo avoidance is taken.
