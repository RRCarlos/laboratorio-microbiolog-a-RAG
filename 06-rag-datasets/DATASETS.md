# Datasets para RAG - Chatbot VeriTest.LAB

## Resumen

Esta carpeta contiene información sobre datasets disponibles para implementar un sistema RAG (Retrieval Augmented Generation) en el chatbot del dashboard del laboratorio.

Los datasets listados son de dominio público y se usables para entrenar/poblar la base de conocimiento del chatbot.

---

## Datasets Relevantes Identificados

### 1. Microbiología General

| Dataset | Descripción | Enlace | Formato |
|---------|------------|--------|---------|
| AMR (R Package) | Datos completos de microbiology, antimicrobiales, codigos SNOMED | https://amr-for-r.org/articles/datasets.html | CSV, Excel, Parquet |
| MIMIC-III Microbiology Events | Eventos de microbiología clínica (demo) | https://physionet.org/content/mimiciii-demo/1.4 | CSV |
| NHS Tayside Microbiology | 8M registros de muestras de microbiología | https://healthdatagateway.org/en/dataset/111 | CSV |

### 2. Bacterias y Clasificación

| Dataset | Descripción | Enlace |
|---------|------------|--------|
| Bacteria Dataset | Imágenes de colonias bacterianas | https://www.kaggle.com/datasets/kanchana1990/bacteria-dataset |
| Bacteria Classification | Clasificación a nivel de género | https://www.kaggle.com/c/bacteria-classification-at-the-genus-level |
| E. coli / K. pneumoniae | Imágenes en MacConkey Agar | https://data.mendeley.com/datasets/kx6gz3wmcf |

### 3. PCR y Diagnóstico

| Dataset | Descripción | Enlace |
|---------|------------|--------|
| COVID-19 PCR Diagnostics | Datos de pruebas PCR | https://www.kaggle.com/datasets/devkambhampati/covid19-diagnostic-laboratory-testing-pcr |
| 16S rRNA Microbiome | Análisis de microbioma | https://www.kaggle.com/datasets/aramelheni/16s-rrna-microbiome-sequencing-analysis-dataset |

### 4. AMR (Antimicrobial Resistance)

| Dataset | Descripción | Enlace |
|---------|------------|--------|
| ARMD (Antibiotic Resistance) | Resistencia antimicrobiana desde EHR | https://www.nature.com/articles/s41597-025-05649-7 |
| NDARO | NCBI Pathogen Detection | https://www.ncbi.nlm.nih.gov/pathogens/antimicrobial-resistance/ |
| CARD Database | Comprehensive Antibiotic Resistance Database | https://card.mcmaster.ca/ |

---

## Recomendaciones para el RAG

### Prioridad Alta

1. **AMR Package Data** — Contains:
   - Full microbial taxonomy (78,679 rows)
   - Antimicrobials (505 rows)
   - Antibiotic susceptibility guidelines (40,217 rows)
   - Example isolates (2,000 rows)
   - Formatos: CSV, Excel, Parquet

2. **NHS Tayside Microbiology** — Contains:
   - 514,000 personas
   - 8,214,000 registros
   - Muestras, resultados, antibiogramas

3. **MIMIC-III Demo** — Contains:
   - 221,959 bytes de eventos microbiológicos
   - Blood cultures, organism identification, antibiotics

---

## Próximos Pasos

1. Descargar datasets prioritarios (AMR, MIMIC demo)
2. Processar y limpiar datos
3. Crear embeddings para RAG
4. Integrar con chatbot del dashboard

---

*Documento para Proyecto VeriTest.LAB - RAG Chatbot*
*Versión 1.0 — Abril 2026*