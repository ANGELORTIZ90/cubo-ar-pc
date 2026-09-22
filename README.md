# Cubo AR — Componentes de PC (SMX)

Cubo de papel estilo "Merge Cube" con marcadores propios. Al enfocar una cara con la
cámara, el visor web muestra el componente de PC en 3D (modelos GLB del proyecto
Ensamblaje-PC-3D).

## Contenido

| Archivo | Función |
|---|---|
| `plantilla.html` | Plantilla imprimible del cubo 1 (abrir y Ctrl+P → PDF, escala 100%) |
| `plantilla2.html` | Plantilla imprimible del cubo 2 (incluye QR del visor y cara de título) |
| `plantilla-8cm.html` | Cubo 1 con caras de 8 cm, en 2 páginas A4 apaisadas (para webcams de portátil) |
| `plantilla2-8cm.html` | Cubo 2 con caras de 8 cm, en 2 páginas A4 apaisadas |
| `plantilla3.html` / `plantilla3-8cm.html` | Cubo 3: arquitectura del PC con diagramas animados |
| `plantilla4.html` / `plantilla4-8cm.html` | Cubo 4: conectividad y expansión (incluye QR y cara de título) |
| `index.html` | Visor AR web (A-Frame + AR.js, marcadores barcode 3x3) |
| `modelos/` | 13 modelos GLB de componentes de PC |
| `marcadores/` | Marcadores barcode 0-15 (colección oficial AR.js) |
| `qr-visor.png` | QR con la URL del visor publicado |
| `cubo1-6cm.pdf` / `cubo2-6cm.pdf` | PDFs listos para imprimir (A4 vertical, 100%) |
| `cubo1-8cm.pdf` / `cubo2-8cm.pdf` | PDFs listos para imprimir (A4 horizontal, 100%) |
| `cubo3-6cm.pdf` / `cubo3-8cm.pdf` | PDFs del cubo 3 |
| `cubo4-6cm.pdf` / `cubo4-8cm.pdf` | PDFs del cubo 4 |

## Caras de los cubos

| Marcador | Componente | Cubo |
|---|---|---|
| 0 | Placa base | 1 |
| 1 | Procesador (CPU) | 1 |
| 2 | Disipador de CPU | 1 |
| 3 | Memoria RAM | 1 |
| 4 | Tarjeta gráfica (GPU) | 1 |
| 5 | Fuente de alimentación | 1 |
| 6 | Caja / Torre | 2 |
| 7 | Almacenamiento (SSD / HDD) | 2 |
| 8 | SSD NVMe (M.2) | 2 |
| 9 | Ventilador de caja | 2 |
| 10 | Arquitectura clásica: puentes norte/sur (diagrama animado) | 3 |
| 11 | SoC moderno: CPU + GPU + NPU (diagrama animado) | 3 |
| 12 | Tarjeta de red (NIC) | 4 |
| 13 | Tarjeta de sonido | 4 |
| 14 | Panel de E/S trasero | 4 |
| 15 | Puertos y velocidades (diagrama animado) | 4 |

El cubo 2 usa las 2 caras libres para el QR del visor y el título.
El cubo 3 lleva QR, título y 2 caras de teoría impresa; sus marcadores muestran
diagramas 3D animados (partículas recorriendo los buses) en vez de modelos GLB.
El cubo 4 (conectividad y expansión) usa 3 caras con modelos GLB, una cara con el
diagrama animado de puertos y anchos de banda, y las 2 restantes para QR y título.

## Probar en el portátil (webcam)

```powershell
cd D:\Cubo-AR-PC
python -m http.server 8080
```

Abrir <http://localhost:8080> y permitir la cámara. Mostrar el cubo impreso (o la
plantilla en pantalla del móvil) delante de la webcam.

## Usar con móviles en el aula

La cámara del móvil exige **HTTPS**, así que hay que publicar la carpeta:

1. Crear repositorio en GitHub y subir esta carpeta.
2. Settings → Pages → Deploy from branch → main.
3. Los alumnos abren `https://<usuario>.github.io/<repo>/` y apuntan al cubo.

Alternativa sin GitHub: `npx serve` + túnel (`cloudflared tunnel --url http://localhost:3000`).

## Créditos y licencia de los modelos

Ficha completa por pieza (origen, autor, licencia y trabajo aplicado) en
**[CREDITOS.md](CREDITOS.md)**.

- `caja.glb` (semitorre ATX): modelo **original de este proyecto**, hecho en Blender.
- El resto de modelos GLB proviene de la colección renderizada del proyecto
  **Ensamblaje-PC-3D** del mismo autor (Angel Ortiz), preparada para uso educativo.
  Su procedencia original está **pendiente de verificar**: ver la nota (1) de
  `CREDITOS.md`.
- No se ha incorporado ningún modelo descargado de terceros; la búsqueda de
  alternativas CC0 en Poly Pizza queda documentada en `CREDITOS.md`.

## Notas

- Requiere internet (A-Frame y AR.js se cargan por CDN).
- Todos los modelos pesan 8,2 MB o menos (`nvme.glb` es el mayor): carga fluida en móvil.
- La escena usa un **mapa de entorno generado por código** (`entorno-estudio` en
  `index.html`) además de las luces: sin él, los materiales metálicos de three.js
  se ven planos o negros en AR.
- Imprimir mate mejor que brillante (los reflejos dificultan la detección).
- `test-modelos.html`: página de prueba sin cámara que carga los 10 GLB de los cubos 1
  y 2 en rejilla (útil para validar los modelos sin AR).
