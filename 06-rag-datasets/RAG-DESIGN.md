# RAG para Chatbot de Laboratorio Microbiología - Diseño

## Resumen

Este documento establece el diseño y principios para implementar un RAG efectivo para el chatbot del laboratorio VeriTest.LAB.

---

## 1. Fundamentos de RAG en Laboratorio

### ¿Qué es un RAG?

Un RAG (Retrieval Augmented Generation) combina:
- **Retrieval**: Búsqueda de información relevante en una base de conocimiento
- **Generation**: Generación de respuestas basadas en la información recuperada

### Aplicación en Laboratorio (basado en estudio Raven - PMC 2025)

| Aspecto | Recomendación |
|---------|---------------|
| **Fuente autoritativa** | Normativas oficiales (ISO, CFR), no Wikipedia |
| **Tasa de acierto** | 92% respuestas correctas en Ravena |
| **Ground truth** | Siempre citar fuentes |

---

## 2. Arquitectura del Sistema RAG

```
┌─────────────────────────────────────────────────────────────┐
│                      USUARIO                                │
│                  (Consulta en lenguaje natural)             │
└─────────────────────────┬───────────────────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                    CHATBOT UI                               │
│               (Interfaz conversacional)                      │
└─────────────────────────┬───────────────────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  ORQUESTADOR                                 │
│        (Coordina retrieval + generation)                    │
└─────────────────────────┬───────────────────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              VECTOR DATABASE                              │
│      (Embeddings del conocimiento del laboratorio)          │
└─────────────────────────┬───────────────────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              LLM GENERATOR                               │
│        (Genera respuestas grounded)                        │
└─────────────────────────────────────────────────────────────┘
```

---

## 3. Base de Conocimiento (Knowledge Base)

### Tipos de Contenido

| Categoría | Contenido | Prioridad |
|-----------|----------|----------|
| **Normativas** | ISO 15189, ISO 15190, ISO 35001, ISO 45001 | 🔥 Alta |
| **SOPs** | Procedimientos operativos del laboratorio | 🔥 Alta |
| **Protocolos** | Preparación medios, cultivo, identificación | 🔥 Alta |
| **Equipment** | Fichas técnicas, mantenimiento | Alta |
| **FAQs** | Preguntas frecuentes de clientes | Alta |
| **Resultados** | Interpretación de resultados | Media |

---

## 4. Casos de Uso del Chatbot

### Pre-Analytics
- Guía de preparación de muestras
- Tipos de pruebas disponibles
- Volumen y calidad de muestra requerida
- Transporte y almacenamiento

### Analytics
- Recetas de medios de cultivo
- Troubleshooting de PCR fallidas
- Diseño de PCR primers
- Guía de tinción

### Post-Analytics
- Interpretación de resultados
- Recomendaciones de antibiótico
- Siguientes pasos en diagnóstico
- Explicación de métodos

---

## 5. Datasets para el RAG

### Fuentes de Conocimiento

| Fuente | Tipo | Disponibilidad |
|--------|------|-----------------|
| **42 CFR Part 493** | Regulación laboratorio EE.UU. | Público |
| **ISO 15189** | Calidad laboratorio | Compra (200€) |
| **ISO 15190** | Seguridad laboratorio | Compra (200€) |
| **BMBL 6th Edition** | Bioseguridad | Gratuito (CDC) |
| **WHO LBM 4th** | Bioseguridad | Gratuito (WHO) |
| **SOPs propios** | Procedimientos internos | Propios |

---

## 6. Evaluación y Red Teaming

### Métricas de Éxito

| Métrica | Objetivo |
|--------|----------|
| Completitud de respuesta | >90% |
| Correctitud factual | >90% |
| Citas a fuentes | 100% |
| Hallucinations | 0% |

---

## 7. Principios de Diseño

### Seguridad Primero

1. **Confidence Thresholds**
   - Solo predicciones >90% son accionables
   - Por debajo → revisar humano

2. **Explainability**
   - Cada respuesta incluye fuente
   - Citar normativa específica

3. **Never Authoritative**
   - El chatbot asesora, no diagnostica
   - Siempre indicar "consultar especialista"

---

## 8. Implementación Roadmap

### Fase 1: Base (meses 1-2)
- [x] Compilar normativas oficiales
- [x] Crear FAQs estructurados (350+)
- [x] Vectorizar con embeddings

### Fase 2: ML (meses 3-4)
- [ ] Integrar modelo clasificación bacteriana
- [ ] Confidence scoring
- [ ] Red teaming interno

### Fase 3: Producción (meses 5-6)
- [ ] Testing con usuarios reales
- [ ] Iterar basado en feedback
- [ ] Monitorización de hallucinations

---

## 9. Referencias

- Raven RAG System (PMC 2025): https://pmc.ncbi.nlm.nih.gov/articles/PMC12616094/
- BactAI-D (GitHub): https://github.com/EphraimAsad/BactAI-D
- Red Teaming Healthcare (PMC 2024): https://imerit.net/resources/blog/red-teaming-rag-healthcare-chatbots/
- LLMs in Clinical Microbiology (PMC 2023): https://pmc.ncbi.nlm.nih.gov/articles/PMC10640689/

---

*Documento de diseño para Proyecto VeriTest.LAB - RAG Chatbot*
*Versión 1.0 — Abril 2026*