# AI Roadmap — Full Detail Edition (Topics, Free Resources, Guidance)
 
**Goal:** Switch into a stable, hands-on AI-adjacent role (AI Solutions/Implementation Engineer, Applied AI Support, Applied AI Engineer) efficiently, with zero wasted theory.
**Total timeline:** ~8–10 weeks at ~10-15 hrs/week alongside a full-time job. Faster if you can go full-time on this.
 
---
 
## How to Use This Roadmap
 
- Work top to bottom — each step assumes the previous one.
- Don't binge-watch courses without typing code yourself. Every "free resource" below should end with you writing something, not just watching.
- Keep a public GitHub from Day 1, even for tiny scripts. Recruiters and hiring managers do check.
- Join at least one community (list at the bottom) — half of this journey is knowing what's normal to not-know yet.
---
 
## Step 1: Python + API Basics (2 weeks)
 
### Detailed topics
- **Syntax fundamentals:** variables, data types, conditionals, loops, functions, list/dict comprehensions
- **Data structures:** lists, dicts, sets, tuples — when to use which
- **File handling:** reading/writing `.txt`, `.json`, `.csv`
- **Environments & packaging:** `venv`, `pip install`, `requirements.txt`
- **HTTP & APIs:** what REST APIs are, GET vs POST, headers, authentication (API keys, bearer tokens)
- **Calling an LLM API:** Anthropic or OpenAI SDK — sending a message, handling the response object, streaming vs non-streaming
- **Error handling:** `try/except`, retries, timeouts — APIs fail in production, you must handle it
- **pandas basics:** loading CSVs, filtering rows, groupby, basic aggregation
- **JSON parsing:** nested dicts, `.get()` safely, handling malformed responses
### Free resources
- **freeCodeCamp — "Python for Everybody" (full course, video, free)** — https://www.freecodecamp.org/news/python-full-course/
- **Official Python Tutorial (best as reference)** — https://docs.python.org/3/tutorial/
- **Automate the Boring Stuff with Python (entire book free online)** — https://automatetheboringstuff.com/
- **Corey Schafer's YouTube channel** — search "Corey Schafer Python OOP," "Corey Schafer requests module," "Corey Schafer pandas" some of the clearest free explanations available
- **Kaggle Learn — "Python" and "Pandas" micro-courses (free, hands-on, ~3-4 hrs each)** — https://www.kaggle.com/learn
- **Anthropic API Quickstart** — https://docs.claude.com/en/docs/get-started
- **OpenAI API Quickstart** — https://platform.openai.com/docs/quickstart
- **Real Python — "API Integration in Python"** — https://realpython.com/api-integration-in-python/
- **HTTPie or Postman (free tools)** for testing API calls before writing code — https://httpie.io/ / https://www.postman.com/
**Milestone:** A script that reads a `.txt` file, sends it to an LLM API with a specific instruction, and writes the structured response to a new file — with error handling.
 
---
 
## Step 2: How LLMs Work, Conceptually (3–5 days)
 
### Detailed topics
- **Tokenization:** subword tokenization, why "strawberry" might be 3 tokens, cost implications
- **Embeddings:** vectors, cosine similarity, why "king - man + woman ≈ queen" works conceptually
- **Attention mechanism:** high-level — how the model decides what to "focus on" in context (no matrix math needed)
- **Context window:** what it is, "lost in the middle" phenomenon, cost/latency trade-offs of long context
- **Model training phases:** pretraining (raw text prediction) → fine-tuning (task-specific) → RLHF/RLAIF (alignment to human/AI preference)
- **Sampling parameters:** temperature, top-p, top-k — what each does to output randomness
- **Hallucination:** why it happens (next-token prediction ≠ fact-checking), how RAG mitigates it
- **Model families landscape (2026):** rough sense of Claude, GPT, Gemini, and open-weight models (Llama, Mistral, Qwen) — what "open-weight" even means
### Free resources
- **"The Illustrated Transformer" — Jay Alammar** — https://jalammar.github.io/illustrated-transformer/ (the best visual explainer that exists)
- **"The Illustrated GPT-2" — Jay Alammar** — https://jalammar.github.io/illustrated-gpt2/
- **3Blue1Brown — "Neural Networks" playlist (YouTube, free)** — search "3Blue1Brown neural networks"; also his "Attention in transformers, step by step" video is excellent
- **Hugging Face LLM Course (free, chapters 1–2 cover exactly this)** — https://huggingface.co/learn/llm-course
- **Anthropic's "Prompt Engineering Overview"** (also explains model behavior) — https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview
- **Andrej Karpathy — "Let's build GPT: from scratch, in code" (YouTube, free)** — search "Karpathy let's build GPT" — optional but excellent if you want to go one level deeper
- **StatQuest with Josh Starmer — "Transformers" video** — clear, beginner-friendly explanations, free on YouTube
**Milestone:** Explain out loud, without notes, why an LLM can be confidently wrong, and what temperature=0 vs temperature=1 would change about its output.
 
---
 
## Step 3: Prompt Engineering + RAG (2–3 weeks) — highest leverage step
 
