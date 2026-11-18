# 🤖 Murshid Mini — LLM Application Engineering Project

**Course:** LLM Application Engineering (SDA-AIE-213)  
**Instructor:** Meaad Al-Marri  
**Developer:** Jana Kariri

## 📌 Project Overview

Murshid Mini is a fictional AI-powered service assistant developed as a four-day learning project using Python and Google Colab.

The project explores how to build an assistant that understands service-related questions, retrieves application statuses through controlled tools, validates user requests, and handles responses safely.

The project is designed to demonstrate the engineering concepts behind LLM applications, from basic question handling to testing, safety, and performance evaluation.

**Important:** The core application uses a deterministic mock client (`FakeClient`) rather than a live LLM. A separate notebook demonstrates a real language model.

---

## 📅 Project Development Journey

The project is organized into four development days, with each day focusing on a different stage of LLM application engineering.

### Day 1 — Foundations & Basic Assistant

**Goal:** Build the foundation of the service assistant.

What we did:

- Created a synthetic service directory containing predefined answers in Arabic and English.
- Built a `FakeClient` to simulate an AI client without requiring an external API.
- Implemented the `ask()` function to receive questions and return structured responses.
- Defined a response contract containing:
  - `trace_id`
  - `answer`
  - `model`
  - `latency_ms`
- Added input validation to handle empty or invalid questions.
- Used assertions to verify the assistant's responses.
- Saved baseline results as JSON.

**What we learned:** How to structure a basic assistant, simulate model interactions, validate inputs, and test expected outputs.

**Deliverable:** `baseline_results.json`

### Day 1 Extra — Real Language Model Demonstration

**Goal:** Explore how an actual language model generates responses.

What we did:

- Used Google's `FLAN-T5-small` model.
- Integrated Hugging Face Transformers.
- Ran inference locally on a CPU using Google Colab.
- Tested the model with an English service-related question.
- Recorded inference time and token counts.
- Compared a real model demonstration with the deterministic mock implementation.

**What we learned:** The difference between a simulated assistant and a real language model, including inference time and generated responses.

**Deliverable:** `live_model_demo.ipynb`

### Day 2 — Structured Data & Tool Integration

**Goal:** Make the assistant capable of retrieving application information safely.

What we did:

- Created synthetic application records with unique reference numbers.
- Introduced user identity and ownership verification.
- Built `extract_ticket()` to extract ticket information using simple rules and regular expressions.
- Implemented `validate_ticket()` to check the structure and validity of extracted information.
- Developed a read-only `check_status()` tool to retrieve application statuses.
- Built a routing function to determine whether a request should be answered, clarified, or rejected.
- Added protection against unauthorized access.
- Tested five different scenarios.
- Verified that application records remained unchanged.
- Checked that Day 1 functionality still worked through regression testing.

**What we learned:** How to connect an assistant to tools, validate structured information, manage user permissions, and prevent unauthorized data access.

**Deliverable:** `day2_results.json`

### Day 3 — Safety Guards & Testing

**Planned focus:** Improve the assistant's reliability and control how it handles different user requests.

The planned work includes:

- Introducing versioned prompts.
- Adding input safety guards.
- Building a structured processing pipeline.
- Creating golden test cases.
- Testing expected behavior across different inputs.
- Improving consistency and handling unsupported requests.

**Learning objective:** Understand how prompt design, safety checks, and systematic testing contribute to reliable LLM applications.

**Status:** Planned / Not yet completed.

### Day 4 — Evaluation, Caching & Finalization

**Planned focus:** Evaluate the assistant and prepare the project for its final version.

The planned work includes:

- Implementing a cache for public answers.
- Measuring application performance.
- Evaluating response behavior.
- Running regression tests.
- Exporting final results.
- Reviewing the complete project workflow.

**Learning objective:** Understand how caching, evaluation, and performance measurements help improve AI application efficiency and reliability.

**Status:** Planned / Not yet completed.

---

## 🛠️ Technologies & Tools

| Technology | Purpose |
|---|---|
| Python | Core application development |
| Google Colab | Development environment |
| Hugging Face Transformers | Real-model demonstration |
| FLAN-T5-small | Language model experiment |
| JSON | Structured data and result storage |
| Regular Expressions | Ticket information extraction |
| Assertions | Functional testing |

## 📂 Repository Structure

- `notebooks/` — Project notebooks.
- `homework/` — Course exercises and assignments.
- `result/core/` — Core project outputs.
- `README.md` — Project documentation.
- `Untitled2.ipynb` — Additional notebook.

The main project notebook covers Days 1–2, while the real-model demonstration is maintained separately.

## 🚀 How to Run

1. Open the project notebook in Google Colab.
2. Select a Python 3.9+ CPU runtime.
3. Run the notebook cells in order.
4. Review the generated outputs and test results.

The core mock-based implementation does not require an API key, paid API, GPU, or additional package installation.

For the optional real-model demonstration, internet access is required to download the model and its dependencies.

## 🔒 Limitations & Considerations

- The core application is a simulation, not a production-ready AI service.
- The mock client does not generate responses using a real LLM.
- All application records are synthetic.
- Ownership verification is a teaching example, not production authentication.
- Passing predefined tests does not guarantee general reliability.
- The optional real-model demonstration is a limited experiment, not a full performance benchmark.

## 🎓 Learning Outcomes

Throughout this project, I explored:

- Building structured LLM application workflows.
- Understanding the difference between mock clients and real language models.
- Designing prompts and response contracts.
- Integrating tools into assistant workflows.
- Validating structured data and user inputs.
- Implementing basic access-control logic.
- Testing application behavior using predefined scenarios.
- Understanding reliability and performance evaluation.

## 👩🏻‍💻 Author

**Jana Kariri**

LLM Application Engineering Student | AI Enthusiast

- [GitHub Profile](https://github.com/janakariri)
- [SDAIA Academy](https://github.com/SDAIAAcademy)

---

*Developed as part of the LLM Application Engineering course (SDA-AIE-213).* 
---

*Built as part of the LLM Application Engineering course — SDA-AIE-213.*

---

*Built as part of the LLM Application Engineering course — SDA-AIE-213.*
