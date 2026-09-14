# DermaCasos · Prueba de concepto

Sistema de carga y consulta de casos dermatológicos. Es un único archivo HTML sin dependencias: se abre directamente en el navegador (`dermacasos.html`), sin servidor ni instalación.

## Funcionalidades

- **Casos** (inicio): buscador por paciente, DNI, patología, severidad, origen, estado de validación, fecha y palabra clave.
- **Nuevo caso**: carga manual con datos del paciente, patología, severidad, primera consulta, imágenes y PDFs.
- **Importar caso**
  - *OCR* (simulado): se sube la ficha en PDF, se extraen los datos con indicador de confianza por campo y el médico los valida o los deja pendientes.
  - *Carga masiva*: se selecciona una carpeta con casos ya organizados (estructura configurable, p. ej. `Patología/Paciente - DNI/`); todos quedan pendientes de validación.
- **Ficha del caso**: línea de tiempo con visitas e histopatologías, cada una con fecha, descripción, imágenes y documentos.
- **Configuración**: patologías, niveles de severidad y colores, datos del centro, estructura de carpetas para carga masiva, respaldo (exportar / importar JSON) y almacenamiento.

## Notas

- Los datos se guardan en `localStorage` del navegador (~5 MB). Para conservarlos o moverlos a otro equipo, usar *Configuración → Respaldo*.
- El OCR está simulado; los datos extraídos son ficticios.
- Las imágenes de ejemplo son sintéticas (generadas en SVG), no material clínico real.