### Detailed topics
 
**Prompt engineering:**
- System prompts vs. user prompts — what belongs in each
- Zero-shot vs. few-shot prompting — when examples help vs. add noise
- Chain-of-thought prompting — "think step by step," why it improves reasoning tasks
- Structured output — forcing JSON schemas, XML tags, function-call-style outputs
- Role prompting — giving the model a persona/context to shape tone
- Prompt failure modes — ambiguity, contradictory instructions, prompt injection basics, context overflow
- Iterative prompt testing — treating prompts like code you version and test
**RAG (Retrieval-Augmented Generation):**
- Why RAG exists — grounding in real/current data vs. relying on parametric memory
- Embeddings for semantic search — how text becomes a vector, cosine similarity for "closeness"
- Vector databases — Chroma (easiest/free/local), Pinecone (managed, free tier), Weaviate, or pgvector (if you know Postgres)
- Chunking strategies — fixed-size vs. semantic chunking, overlap, why chunk size affects retrieval quality
- Embedding models — OpenAI's `text-embedding-3-small`, open-source options via Hugging Face (`sentence-transformers`)
- Retrieval + generation pipeline — retrieve top-k chunks → construct prompt → generate answer
- Hybrid search — combining keyword (BM25) + vector search for better retrieval
- Evaluating retrieval quality — precision@k, manually reviewing whether retrieved chunks are actually relevant
### Free resources
- **Anthropic's Prompt Engineering docs (full section, very thorough)** — https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview
- **"Prompt Engineering Guide" (comprehensive, community-run, free)** — https://www.promptingguide.ai/
- **OpenAI's Prompt Engineering guide** — https://platform.openai.com/docs/guides/prompt-engineering
- **DeepLearning.AI short courses (all completely free, ~1-2 hrs each, by Andrew Ng's team):**
  - "ChatGPT Prompt Engineering for Developers" — https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/
  - "Building Applications with Vector Databases" — https://www.deeplearning.ai/short-courses/building-applications-vector-databases/
  - "LangChain: Chat with Your Data" — https://www.deeplearning.ai/short-courses/langchain-chat-with-your-data/
  - "LangChain for LLM Application Development" — https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/
  - "Advanced Retrieval for AI with Chroma" — https://www.deeplearning.ai/short-courses/advanced-retrieval-for-ai/
- **Chroma DB — Getting Started (free, open-source, runs locally)** — https://docs.trychroma.com/getting-started
- **LlamaIndex — Starter Tutorial** — https://docs.llamaindex.ai/en/stable/getting_started/starter_example/
- **Pinecone Learning Center (excellent free conceptual articles on RAG, embeddings, vector search)** — https://www.pinecone.io/learn/
- **Hugging Face `sentence-transformers` docs (free open-source embeddings)** — https://www.sbert.net/
- **"RAG From Scratch" video series by LangChain (YouTube, free)** — search "LangChain RAG from scratch"
**Milestone:** Build a working script: takes a question → embeds it → retrieves top-k relevant chunks from a small document set → generates a grounded answer citing the source chunk.
 
---
 
## Step 4: Build ONE Real Project (2–3 weeks)
 
### What to build
A **RAG chatbot over real documents.** Good source material options:
- Public documentation for any product or open-source tool you know reasonably well
- A hobby topic you have plenty of reference material on (recipes, a game's wiki, a course's lecture notes)
- Your own notes, essays, or a personal knowledge base
- Functionality: user asks a question → system retrieves relevant chunks → generates a grounded answer → **cites which document/section** it came from
- Bonus (do this if time allows): add a simple feedback mechanism — thumbs up/down on answers, logged for review
### Detailed topics to apply while building
- Project structure: clear folder layout, `requirements.txt`, `.env` for secrets
- Basic evaluation: write 15-20 real test questions with expected answers, check pass/fail manually or with a simple script
- Handling edge cases: what happens when no relevant chunk is found? (Should say "I don't know," not hallucinate)
- README writing: problem statement, architecture diagram (even simple), design decisions, known limitations, what you'd improve with more time
- GitHub hygiene: `.gitignore` for secrets/venvs, meaningful commit messages, no leaked API keys
### Free resources
- **GitHub's official "Get Started" docs** — https://docs.github.com/en/get-started
- **"Make a README" (a genuinely useful, simple guide)** — https://www.makeareadme.com/
- **Streamlit (free, fastest way to wrap a project in a usable UI)** — https://docs.streamlit.io/get-started
- **Gradio (alternative to Streamlit, also free, popular for AI demos)** — https://www.gradio.app/guides/quickstart
- **promptfoo (free, open-source eval framework for LLM apps)** — https://www.promptfoo.dev/docs/intro/
- **"Awesome RAG" GitHub repo (curated list of RAG resources/examples)** — search "awesome-rag github" for the latest curated list
- **Render or Railway (free tiers for deploying your project publicly)** — https://render.com/ / https://railway.app/
**Milestone:** A working, publicly viewable RAG chatbot on GitHub (and ideally deployed live), with a README a hiring manager would actually want to read.
 
---
 
## Step 5: Basic Tool/Agent Use (1 week)
 
### Detailed topics
- Function calling — defining a tool schema (name, description, parameters) the model can choose to invoke
- The request/response loop: model decides to call a tool → your code executes the real function → result returned to model → model responds using it
- Multi-tool setups — giving the model 2-3 tools and letting it pick the right one
- Where agents differ from RAG — RAG retrieves passively before generation; agents can take multi-step actions and decide what to do next
- Basic agent loops — reasoning → action → observation → repeat (ReAct-style pattern), at a conceptual level
- Guardrails — why you validate tool inputs/outputs before executing anything real (never let a model run arbitrary code unchecked)
### Free resources
- **Anthropic's Tool Use documentation** — https://docs.claude.com/en/docs/build-with-claude/tool-use
- **OpenAI's Function Calling guide** — https://platform.openai.com/docs/guides/function-calling
- **DeepLearning.AI — "Functions, Tools and Agents with LangChain" (free)** — https://www.deeplearning.ai/short-courses/functions-tools-agents-langchain/
- **DeepLearning.AI — "AI Agents in LangGraph" (free)** — https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/
- **ReAct paper explained (search "ReAct prompting explained" on YouTube for a free walkthrough rather than reading the raw paper)**
- **LangChain Agents documentation** — https://python.langchain.com/docs/how_to/#agents
**Milestone:** Add one real tool call to your Step 4 project — e.g., a "search documents" function the model explicitly invokes, or a calculator tool for numeric questions.
 
---
 
## Step 6: Reframe Resume + Target Roles (ongoing, start in parallel from Week 1)
 
### Detailed guidance
- **Rewrite bullet points to emphasize transferable skills**, don't just add keywords:
  - Problem-diagnosis or troubleshooting experience → "Performed root-cause analysis on complex systems, reducing repeat issues"
  - Experience explaining technical concepts to non-technical people → "Bridged technical and non-technical stakeholders, translating system behavior into actionable guidance"
  - Any experience with data, process improvement, or customer-facing technical work maps well onto AI-adjacent roles — reframe it explicitly
- **Feature your Step 4 project prominently** — top of resume or a dedicated "Projects" section with the GitHub link and a one-line result/impact
- **Target company types** that hire faster for this transition:
  - Enterprise SaaS adding AI copilots/agents (support tooling, CRM, dev tools)
  - AI-native startups with real paying customers (check they have revenue, not just funding — funding alone isn't stability)
  - Companies explicitly hiring "AI Solutions Engineer," "Implementation Engineer, AI," "Technical Support Engineer — AI/ML," "Forward Deployed Engineer"
- **Networking matters more than cold applications** for this kind of transition — reach out to people already in these roles for a 15-min chat before applying blind
### Free resources
- **LinkedIn job alerts** — set alerts for the exact titles above
- **Levels.fyi (free)** — https://www.levels.fyi/ — benchmark comp for these roles
- **AngelList/Wellfound (free)** — https://wellfound.com/ — good for AI-native startup roles specifically
- **"Cracking the PM Interview" style prep is NOT needed here** — instead prep to explain your project's architecture, trade-offs, and what you'd do differently, since that's what these interviews actually test
- **Pramp (free peer mock interviews)** — https://www.pramp.com/
---
 
## Communities & Ongoing Learning (join at least one)
 
- **Hugging Face Discord/Forums** — https://discuss.huggingface.co/ — active, beginner-friendly
- **r/LocalLLaMA and r/MachineLearning (Reddit)** — good pulse on what's actually being used in industry right now
- **LangChain Discord** — for RAG/agent-specific help when you're stuck
- **Latent Space (newsletter + podcast, free)** — search "Latent Space newsletter" — one of the best free ways to track what's actually shipping in AI, not just hype
- **Simon Willison's blog** — https://simonwillison.net/ — extremely practical, free, opinionated takes on LLM engineering from someone who builds real things
---
 
## Suggested Weekly Rhythm (10-15 hrs/week alongside a job)
 
| Day | Focus |
|-----|-------|
| Mon/Wed/Fri evenings (1.5-2 hrs) | New topic learning (watch/read + take notes) |
| Sat (3-4 hrs) | Hands-on coding — apply what you learned that week |
| Sun (2 hrs) | Review, debug, write up progress in your project's README or a personal log |
 
Consistency beats intensity — 10 focused hours a week for 8 weeks beats one chaotic 40-hour week.
 
---
 
## Summary Timeline
 
| Week | Focus |
|------|-------|
| 1–2 | Python + API basics |
| 2 (overlap) | How LLMs work conceptually |
| 3–5 | Prompt engineering + RAG |
| 5–7 | Build your one real project |
| 7–8 | Add basic agent/tool use |
| Throughout | Resume reframing + active networking/applications |
 
**The one thing that matters most:** Step 4. A real, working, well-documented project — with a clear story about the trade-offs you made — beats every course certificate combined. Everything else exists to make that project possible and defensible in an interview.
