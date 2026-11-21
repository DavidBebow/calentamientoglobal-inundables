# Zonas inundables por periodo de retorno · calentamientoglobal.es

Fuente: © Ministerio para la Transición Ecológica y el Reto Demográfico. Sistema Nacional de Cartografía de Zonas Inundables (SNCZI). Uso libre citando la fuente (CC BY 4.0).
Ficheros de origen: T=10: Q10_3Ciclo_PB_20260727.shp (2026-07-27), T=50: LAMINAS_Q50_ALTA_20260727.shp (2026-07-27), T=100: Q100_3Ciclo_PB_20260727.shp (2026-07-27), T=500: Q500_3Ciclo_PB_20260727.shp (2026-07-27). Generado el 21/11/2026.

Método:
1. Se leen los shapefiles oficiales (ETRS89 UTM 30N) por lotes de 200 tramos y se normalizan los atributos (nombres, caudal máximo del tramo, año del estudio, régimen).
2. Un caudal inferior a 2 m³/s en un tramo de más de 20 km (sospechoso) se publica como «sin dato». Fechas anteriores a 1950 = sin fecha.
3. Las geometrías se simplifican a 2 m y se corrigen (make_valid); las hectáreas salen de esa geometría.
4. Cada mancha se cruza con los términos municipales (capa abierta derivada de los límites del INE, SpainLayers/AlexGPlay). Hectáreas y porcentaje por municipio salen de la unión de las manchas.
5. Detalle por municipio: mancha recortada al término, simplificada a 5 m (10 o 20 m si el fichero pasaría de 3 MB). Vista general por provincia: 25 m, sin polígonos de menos de 2.500 m².
6. Los km por municipio son un reparto proporcional a la superficie del tramo dentro del término (aproximados).
7. Donde no hay estudio no hay mancha: no significa que no haya riesgo. Cartografía orientativa; para trámites, el visor oficial del SNCZI.
8. Limitaciones: estudios de fechas distintas, mapas del tercer ciclo en revisión en algunas demarcaciones, Canarias pendiente, geometría simplificada.
9. Ficheros: index.json (índice), nac/t<T>.json (vista nacional ligera), prov/t<T>/<provincia>.json, mun/t<T>/<INE>.json (detalle), mun/<INE>.json (cifras y frase).
   Vista nacional (rio, q): T=10 a 600 m sin manchas de menos de 30 ha; T=50 a 450 m sin manchas de menos de 20 ha; T=100 a 900 m sin manchas de menos de 50 ha; T=500 a 900 m sin manchas de menos de 50 ha. Los estudios de T=10 y T=50 cubren menos cauces que los de T=100 y T=500; T=50 incluye 71 tramos de delimitación puramente geomorfológica («probabilidad muy alta»).
10. Se regenera con: python3 inundables/inundables_procesar.py (ver claude/zonas-inundables-2026-11-21.md).
