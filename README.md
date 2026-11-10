# Rutas de transporte público del Cusco (2024)

Primera digitalización abierta de las **36 rutas de transporte público urbano e interurbano** que operan en la ciudad del Cusco (Perú), en formato geoespacial (GeoJSON) y tabular (CSV).

Hasta ahora, los recorridos de estas rutas solo estaban disponibles como imágenes dentro de informes técnicos en PDF. Este conjunto permite analizarlos con cualquier SIG o lenguaje de programación.

## Contenido

| Archivo | Descripción |
|---|---|
| `datos/rutas_transporte_publico_cusco_2024.geojson` | 36 líneas (WGS 84, EPSG:4326), una por ruta, con sus atributos |
| `datos/rutas_transporte_publico_cusco_2024.csv` | Tabla de atributos sin geometría |

### Atributos

| Campo | Descripción |
|---|---|
| `codigo` | Código de la ruta (RTU = urbana, RTI = interurbana) |
| `empresa` | Empresa concesionaria |
| `tipo` | urbana / interurbana |
| `intervalo_min` | Intervalo entre buses (minutos), según el modelo de transporte del PMUS |
| `buses_hora` | Frecuencia equivalente (60 / intervalo) |
| `longitud_km` | Longitud del recorrido completo (ida y vuelta) |
| `referencia_temporal` | Fecha de referencia del trazado (conteos a bordo de noviembre de 2024) |
| `fuente` | Origen del trazo y de la frecuencia |

## Método

1. **Fuente del trazo.** Mapas por ruta del Anexo 10 («Carga por ruta de transporte público») del Entregable 02 del estudio del Plan de Movilidad Urbana Sostenible del Cusco, elaborados a partir de conteos de ascenso y descenso a bordo de noviembre de 2024.
2. **Extracción.** La línea de cada ruta se aisló por segmentación de color y grosor (OpenCV), se georreferenció contra la red vial de OpenStreetMap y se reconstruyó como un recorrido continuo sobre el grafo de calles (NetworkX).
3. **Control.** Cada ruta se comparó visualmente con su mapa original. El nombre de la empresa de la RTU-11B figura en la fuente como «Luis Vallero Santori» y se corrigió a «Luis Vallejos Santoni».
4. **Frecuencias.** Tabla 5 del Entregable 03 (modelo de transporte) del mismo estudio.

## Limitaciones

- No son datos oficiales. Las rutas no se verificaron en campo con trazas GPS.
- No incluye la ubicación de paraderos.
- Las frecuencias son las codificadas en el modelo del PMUS, no frecuencias observadas.
- Representa la red de 2024; no incluye las modificaciones del Plan Regulador de Rutas 2025.

## Licencia

Los datos se publican bajo la **Open Database License (ODbL) 1.0**, porque la geometría está ajustada a la red de OpenStreetMap (© colaboradores de OpenStreetMap, ODbL). Puedes usarlos, compartirlos y adaptarlos citando la fuente; las bases derivadas deben compartirse con la misma licencia.

Fuentes que deben reconocerse al usar estos datos:
- Consorcio PMUS (2026a). *Entregable 02: Estudio de caracterización de la demanda (Origen-Destino)*, Versión 3. COPESCO, PRODER y Municipalidad Provincial del Cusco.
- Consorcio PMUS (2026b). *Entregable 03: Modelo de transporte*, Versión 3. COPESCO, PRODER y Municipalidad Provincial del Cusco.
- © OpenStreetMap contributors.

## Cómo citar

Contreras Valenzuela, R. S. (2026). *Rutas de transporte público del Cusco (2024)* [Conjunto de datos]. Ver `CITATION.cff`.

Este conjunto acompaña el artículo «Desiertos de transporte en el Cusco: desigualdad socioespacial en el acceso al transporte público urbano según estrato de ingreso».
