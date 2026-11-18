# 🤖 Murshid Mini — LLM Application Engineering

**Course:** LLM Application Engineering · SDA-AIE-213  
**Instructor:** Meaad Al-Marri  
**Developer:** Jana Kariri

## 📌 Project Overview

Murshid Mini is a fictional AI-powered service assistant developed as a four-day learning project using Python and Google Colab.

The assistant handles service-related questions, retrieves application statuses through authorized tools, validates user inputs, applies safety checks, and uses caching to improve efficiency.

The project demonstrates the engineering workflow behind building reliable LLM applications, from basic assistant development to testing, evaluation, and performance optimization.

**Note:** The core implementation uses a deterministic `FakeClient` in mock mode rather than a live LLM. All application records are synthetic.

---

## 📅 Development Progress

| Day | Topic | Status |
|---|---|---|
| Day 1 | Foundations, mock client, response contract | Completed |
| Day 1 Extra | Real-model demonstration using FLAN-T5-small | Completed |
| Day 2 | Structured data, tool integration, validation and access control | Completed |
| Day 3 | Prompt versioning, safety guards, pipeline and golden tests | Completed |
| Day 4 | Caching, performance measurements, regression testing and export | Completed |

---

## Day 1 — Foundations & Basic Assistant

**Objective:** Build the initial service assistant and establish its response structure.

### What I implemented

- Created a synthetic service directory with Arabic and English answers.
- Built `FakeClient` to simulate model responses without an external API.
- Implemented `ask(question)` to process user questions.
- Defined a structured response contract:
  - `trace_id`
  - `answer`
  - `model`
  - `latency_ms`
- Added input validation for empty and invalid questions.
- Used assertions to verify expected responses.
- Saved baseline results in JSON format.

### Results

Tested three sample questions covering Arabic, English, and general assistance.

<badge color="success">All checks passed</badge>

**Output:** `baseline_results.json`

### Day 1 Extra — Real Model Demonstration

- Integrated Hugging Face Transformers.
- Used `google/flan-t5-small`.
- Ran local inference on CPU.
- Recorded input/output tokens and inference time.
- Compared the real-model experiment with the mock implementation.

**Observed inference time:** 0.775 seconds.

**Output:** `live_model_demo.ipynb`

---

## Day 2 — Structured Data & Tool Integration

**Objective:** Enable the assistant to retrieve application information through controlled tools.

### What I implemented

- Created synthetic application records.
- Added reference number extraction using `extract_ticket()`.
- Implemented `validate_ticket()` to validate extracted information.
- Developed the read-only `check_status()` tool.
- Added ownership verification before accessing application records.
- Implemented request routing using `route()`.
- Handled missing references and unsupported actions.
- Added regression tests to ensure Day 1 functionality remained intact.

### Results

Tested five scenarios:

| Test Scenario | Expected Result |
|---|---|
| Valid application reference | Status retrieved |
| Missing reference number | Needs clarification |
| Non-existing reference | Not found |
| Cancellation request | Unsupported action |
| Unauthorized record access | Access denied |

**Output:** `day2_results.json`

The tests also verified that application records remained unchanged.

---

## Day 3 — Prompt Engineering & Safety Guards

**Objective:** Improve assistant reliability and control how requests are processed.

### What I implemented

- Introduced prompt versioning to organize and maintain prompt configurations.
- Added input safety guards to handle unsuitable or unsupported requests.
- Built a structured processing pipeline.
- Implemented golden test cases to verify expected assistant behavior.
- Tested different input scenarios.
- Improved request handling and response consistency.
- Verified that the assistant follows the defined safety rules.

### Key Learning Outcomes

- Understanding prompt versioning.
- Applying safety checks before processing requests.
- Organizing assistant logic into a structured pipeline.
- Using golden tests to validate expected behavior.

**Status:** Completed.

---

## Day 4 — Caching, Evaluation & Finalization

**Objective:** Improve application efficiency and validate the final workflow.

### What I implemented

- Added caching for public service answers.
- Implemented cache handling to reuse previously generated public responses.
- Measured application performance.
- Evaluated response behavior and execution efficiency.
- Ran regression tests to verify previously implemented functionality.
- Exported project results for review and documentation.
- Reviewed the complete application workflow.

### Key Learning Outcomes

- Understanding caching and its role in performance optimization.
- Measuring application execution performance.
- Evaluating application behavior.
- Using regression testing to maintain functionality.
- Organizing and exporting final project results.

**Status:** Completed.

---

## 🛠️ Technologies & Tools

| Technology | Purpose |
|---|---|
| Python | Application development |
| Google Colab | Development environment |
| Hugging Face Transformers | Model integration |
| FLAN-T5-small | Real-model demonstration |
| JSON | Data and results storage |
| Regular Expressions | Reference extraction |
| Assertions | Testing and validation |
| Caching | Performance optimization |

## 📂 Repository Structure

| Directory / File | Description |
|---|---|
| `homework/` | Course homework and exercises |
| `notebooks/` | Development notebooks |
| `result/core/` | Core project results |
| `Murshid_lab1-2.ipynb` | Main project notebook |
| `live_model_demo.ipynb` | Real-model demonstration |
| `README.md` | Project documentation |

## 🚀 How to Run

1. Open the project notebook in Google Colab.
2. Select a Python runtime.
3. Run the notebook cells in order.
4. Review the generated outputs and test results.

The core mock implementation does not require an API key or paid service.

The optional real-model demonstration requires internet access to download the model and its dependencies.

## 🔒 Limitations

- The core application uses a simulated client rather than a production LLM.
- All application records are synthetic.
- Ownership verification is a learning example, not production authentication.
- The real-model demonstration is limited and does not represent a full benchmark.
- Passing predefined test cases does not guarantee general reliability.

## 🎓 Key Learning Outcomes

Throughout this four-day project, I gained practical experience in:

- Building structured LLM applications.
- Working with mock clients and real language models.
- Prompt engineering and prompt versioning.
- Integrating tools into assistant workflows.
- Implementing input validation and safety guards.
- Managing structured data and access control.
- Creating automated tests and regression checks.
- Applying caching and measuring performance.
- Evaluating and documenting AI application workflows.

## 👩🏻‍💻 Author

**Jana Kariri**

LLM Application Engineering Student | AI Enthusiast

- [GitHub Profile](https://github.com/janakariri)
- [SDAIA Academy](https://github.com/SDAIAAcademy)

---

*Developed as part of the LLM Application Engineering course — SDA-AIE-213.*


*Built as part of the LLM Application Engineering course — SDA-AIE-213.*
