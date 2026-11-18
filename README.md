# 🤖 Murshid Mini — AI-Powered Service Assistant

**LLM Application Engineering | SDA-AIE-213**  
**Instructor:** Meaad Al-Marri  
**Developer:** Jana Kariri

---

## 📌 Overview

Murshid Mini is an educational AI application engineering project that demonstrates how to build a structured service assistant capable of understanding user requests, answering frequently asked questions, and retrieving application statuses through controlled tool interactions.

The project focuses on building reliable AI application workflows, with particular attention to input validation, access control, safety, testing, and response consistency.

> **Project Goal:** Build a reliable assistant by combining language-model concepts with structured application logic and controlled tool execution.

## ✨ Key Features

- **Bilingual Support:** Handles Arabic and English service-related questions.
- **Question Handling:** Provides predefined answers to common service inquiries.
- **Application Status Tracking:** Retrieves application status through a controlled, read-only tool.
- **Input Validation:** Validates user inputs and requests clarification when information is missing.
- **Access Control:** Checks record ownership before returning application information.
- **Safety Guards:** Rejects unsupported actions and unsuitable requests.
- **Testing & Evaluation:** Uses predefined test cases to verify expected behavior.
- **Response Consistency:** Follows a structured response format.

## 🛠️ Technical Concepts

| Concept | Description |
|---|---|
| Python | Core application development |
| LLM Engineering | Language-model application design |
| Prompt Engineering | Structured prompt design |
| Tool Calling | Controlled external tool interactions |
| Input Validation | Checking and validating user requests |
| Access Control | Protecting user-specific information |
| JSON | Structured data and result storage |
| Testing | Assertions and regression testing |

## 🏗️ Project Architecture

The application follows a structured workflow:

1. **User Input:** Receives a question in Arabic or English.
2. **Input Validation:** Checks whether the request is valid.
3. **Request Processing:** Identifies the requested service.
4. **Tool Execution:** Retrieves application information when authorized.
5. **Safety Checks:** Prevents unauthorized access and unsupported actions.
6. **Response Generation:** Returns a structured response to the user.

## 🔒 Security & Reliability

Security and reliability are important learning objectives in this project.

- Ownership verification before accessing application records.
- No disclosure of another user's application status.
- Missing information is handled through clarification requests.
- Unsupported operations are rejected.
- Synthetic data is used throughout the project.

## 🧪 Testing

The project includes predefined test scenarios covering:

- Successful application status retrieval.
- Missing reference numbers.
- Non-existing application records.
- Unsupported requests.
- Unauthorized access attempts.

## 🚀 Getting Started

### Requirements

- Python 3.9+
- Google Colab
- Internet connection for the optional real-model demonstration.

### Run the Project

1. Clone or download this repository.
2. Open the project notebook in Google Colab.
3. Select a Python runtime.
4. Run the notebook cells in order.
5. Review the generated outputs and test results.

The core mock-based implementation does not require an API key or paid services.

## ⚠️ Limitations

- This is an educational project, not a production-ready service.
- The core implementation uses a deterministic mock client rather than a live LLM.
- All application records are synthetic.
- Security and authentication mechanisms are simplified for learning purposes.
- Test results do not guarantee general-purpose reliability.

## 🎓 Learning Outcomes

Through this project, I explored practical concepts in AI application engineering, including:

- Designing structured AI application workflows.
- Understanding tool integration and controlled execution.
- Implementing input validation and access control.
- Building testable and reliable application components.
- Understanding the difference between mock-based systems and real language models.
- 
## 👩🏻‍💻 Author

**Jana Kariri**

Student & AI Enthusiast

- [GitHub Profile](https://github.com/janakariri)
- [SDAIA Academy](https://github.com/SDAIAAcademy)

---

*Built as part of the LLM Application Engineering course — SDA-AIE-213.*

---

*Built as part of the LLM Application Engineering course — SDA-AIE-213.*
