# Detección sensibilidad

## Algoritmo de sensibilidad

Actualmente tenemos 4 modelos de detección de sensibilidad:

* Sensibilidad Oref0
* Sensibilidad AAPS
* Sensibilidad promedio ponderada
* Sensibilidad Oref1

### Sensibilidad Oref0

Básicamente, la sensibilidad se calcula a partir de los datos de las pasadas 24h y los carbohidratos (si no se absorben) se anulan después del tiempo especificado en las preferencias. The algorithm is similiar to OpenAPS Oref0, described in [OpenAPS Oref0 documentation](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autosens.html).

### Sensibilidad AAPS

La sensibilidad se calcula de la misma forma que en Oref0, pero puede especificar la cantidad de horas a contabilizar del pasado. La absorción de los mínima de los carbohidratos se calcula a partir del tiempo máximo de absorción de los carbohidratos en las preferencias

### Sensibilidad promedio ponderada

La sensibilidad se calcula como un promedio ponderado de las desviaciones. Puede especificar una hora en el pasado. Las desviaciones más recientes tienen un peso más alto. La absorción de los mínima de los carbohidratos se calcula a partir del tiempo máximo de absorción de los carbohidratos en las preferencias. Este algoritmo es más rápido para seguir los cambios de sensibilidad.

### Sensibilidad Oref1

La sensibilidad se calcula a partir de los datos de 8h en el pasado o en el último cambio de sitio(cánula), si es menor a 8h. Las carbohidratos (si no se absorben) se anulan tras el tiempo especificado en las preferencias. Únicamente el algoritmo Oref1 soporta las comidas no anunciadas (UAM). Esto significa que los tiempos al detectar UAM se excluyen del cálculo de sensibilidad. Por lo tanto, si utiliza SMB con UAM, tiene que elegir el algoritmo Oref1 para trabajar correctamente. For more information read [OpenAPS Oref1 documentation](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html).

## Carbohidratos simultáneos

Hay una diferencia significativa al utilizar AAPS, Promedio ponderado vs Oref0, Oref1. Los plugins de Oref sólo esperan una comida a la vez, que va siendo absorbida. Esto significa que la segunda comida comienza a absorberse después de que la primer comida fue totalmente absorvida. AAPS + Promedio ponderado empieza a absorber inmediatamente cuando se especifican los carbohidratos. Si hay más de una comida a bordo, la absorción mínima de carbohidratos se ajustará según el tamaño de la comida y el tiempo máximo de absorción. En consecuencia, la absorción mínima será más alta en comparación con los plugins de Oref.