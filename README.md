# P05 — Docs Chat 📄💬

> Una plataforma moderna de **RAG (Retrieval-Augmented Generation)** para conversar con tus documentos con precisión quirúrgica y atribución de fuentes.

[![Next.js](https://img.shields.io/badge/Next.js-16-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![Supabase](https://img.shields.io/badge/Supabase-pgvector-green?style=flat-square&logo=supabase)](https://supabase.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC?style=flat-square&logo=tailwind-css)](https://tailwindcss.com/)
[![OpenAI](https://img.shields.io/badge/OpenAI-Embeddings-412991?style=flat-square&logo=openai)](https://openai.com/)
[![Anthropic](https://img.shields.io/badge/Anthropic-Claude-D97757?style=flat-square&logo=anthropic)](https://anthropic.com/)

---

## 🚀 Características Principales

*   **Ingesta Inteligente:** Procesamiento automático de archivos **PDF y Markdown** con extracción de texto limpio.
*   **Búsqueda Semántica:** Implementación de `pgvector` en Supabase para una recuperación de fragmentos extremadamente rápida y relevante.
*   **Atribución de Fuentes:** Cada respuesta generada incluye los fragmentos exactos utilizados y un **Score de Confianza** basado en similitud vectorial.
*   **Gestión de Contexto:** Selección dinámica de documentos para focalizar la conversación en fuentes específicas.
*   **Streaming UI:** Respuestas en tiempo real con una interfaz moderna construida sobre `shadcn/ui`.

---

## 🛠️ Stack Tecnológico

- **Frontend:** Next.js 16 (App Router), TypeScript, Tailwind CSS, shadcn/ui.
- **Base de Datos:** Supabase + `pgvector` para almacenamiento vectorial.
- **Embeddings:** OpenAI `text-embedding-3-small`.
- **LLM:** Anthropic `claude-sonnet-4-6` (vía SDK oficial).
- **Procesamiento:** LangChain (Recursive Character Splitting), `pdf-parse`.

---

## 🧠 El Pipeline RAG

```mermaid
graph TD
    A[Documento PDF/MD] --> B[Extracción de Texto]
    B --> C[Chunking recursivo]
    C --> D[OpenAI Embeddings]
    D --> E[(Supabase pgvector)]
    
    F[User Query] --> G[Query Embedding]
    G --> H[Similarity Search]
    E --> H
    H --> I[Top-K Context Chunks]
    I --> J[Anthropic Claude]
    J --> K[Streaming Response + Sources]
```

---

## ⚙️ Configuración

### Requisitos Previos

- Node.js 20+
- Cuenta en Supabase con pgvector habilitado
- API Keys de OpenAI y Anthropic

### Instalación

1. Clonar el repositorio
2. Instalar dependencias:
   ```bash
   npm install
   ```
3. Configurar variables de entorno (`.env.local`):
   ```env
   NEXT_PUBLIC_SUPABASE_URL=tu_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=tu_key
   OPENAI_API_KEY=tu_openai_key
   ANTHROPIC_API_KEY=tu_anthropic_key
   MATCH_THRESHOLD=0.5
   ```
4. Ejecutar el servidor de desarrollo:
   ```bash
   npm run dev
   ```

---

## 🏗️ Estructura del Proyecto

- `app/api/`: Ruteo de API para ingestión, búsqueda y chat por streaming.
- `lib/supabase/`: Configuración del cliente y tipos de base de datos.
- `components/`: UI basada en componentes atómicos de shadcn.
- `supabase/migrations/`: Esquema de la base de datos (documents, document_chunks).

---

## 🎓 Contexto Académico

Este es el **Proyecto 05** del currículum *Full Stack AI Developer*. Representa la culminación de la **Fase 3: RAG y Pipelines de Conocimiento**, donde se abordan los desafíos de contextualización, balance de chunks y recuperación precisa de información técnica.
