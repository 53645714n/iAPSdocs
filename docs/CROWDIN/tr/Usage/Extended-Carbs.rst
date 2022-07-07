Yayma karbonhidratlar / "yCarbs"
**************************************************
yCarb nedir ve ne zaman faydalıdır?
==================================================
Düzenli bir pompa tedavisinde yayma boluslar, kan şekerini insülinin etkisinden daha uzun sürede artıran yağlı veya başka türlü yavaş emilen yemeklerle baş etmenin iyi bir yoludur. Bununla birlikte bir döngü sistemi kullanıyorsanız uzatılmış boluslar o kadar anlamlı değildir (ve teknik zorluklar yaratır), çünkü yayma bolus temelde sabit bir yüksek geçici bazal hızdır, bu da döngü mantığına aykırıdır, çünkü bazal hızı dinamik olarak ayarlanır. Ayrıntılar için aşağıdaki 'yayma bolus <../Usage/Extended-Carbs.html#why-extended-boluses-won-t-work-in-a-closed-loop-environment>'__ bölümüne bakın.

Döngü kullansanız da bu tip yemeklerle başetme ihtiyacı hala vardır. Bu nedenle, sürüm 2.0'dan itibaren AndroidAPS, yayma karbonhidratları veya yKarb'ları destekler.

yKarb, birkaç saat içinde parçalanan karbonhidratlardır. Yağ/protein içerikli olmayan standart öğünler için, karbonhidratları önden girmek (ve gerekirse ilk bolusu azaltmak) genellikle çok erken insülin verilmesini önlemek için yeterlidir.  But for slower-absorbing meals where full carb entry up front results in too much IOB from SMB, eCarbs can be used to more accurately simulate how the carbs (and any carb equivalents you enter for other macronutrients) are absorbed and influence the blood glucose. Bu bilgi ile döngü, dinamik yayma bolus olarak görülebilen bu karbonhidratlarla başa çıkmak için SMB'leri daha kademeli olarak yönetebilir (Normalde döngü SMB'ler olmadan da çalışmalıdır, ancak muhtemelen etkisi daha az olacaktır).

**Not:** yKarb, yağlı / protein ağırlıklı yemeklerle sınırlı değildir: kan şekerini artıran etkilerin olduğu herhangi bir durumda yardımcı olmak için de kullanılabilirler, örn. kortikosteroidler gibi diğer ilaçlar.

yKarb kullanmanın mekaniği
==================================================
yKarb girmek için, genel bakış (Giriş) sekmesindeki *Karbonhidrat* iletişim kutusunda bir süre, toplam karbonhidrat ve isteğe bağlı olarak bir zaman kayması ayarlayın (*aşağıdaki sayılar sadece örnektir, kullanım durumlarınız için tatmin edici glikoz yanıtına ulaşmak için kendi değerlerinizi denemeniz gerekecektir*):

.. image:: ../images/eCarbs_Dialog.png
  :alt: Karbonhidrat girişi

The eCarbs on the overview tab, note the carbs in brackets at the COB field, which shows the carbs in the future:

.. image:: ../images/eCarbs_Graph.png
  :alt: Grafikteki yKarb

Gelecekteki karbonhidrat girişleri, tedavi sekmesinde koyu turuncu renktedir:

.. image:: ../images/eCarbs_Treatment.png
  :alt: Tedavi sekmesinde gelecekteki yKarb


-----

Aşağıdaki linkte özellikle yağ ve proteini işlemenin bir yolu açıklanmaktadır: `https://adriansloop.blogspot.com/2018/04/page-margin-0.html <https://adriansloop.blogspot.com/2018/04 /page-margin-0.html>`_

-----

Önerilen kurulum, örnek senaryo ve önemli notlar
=====================================================================
The recommended setup is to use the OpenAPS SMB APS plugin, with SMBs enabled as well as the *Enable SMB with COB* preference being enabled.

Bir senaryo ör. Bir Pizza için, *hesap makinesi* aracılığıyla önden (kısmi) bir bolus vermek ve ardından 1 veya 2 saat sonra başlamak üzere 4-6 saat süreyle *karbonhidrat* düğmesini kullanarak kalan karbonhidratları girmek olabilir. 

**Önemli notlar:** Elbette sizin için hangi somut değerlerin işe yaradığını denemeniz ve görmeniz gerekecek. Algoritmayı daha fazla veya daha az agresif hale getirmek için *SMB'yi sınırlamak için maksimum bazal dakika* ayarını dikkatli bir şekilde ayarlayabilirsiniz.
Düşük karbonhidratlı, yüksek yağlı/proteinli öğünlerde, manuel bolus olmadan yalnızca yKarb kullanmak yeterli olabilir (yukarıdaki blog gönderisine bakın). yKarb oluşturulduğunda, girdileri yinelemeyi ve iyileştirmeyi kolaylaştırmak için tüm girdileri belgelemek için bir Careportal notu da oluşturulur.

Yayma bolus ve neden kapalı döngü ortamında çalışmaz?
=====================================================================
Yukarıda belirtildiği gibi, yayma veya çoklu yayma boluslar, kapalı döngü ortamında gerçekten çalışmaz. `Ayrıntılar için aşağıya bakın <../Usage/Extended-Carbs.html#why-extended-boluses-won-t-work-in-a-closed-loop-environment>`_

Yayma bolus ve açık döngüye geçiş - yalnızca Dana ve Insight pompası
-----------------------------------------------------------------------------
Bazı insanlar, özel gıdaları alıştıkları şekilde tedavi uygulamak istedikleri için, yine de AAPS'de yayma bolus kullanmak istiyorlardı. 

Bu nedenle 2.6 sürümünden itibaren Dana ve Insight pompa kullanıcıları için yayma bolus seçeneği vardır. 

* Kapalı döngü, yayma bolus çalıştığı süre boyunca otomatik olarak durdurulacak ve açık döngü moduna geçecektir. 
* Kalan Bolus ve toplam süre ana ekranda gösterilecektir.
* Insight pompasında `GBO emülasyonu <../Configuration/Accu-Chek-Insight-Pump.html#settings-in-aaps>`_ kullanılıyorsa yayma bolus *mevcut değildir*. 

.. image:: ../images/ExtendedBolus2_6.png
  :alt: AAPS 2.6'da yayma bolus

Yayma boluslar neden kapalı döngü ortamında çalışmaz?
----------------------------------------------------------------------------------------------------
1. Şimdi döngü 1,55Ü/s teslim edileceğini belirler. Bunun yayma bir bolus olarak mı yoksa GBO olarak mı iletildiği, algoritma için önemli değildir. Aslında, bazı pompalar yayma bolusu kullanır. O zaman ne olmalı? Çoğu pompa sürücüsü daha sonra yayma bolusu durdurur -> Başlatmanıza bile gerek yoktur.
2. Girdi olarak yayma bolus yaptıysanız, modelde ne olması gerekir?

   1. Bazal oran ile birlikte nötr olarak kabul edilmeli ve döngüye devam mı edilmeli? O zaman, örneğin, düşük yaşarsanız ve tüm "nötr" insülin alınırsa, döngü de bolusu azaltabilmelidir?
   2. Yayma bolus basitçe eklenmeli mi? Yani döngünün devam etmesine izin verilmeli mi? En kötü hipoda bile mi? Bunun çok iyi olduğunu düşünmüyorum: Bir hipo öngörülüyor ama önlenmemeli mi?
   
3. The IOB that the extended bolus builds up materializes after 5 minutes at the next run. Buna göre, döngü daha az bazal verecektir. Yani pek birdeğişiklik olmayacaktır... hipodan kaçınma olasılığı dışında.
