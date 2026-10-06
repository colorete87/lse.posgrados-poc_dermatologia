# DermaCasos · Prueba de concepto

Sistema de carga y consulta de casos dermatológicos. Es un único archivo HTML sin dependencias: se abre directamente en el navegador (`dermacasos.html`), sin servidor ni instalación.

Es una **prueba de concepto de interfaz**: su objetivo es mostrar el modelo de datos, las vías de carga y el flujo de validación de un sistema de archivo dermatológico, para poder discutirlos con los profesionales antes de construir nada. No implementa backend, autenticación ni OCR real; todo corre en el navegador.

## Uso

Descargar el repositorio y abrir `dermacasos.html` con doble clic. La primera vez se cargan casos de ejemplo para poder recorrer todas las pantallas.

## Funcionalidades

- **Casos** (inicio): buscador por paciente, DNI, patología, severidad, origen, estado de validación, fecha y palabra clave.
- **Nuevo caso**: carga manual con datos del paciente, patología, severidad, primera consulta, imágenes y PDFs.
- **Importar caso**
  - *OCR* (simulado): se sube la ficha en PDF, se extraen los datos con indicador de confianza por campo y el médico los valida o los deja pendientes.
  - *Carga masiva*: se selecciona una carpeta con casos ya organizados (estructura configurable, p. ej. `Patología/Paciente - DNI/`); todos quedan pendientes de validación.
- **Validación**: los casos importados quedan marcados como pendientes hasta que un médico revisa los datos extraídos. El buscador permite filtrarlos y validarlos desde la ficha.
- **Ficha del caso**: línea de tiempo con visitas e histopatologías, cada una con fecha, descripción, imágenes y documentos.
- **Configuración**: patologías, niveles de severidad y colores, datos del centro, estructura de carpetas para carga masiva, respaldo (exportar / importar JSON) y almacenamiento.
- **Tema claro / oscuro**: botón en la barra de navegación. Por defecto sigue la preferencia del sistema operativo; la elección del usuario se recuerda en el navegador.

## Documentación

- [`docs/datasets.md`](docs/datasets.md) — relevamiento de diez datasets abiertos de imágenes dermatológicas, con tamaño, tipo de imagen, licencia y condiciones de acceso, verificados en septiembre de 2026.

## Notas

- Los datos se guardan en `localStorage` del navegador (~5 MB). Para conservarlos o moverlos a otro equipo, usar *Configuración → Respaldo*.
- El OCR está simulado; los datos extraídos son ficticios.
- Las imágenes de ejemplo son sintéticas (generadas en SVG), no material clínico real.

## Limitaciones conocidas

Al ser una prueba de concepto de interfaz, quedan fuera de alcance aspectos necesarios para un uso real, que corresponderían a un desarrollo posterior:

- **Capacidad**: `localStorage` admite unos 5 MB, por lo que con fotos de celular sin comprimir se llena rápido. Un paso siguiente sería comprimir las imágenes al cargarlas o migrar a IndexedDB.
- **Seguridad y privacidad**: los datos de los pacientes (nombre, DNI) se guardan sin cifrar en el navegador. Un sistema real requiere backend, autenticación con control de acceso por rol, registro de auditoría, cifrado y consentimiento informado.
- **OCR**: falta definir e integrar un motor real de reconocimiento.
- **Carga masiva**: la selección de carpetas usa `webkitdirectory`, con soporte limitado en navegadores móviles.
