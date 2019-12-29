# Bomba Accu-Chek Insight

**Este software es parte de una solución de páncreas artificial de "hágalo usted mismo" y no es un producto, pero requiere que lea, aprenda y entienda el sistema, incluyendo cómo utilizarlo. No es algo que haga todo el manejo de su diabetes, pero le permite mejorar su diabetes y su calidad de vida si está dispuesto a dedicar el tiempo necesario. No te precipites, pero date tiempo para aprender. Solo Usted es responsable de lo que hace con él.**

* * *

## ***AVISO: ** Si ha estado utilizando la bomba con **SightRemote ** en el pasado, por favor, **actualice a la versión más reciente de AAPS ** y **desinstale SightRemote **.*

## Requisitos hardware y software

* Una bomba de insulina Roche Accu-Chek Combo (cualquier firmware, todos funcionan)
    
    Nota: AAPS escribirá los datos siempre en **primer perfil de tasa basal en la bomba**.

* Un teléfono Android (Basicamente todas las versiones de Android funcionarían, pero el AndroidAPS requiere al menos Android 5 (Lollipop)

* La aplicación AndroidAPS instalada en el teléfono

## Configuración

* La bomba Insight sólo debe estar conectado a un dispositivo a la vez. Si ha utilizado previamente el Insight remote control (medidor), debe quitar el medidor de la lista de dispositivos emparejados de la bomba: Menú > ajustes > Ajustes Comunicación > Quitar dispositivo
    
    ![Pantallazo de quitar el medidor Insight](../images/Insight_RemoveMeter.png)

* En [Config Builder ](../Configuration/Config-Builder) de la aplicación AndroidAPS, seleccione Accu-Chek Insight en la sección de la bomba
    
    ![Pantalla de Configuración de Insight](../images/Insight_ConfigBuilder.png)

* Toque el engranaje para abrir la configuración de la bomba.

* En configuración, pulsa en el botón 'Insight emparejamiento" en la parte superior de la pantalla. Debería ver una lista de todos los dispositivos Bluetooth cercanos (por debajo de la izquierda).
* En la bomba Insight, ir a Menu > Settings > Communication > Add Device. La bomba mostrará la siguiente pantalla (a la derecha) mostrando el número de serie de la bomba.
    
    ![Pantalla de emparejamiento 1 de Insight](../images/Insight_Pairing1.png)

* Volviendo a tu teléfono, toca el número de serie de la bomba en la lista de dispositivos Bluetooth. Entonces toca "Pair" para confirmar.
    
    ![Pantalla de emparejamiento 2 de Insight](../images/Insight_Pairing2.png)

* A continuación, la bomba y el teléfono mostrarán un código. Compruebe que los códigos sean los mismos en ambos dispositivos y confirme tanto en la bomba como en el teléfono.
    
    ![Pantalla de emparejamiento 3 de Insight](../images/Insight_Pairing3.png)

* Correcto! Una palmadita en la espalda por el éxito en la vinculación de la bomba con AndroidAPS.
    
    ![Pantalla de emparejamiento 4 de Insight](../images/Insight_Pairing4.png)

* Para comprobar todo está bien, vuelve a Config builder en AndroidAPS y pulsa sobre el engranaje de la bomba Insight para entrar en la configuración Insight, luego pulsa en el emparejamiento Insight y verás alguna información sobre la bomba:
    
    ![Pantalla de información de emparejamiento Insight](../images/Insight_PairingInformation.png)

Nota: No habrá una conexión permanente entre la bomba y el teléfono. Sólo se establecerá una conexión si es necesario (por ejemplo, fijar la tasa basal temporal, dar bolo, leer la historia de la bomba...). De lo contrario, la batería del teléfono y de la bomba se agotarían demasiado rápido.

## Valores en AAPS

Usted **no debe utilizar 'Siempre usar valores basales absolutos'** con la bomba Insight. En AAPS vaya a Preferencias > Nightscout-Client > Configuración Avanzada y asegúrese de que 'Siempre usar valores basales absolutos' está deshabilitado. Esto conduciría a valores de TBR falsos en la bomba Insight.

Only workaround at the moment is to **disable sync** with Nightscout (upload only) if you need to use autotune.

![Screenshot of Insight Settings](../images/Insight_pairing_V2_5.png)

In the Insight settings in AndroidAPS you can enable the following options:

* "Registrar cambios en el depósito": Esto registrará automáticamente un cambio de cartucho de insulina cuando se ejecute el programa de "llenar la cánula" en la bomba.
* "Registro de cambios de tubo": Esto agrega una nota a la base de datos de AndroidAPS al ejecutar el programa de "llenado de tubo" de la bomba.
* "Registro de cambio de cánula”: Esto agrega una nota a la base de datos de AndroidAPS cuando se ejecuta "el llenado de la cánula" del programa de la bomba. **Nota: un cambio de cánula también restablece el autosens.**
* "Registro de cambios de batería": Se registra el cambio de la batería cuando usted pone una batería nueva en la bomba.
* "Registro de cambios del modo de operación": Se agrega una nota en la base de datos de AndroidAPS cuando: se inicia, detiene o pausa la bomba.
* "Registro de alertas": Se agrega una nota en la base de datos AndroidAPS siempre que la bomba emite una alerta (excepto los recordatorios, el bolo y la cancelación de TBR, eventos que no se registran).
* "Habilitar emulación TBR": La bomba Insight sólo puede realizar las tasas basales temporales (TBRs) hasta el 250%. Para evitar esta restricción, La emulación TBR dará instrucciones a la bomba para que proporcione un bolus extendido para la insulina extra si solicita un TBR de más del 250%.
    
    **Sólo utilice un bolo extendido, ya que múltiples bolos extendidos al mismo tiempo pueden causar errores.**

* "Tiempo de recuperación": Esto define cuánto tiempo esperará el AndroidAPS antes de volver a intentarlo, después de un intento de conexión fallido. Puede elegir entre 0 y 20 segundos. Si experimenta problemas de conexión, elija un tiempo de espera más largo.   
      
    Ejemplo de min. tiempo de recuperación = 5 y max. tiempo de recuperación = 20   
      
    no conexión-> espere **5 ** seg.   
    reintento-> sin conexión-> espera **6 ** seg.   
    reintento-> sin conexión-> espera **7 ** seg.   
    reintento-> sin conexión-> espera **8 ** seg.   
    ...   
    reintento-> sin conexión-> espera **20 ** seg.   
    reintento-> sin conexión-> espera **20 ** seg.   
    ...

* "Retraso de desconexión": Define cuánto tiempo (en segundos) AndroidAPS esperará a desconectarse de la bomba después de que finalice una operación. El valor predeterminado es de 5 segundos.

For periods when pump was stopped AAPS will log a temp. basal rate with 0%.

In AndroidAPS, the Accu-Chek Insight tab shows the current status of the pump and has two buttons:

* "Actualizar": Refresca el estado de la bomba
* "Activar/Desactivar TBR notificación": Una bomba Insight estándar emite una alarma cuando un TBR está terminado. Este botón le permite habilitar o inhabilitar esta alarma sin necesidad de software de configuración.
    
    ![Pantalla de estados de Insight](../images/Insight_Status2.png)

## Configuración de la bomba

Configure alarms in the pump as follows:

* Menu > Settings > Device settings > Mode settings > Quiet > Signal > Sound
* Menu > Settings > Device settings > Mode settings > Quiet > Volume > 0 (remove all bars)
* Menu > Modes > Signal mode > Quiet

This will silence all alarms from the pump, allowing AndroidAPS to decide if an alarm is relevant to you. If AndroidAPS does not acknowledge an alarm, its volume will increase (first beep, then vibration).

Insight pumps with newer firmware will vibrate briefly every time a bolus is delivered (for example, when AndroidAPS issues an SMB or TBR emulation delivers an extended bolus). Vibration cannot be disabled. Older pumps do not vibrate in these circumstances.

## Reemplazo de la batería

Battery life for Insight when looping range from 10 to 14 days, max. 20 days. The user reporting this is using Energizer lithium batteries.

The Insight pump has a small internal battery to keep essential functions like the clock running while you are changing the removable battery. If changing the battery takes too long, this internal battery may run out of power, the clock will reset, and you will be asked to enter a new time and date after inserting a new battery. If this happens, all entries in AndroidAPS prior to the battery change will no longer be included in calculations as the correct time cannot be identified properly.

## Errores específicos de Insight

### Bolo extendido

Just use one extended bolus at a time as multiple extended boluses at the same time might cause errors.

### Tiempo de espera agotado (Time out)

Sometimes it might happen that the Insight pump does not answer during connection setup. In this case AAPS will display the following message: "Timeout during handshake - reset bluetooth".

![Insight Reset Bluetooth](../images/Insight_ResetBT.png)

In this case turn off bluetooth on pump AND smartphone for about 10 seconds and then turn it back on.

## Cruzando zonas horarias con la bomba Insight

For information on traveling across time zones see section [Timezone traveling with pumps](../Usage/Timezone-traveling#insight).