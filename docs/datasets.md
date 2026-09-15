# Datasets abiertos de imágenes dermatológicas

Relevamiento de datasets públicos con imágenes de patologías de piel, útiles para entrenar y evaluar modelos de IA en dermatología. Puede servir como referencia para las etapas siguientes de este proyecto (clasificación asistida, OCR + imágenes, evaluación de sesgos por fototipo, etc.).

Salvo que se indique lo contrario, los datasets son de uso **académico / no comercial**. Verificar la licencia de cada uno antes de incorporarlo a un producto.

## Resumen

| Dataset | Imágenes | Tipo de imagen | Categorías | Uso principal |
|---|---|---|---|---|
| ISIC Archive | > 85.000 | Dermatoscópica | Cáncer de piel y lesiones benignas | Clasificación de melanoma, benchmark |
| HAM10000 | 10.015 | Dermatoscópica | 7 clases | Clasificación general, modelos introductorios |
| DDI | 656 | Clínica | Benignas / malignas, por fototipo | Equidad y sesgo por tono de piel |
| Fitzpatrick 17K | 16.577 | Clínica | 114 condiciones + fototipo | Modelos robustos a diversidad demográfica |
| SkinCAP | 4.000 | Clínica | Varias, con descripciones en texto | Modelos visión-lenguaje |
| SD-198 | 6.584 | Clínica | 198 condiciones | Clasificación multiclase clínica |
| BCN20000 | 26.426 | Dermatoscópica | 8 tipos de lesión | Deep learning clínico y dermatoscópico |
| PAD-UFES-20 | 2.298 | Clínica (smartphone) | 6 diagnósticos + metadatos | Aplicaciones móviles |
| PH² | 200 | Dermatoscópica | Melanoma, nevos atípicos y comunes | Segmentación |
| Derm7pt | 1.011 | Dermatoscópica + clínica | Melanoma / no melanoma, checklist de 7 puntos | IA explicable |

## 1. ISIC Archive (International Skin Imaging Collaboration)

El repositorio público más grande y usado de imágenes dermatoscópicas. Es la base de los *ISIC Challenges* anuales (2016 en adelante).

- **Tamaño:** más de 85.000 imágenes.
- **Categorías:** principalmente cáncer de piel — melanoma, carcinoma basocelular, carcinoma espinocelular — y diversas lesiones benignas.
- **Tipo de imagen:** dermatoscópica de alta resolución, con metadatos (edad, sexo, localización, diagnóstico y método de confirmación).
- **Ideal para:** clasificación de melanoma y benchmarking de modelos.
- **Acceso:** https://www.isic-archive.com · API: https://api.isic-archive.com
- **Licencia:** varía por colección (CC-0, CC BY, CC BY-NC).

## 2. HAM10000 (Human Against Machine with 10000 training images)

Dataset balanceado, muy popular como benchmark. Fue el conjunto de entrenamiento del ISIC Challenge 2018.

- **Tamaño:** 10.015 imágenes.
- **Categorías (7):** melanoma, nevo melanocítico, carcinoma basocelular, queratosis actínica / enfermedad de Bowen, queratosis benigna, dermatofibroma, lesiones vasculares.
- **Tipo de imagen:** dermatoscópica de alta resolución.
- **Ideal para:** clasificación general de cáncer de piel y primeros modelos (disponible también en Kaggle).
- **Acceso:** https://doi.org/10.7910/DVN/DBW86T (Harvard Dataverse)
- **Referencia:** Tschandl P., Rosendahl C., Kittler H. *Scientific Data*, 2018.
- **Licencia:** CC BY-NC 4.0.

## 3. DDI — Diverse Dermatology Images

Diseñado para evaluar el sesgo racial de los algoritmos, garantizando representación de distintos tonos de piel.

- **Tamaño:** 656 imágenes curadas, todas con confirmación histopatológica.
- **Categorías:** lesiones benignas y malignas.
- **Particularidad:** cada imagen está clasificada por fototipo de Fitzpatrick (I-VI), pensado para comparar piel clara (FST I-II) contra piel oscura (FST V-VI).
- **Ideal para:** evaluar equidad y reducir sesgos en detección de enfermedades de piel.
- **Acceso:** https://ddi-dataset.github.io
- **Referencia:** Daneshjou R. et al. *Science Advances*, 2022.

## 4. Fitzpatrick 17K

Otro dataset centrado en la diversidad de tonos de piel.

- **Tamaño:** 16.577 imágenes clínicas.
- **Categorías:** 114 condiciones de piel.
- **Particularidad:** anotado tanto con la condición como con el fototipo de Fitzpatrick. Las imágenes provienen de atlas dermatológicos en línea (DermaAmin y Atlas Dermatologico).
- **Ideal para:** entrenar modelos robustos que funcionen en poblaciones diversas.
- **Acceso:** https://github.com/mattgroh/fitzpatrick17k
- **Referencia:** Groh M. et al. *CVPR Workshops*, 2021.

## 5. SkinCAP

Dataset multimodal que combina imágenes con descripciones en lenguaje natural.

