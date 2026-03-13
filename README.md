# 🧠 MindKeeper: A Dual-Brain AI Agent for Dementia Homecare

**Course:** EECS E6895 Advanced Big Data and AI (Midterm Project)  
**Role of AI Agent:** Dementia Homecare Companion and Clinical Triage Agent  

MindKeeper is an AI system designed to solve the critical alignment conflict in dementia care. It uses a **Dual-Brain Architecture** to simultaneously provide profound emotional empathy to patients (via Validation Therapy) and strict, objective medical advice to caregivers (via a logical evaluation engine), ensuring both patient comfort and clinical safety.

---

## 📂 Repository Structure
Our repository is organized as follows to ensure reproducibility and out-of-the-box local execution:

    ├── src/ 
    │   └── MindKeeper_main.ipynb    # Main runnable notebook (UI, RAG, Eval, Memory Test)
    ├── data/
    │   ├── medical_corpus.jsonl     # Local knowledge base for RAG (Alzheimer's Guidelines)
    │   └── uniformed_dementia_finetuning_dataset.jsonl # Distilled dataset for evaluation
    ├── lora_weights/                # Fine-tuned QLoRA model adapter files (Included)
    ├── assets/                      # UI screenshots and evaluation reports
    ├── requirements.txt             # Python dependencies
    └── README.md

---

## 🛠️ How to Install Dependencies

To run MindKeeper, a GPU-enabled environment is highly recommended (e.g., a local machine with CUDA, or Google Colab with L4/T4 GPU).

**Step 1: Clone the repository**

    git clone https://github.com/Yiwen543/6895-midterm-project.git
    cd 6895-midterm-project

**Step 2: Install required Python packages**
You can install all dependencies via pip using the provided requirements file:

    pip install -r requirements.txt

*(Note: If you are running this in Google Colab or a fresh Jupyter environment, the first cell of our `MindKeeper_main.ipynb` already includes all the necessary pip install commands).*

---

## 🚀 How to Run the System

Because we have included the fine-tuned LoRA weights directly in this repository, the project is configured to run **out-of-the-box** locally without requiring Google Drive mounting.

**Step 1: Set up Hugging Face Token**
You need a valid Hugging Face token to download the base model (`Qwen/Qwen2.5-3B-Instruct`). Open `src/MindKeeper_main.ipynb`, locate the environment variable configuration in the first cell, and insert your token:

    os.environ["HF_TOKEN"] = "your_hf_token_here"

**Step 2: Verify Relative File Paths**
The paths to the dataset, RAG corpus, and LoRA weights are already configured using relative paths. As long as you run the notebook from within the `src/` directory, no changes are needed:

    adapter_path = "../lora_weights" 
    CORPUS_PATH = "../data/medical_corpus.jsonl" 
    EVAL_DATASET_PATH = "../data/uniformed_dementia_finetuning_dataset.jsonl"

**Step 3: Execute the Pipeline**
Simply "Run All" cells in the `MindKeeper_main.ipynb` notebook. The script will automatically:
1. Initialize the Base Model and load our local QLoRA weights.
2. Build the FAISS Vector Database for RAG.
3. Run the **Large-Scale Academic Evaluation Suite** (evaluating 50 cases for safety and empathy).
4. Run the **Deep Multiturn Memory Stress Test** with terminal UI rendering.

---

## 💡 Example Usage

When the system runs, it dynamically routes the user input and generates a split-screen response. Below is an example from our Multiturn Memory Stress Test demonstrating handling of hallucinations and memory recall:

### Scenario: Hallucination Management
**👤 [Patient]:** *"Look! There are little green men dancing on the television screen! They are laughing at me!"*

**MindKeeper Dual-Brain Output:**
* **🗣️ PATIENT FACING RESPONSE (Empathy Engine):** *"I see those little green men dancing right now, and they are making fun of everyone! Let's turn the TV off so they can't bother us anymore."* (Applies Validation Therapy instead of correcting the patient's reality).
* **📱 CAREGIVER ACTION DASHBOARD (Logic Engine):** * 🧠 **Risk Score:** `7/10 (🔴 HIGH RISK)`
  * 🔎 **Signs:** `Hallucination, Delusion`
  * 👨‍⚕️ **Actions:** `"Monitor the patient’s environment for potential triggers of hallucinations and ensure safety..."`

![Memory Test Screenshot](./assets/memory_test.jpg)

### Quantitative Evaluation
The system also outputs an automated academic evaluation report. In our 50-sample stress test, MindKeeper achieved a **100% Clinical Emergency Interception Rate**, a **100% Caregiver Action Compliance Rate**, and a **0.89+ BERTScore F1** for empathy semantic alignment.

![Evaluation Report Screenshot](./assets/eval_report.jpg)
