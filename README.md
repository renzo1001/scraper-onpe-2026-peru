# 🇵🇪 Scraper ONPE 2026 - Resultados Presidenciales

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/renzo1001/scraper-onpe-2026-peru/blob/main/ONPE_2026.ipynb)

Este repositorio contiene un script asíncrono en Python diseñado para extraer y estructurar los resultados de las Elecciones Presidenciales de Perú 2026 directamente desde el backend público de la ONPE. 

Está optimizado para ejecutarse en **Google Colab**, permitiendo a investigadores, periodistas y analistas de datos obtener la información completa en cuestión de minutos sin necesidad de configurar entornos locales.

## 🚀 Características principales

* **Granularidad Máxima:** Extrae datos de participación y resultados (votos emitidos, válidos, actas contabilizadas) a nivel distrital para todo el Perú, y a nivel continental para el extranjero.
* **Alta Velocidad:** Utiliza concurrencia asíncrona (`asyncio` + `curl_cffi`) para realizar múltiples peticiones simultáneas, reduciendo drásticamente el tiempo de descarga.
* **Tolerancia a Fallos:** Implementa un sistema de reintentos automáticos para manejar caídas del servidor o respuestas inestables (como devoluciones de HTML en lugar de JSON).
* **Exportación Estructurada:** Genera un archivo `.zip` consolidado que incluye archivos `.csv` relacionales (participantes y avances) y un `.json` maestro, listos para importar a Excel, Power BI, Python o cualquier software de auditoría de datos.

## 🛠️ Cómo usarlo

La forma más sencilla de ejecutar este scraper es a través de Google Colab:

1. Haz clic en el botón **Open in Colab** en la parte superior de este documento.
2. En el menú superior de Colab, ve a `Entorno de ejecución` > `Ejecutar todas` (o presiona `Ctrl + F9`).
3. El script instalará las dependencias necesarias (`curl_cffi`), iniciará la extracción y mostrará el progreso en tiempo real.
4. Al finalizar, descargará automáticamente un archivo `onpe_data_YYYYMMDD.zip` con todos los CSVs listos para usar.

## ⚙️ Configuración Avanzada

Si deseas modificar el comportamiento del scraper, puedes editar las siguientes variables directamente en la primera celda del notebook:

* `SOLO_DEP`: Define el código de un departamento específico (ej. `"140000"` para Lima) si no deseas descargar todo el país. Déjalo en `None` para extracción nacional.
* `INCLUIR_EXT`: Cambia a `False` si no deseas descargar los datos del extranjero.
* `CONCURRENCY`: Número de peticiones simultáneas (por defecto `6`). Puedes bajarlo si la web de la ONPE está muy inestable.

## ⚠️ Descargo de Responsabilidad
Este proyecto tiene fines estrictamente informativos y de análisis de datos públicos. Por favor, utiliza el código con responsabilidad para no saturar los servidores gubernamentales.
