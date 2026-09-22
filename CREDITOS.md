# Créditos y licencias de los modelos 3D

Fecha de la última revisión: **22-09-2026**.

## Resumen

| Marcador | Archivo | Origen | Licencia | Autor |
|---|---|---|---|---|
| 0 | `modelos/placa_base.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 1 | `modelos/cpu.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 2 | `modelos/disipador.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 3 | `modelos/ram.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 4 | `modelos/gpu.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 5 | `modelos/fuente.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 6 | `modelos/caja.glb` | **Original de este proyecto** (Blender) | Uso libre del autor | Angel Ortiz |
| 7 | `modelos/almacenamiento.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 8 | `modelos/nvme.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 9 | `modelos/ventilador.glb` | Colección Ensamblaje-PC-3D (sustituto original en Blender pendiente de aprobar) | Ver nota (1) | Ver nota (1) |
| 12 | `modelos/tarjeta_red.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 13 | `modelos/tarjeta_sonido.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |
| 14 | `modelos/panel_io.glb` | Colección Ensamblaje-PC-3D | Ver nota (1) | Ver nota (1) |

Los marcadores 10, 11 y 15 no usan modelos: son diagramas generados con primitivas
de A-Frame dentro de `index.html`.

## Nota (1): procedencia pendiente de verificar

Los modelos heredados de la colección **Ensamblaje-PC-3D** llevan materiales con
nombres del tipo `Converted_Material #2209`, huella típica de una escena de
**3ds Max** exportada a glTF. **No consta en este repositorio quién es el autor
original ni con qué licencia se obtuvieron.** Mientras no se documente:

- Uso estrictamente **docente y no comercial** dentro del aula.
- No redistribuir los `.glb` fuera del material de clase.
- Si el Profesor localiza la web de descarga original, hay que anotar aquí autor,
  licencia y enlace.

Varios modelos llevan además **texturas con marcas registradas** (Thermaltake,
Intel Core i5-3470, Samsung 960 PRO, Apacer Panther, Aerocool VX Plus 600,
NVIDIA RTX 3080, Swissbit). Son marcas de sus respectivos titulares y aquí
aparecen solo con finalidad ilustrativa y educativa.

## Búsqueda de alternativas libres (22-09-2026)

