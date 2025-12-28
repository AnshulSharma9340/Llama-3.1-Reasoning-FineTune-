🚀 ReasonMind-3B
Distilling Deep Reasoning into a 3B Parameter LLM using Unsloth, QLoRA & Llama-3.1

ReasonMind-3B is an advanced reasoning-distilled language model built on Llama-3.1 (3B), fine-tuned using Unsloth and 4-bit QLoRA.
The model learns to perform Chain-of-Thought (CoT) reasoning inspired by DeepSeek-R1 — enabling structured, step-by-step logical thinking even on small hardware.

This project demonstrates how reasoning capabilities can be compressed, distilled, and efficiently deployed in a compact model format that runs fully offline.

🔍 Project Overview

Standard small LLMs struggle with complex reasoning. ReasonMind-3B solves this by:

Using DeepSeek-R1 reasoning traces through the R1-Distill-SFT dataset

Fine-tuning with Unsloth to reduce VRAM usage by ~60%

Leveraging 4-bit QLoRA, training only ~0.5% parameters

Adding a built-in <think> reasoning phase for structured problem solving

Deploying in GGUF (Q8_0) format compatible with Ollama, LM Studio, and llama.cpp

This enables accurate reasoning on multi-step math, logic puzzles, word problems, and analytical tasks — all on a single GPU or CPU.

🧠 Key Features
✔ Chain-of-Thought Reasoning

Model generates a hidden <think> block replicating step-by-step reasoning.

✔ Unsloth-Optimized Training

2× faster training
60% lower VRAM usage
Ideal for low-resource environments

✔ 4-bit QLoRA Fine-Tuning

Training is lightweight — you only update a tiny slice of parameters.

✔ Distilled from DeepSeek-R1 Logic

High-quality reasoning examples = stronger logic abilities.

✔ Offline Deployment via GGUF

Compatible with:

Ollama

LM Studio

llama.cpp / llama-cpp-python

📁 Repository Structure after Run the Ipynb File
ReasonMind-3B/
│
├── train_model.ipynb        # Full Unsloth + QLoRA training notebook
├── evaluation.ipynb         # Reasoning evaluation tests
├── inference_demo.py        # Offline inference demo using GGUF
│
├── unsloth_config.py        # Training hyperparameters & LoRA config
├── prompt_template.txt      # Llama-3.1 Chat Template
│
├── data/
│   └── r1_distill/          # Instructions for dataset download
│
├── model/
│   └── gguf/                # Final exported GGUF model (Q8_0)
│
├── README.md
└── requirements.txt

🔧 Technical Details
Base Model

Llama-3.1 3B (Instruct)

Fine-Tuning Stack

Unsloth (for optimized training)

QLoRA (4-bit quantization, LoRA ranks)

Gradient Checkpointing

PagedAttention

Dataset

ServiceNow-AI / R1-Distill-SFT
(Derived from DeepSeek-R1 reasoning traces)

Training Hardware

Single GPU setup

< 16GB VRAM required

Extremely lightweight training

Deployment Format

GGUF (Q8_0)

Compatible with llama.cpp ecosystem

🔥 Inference Example (Python)
from llama_cpp import Llama

llm = Llama(model_path="model/gguf/reasonmind-3b-q8_0.gguf")

response = llm("Solve: If A has 3 apples and buys 5 more, how many total?")
print(response["choices"][0]["text"])

🧪 Sample Output (Reasoning + Final Answer)
<think>
A has 3 apples. He buys 5 more.  
3 + 5 = 8 apples.  
</think>

Final Answer: 8 apples.

⚙️ Installation
1. Clone Repository
git clone https://github.com/yourusername/ReasonMind-3B.git
cd ReasonMind-3B

2. Install Requirements
pip install -r requirements.txt

3. Download GGUF Model

Place your exported Q8_0 GGUF file into:

model/gguf/

🏁 Training Instructions (Unsloth + QLoRA)

Inside train_model.ipynb, you will find:

Full model loading code

LoRA configuration

Chat template formatting

Reasoning-distillation training loop

Checkpointing & GGUF export

Simply run the notebook end-to-end.

📊 Evaluation

Run:

jupyter notebook evaluation.ipynb


Includes tests for:

Multi-step logical reasoning

Math chain-of-thought

Word puzzles

Analytical tasks

🎯 Why This Project Matters

ReasonMind-3B showcases how deep reasoning abilities can be distilled into tiny models, enabling:

Offline private inference

Low-cost intelligent assistants

Teaching models reasoning patterns

Foundation for building custom domain reasoning LLMs

This project brings powerful reasoning AI closer to everyone — even on machines with limited hardware.

🤝 Contributing

Pull requests, suggestions, and improvements are welcome!

⭐ Give a Star!

If you find this project useful, please consider starring the repo — it helps a lot. ⭐
