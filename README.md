# Murshid Mini — My Learning Project

**LLM Application Engineering · SDA-AIE-213**
Instructor: **Meaad Al-Marri** · Student: **Jana**

A small fictional service assistant, built step by step over four days in Google Colab. It answers known service questions, will read application status through an authorized tool, rejects unsuitable inputs, is tested against fixed cases, and caches public answers safely.

> **What this project is:** the core project runs in `mode=mock`. `FakeClient` is a finite, deterministic simulator, **not a live language model**. The goal is to learn the engineering around an LLM-shaped interface. All data is synthetic. No paid API, API key, GPU or extra package is needed for the core notebook.

## Progress

| Day | Topic | Status |
|---|---|---|
| 1 | Foundations: synthetic directory, mock client, `ask`, response contract | Done |
| 1 (extra) | Real-model demo with FLAN-T5 small on CPU | Done |
| 2 | Structure and tools: validated ticket, read-only status lookup, ownership check | Done |
| 3 | Guard and test: versioned prompt, input guards, pipeline, golden cases | Planned |
| 4 | Measure and finish: public cache, measurements, regression, export | Planned |

## Repository contents

| File | Description |
|---|---|
| [`Murshid_lab1-2.ipynb`](Murshid_lab1-2.ipynb) | Core project notebook, Days 1–2. Later days are appended to this same notebook. |
| [`live_model_demo.ipynb`](live_model_demo.ipynb) | Optional, separate notebook: a real model generating one answer on CPU. |
| [`murshid_outputs/`](murshid_outputs) | JSON results saved by the notebook: `baseline_results.json` (Day 1) and `day2_results.json` (Day 2). |

## Day 1 — what I built

1. **Environment and mock client.** A synthetic service directory with an Arabic and an English answer, `save_json` for saving results, and `FakeClient`, which looks up fixed answers and counts its calls. It never calls an API.
2. **Baseline application.** `ask(question)` returns a response contract with four fields: `trace_id`, `answer`, `model`, `latency_ms`. Blank or non-string input returns a polite message and makes no mock call.
3. **Verification and milestone.** Assertions check the three known answers, the response fields, and that a blank question adds no mock call. Results are saved to `murshid_outputs/baseline_results.json`.

### Day 1 results

| Question | Answer |
|---|---|
| `كيف أتابع طلبي؟` | `يمكنك متابعة حالة طلبك باستخدام رقم المرجع.` |
| `How can I check my application status?` | `You can check your application status using its reference number.` |
| `ساعدني` | `ما الخدمة التي تحتاج مساعدة بشأنها؟` |

All checks passed. `trace_id` values and `latency_ms` vary between runs, which is expected.

## Day 2 — what I built

Added to the same notebook, below Day 1:

1. **Synthetic records and ticket.** Two fictional records (`REF-1001` owned by `demo-user-1`, `REF-1002` owned by `demo-user-2`), a trusted session identity, `extract_ticket` (simple rules and regex, not general NLP) and `validate_ticket` (exact keys, types, allowed values, and clarification consistency).
2. **Read-only tool and routing.** `check_status` looks up a record and checks ownership before returning any status. `route` refuses cancellation, asks for clarification when the reference number is missing, and sends status requests to the tool.
3. **Verification.** Five reference cases, a Day 1 regression check, and a check that the records are unchanged. Results are saved to `murshid_outputs/day2_results.json`.

### Day 2 results

| Question | Code | Tool calls |
|---|---|---:|
| `ما حالة طلبي REF-1001 في الرياض؟` | `under_review` | 1 |
| `أريد حالة طلبي` (no reference) | `needs_clarification` | 0 |
| `ما حالة REF-9999؟` (absent record) | `not_found` | 1 |
| `ألغ طلبي REF-1001` (cancellation) | `unsupported_action` | 0 |
| `ما حالة REF-1002؟` (another user's record) | `access_denied` | 1 |

Missing and unauthorized records both give the user the same outward message, so another user's status is never revealed. The identity check is a teaching fixture, not real authentication.

## Extra: real-model demonstration

`live_model_demo.ipynb` runs **`google/flan-t5-small`** (a pinned revision) locally on CPU through Hugging Face `transformers`. It needs internet access to download the library and model weights, but no API key and no paid service. Use a separate runtime from the core notebook.

Observed in my run:

| Item | Value |
|---|---|
| Question | `How can I check my application status?` |
| Answer | `Use its reference number` |
| Input tokens | 34 |
| Output tokens (including special) | 6 |
| Inference time | 0.775 s |
| External inference API calls | 0 |

This is one observation, not a benchmark. A non-empty answer is not proof of correctness; I checked that it points the user to the reference number and does not invent fees, dates or statuses. A small English-only example says nothing about Arabic quality or suitability for real deployment.

## How to run

1. Open `Murshid_lab1-2.ipynb` in [Google Colab](https://colab.research.google.com/) (File → Open notebook → GitHub, paste this repository's URL) with a Python 3.9+ CPU runtime.
2. Run the cells in order from the top; Day 2 depends on Day 1. Nothing needs installing.
3. For the optional demo, open `live_model_demo.ipynb` in a **separate** runtime and run the setup cell first. If Colab asks for a restart, restart and run all cells again.

## Limitations

- The core project is a simulation. It does not train a model or measure live LLM quality, and it does not implement production security.
- Keyword guards and ownership checks (in later days) are teaching examples, not real authentication.
- Passing fixed example cases is not a general reliability guarantee.
- Never add real personal or ministry records. Keep all data synthetic.

## Attribution

Based on the course **LLM Application Engineering · SDA-AIE-213**, instructor **Meaad Al-Marri**, with reference to the [SDAIA Academy GitHub account](https://github.com/SDAIAAcademy). Course reference repository: [almiyead-rgb/murshid-llm-application-engineering-sda-aie-213](https://github.com/almiyead-rgb/murshid-llm-application-engineering-sda-aie-213). This repository does not claim Academy endorsement or certification.
