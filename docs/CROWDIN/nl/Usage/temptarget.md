# Tijdelijk streefdoel

## Wat is een Tijdelijk streefdoel en hoe kan ik dat instellen?

Met een Tijdelijk streefdoel ("Temp-Target” of TT in het Engels), kun je het streefdoel wijzigen voor jouw bloedglucose gedurende een zelfgekozen periode. Dit is vooral handig in bepaalde situaties: bij fysieke activiteit, tijdens een hypo (waarbij je koolhydraten nodig hebt) of wanneer je binnenkort gaat eten. Voor deze situaties heeft AAPS standaardinstellingen, die je zelf kunt kiezen. Tik hiervoor op de 3 puntjes in de rechter bovenhoek en kies Instellingen -> Overig -> Standaardwaardes tijdelijke streefdoelen. Hier heb je de mogelijkheid om de standaardinstellingen van AAPS te wijzigen.

![Set default temp targets](../images/TempTarget_Default.png)

To use one of the set “Default-Temp-Targets”, you can press long on your target in the right corner on the top in the overview-tab or use the shortcuts in the orange “Carbs” button. To manually set a [“Custom Temp-Target”](../Usage/temptarget#custom-temp-target) (BG value and/or duration) use “Custom“ after long-pressing your target in the top right corner or use the “Temporary Target“ button in the “Actions”-tab.

![Set temp target](../images/TempTarget_Set2.png)

## Hypo Tijdelijk streefdoel

This can be considered as the most important Temp-Target. There are several reasons for it:

1. Realizing you will go low: Usually, the Loop should handle it, but sometimes you can see better in advance than the loop, so the loop can react faster when it targets a higher blood glucose value.
2. When you eat hypo treatments carbs, your blood glucose will rise very fast. The loop will correct against the rising or even give SMBs if enabled. A "Hypo Temp-Target" can prevent that. 
3. (advanced, [objective 10](../Usage/Objectives#objective-10-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb)): You can enable “High Temp-Targets raises sensitivity” for Temp-Targets of 100mg/dl or 5.5mmol/l or higher in OpenAPS SMB, so AndroidAPS is more sensitive.
4. (advanced, [objective 10](../Usage/Objectives#objective-10-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb)): You can deactivate “SMB with high temp target”, so that even if you have COB > 0, "SMB with Temp-Target" or "SMB always" enabled and OpenAPS SMB active, AndroidAPS won’t give SMBs while high temp targets are active. 

Note: if you enter carbs with the carb button and your blood glucose is less then 72mg/dl or 4mmol/l, Hypo TT is automatically enabled.

## Activiteit Tijdelijk streefdoel

Before and during activity, you might want to have a higher target to prevent getting low. To simplify setting the Temp-Target, you can configure a default "Activity Temp-Target".

Advanced, [objective 10](../Usage/Objectives#objective-10-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb): The advantages about “Activity Temp-Target”, is that you can enable “High Temp-Targets raises sensitivity” for Temp-Targets higher or equal 100mg/dl or 5.5mmol/L in OpenAPS SMB. Then AndroidAPS is more sensitive. Some people do instead a profile switch before/while activity TT, but everybody is different. If “SMB with high Temp-Target” is deactivated, AndroidAPS won't use SMBs, even with COB > 0, "SMB with Temp-Target" or "SMB always" enabled and OpenAPS SMB active.

## Eet binnenkort Tijdelijk streefdoel

If you know, that you want to eat soon, you can enable this Temp-Target, so there is already more IOB before eating. Especially for those who don’t do prebolusing, it might be a good alternative to already get the blood glucose to a lower target. You can read more about the "Eating soon mode" in the article ['How to do “eating soon” mode'](https://diyps.org/2015/03/26/how-to-do-eating-soon-mode-diyps-lessons-learned/) or [here](https://diyps.org/tag/eating-soon-mode/).

Advanced, [objective 10](../Usage/Objectives#objective-10-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb): If you use OpenAPS SMB and have “Low temptarget lowers sensitivity”, AndroidAPS works a little bit more aggressive. Requirement is a Temp-Target less than 100mg/dl or 5.5mmol/l for this option.

## Aangepast Tijdelijk streefdoel

Sometimes, you just want to have a temp target other than the default ones. You can set one by long pressing on the target (range) on the right corner in overview or in the “Action”-Tab.

![Set temp target through Action tab](../images/TempTarget_ActionTab.png)