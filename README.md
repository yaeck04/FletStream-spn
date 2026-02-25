# 🎬 FletStream Pro

![Version](https://img.shields.io/badge/version-1.5.0-red)
![Python](https://img.shields.io/badge/python-3.9+-blue.svg)
![Flet](https://img.shields.io/badge/Flet-0.80.1-cyan)

Una aplicación de streaming y descarga de películas moderna, desarrollada con **Flet** (Python). Diseñada con una interfaz oscura estilo Netflix, enfocada en contenido en español para Latinoamérica y Cuba.

Cuenta con un potente **gestor de descargas**, un **extractor de enlaces robusto** para servidores VOE y un reproductor integrado.

## ✨ Características

*   🎨 **Interfaz Moderna:** Diseño oscuro (Dark Mode) con grid responsivo, búsqueda en tiempo real y filtros por género.
*   📥 **Gestor de Descargas Avanzado:**
    *   Sistema de cola con descargas simultáneas (hasta 2 hilos).
    *   Interfaz de tarjetas con barras de progreso en tiempo real.
    *   Historial de descargas persistente en JSON.
    *   Cancelación de descargas en curso.
*   🔍 **Extractor Robusto (VOE):** Motor de extracción de enlaces que utiliza múltiples técnicas (Regex, BeautifulSoup, deobfuscación ROT13/Base64) para obtener enlaces directos `.mp4` o `.m3u8`.
*   📺 **Reproductor Integrado:** Uso de `flet-video` para reproducir contenido dentro de la aplicación sin salir de ella.
*   📝 **Logs del Sistema:** Visualización de logs en tiempo real para depuración y seguimiento de descargas.
*   💾 **Caché de Posters:** Descarga automática de pósters en segundo plano para mejorar la carga.

## 🛠️ Stack Tecnológico

*   **Frontend:** [Flet](https://flet.dev/) (Framework Flutter para Python).
*   **Video:** [flet-video](https://github.com/flet-dev/flet-video).
*   **Scraping:** [Requests](https://requests.readthedocs.io/), [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/).
*   **Concurrencia:** `threading`, `asyncio`.

## 📦 Instalación y Ejecución

### Prerrequisitos

*   Python 3.9 o superior.
*   Pip (gestor de paquetes de Python).

### Pasos

1.  **Clona el repositorio:**
    ```bash
    git clone https://github.com/yaeck04/FletStream-spn.git
    cd FletStream-spn
    ```

2.  **Crea un entorno virtual (Recomendado):**
    ```bash
    python -m venv venv
    # Windows:
    venv\Scripts\activate
    # Linux/Mac:
    source venv/bin/activate
    ```

3.  **Instala las dependencias:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Configura los datos:**
    Crea un archivo llamado `peliculas_con_reproductores.json` en la raíz del proyecto (o en la carpeta `src` si ejecutas desde allí). Ver el formato abajo.

5.  **Ejecuta la aplicación:**
    ```bash
    python src/main.py
    ```

## ⚙️ Formato de Datos (JSON)

La aplicación lee el catálogo desde un archivo JSON. Asegúrate de que siga esta estructura:

```json
[
  {
    "titulo": "Nombre de la Película",
    "anio": 2024,
    "poster": "https://ejemplo.com/poster.jpg",
    "genero": ["Acción", "Aventura"],
    "sinopsis": "Descripción breve de la trama...",
    "reproductores": [
      {
        "servidor": "VOE",
        "idioma": "Latino",
        "url": "https://voe.sx/..."
      }
    ]
  }
]
```

*   **Nota:** Actualmente el extractor está optimizado para enlaces del servidor **VOE**.

## 🏗️ Compilar para Android (APK)

Este proyecto está configurado con **GitHub Actions** para compilar automáticamente la APK cuando haces un push a la rama `main`.

### Compilación Manual
Si prefieres compilar localmente, asegúrate de tener instalado el SDK de Android y Java, luego ejecuta:

```bash
flet build apk --project src
```

### Compilación Automática (CI/CD)
1.  Sube tus cambios a GitHub.
2.  Ve a la pestaña **Actions**.
3.  Espera a que termine el workflow.
4.  El APK se generará automáticamente en la sección **Releases** de tu repositorio.

## 📂 Estructura del Proyecto

```text
FletStream/
├── src/
│   └── main.py              # Código principal de la app
├── downloads/               # Carpeta donde se guardan los videos (Creada auto)
├── posters/                 # Carpeta de caché de imágenes (Creada auto)
├── peliculas_con_reproductores.json # Base de datos local
├── requirements.txt         # Dependencias de Python
├── pyproject.toml          # Configuración del proyecto
└── README.md               # Esta documentación
```

## 🤝 Contribuir

Las contribuciones son bienvenidas. Si encuentras un bug o tienes una mejora, por favor abre un *Issue* o un *Pull Request*.

## ⚠️ Aviso Legal

Este software es una herramienta de gestión y reproducción. El desarrollador no aloja ningún contenido multimedia. El usuario es responsable del uso que le dé a la aplicación y de respetar las leyes de derechos de autor de su país.

## 📜 Licencia

Este proyecto es de código abierto y está disponible bajo la [Licencia MIT](LICENSE).

---
Desarrollado con ❤️ usando Python y Flet.

