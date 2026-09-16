# NeuraStore+

### The Intelligent Data Workspace for Files, Datasets, and Document Intelligence

[![Status](https://img.shields.io/badge/status-active%20development-brightgreen)](#project-status)
[![Built With](https://img.shields.io/badge/built%20with-Next.js%20%7C%20TypeScript%20%7C%20Supabase-black)](#technology-stack)
[![GSSoC](https://img.shields.io/badge/GSSoC-2026-orange)](#contributing)
[![License](https://img.shields.io/badge/license-MIT-blue)](#license)

> **NeuraStore+ transforms raw files and datasets into structured, searchable, queryable, and understandable information.**

NeuraStore+ is an intelligent data workspace designed to bridge the gap between **traditional file storage, structured data processing, database interaction, analytics, and document intelligence**.

Instead of treating uploaded data as passive files, NeuraStore+ provides a unified environment where data can be **stored, inspected, transformed, queried, analyzed, and understood**.
## ✦ Why NeuraStore+?
Modern applications generate enormous amounts of heterogeneous data:
* Documents
* JSON datasets
* Images
* Audio
* Video
* Source code
* Structured records
* Research material
* Business data

Traditional storage systems answer:

> **"Where is my file?"**

NeuraStore+ aims to answer a much broader set of questions:

> **"What is inside my data?"**
> **"How is this dataset structured?"**
> **"Can I turn this JSON into a database?"**
> **"Can I query it?"**
> **"What does this document actually say?"**
> **"Can I ask questions about it and see where the answer came from?"**

The platform therefore follows an intelligence-oriented workflow:

```text
                 ┌──────────────────────┐
                 │      RAW DATA        │
                 │ Files • JSON • Docs   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   INGEST & ANALYZE   │
                 │ Classification       │
                 │ Metadata             │
                 │ Structure Analysis   │
                 └──────────┬───────────┘
                            │
                ┌───────────┴────────────┐
                ▼                        ▼
       ┌─────────────────┐      ┌──────────────────┐
       │ DATA PIPELINE   │      │ DOCUMENT         │
       │                 │      │ INTELLIGENCE     │
       │ JSON → SQL      │      │                  │
       │ Schema Inference│      │ NeuraNotebook    │
       │ Querying        │      │ Summarization    │
       │ Search          │      │ Grounded Q&A     │
       └────────┬────────┘      └────────┬─────────┘
                │                        │
                └────────────┬───────────┘
                             ▼
                  ┌─────────────────────┐
                  │  INTELLIGENT DATA   │
                  │      WORKSPACE      │
                  └─────────────────────┘
```

---

# 🚀 Core Capabilities

## 1. Unified Multi-Format Data Workspace

NeuraStore+ provides a centralized environment for working with different classes of data.

Supported workflows include:

* PDF documents
* Microsoft Word documents
* Plain text
* Markdown
* JSON
* Images
* Video
* Audio
* Source/code files
* Other uploaded assets

Files can be uploaded, inspected, previewed, searched, analyzed, and managed from a unified interface.

---

# 2. Intelligent JSON Processing

JSON is one of the most common formats for APIs, datasets, configuration files, and application exports.

NeuraStore+ analyzes incoming JSON structures and determines their characteristics before processing them.

The processing pipeline supports:

```text
JSON Input
    ↓
Structural Analysis
    ↓
Classification
    ↓
Schema Inference
    ↓
Normalization
    ↓
Database Representation
    ↓
Query
```

The system handles structures including:

* Single JSON objects
* Arrays of objects
* Nested objects
* Nested arrays
* Mixed structures
* Null values
* Boolean values
* Numeric values
* Schema variations

Malformed JSON is detected and handled without crashing the application.

---

# 3. JSON → SQL Data Pipeline

One of NeuraStore+'s core capabilities is converting structured JSON data into queryable relational database structures.

Instead of manually designing database tables from an unknown JSON dataset, NeuraStore+ can infer an appropriate relational representation.

### Pipeline

```text
Raw JSON
   ↓
Schema Analysis
   ↓
Field Detection
   ↓
Type Inference
   ↓
Relational Schema Generation
   ↓
PostgreSQL Table
   ↓
Batch Data Insertion
   ↓
SQL Querying
```

The system also considers:

* Nested structures
* Missing fields
* Null values
* Conflicting types
* Schema evolution
* Table naming
* Data insertion
* Query access

Dynamic database identifiers are validated and constrained before being used.

---

# 4. SQL Querying

Once JSON data has been transformed into relational structures, users can interact with the resulting data through the application's querying interface.

The query layer supports:

* Table selection
* Column selection
* Ordering
* Pagination
* Limit/offset handling
* Empty result handling
* Invalid-resource handling

The implementation also includes validation and sanitization around dynamically supplied table and column identifiers.

---

# 5. NeuraNotebook

## Document Intelligence Inside NeuraStore+

**NeuraNotebook** is the document-intelligence layer of NeuraStore+.

It provides a focused workspace for understanding uploaded documents without requiring users to manually read through an entire file.

Inspired by the broader concept of AI-powered research notebooks, NeuraNotebook is intentionally implemented as a focused document intelligence MVP rather than a clone of another product.

### Supported document formats

* PDF
* DOCX
* TXT
* Markdown

### Document workflow

```text
Upload Document
      ↓
Text Extraction
      ↓
Normalization
      ↓
Chunking
      ↓
Relevance Retrieval
      ↓
Context Assembly
      ↓
Grounded Answer
      ↓
Source Citation
```

---

# 6. Document Extraction

NeuraNotebook performs server-side document extraction.

### PDF

Uses dynamic PDF parsing with fallback text recovery.

### DOCX

Uses Microsoft Word document extraction through `mammoth`.

### TXT

Uses UTF-8 text decoding and paragraph normalization.

### Markdown

Processes Markdown documents while preserving useful textual structure for analysis.

The extracted document becomes the basis for downstream summarization and question answering.

---

# 7. Grounded Document Q&A

NeuraNotebook allows users to ask questions about the contents of a document.

For example:

```text
"What is the main argument of this document?"

"What are the key findings?"

"What methodology does the document describe?"

"What are the major conclusions?"
```

The retrieval pipeline divides documents into chunks and ranks relevant passages using lexical TF-IDF relevance scoring.

Relevant context is then supplied to the answering layer.

The objective is simple:

> **Answers should be derived from the document rather than invented from unrelated knowledge.**

---

# 8. Anti-Hallucination Behavior

Grounding is a core design principle of NeuraNotebook.

When the required information cannot be found in the document, the system is designed to explicitly communicate that limitation.

Example:

```text
User:
Who won the 2022 FIFA World Cup?

NeuraNotebook:
I couldn't find the answer in this document.
```

This behavior prevents the system from presenting unrelated external knowledge as though it were contained in the uploaded document.

---

# 9. Source Citations

NeuraNotebook associates generated answers with the document chunks used to construct the response.

Example:

```text
Answer...

[Chunk 2]
[Chunk 5]
```

Users can inspect the associated source snippets to understand where the response originated.

This creates a simple verification loop:

```text
Question
   ↓
Retrieved Context
   ↓
Generated Answer
   ↓
Source Chunks
   ↓
Human Verification
```

---

# 10. Intelligent Document Summarization

NeuraNotebook automatically generates document-level information including:

* Executive summary
* Key takeaways
* Topics
* Entities / keywords
* Word count
* Estimated reading time
* Page count where available
* File metadata

This allows users to understand the broad structure of a document before asking detailed questions.

---

# 📊 Analytics & Visualization

NeuraStore+ includes an analytics-oriented dashboard designed to provide an overview of the stored workspace.

The interface can surface information such as:

* File counts
* File categories
* File sizes
* Recent activity
* Uploaded assets
* Dataset information

For structured JSON data, the application also provides visualization-oriented interfaces for understanding data structure.

---

# 🔎 Search

NeuraStore+ provides search across stored file information.

Search can operate across fields such as:

* File names
* Categories
* Tags
* MIME types

The workspace also provides a directory-oriented browsing experience for navigating stored assets.

---

# 🕒 History & File Management

The history interface provides visibility into activity performed within the workspace.

Users can inspect:

* Uploaded files
* Metadata
* File sizes
* Activity records
* Downloadable assets
* File deletion operations

The system is designed to keep file-management operations connected with the broader workspace experience.

---

# 🧩 JSON Editor

NeuraStore+ includes an in-browser JSON editing and validation environment.

Users can work with structured JSON without leaving the application.

The editor supports:

* JSON validation
* Nested structures
* Arrays
* Objects
* Formatting
* Structural inspection
* Schema-oriented visualization

Malformed JSON is surfaced through validation errors instead of being silently processed.

---

# 🏗️ Architecture

NeuraStore+ follows a modern full-stack web architecture.

```text
┌─────────────────────────────────────────────────────────────┐
│                         FRONTEND                            │
│                                                             │
│ Next.js • React • TypeScript • Tailwind CSS                 │
│                                                             │
│ Upload • Dashboard • Search • History • Notebook • Editor    │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              │ HTTP / API
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                       APPLICATION API                       │
│                                                             │
│ Upload • Analysis • JSON Processing • SQL • Notebook        │
│ Search • Metadata • Document Summarization                  │
└───────────────┬─────────────────────┬───────────────────────┘
                │                     │
                ▼                     ▼
      ┌──────────────────┐   ┌────────────────────────┐
      │    SUPABASE      │   │ DOCUMENT INTELLIGENCE  │
      │                  │   │                        │
      │ PostgreSQL       │   │ PDF Parser              │
      │ Storage          │   │ DOCX / Mammoth          │
      │ Metadata         │   │ Chunking                │
      └──────────────────┘   │ TF-IDF Retrieval        │
                             │ Grounded Q&A            │
                             └────────────────────────┘
```

---

# 🛠️ Technology Stack

| Layer                | Technology                     |
| -------------------- | ------------------------------ |
| Frontend             | Next.js                        |
| UI                   | React                          |
| Language             | TypeScript                     |
| Styling              | Tailwind CSS                   |
| Database             | PostgreSQL                     |
| Backend Platform     | Supabase                       |
| Storage              | Supabase Storage               |
| Document Extraction  | `pdf-parse`, `mammoth`         |
| Retrieval            | TF-IDF lexical relevance       |
| Visualization        | React-based data visualization |
| Schema Visualization | React Flow                     |
| Deployment           | Vercel                         |

---

# 🔐 Security

Security is treated as a first-class engineering concern.

Current protections include:

### Secret Management

Production credentials are loaded through environment variables rather than committed source code.

### File Upload Safety

Uploaded filenames are sanitized before being used in storage paths.

### SQL Safety

Dynamic identifiers are validated before database operations.

### XSS Protection

React's standard escaping behavior is preserved for rendered user-controlled content.

### Error Handling

The application attempts to return controlled errors instead of exposing internal stack traces or implementation details.

---

# ⚙️ Local Development

## Prerequisites

Make sure you have:

* Node.js
* npm
* A Supabase project for cloud-backed storage/database functionality

---

## Installation

Clone the repository:

```bash
git clone https://github.com/Vaedshukla/neurastore.git
cd neurastore
```

Install dependencies:

```bash
npm install
```

---

## Environment Variables

Create a local environment file:

```text
.env.local
```

Configure the required Supabase variables:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
```

Optional AI providers can be configured where supported:

```env
GEMINI_API_KEY=your_gemini_key
```

or:

```env
OPENAI_API_KEY=your_openai_key
```

### Important

Never commit real credentials to Git.

---

## Run Development Server

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

---

# 🧪 Testing

NeuraStore+ includes automated validation for its core workflows.

Run the document intelligence pipeline test:

```bash
node test_notebook_pipeline.js
```

Run API integration tests:

```bash
node test_api_integration.js
```

Run upload endpoint verification:

```bash
node test_upload_endpoint.js
```

Run live endpoint verification:

```bash
node verify_live_endpoint.js
```

Run TypeScript validation:

```bash
npx tsc --noEmit
```

Run linting:

```bash
npm run lint
```

Run the production build:

```bash
npm run build
```

The current QA cycle verified the core application areas and reported successful TypeScript, lint, build, Notebook, API, upload, and live endpoint tests.

---

# 🧭 Project Structure

A simplified view of the application:

```text
neurastore/
│
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── analyze/
│   │   │   ├── analyze-json/
│   │   │   ├── create-sql-table/
│   │   │   ├── file-metadata/
│   │   │   ├── handle-schema-conflict/
│   │   │   ├── infer-schema/
│   │   │   ├── insert-sql-rows/
│   │   │   ├── process-json/
│   │   │   ├── query-table/
│   │   │   ├── search/
│   │   │   ├── store-manual-json/
│   │   │   ├── summarize-document/
│   │   │   └── upload/
│   │   │
│   │   ├── dashboard/
│   │   ├── history/
│   │   ├── json-editor/
│   │   ├── notebook/
│   │   ├── search/
│   │   ├── settings/
│   │   └── upload/
│   │
│   ├── components/
│   └── lib/
│
├── public/
├── tests/
├── package.json
├── tsconfig.json
└── README.md
```

---

# 🔬 Engineering Philosophy

NeuraStore+ is built around several principles:

### 1. Data should be understandable

Storage should not be the final destination of data.

### 2. Structure should be discoverable

Users should not need to manually understand every incoming dataset before working with it.

### 3. Transformation should be accessible

Raw JSON should be capable of becoming structured, queryable data.

### 4. AI should remain grounded

Document intelligence should expose its supporting context rather than presenting unsupported answers as facts.

### 5. Failure should be explicit

Malformed input, missing resources, unsupported formats, and unavailable services should result in controlled behavior.

### 6. Human verification matters

Source citations and transparent retrieval make it easier for users to verify generated document answers.

---

# 🗺️ Roadmap

NeuraStore+ is intentionally designed as an extensible foundation rather than a finished endpoint.

## Phase I — Foundation

* [x] Multi-format upload
* [x] File metadata
* [x] File preview
* [x] Search
* [x] History
* [x] Dashboard
* [x] JSON analysis
* [x] JSON editor

## Phase II — Structured Data Intelligence

* [x] JSON structural analysis
* [x] Schema inference
* [x] JSON → SQL workflow
* [x] PostgreSQL integration
* [x] SQL querying
* [x] Schema conflict handling

## Phase III — Document Intelligence

* [x] PDF extraction
* [x] DOCX extraction
* [x] TXT extraction
* [x] Markdown extraction
* [x] Document chunking
* [x] Relevance retrieval
* [x] Summarization
* [x] Grounded Q&A
* [x] Source citations
* [x] Out-of-scope refusal behavior

## Future Directions

Potential future development areas include:

* Semantic/vector retrieval
* OCR for scanned documents
* Advanced multimodal understanding
* Richer dataset visualization
* More database targets
* Advanced schema evolution
* Collaborative workspaces
* Authentication and authorization
* Fine-grained access control
* Background processing
* Large-scale document ingestion
* Pluggable AI providers
* Advanced observability
* Production-scale storage pipelines

> These represent future directions rather than current capabilities.

---

# ⚠️ Current Limitations

NeuraStore+ is an actively evolving project.

### OCR

Image-only/scanned PDFs are not currently processed through a dedicated OCR pipeline.

### Retrieval

NeuraNotebook currently uses lexical TF-IDF relevance scoring rather than a vector-embedding retrieval architecture.

### Serverless Storage

Local filesystem fallback is intended for development scenarios. Production serverless deployments should use persistent cloud storage such as Supabase Storage.

These limitations are deliberately documented rather than hidden so contributors can clearly understand where future engineering work can have the greatest impact.

---

# 🌐 Deployment

NeuraStore+ is designed to be deployable as a modern Next.js application.

For serverless deployment platforms such as Vercel:

```text
Frontend / API
      ↓
Vercel
      ↓
Supabase
 ┌────┴─────┐
 ▼          ▼
Database   Storage
```

Persistent file storage should be configured through the cloud storage layer rather than relying on a serverless runtime filesystem.

---

# 🤝 Contributing

Contributions are welcome.

NeuraStore+ is particularly suitable for contributors interested in:

* Full-stack development
* Next.js
* React
* TypeScript
* PostgreSQL
* Data engineering
* JSON schema inference
* Database systems
* Information retrieval
* Document processing
* AI/LLM applications
* UI/UX
* Performance engineering
* Security
* Developer tooling

## Contribution Workflow

```bash
git checkout -b feature/your-feature
```

Make your changes.

Run:

```bash
npm run lint
npx tsc --noEmit
npm run build
```

Run relevant tests:

```bash
node test_notebook_pipeline.js
node test_api_integration.js
node test_upload_endpoint.js
```

Commit:

```bash
git commit -m "feat: describe your change"
```

Push:

```bash
git push origin feature/your-feature
```

Then open a Pull Request.

---

# 🧑‍💻 Open Source Development

NeuraStore+ is being developed with an emphasis on:

* Reproducible development
* Clear architecture
* Automated verification
* Defensive error handling
* Security-conscious implementation
* Incremental feature development
* Contributor-friendly engineering

Contributors are encouraged to focus on **small, testable, reviewable changes** rather than large unverified rewrites.

---

# 📈 Project Status

**Current Status: Active Development / GSSoC 2026**

The current implementation includes:

```text
✓ Multi-format file workspace
✓ Upload & file management
✓ File preview
✓ Search
✓ History
✓ Analytics dashboard
✓ JSON analysis
✓ JSON editor
✓ JSON → PostgreSQL workflow
✓ SQL querying
✓ Schema inference
✓ Document extraction
✓ NeuraNotebook
✓ Document summarization
✓ Grounded document Q&A
✓ Source citations
✓ Out-of-scope question handling
✓ Automated regression testing
✓ TypeScript validation
✓ ESLint validation
✓ Production build validation
```

The project has undergone an adversarial QA cycle covering its principal frontend routes, API surface, document intelligence workflows, error cases, security checks, and responsive behavior.

---

# 🎯 Vision

NeuraStore+ is built around a larger idea:

> **The future of data management should not be limited to storing information. It should help people understand and work with it.**

The long-term vision is to evolve NeuraStore+ from an intelligent file workspace into a broader **data intelligence platform** capable of connecting:

```text
Files
  +
Datasets
  +
Databases
  +
Documents
  +
Search
  +
Analytics
  +
AI
  +
Human Verification
```

into one coherent environment.

The objective is not simply to build another storage interface.

It is to explore what happens when **storage, data engineering, information retrieval, and document intelligence converge into a single workspace.**

---

# ⭐ Why NeuraStore+?

NeuraStore+ sits at the intersection of several traditionally separate workflows:

```text
              ┌───────────────┐
              │ File Storage  │
              └───────┬───────┘
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Data Engineering  Search      Documents
        │             │             │
        ▼             ▼             ▼
    JSON → SQL     Retrieval     Notebook
        │             │             │
        └─────────────┼─────────────┘
                      ▼
              ┌───────────────┐
              │ NeuraStore+   │
              │               │
              │ Data          │
              │ Intelligence  │
              │ Workspace     │
              └───────────────┘
It brings these capabilities together into one application rather than treating them as independent tools.
# 📚 Documentation
For implementation details, architecture decisions, testing procedures, and development notes, refer to the repository documentation and source code.
# 📄 License
This project is licensed under the **MIT License**.
See [`LICENSE`](LICENSE) for details.
# 👨‍💻 Author
**Tanisha Singh**
Built as an open-source project for **Google Summer of Code-style collaborative development and GSSoC 2026 participation**.
# ⭐ Support the Project

If you find NeuraStore+ interesting:
* ⭐ Star the repository
* 🐛 Report bugs
* 💡 Suggest improvements
* 🔧 Submit Pull Requests
* 📖 Improve documentation
* 🧪 Add test coverage
* 🚀 Help shape the roadmap

**Repository:**
https://github.com/Tanisha-pie/neurastore
## NeuraStore+
### Store less blindly. Understand more intelligently.
**Raw data → Structured data → Searchable information → Grounded intelligence**
