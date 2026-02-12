**Specs Extraction**

The goal of this project is to build a system that extracts structured vehicle specifications (e.g., torque values) from an automotive service manual PDF using retrieval and LLM-based techniques.

Given a user query such as:
"Lower ball joint nut torque"
the system retrieves relevant sections from the service manual and returns structured output in JSON or CSV format.

**Model Design**
Query -> Embedding -> FAISS vector search -> Retreive -> Structured Extraction (Regex) -> Semantic Component Filtering -> JSON Output

**Tools and Models Used**

**1. PDF Parsing**
PyMuPDF (fitz) - Used to extract raw text from the service manual PDF.

**2. Text Processing and Chunking**
Custom text cleaning, Section-based chunking (split by section headers like SECTION 204-01A) - This preserves logical structure instead of naive character-based splitting.

**3. Embeddings**
SentenceTransformer - BAAI/bge-base-en-v1.5
Chosen because of strong semantic retrieval performance

**4. Vector Store**
FAISS (Facebook AI Similarity Search)
Retrieving most relevant sections for a given query

**5. Structured Extraction**
Regex-based torque table extraction, instead of relying entirely on LLM output (which can hallucinate or misformat), deterministic regex patterns are used to extract relevant parts.