Antes de repintar se buscaron sustitutos **CC0** en **Poly Pizza**
(<https://poly.pizza>) para las diez piezas de los cubos 1 y 2. Resultado:

| Búsqueda | Mejor candidato CC0 | Decisión |
|---|---|---|
| `motherboard`, `graphics card`, `pc case`, `power supply`, `computer fan` | Nada del ámbito (solo PC completos, ventiladores de techo, baterías) | Descartado |
| `ram memory` | «RAM» de **iPoly3D** (CC0 1.0) | Descargado y descartado |
| `motherboard` / `cpu` | «CPU» de **iPoly3D** (CC0 1.0) | Descargado y descartado |
| `ssd` | «SSD PCB» de **iPoly3D** (CC0 1.0) | Descargado y descartado |

Las tres piezas CC0 se descargaron y se renderizaron para compararlas: son
*low-poly* de estilo cartoon, con color plano saturado, sin texturas y sin
parámetros PBR. Pierden frente a los modelos que ya tenía el proyecto, que sí
llevan geometría real (zócalo, condensadores, ranuras, contactos) y texturas de
etiqueta. Por eso **no se ha sustituido ninguna pieza por una descarga externa**.

Si en el futuro se usa alguna de ellas, el crédito sería:
«Modelo *RAM* / *CPU* / *SSD PCB* de **iPoly3D**, vía Poly Pizza, licencia CC0 1.0».

## Estado del repintado PBR (22-09-2026)

Los modelos heredados venían con `metallic = 0` y `roughness = 0.86` en **todos**
sus materiales (huella del conversor de 3ds Max): de ahí el aspecto de cartulina
en AR. Se ha definido una paleta común (PCB verde mate, aluminio y acero
metálicos, plásticos negros, contactos dorados, conectores en plástico de color
apagado) y se aplica pieza a pieza.

**Aplicado en `modelos/`:**

- **`disipador.glb`** — pieza de prueba. Repintado PBR (aluminio, plástico negro)
  y optimizado de 207.888 a 89.728 triángulos con *planar decimate*, que no
  altera la silueta. De 6,53 a 3,70 MB.
- **Iluminación de `index.html`**: mapa de entorno por código + luz clave con
  sombra suave. Ver el apartado «Notas» del README.

**Aplicadas ya las nueve piezas restantes** (autorizadas por el Profesor tras
validar el disipador; `variantes/pendiente_pbr/` queda vacía):

| Pieza | Trabajo hecho | Peso antes → después (bytes) |
|---|---|---|
| `placa_base.glb` | Repintado PBR | 3.975.208 → 3.974.688 |
| `cpu.glb` | **Quitados los dos SSD de 2,5" que flotaban dentro** + repintado | 4.334.360 → 4.573.200 |
| `ram.glb` | **Sustituido el SO-DIMM de portátil por el DIMM de sobremesa** de `variantes/` | 2.992.648 → 2.237.040 |
| `gpu.glb` | **Sustituida la tarjeta genérica AGP por la de carcasa** de `variantes/` | 3.706.836 → 2.202.392 |
| `fuente.glb` | Repintado PBR | 2.592.272 → 2.592.060 |
| `caja.glb` | Ajuste fino de materiales (chasis más especular, huecos más oscuros) | 309.088 → 308.920 |
| `almacenamiento.glb` | Repintado PBR + **carcasa de aluminio cepillado con etiqueta** (ver abajo) | 1.317.508 → 1.470.244 |
| `nvme.glb` | Optimizado de 398.538 a 55.000 triángulos + repintado | 8.555.820 → 2.997.728 |
| `ventilador.glb` | **Modelado de cero en Blender** (el anterior: 568 triángulos, aspas planas) | 35.372 → 126.104 |

Las diez piezas de los cubos 1 y 2 pasan de 34.667.732 a 24.364.324 bytes (−30 %).
Copias de seguridad de los diez originales en `variantes/<id>_pre_pbr.glb`, y de
`almacenamiento` antes de la etiqueta en `variantes/almacenamiento_pre_etiqueta.glb`.

## Textura original de `almacenamiento.glb` (22-09-2026)

La tapa del SSD venía con la textura de camuflaje del **Apacer Panther**, que en AR
se leía como una piedra y no como un disco. Tras quitarla, la tapa quedaba lisa y
sin rótulo. Se ha sustituido por una textura **creada de cero en Blender** para
este proyecto:

| Dato | Valor |
|---|---|
| Nombre dentro del GLB | `ssd_top` (1024 × 1024, JPEG, ≈ 124 kB) |
| Material | `carcasa_ssd_cepillada` (metallic 0,50 · roughness 0,38) |
| Contenido | aluminio cepillado procedural + etiqueta «SSD / 240 GB / SATA III 6 Gb/s», código de barras y número de serie ficticios |
| Autor | Angel Ortiz (generada por script en Blender 5.1) |
| Licencia | Original del proyecto, uso libre del autor |
| Marcas | **Ninguna**: no hay logotipos ni nombres comerciales reales |

La etiqueta no imita ninguna marca existente a propósito, para no añadir marcas
registradas al material de aula. La textura `Apacer-AP240GAS340G` sigue dentro del
GLB, pero solo en la cara inferior del disco.

## Capturas de comprobación

Renders de verificación en `variantes/capturas/`: `<pieza>_detalle.png` (primer
plano) y `<pieza>_antes_despues.png` (comparativa) de `cpu`, `ram`, `gpu`,
`almacenamiento` y `caja`.
