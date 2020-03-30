Pour les utilisateurs de Eversense
**************************************************
The easiest way to use Eversense with AndroidAPS is to install the non-US modified `Eversense app <https://github.com/BernhardRo/Esel/blob/master/apk/Eversense_CGM_v1.0.410-patched.apk>`_ (and unistall the original one first).

**Attention : en désinstallant l'ancienne application, vos historiques de données de plus d'une semaine seront perdus !**

Pour enfin obtenir vos données dans AndroidAPS, vous devez installer `ESEL <https://github.com/BernhardRo/Esel/blob/master/apk/esel.apk>`_, activer "Send to AAPS and xDrip" dans ESEL et sélectionner "MM640g" comme source des glycémies dans le `Générateur de configuration <../Configuration/Config-Builder.html>`_ dans AndroidAPS. Comme les données de glycémie de Eversense peuvent parfois être incohérente, il est préférable d'activer "Smooth Data" dans ESEL, plutôt que d'activer "Utiliser delta basé sur moyenne courte" dans AAPS.

You can find  all APKs including the one for the US and another instruction for using xDrip with an Eversense `here <https://github.com/BernhardRo/Esel/tree/master/apk>`_.
