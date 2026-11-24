# Perplexity Explorer

An interactive, single-file educational web application that demystifies language model **perplexity** and token probabilities using a real language model running directly inside your browser.

Built with plain HTML, CSS, and modern JavaScript (no build tools, no frameworks, no backend, and no API keys required).

---

## ✨ Features

- **🧠 Real On-Device Language Model**: Runs Hugging Face's `Xenova/distilgpt2` (8-bit quantized) in the browser via [Transformers.js](https://huggingface.co/docs/transformers.js).
- **📝 Sentence Analysis (Section 1)**: Type any sentence or choose from built-in sample phrases (`"I love Python"`, `"Python love I"`, `"The capital of France is Paris"`).
- **📊 Step-by-Step Perplexity Math (Section 2)**:
  - Token breakdown table showing visual space markers (`␣`), token probabilities \(P\), and surprise factor \(\frac{1}{P}\).
  - **Step 1**: Multiplication of all surprise values.
  - **Step 2**: Total token count \(N\).
  - **Step 3**: Perplexity calculated as \((\prod \frac{1}{P})^{1/N}\) and computed stably using logarithms: \(\exp(\text{average of } -\ln P)\).
- **🔮 Next-Token Predictions (Section 3)**: Reads the final token logits to display the top 8 next-word predictions with percentage bars.
- **🎛️ Interactive Manual Simulator (Section 4)**:
  - Experiment with your own token names and probabilities in real time.
  - Includes presets:
    - `"I love Python"` \((0.5, 0.8, 0.2)\) &rarr; Perplexity = **2.32**
    - `"All 1/8"` \((8 \text{ tokens at } 0.125)\) &rarr; Perplexity = **8**
    - `"One surprising word"` \((0.9, 0.9, 0.9, 0.01)\) &rarr; Perplexity = **3.42**

---

## 🚀 How to Run Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/Dhanraj-singh1/perplexity-explorer.git
   cd perplexity-explorer
   ```

2. Start any local static file server:
   ```bash
   # Using Python 3
   python3 -m http.server 8000
   ```

3. Open [http://localhost:8000](http://localhost:8000) in your web browser.

---

## 🛠️ Tech Stack

- **HTML5 & Vanilla CSS**: Clean, light design with white cards, rounded corners, and blue/purple accents.
- **Vanilla JavaScript (ES Modules)**: Self-contained logic for tokenization, stable softmax, and perplexity calculations.
- **Transformers.js v3**: Loads ONNX models directly into WebAssembly / WebGPU in the browser.
