# Características de OpenAPS

## Super Micro Bolo (SMB)

SMB, la forma abreviada de 'super micro bolo ', es la última característica de OpenAPS (desde 2018) dentro del algoritmo Oref1. En contraste con AMA, SMB no utiliza las tasas basales temporales para controlar los niveles de glucosa, pero principalmente usa **super pequeños microbolos**. En situaciones en las que la AMA añadiría 1,0 UI de insulina utilizando una tasa basal temporal, SMB entrega varios microbolos en pequeños pasos a intervalos de **5 minutos**, por ejemplo, 0,4 UI, 0,3 UI, 0,2 UI y 0,1 UI. Al mismo tiempo (por razones de seguridad), la tasa basal real se fija en 0 UI/ h durante un período determinado para evitar la sobredosis (**'cero-temporal'**). Esto permite que el sistema ajuste la glucosa en sangre más rápido que con el incremento temporal de la tasa basal en AMA.

Gracias a SMB, puede ser, básicamente, suficiente para las comidas bajas en carbohidratos el informar al sistema de la cantidad planeada de hidratos de carbono y dejar el resto a AAPS. Sin embargo, esto puede llevar a picos postprandiales más altos porque no es posible pre-enviar bolos. O usted le da, si es necesario con un pre-bolo, un **bolo inicial**, el cual **solo cubre parcialmente** los hidratos de carbono (e. 2/3 de la cantidad estimada) y dejar que la SMB cubra el resto.

La característica SMB contiene algunos mecanismos de seguridad:

1. La única dosis de SMB más grande sólo puede ser un valor más pequeño que:
    
    * el valor correspondiente a la tasa basal actual (ajustado por autoajuste/autosens) para la duración establecida en "Número máximo de minutos de basal para limitar a SMB a", por ejemplo, cantidad basal para los próximos 30 minutos, o
    * la mitad de la cantidad de insulina que se requiere actualmente, o
    * la parte restante de su valor de maxIOB en la configuración.

2. Probablemente notará a menudo bajas tasas basales temporales (llamadas 'bajas temporales') o tasas basales temporales en 0 U/h (llamadas 'cero-temporales'). Esto es por diseño por razones de seguridad y no tiene efectos negativos si el perfil se ha establecido correctamente. La curva de IOB es más significativa que el curso de las tasas basales temporales.

3. Cálculos adicionales para predecir el curso de la glucosa, por ejemplo, por UAM (comidas no anunciadas). Incluso sin la entrada manual de carbohidratos del usuario, UAM puede detectar automáticamente un incremento significativo en los niveles de glucosa debido a las comidas, adrenalina u otras influencias y tratar de ajustar esto con SMB. Para estar en el lado seguro, esto también funciona al revés y puede detener el SMB antes si se produce una caída inesperadamente rápida en la glucosa. Es por eso que UAM siempre debe estar activo en SMB.

