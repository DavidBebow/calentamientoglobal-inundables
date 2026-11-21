# Zonas inundables por periodo de retorno · calentamientoglobal.es

Fuente: © Ministerio para la Transición Ecológica y el Reto Demográfico. Sistema Nacional de Cartografía de Zonas Inundables (SNCZI). Uso libre citando la fuente (CC BY 4.0).
Ficheros de origen: T=100: Q100_3Ciclo_PB_20260727.shp (2026-07-27). Generado el 21/11/2026.

Método:
1. Se leen los shapefiles oficiales (ETRS89 UTM 30N) por lotes de 200 tramos y se normalizan los atributos (nombres, caudal máximo del tramo, año del estudio, régimen).
2. Un caudal inferior a 2 m³/s en un tramo de más de 20 km (sospechoso) se publica como «sin dato». Fechas anteriores a 1950 = sin fecha.
3. Las geometrías se simplifican a 2 m y se corrigen (make_valid); las hectáreas salen de esa geometría.
4. Cada mancha se cruza con los términos municipales (capa abierta derivada de los límites del INE, SpainLayers/AlexGPlay). Hectáreas y porcentaje por municipio salen de la unión de las manchas.
5. Detalle por municipio: mancha recortada al término, simplificada a 5 m (10 o 20 m si el fichero pasaría de 3 MB). Vista general por provincia: 25 m, sin polígonos de menos de 2.500 m².
6. Los km por municipio son un reparto proporcional a la superficie del tramo dentro del término (aproximados).
7. Donde no hay estudio no hay mancha: no significa que no haya riesgo. Cartografía orientativa; para trámites, el visor oficial del SNCZI.
8. Limitaciones: estudios de fechas distintas, mapas del tercer ciclo en revisión en algunas demarcaciones, Canarias pendiente, geometría simplificada.
9. Ficheros: index.json (índice), prov/t<T>/<provincia>.json, mun/t<T>/<INE>.json (detalle), mun/<INE>.json (cifras y frase).
10. Se regenera con: python3 inundables/inundables_procesar.py (ver claude/zonas-inundables-2026-11-21.md).
