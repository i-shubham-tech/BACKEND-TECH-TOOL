# Generative AI

## Table of Contents

1. [What is GenAI (Foundation)](#1-what-is-genai-foundation)
   - Definition (Industry-level)
   - What GenAI is NOT
   - What GenAI actually does

2. [Core GenAI Architecture (Mental Model)](#2-core-genai-architecture-mental-model)

3. [Basic GenAI Setup (Hands-On)](#3-basic-genai-setup-hands-on)
   - Required Skills
   - Minimal Node.js Setup
   - Sample Code

4. [Models (What to Use & Why)](#4-models-what-to-use-why)

5. [Parameters (Control Behavior)](#5-parameters-control-behavior)
   - Core Parameters
   - Practical Guidance

6. [Chat Working (Memory Truth)](#6-chat-working-memory-truth)
   - Important Reality
   - How to Manage Memory

7. [Prompt Engineering (Reality)](#7-prompt-engineering-reality)
   - Good Prompt Structure
   - Examples
   - Tips

8. [Tools (Function Calling)](#8-tools-function-calling)
   - Why Tools Exist
   - Tool Flow
   - Example Tool

9. [Embeddings (Core Concept)](#9-embeddings-core-concept)
   - What Embeddings Are
   - Why Embeddings Matter
   - Create Embedding Example

10. [Vector Databases](#10-vector-databases)
    - Why Normal DB Fails
    - Workflow
    - Popular Options

11. [RAG (Retrieval Augmented Generation)](#11-rag-retrieval-augmented-generation)
    - Most Important Concept
    - RAG Flow
    - Industry Use

12. [Output Control & Structure](#12-output-control-structure)
    - Force JSON Output
    - Uses

13. [Agents (Advanced)](#13-agents-advanced)
    - Definition
    - Use Cases

14. [Security & Best Practices](#14-security-best-practices)
    - Recommendations

15. [What to Build (Mandatory Path)](#15-what-to-build-mandatory-path)
    - Beginner
    - Intermediate
    - Advanced

16. [Interview Expectations (2025)](#16-interview-expectations-2025)
    - Topics to Explain

17. [Final Mindset (Most Important)](#17-final-mindset-most-important)
    - Key Qualities of GenAI Engineers

## 1️⃣ WHAT IS GENAI (FOUNDATION)

### Definition (Industry-level)
Generative AI refers to systems that can generate new content (text, code, images, audio, structured data) using large pre-trained models.

### What GenAI is NOT
❌ Not magic  
❌ Not real intelligence  
❌ Not stateful memory

### What GenAI actually does
- Predicts next token based on probability
- Uses context, not understanding
- Requires your system design to be useful

---

## 2️⃣ CORE GENAI ARCHITECTURE (MENTAL MODEL)
```
User Input
   ↓
Prompt Engineering
   ↓
LLM (Model)
   ↓
Tools / Functions (optional)
   ↓
Response Formatting
```
**In Production:**
```
Frontend
   ↓
Backend API
   ↓
Prompt + Context Builder
   ↓
LLM
   ↓
Post-processing
   ↓
Client
```

---

## 3️⃣ BASIC GENAI SETUP (HANDS-ON)
### Required Skills
- JavaScript / Python
- Async programming
- REST APIs

### Minimal Node.js Setup
```bash
npm init -y
npm install openai dotenv
```

### `.env`
```
OPENAI_API_KEY=your_key
```

### Sample Code
```javascript
import OpenAI from "openai";
import dotenv from "dotenv";
dotenv.config();

const client = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,
});

const res = await client.chat.completions.create({
  model: "gpt-4.1-mini",
  messages: [{ role: "user", content: "Hello GenAI" }]
});

console.log(res.choices[0].message.content);
```
✅ If this works → setup complete.

---

## 4️⃣ MODELS (WHAT TO USE & WHY)
| Model Type    | Use Case             |
|---------------|----------------------|
| GPT-4.x      | Reasoning, interviews |
| GPT-4-mini   | Chatbots, apps        |
| Embedding models | Search, RAG     |
| Image models | Image generation      |

📌 **Rule:** Use the smallest model that solves the task

---

## 5️⃣ PARAMETERS (CONTROL BEHAVIOR)
### Core Parameters (Must Know)
| Parameter     | Purpose                        |
|---------------|--------------------------------|
| model         | Capability & cost              |
| temperature   | Creativity                     |
| max_tokens    | Output size                    |
| system        | Behavior control               |
| top_p         | Token probability              |

### Practical Guidance
| Use Case        | Temperature  |
|-----------------|--------------|
| Code            | 0.1          |
| Interview       | 0.2          |
| Chat            | 0.7          |
| Brainstorming   | 0.9          |

---

## 6️⃣ CHAT WORKING (MEMORY TRUTH)
### Important Reality
- **LLMs:**
  - ❌ Do NOT remember
  - ❌ Do NOT store state

### How to manage memory
- Resend context messages

### Example
```json
messages = [
  { role: "system", content: "You are an interviewer" },
  { role: "user", content: "What is Node.js?" },
  { role: "assistant", content: "..." },
  { role: "user", content: "Explain Event Loop" }
]
```

📌 **Production Tip:** Summarize old messages to reduce cost.

---

## 7️⃣ PROMPT ENGINEERING (REALITY)
### Good Prompt Structure
- Role
- Task
- Constraints
- Output format

### Example
```
You are a senior backend interviewer.
Explain Node.js event loop.
Use simple language.
Limit to 150 words.
```

❌ Long prompts ≠ better prompts  
✅ Clear prompts = predictable output

---

## 8️⃣ TOOLS (FUNCTION CALLING)
### Why Tools Exist
- LLM cannot:
  - Call APIs
  - Read DB
  - Access live data

### Tool Flow
User → LLM → Tool Decision → Your Function → LLM → Final Answer

### Example Tool
```json
{
  name: "getUser",
  description: "Fetch user data",
  parameters: {
    userId: "string"
  }
}
```

📌 Tools turn LLM into real applications

---

## 9️⃣ EMBEDDINGS (CORE CONCEPT)
### What Embeddings Are
- Text → Vector (numbers)
- Same meaning → vectors close together

### Why Embeddings Matter
Used in:
- Search
- Chat with PDFs
- Recommendations
- Memory
- RAG

### Create Embedding Example
```javascript
const emb = await client.embeddings.create({
  model: "text-embedding-3-small",
  input: "Node.js is asynchronous"
});
```

Output = numeric array

---

## 🔟 VECTOR DATABASES
### Why Normal DB Fails
- SQL = keyword match
- Vector DB = meaning match

### Workflow
Data → Chunk → Embed → Store  
Query → Embed → Similarity Search

### Popular Options
| Database    | Type      |
|-------------|-----------|
| Pinecone    | Managed   |
| ChromaDB   | Local     |
| FAISS       | Low-level |

---

## 1️⃣1️⃣ RAG (RETRIEVAL AUGMENTED GENERATION)
### Most Important Concept in GenAI
- LLM + Your data = Real AI app

### RAG Flow
1. User Question
2. Embedding
3. Vector Search
4. Relevant Docs
5. LLM + Context
6. Answer

### Industry Use
- No retraining
- Cheap
- Secure
- Live data

📌 90% enterprise GenAI = RAG

---

## 1️⃣2️⃣ OUTPUT CONTROL & STRUCTURE
### Force JSON Output
- Respond only in valid JSON

### Uses
- APIs
- Agents
- Automation

---

## 1️⃣3️⃣ AGENTS (ADVANCED)
- Agent = LLM + Tools + Goal
- Used for:
  - Code generation
  - Task automation
  - Analysis pipelines

---

## 1️⃣4️⃣ SECURITY & BEST PRACTICES
- Never expose API key
- Rate limit requests
- Validate user input
- Protect from prompt injection
- Log model responses

---

## 1️⃣5️⃣ WHAT TO BUILD (MANDATORY PATH)
### Beginner
- Simple chatbot
- Interview answer generator

### Intermediate
- PDF chat (RAG)
- Resume analyzer

### Advanced
- AI coding assistant
- Multi-tool agent

---

## 1️⃣6️⃣ INTERVIEW EXPECTATIONS (2025)
You must explain:
- How chat works internally
- RAG vs fine-tuning
- Embeddings & vectors
- Tools vs APIs
- Cost optimization

---

## 1️⃣7️⃣ FINAL MINDSET (MOST IMPORTANT)
GenAI engineers are:
- System designers, not prompt writers
- Cost-aware
- Security-first
- Product-oriented
```
