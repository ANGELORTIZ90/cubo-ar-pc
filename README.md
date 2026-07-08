# Cubo AR — Componentes de PC (SMX)

Cubo de papel estilo "Merge Cube" con marcadores propios. Al enfocar una cara con la
cámara, el visor web muestra el componente de PC en 3D (modelos GLB del proyecto
Ensamblaje-PC-3D).

## Contenido

| Archivo | Función |
|---|---|
| `plantilla.html` | Plantilla imprimible del cubo (abrir y Ctrl+P → PDF, escala 100%) |
| `index.html` | Visor AR web (A-Frame + AR.js, marcadores barcode 3x3) |
| `modelos/` | 6 modelos GLB (placa base, CPU, disipador, RAM, GPU, fuente) |
| `marcadores/` | Marcadores barcode 0-5 (colección oficial AR.js) |

## Caras del cubo

| Marcador | Componente |
|---|---|
| 0 | Placa base |
| 1 | Procesador (CPU) |
| 2 | Disipador de CPU |
| 3 | Memoria RAM |
| 4 | Tarjeta gráfica (GPU) |
| 5 | Fuente de alimentación |

## Probar en el portátil (webcam)

```powershell
cd $env:USERPROFILE\Desktop\Cubo-AR-PC
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

## Notas

- Requiere internet (A-Frame y AR.js se cargan por CDN).
- `cpu.glb` pesa 16 MB: en móviles lentos tarda en cargar la primera vez.
- Imprimir mate mejor que brillante (los reflejos dificultan la detección).
- Para más componentes (caja, NVMe, SSD, ventilador): añadir marcadores 6-11 y
  duplicar bloques `<a-marker>` en `index.html` → segundo cubo.