- **Tamaño:** 4.000 imágenes (tomadas de Fitzpatrick 17K y DDI).
- **Categorías:** diversas enfermedades de piel.
- **Particularidad:** anotado por dermatólogos certificados con descripciones médicas extensas y *captions*.
- **Ideal para:** modelos visión-lenguaje y generación de descripciones de lesiones. Muy relevante si se quiere asistir la redacción de la descripción clínica a partir de la foto.
- **Acceso:** https://huggingface.co/datasets/joshuachou/SkinCAP
- **Referencia:** Zhou J. et al., 2024 (arXiv:2405.18004).

## 6. SD-198

Dataset de imágenes **clínicas** (no dermatoscópicas) con gran cantidad de clases.

- **Tamaño:** 6.584 imágenes.
- **Categorías:** 198 condiciones distintas, desde eccema y acné hasta patologías raras.
- **Ideal para:** dermatología clínica general y clasificación multiclase. Existe una variante reducida, SD-136, con las clases que tienen al menos 20 imágenes.
- **Acceso:** se solicita a los autores (ver paper).
- **Referencia:** Sun X. et al. *A Benchmark for Automatic Visual Classification of Clinical Skin Disease Images*, ECCV 2016.

## 7. BCN20000

Desarrollado por el Hospital Clínic de Barcelona; formó parte del ISIC Challenge 2019.

- **Tamaño:** 26.426 imágenes (19.424 con diagnóstico confirmado).
- **Categorías:** 8 tipos de lesión — melanoma, nevo, carcinoma basocelular, queratosis actínica, queratosis seborreica, dermatofibroma, lesión vascular, carcinoma espinocelular.
- **Particularidad:** incluye lesiones en localizaciones difíciles (uñas, mucosas) y lesiones grandes que no entran en el campo del dermatoscopio.
- **Ideal para:** entrenar modelos de deep learning clínicos y dermatoscópicos.
- **Acceso:** a través del ISIC Archive (colección BCN20000).
- **Referencia:** Combalia M. et al., 2019 (arXiv:1908.02288).

## 8. PAD-UFES-20

Imágenes clínicas del mundo real tomadas con smartphones, recolectadas en la Universidad Federal de Espírito Santo (Brasil).

- **Tamaño:** 2.298 imágenes de 1.641 lesiones en 1.373 pacientes.
- **Categorías:** 6 diagnósticos — carcinoma basocelular, carcinoma espinocelular, queratosis actínica, queratosis seborreica, melanoma y nevo (los 3 cánceres con confirmación histopatológica).
- **Particularidad:** metadatos clínicos ricos (edad, sexo, localización, antecedentes, hábitos, síntomas como prurito o sangrado). Es el más parecido al contexto de uso de esta PoC: fotos de celular + ficha clínica.
- **Ideal para:** aplicaciones móviles de salud y dermatología general.
- **Acceso:** https://data.mendeley.com/datasets/zr7vgbcyr2
- **Referencia:** Pacheco A. G. C. et al. *Data in Brief*, 2020.
- **Licencia:** CC BY 4.0.

## 9. PH² Dataset

Dataset pequeño y muy detallado, orientado a segmentación.

- **Tamaño:** 200 imágenes dermatoscópicas.
- **Categorías:** melanoma (40), nevos atípicos (80) y nevos comunes (80).
- **Particularidad:** máscaras de segmentación a nivel de píxel hechas por expertos, más criterios clínicos (asimetría, colores, red pigmentada, etc.).
- **Ideal para:** segmentación de lesiones y extracción de características.
- **Acceso:** https://www.fc.up.pt/addi/ph2%20database.html
- **Referencia:** Mendonça T. et al. *IEEE EMBC*, 2013.

## 10. Derm7pt

Construido alrededor del *checklist de 7 puntos* para diagnóstico de melanoma.

- **Tamaño:** 1.011 casos, cada uno con imagen dermatoscópica y clínica.
- **Categorías:** melanoma y no melanoma.
- **Particularidad:** anotaciones de cada criterio del checklist (red pigmentada atípica, velo azul-blanquecino, estrías, puntos/glóbulos irregulares, manchas, áreas de regresión, vasos), más metadatos del paciente.
- **Ideal para:** IA explicable (XAI) y clasificación basada en características.
- **Acceso:** https://derm.cs.sfu.ca
- **Referencia:** Kawahara J. et al. *IEEE JBHI*, 2019.

## Consideraciones para este proyecto

- **Tipo de imagen:** la mayoría de los datasets grandes son dermatoscópicos. Las fotos que se cargan en DermaCasos son clínicas (celular / cámara), por lo que PAD-UFES-20, Fitzpatrick 17K, SD-198 y DDI son los más comparables.
- **Población:** ninguno de estos datasets tiene una base fuerte de población latinoamericana. Para un modelo usable localmente probablemente haga falta un dataset propio, y esta PoC (con su flujo de validación por médico) puede ser el punto de partida para construirlo.
- **Privacidad:** cualquier dataset propio requiere consentimiento informado, anonimización (sin rostro, sin DNI en metadatos) y aprobación de comité de ética.
- **Uso de la información de texto:** SkinCAP y los metadatos de PAD-UFES-20 son referencias útiles para definir qué campos conviene estructurar en la ficha (localización, síntomas, evolución) de cara a un futuro modelo multimodal.