**Debes haber completado [objetivo 10](../Usage/Objectives#objective-10-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb) para usar SMB.**

Vea también: [documentación OpenAPS para oref1 SMB](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html) y [información de Tims sobre SMB](http://www.diabettech.com/artificial-pancreas/understanding-smb-and-oref1/).

### Max U/h una basal temporal puede establecerse en (OpenAPS “max-basal”)

Este valor de seguridad determina la velocidad basal temporal máxima que puede entregar la bomba de insulina. El valor debe ser el mismo en la bomba y en la AAPS y debe ser al menos 3 veces el valor de la tasa basal más alta.

Ejemplo:

La tasa basal más alta de su perfil basal durante el día es de 1: 00 U/h. Entonces se recomienda un valor basal máximo de al menos 3 U/h.

Pero no se puede elegir ningún valor. AAPS limita el valor como un límite según la edad de los pacientes que usted ha seleccionado bajo la configuración. El valor más bajo permitido es para los niños y el más alto para adultos resistentes a la insulina.

AndroidAPS limita el valor de la forma siguiente:

* Niños: 2
* Adolescentes: 5
* Adultos: 10
* Adultos resistente a la insulina: 12

### El número máximo de IOB que OpenAPS no puede sobrepasar (OpenAPS "max-iob")

Este valor determina qué maxIOB tiene que ser considerado por AAPS en ejecución en modalidad de lazo cerrado. Si el IOB actual (por ejemplo, después de un bolo de comida) está por encima del valor definido, el lazo deja de dosificación de insulina hasta que el límite de IOB esté por debajo del valor dado.

Al utilizar OpenAPS SMB, max-IOB se calcula de forma diferente que en OpenAPS AMA. En AMA, maxIOB era sólo un parámetro de seguridad para basal IOB, mientras que en el modo SMB, también incluye el Bolo IOB. Un buen comienzo es

    maxIOB = promedio bolos de comidas + 3x basal máx
    

Sea cuidadoso y paciente, y sólo cambie los valores paso a paso. Es diferente para distintas personas y también depende de la dosis diaria total diaria (TDD). Por razones de seguridad, hay un límite, que depende de la edad del paciente. El 'límite ' para maxIOB es superior al de AMA.

* Niños: 3
* Adolescentes: 7
* Adultos: 12
* Adultos resistente a la insulina: 25

Véase también [OpenAPS documentación para SMB](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html#understanding-smb).

### Habilitar el autosensado de AMA

Aquí, puede elegir si desea utilizar la detección de sensibilidad [](../Configuration/Sensitivity-detection-and-COB.md) 'autosensado' o no.

### Activar SMB

Aquí puede habilitar o inhabilitar completamente la característica SMB.

### Habilitar SMB con COB

SMB está trabajando cuando hay COB activo.

### Habilitar SMB con Objetivos Temporales

SMB está trabajando cuando hay un objetivo temporal bajo o alto activo (comer pronto, actividad, hipo, personalizado)

### Habilitar SMB con Objetivo Temporal Alto

SMB está trabajando cuando hay un alto objetivo temporal activo (actividad, hipo). Esta opción puede limitar otros valores de SMB, es decir, si 'SMB con objetivos temporales' está habilitado y 'SMB con objetivos temporales altos' está desactivado, SMB sólo funciona con destinos bajos y no con altos temporales. Es lo mismo para SMB habilitado con COB: si se desactiva 'SMB con objetivos temporales altos', no hay ningún SMB con un destino de alto temporal, incluso si COB está activo.

### Habilitar SMB siempre

SMB está trabajando siempre (independiente de COB, objetivos temporales o bolos). Por razones de seguridad, esta opción es solamente para fuentes de BG con un buen sistema de filtrado para los datos ruidosos. Por ahora, sólo funciona con Dexcom G5, si utiliza la aplicación Dexcom (parcheado) o "modalidad nativa" en xDrip+. Si un valor BG tiene una desviación demasiado grande, el G5 no lo envía y espera a que el siguiente valor se haga en 5 minutos.

Para otros CGM/FGM como Freestyle Libre, 'SMB siempre' se desactiva hasta que xDrip+ tenga un mejor plugin de suavizado de ruido. Usted puede encontrar más [aquí](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md).

### Habilitar SMB después de Carbohidratos

SMB está trabajando por 6h después de los hidratos de carbono, incluso si COB está en 0. Por razones de seguridad, esta opción es solamente para fuentes de BG con un buen sistema de filtrado para los datos ruidosos. Por ahora, sólo funciona con Dexcom G5, si utiliza la aplicación Dexcom (parcheado) o "modalidad nativa" en xDrip+. Si un valor BG tiene una desviación demasiado grande, el G5 no lo envía y espera a que el siguiente valor se haga en 5 minutos.

Para otros MCG/FGM como Freestyle Libre, 'SMB siempre' se desactiva hasta que xDrip+ tenga un mejor plugin de suavizado de ruido. Usted puede encontrar [más información aquí](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md).

### Minutos máximos de basal para limitar SMB

Esta es una configuración importante. Este valor determina la cantidad de SMB que se puede dar en función de la cantidad de insulina basal en un momento determinado, cuando no está cubierto por los COB.

Esto hace que el SMB sea más agresivo. Para el principio, debe empezar por el valor predeterminado de 30 minutos. Después de cierta experiencia, puede aumentar el valor con pasos de 15 minutos y observar cómo están afectando estos cambios.

Se recomienda no establecer el valor superior a 90 minutos, ya que esto conduciría a un punto en el que el algoritmo podría no ser capaz de ajustar un BG decreciente con 0 IE/h basal ('cero-temporal'). También debe establecer alarmas, especialmente si todavía está probando nuevas configuraciones, lo que le avisa antes de entrar en hipoglucemias.

Valor predeterminado: 30 min.

### Activar UAM

Con esta opción habilitada, el algoritmo SMB puede reconocer las comidas no anunciadas. Esto es útil, si se olvida de decirle a AndroidAPS sobre sus carbohidratos o estima erroneamente sus carbohidratos haciendo que la cantidad ingresada de carbohidratos dea errónea o si una comida con mucha grasa y proteína tiene una duración más larga de lo esperado. Sin ninguna entrada de carbohidratos, UAM puede reconocer los incrementos de glucosa rápidos causados por carbohidratos, adrenalina, etc, e intenta ajustarlo con los SMB. Esto también funciona de la manera opuesta: si hay una reducción rápida de la glucosa, puede detener a las SMB antes.

**Por lo tanto, la UAM siempre debe activarse cuando se utiliza SMB.**

### Objetivo temporal elevado aumenta la sensibilidad

Si tiene habilitada esta opción, la sensibilidad a la insulina se incrementará mientras tenga un objetivo temporal superior a 100 mg/dl o 5,6 mmol/l. Esto significa que la ISF aumentará, mientras que la IC y la basal disminuirán.

### Objetivo temporal bajo reduce la sensibilidad

Si tiene habilitada esta opción, la sensibilidad a la insulina se reducirá mientras tenga un objetivo temporal inferior a 100 mg/dl o 5,6 mmol/l. Esto significa que el ISF disminuirá, mientras que el CI y el basal aumentarán.

### Ajustes avanzados

**Always use short average delta instead of simple data** If you enable this feature, AndroidAPS uses the short average delta/blood glucose from the last 15 minutes, which is usually the average of the last three values. Esto ayuda a AndroidAPS a trabajar más estable con los orígenes de datos ruidosos como xDrip + y Libre.

**Max daily safety multiplier** Este es un límite de seguridad importante. El valor predeterminado (que es poco probable que sea necesario ajustar) es 3. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 3x the highest hourly basal rate programmed in a user’s pump. Example: if your highest basal rate is 1.0 U/h and max daily safety multiplier is 3, then AndroidAPS can set a maximum temporary basal rate of 3.0 U/h (= 3 x 1.0 U/h).

Valor predeterminado: 3 (no se debe cambiar a menos que realmente necesite y sepa, lo que está haciendo)

**Current Basal safety multiplier** Este es otro límite de seguridad importante. El valor predeterminado (que también es poco probable que necesite ajustar) es 4. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 4x the current hourly basal rate programmed in a user’s pump.

Valor predeterminado: 4 (no se debe cambiar a menos que realmente necesite y sepa, lo que está haciendo)

* * *

## Asistente de comida avanzada (AMA)

AMA, la forma abreviada de "asistencia avanzada para comidas" es una función OpenAPS a partir de 2017 (oref0). OpenAPS Advanced Meal Assist (AMA) allows the system to high-temp more quickly after a meal bolus if you enter carbs reliably.

**Debes haber completado [objectivo 9](../Usage/Objectives#objective-9-enabling-additional-oref0-features-for-daytime-use-such-as-advanced-meal-assist-ama) para usar esta característica**

Usted puede encontrar más información en la documentación [Documentación de OpenAPS](http://openaps.readthedocs.io/en/latest/docs/walkthrough/phase-4/advanced-features.html#advanced-meal-assist-or-ama).

### Max U/h una basal temporal puede establecerse en (OpenAPS “max-basal")

This safety setting helps AndroidAPS from ever being capable of giving a dangerously high basal rate and limits the temp basal rate to x U/h. Se aconseja establecer esto en algo sensato. Una buena recomendación es tomar la más alta tasa basal en su perfil y multiplicarla por 4 o por lo menos 3. For example, if the highest basal rate in your profile is 1.0 U/h you could multiply that by 4 to get a value of 4 U/h and set the 4 as your safety parameter.

You cannot chose any value: For safety reason, there is a 'hard limit', which depends on the patient age. El límite para maxIOB es más bajo en AMA que en SMB. Para los niños, el valor es el más bajo mientras que para los adultos resistentes a la insulina, es el más grande.

Los parámetros codificados en AndroidAPS son los siguientes:

* Niños: 2
* Adolescentes: 5
* Adultos: 10
* Adultos resistente a la insulina: 12

### El máximo basal IOB que OpenAPS puede entregar \[U\] (OpenAPS "max-iob")

Este parámetro limita el máximo de IOB basal donde todavía funciona AndroidAPS. Si el IOB es más alto, deja de inyectar insulina basal adicional hasta que el basal IOB esté bajo el límite.

El valor predeterminado es 2, pero debe aumentar este parámetro lentamente para ver lo mucho que le afecta y qué valor se ajusta mejor. Es diferente para distintas personas y también depende de la dosis diaria total diaria (TDD). Por razones de seguridad, hay un límite, que depende de la edad del paciente. El límite para maxIOB es más bajo en AMA que en SMB.

* Niños: 3
* Adolescentes: 5
* Adultos: 7
* Adultos resistente a la insulina: 12

### Habilitar el autosensado de AMA

Aquí, puede elegir, si desea utilizar la [detección de sensibilidad](../Configuration/Sensitivity-detection-and-COB.md) autosensado o no.

### El autosensado ajusta los objetivos temporales también

Si tiene esta opción habilitada, el autosensado puede ajustar los objetivos (junto a basal, ISF e IC), también. Esto permite a AndroidAPS trabajar más 'agresivo' o no. Es posible que el destino real se alcance más rápido con esto.

### Ajustes avanzados

**Always use short average delta instead of simple data** If you enable this feature, AndroidAPS uses the short average delta/blood glucose from the last 15 minutes, which is usually the average of the last three values. Esto ayuda a AndroidAPS a trabajar más estable con los orígenes de datos ruidosos como xDrip + y Libre.

**Max daily safety multiplier** Este es un límite de seguridad importante. El valor predeterminado (que es poco probable que sea necesario ajustar) es 3. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 3x the highest hourly basal rate programmed in a user’s pump, or, if enabled, determined by autotune. Example: if your highest basal rate is 1.0 U/h and max daily safety multiplier is 3, then AndroidAPS can set a maximum temporary basal rate of 3.0 U/h (= 3 x 1.0 U/h).

Valor predeterminado: 3 (no se debe cambiar a menos que realmente necesite y sepa, lo que está haciendo)

**Current Basal safety multiplier** Este es otro límite de seguridad importante. El valor predeterminado (que también es poco probable que necesite ajustar) es 4. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 4x the current hourly basal rate programmed in a user’s pump, or, if enabled, determined by autotune.

Valor predeterminado: 4 (no se debe cambiar a menos que realmente necesite y sepa, lo que está haciendo)

**Bolus snooze dia divisor** The feature “bolus snooze” works after a meal bolus. AAPS doesn’t set low temporary basal rates after a meal in the period of the DIA divided by the “bolus snooze”-parameter. El valor predeterminado es 2. Eso significa que con un DIA de 5h, el "bolus snooze" sería 5h: 2 = 2.5h de tiempo.

Valor predeterminado: 2

* * *

## Asistente de comida (MA)

### Max U/h una basal temporal puede establecerse en (OpenAPS “max-basal")

This safety setting helps AndroidAPS from ever being capable of giving a dangerously high basal rate and limits the temp basal rate to x U/h. Se aconseja establecer esto en algo sensato. Una buena recomendación es tomar la más alta tasa basal en su perfil y multiplicarla por 4 o por lo menos 3. For example, if the highest basal rate in your profile is 1.0 U/h you could multiply that by 4 to get a value of 4 U/h and set the 4 as your safety parameter.

You cannot chose any value: For safety reason, there is a 'hard limit', which depends on the patient age. El limite para maxIOB es más bajo en MA que en SMB. Para los niños, el valor es el más bajo mientras que para los adultos resistentes a la insulina, es el más grande.

Los parámetros codificados en AndroidAPS son los siguientes:

* Niños: 2
* Adolescentes: 5
* Adultos: 10
* Adultos resistente a la insulina: 12

### El máximo basal IOB que OpenAPS puede entregar \[U\] (OpenAPS "max-iob")

Este parámetro limita el máximo de IOB basal donde todavía funciona AndroidAPS. Si el IOB es más alto, deja de inyectar insulina basal adicional hasta que el basal IOB esté bajo el límite.

El valor predeterminado es 2, pero debe aumentar este parámetro lentamente para ver lo mucho que le afecta y qué valor se ajusta mejor. Es diferente para distintas personas y también depende de la dosis diaria total diaria (TDD). Por razones de seguridad, hay un límite, que depende de la edad del paciente. El limite para maxIOB es más bajo en MA que en SMB.

* Niños: 3
* Adolescentes: 5
* Adultos: 7
* Adultos resistente a la insulina: 12

### Ajustes avanzados

**Always use short average delta instead of simple data** If you enable this feature, AndroidAPS uses the short average delta/blood glucose from the last 15 minutes, which is usually the average of the last three values. Esto ayuda a AndroidAPS a trabajar más estable con los orígenes de datos ruidosos como xDrip + y Libre.

**Bolus snooze dia divisor** The feature “bolus snooze” works after a meal bolus. AAPS doesn’t set low temporary basal rates after a meal in the period of the DIA divided by the “bolus snooze”-parameter. El valor predeterminado es 2.Eso significa que con un DIA de 5h, el "bolo snooze" sería 5h : 2 = 2.5 h de largo.

Valor predeterminado: 2