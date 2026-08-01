# AI Code Architect | Hybrid Edition 🚀

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat&logo=react&logoColor=white)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38Bdf8?style=flat&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Ollama](https://img.shields.io/badge/Ollama-Local%20AI-orange?style=flat&logo=ollama&logoColor=white)](https://ollama.com/)
[![Gemini API](https://img.shields.io/badge/Google-Gemini%20API-4285F4?style=flat&logo=google&logoColor=white)](https://ai.google.dev/)

**AI Code Architect** is a cutting-edge, client-side web application designed to act as your Senior Software Architecture mentor. It ingests multi-file source code projects (`.cpp`, `.py`, `.js`, `.rs`, `.go`, etc.), performs semantic code analysis using either **local LLMs (via Ollama)** or **cloud LLMs (Google Gemini API)**, and generates an interactive, node-based system architecture diagram with step-by-step code simulation and traceability.

---

## 🌟 Key Features

*   **Hybrid AI Engine (Local vs. Cloud):**
    *   **Local Mode (Ollama):** Run completely offline with privacy using local coding models like `qwen2.5-coder:7b` with GPU/CPU acceleration.
    *   **Cloud Mode (Gemini API):** Utilize Google's high-speed Flash/Pro models for lightning-fast analysis and deep architectural insights.
*   **Multi-File Workspace:** Upload or create multiple source files simultaneously. Switch seamlessly between tabs while keeping track of line mapping.
*   **Interactive Architecture Canvas:**
    *   Semantic classification of nodes (`Classes/Structs`, `Functions/Methods`, `Control/Loops`, `I/O/Hardware`, `Variables/State`).
    *   Dynamic zoom, pan, and node dragging capabilities.
    *   Visual data-flow and control-flow edges with animated indicators.
*   **Step-by-Step Code Flow Simulator:** Play, pause, and step through the logical execution flow of the project. Watch as the inspector highlights the exact purpose, inputs, outputs, and corresponding source lines for each component.
*   **Robust Fallback & Safety Heuristics:** Built-in Regex fallback parser ensures the canvas still renders functional nodes even if AI endpoints are unreachable.

---

## 🛠️ Tech Stack

*   **Frontend UI:** React 18 (via UMD / Babel standalone for zero-build-step deployment).
*   **Styling & Animations:** Tailwind CSS with custom glassmorphism and smooth SVG transitions.
*   **AI Integration:** Native Fetch API interfacing with Ollama (`http://localhost:11434`) and Google Gemini REST API (`generativelanguage.googleapis.com`).

---

## 🚀 Quick Start & Installation

Because this project is packaged as a single standalone HTML file with embedded React and Tailwind, you don't need Node.js, Webpack, or Vite to run it.

1. Clone or download the repository:
   ```bash
   git clone https://github.com/your-username/ai-code-architect.git
   cd ai-code-architect
   ```
2. Open `index.html` directly in any modern browser, or serve it locally using a simple HTTP server (recommended for local Ollama CORS support):
   ```bash
   python3 -m http.server 8080
   ```
3. Navigate to `http://localhost:8080` in your browser.

---

## ⚙️ Configuration Guides

### 1. Local Mode Setup (Ollama)
To run AI analysis completely offline and privately:
1. Install [Ollama](https://ollama.com).
2. Download a coding model:
   ```bash
   ollama pull qwen2.5-coder:7b
   ```
3. Configure CORS headers so the web app can communicate with Ollama (crucial for Linux/systemd):
   ```bash
   sudo systemctl edit ollama
   ```
   Add the following lines under `[Service]`:
   ```ini
   [Service]
   Environment="OLLAMA_ORIGINS=*"
   ```
4. Restart the service:
   ```bash
   sudo systemctl restart ollama
   ```

### 2. Cloud Mode Setup (Gemini API)
1. Obtain a free API key from [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Open the **Settings** panel (`⚙️` icon) in the top right of the application.
3. Switch to **Cloud (Gemini)** tab, enter your API Key, and select your preferred model (e.g., `gemini-1.5-flash`).

---

## 🎮 Usage Guide

1. **Load Code:** Paste your code into the workspace editor or click **Subir** to upload single or multiple source files (`.cpp`, `.py`, `.js`, etc.).
2. **Select AI Mode:** Choose between *Local Mode (Ollama)* or *Cloud Mode (Gemini)* via the header toggle.
3. **Interpret:** Click **Interpretar Proyecto**. The system will scan your codebase, classify components semantically, and build the architectural node map.
4. **Explore & Simulate:**
   * Click any node on the canvas to inspect its role, inputs, outputs, and corresponding source lines.
   * Use the bottom floating playback controls (`▶`, `⏸`, `⏭`) to simulate the logical execution flow step-by-step.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an issue for feature requests and bug reports.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git origin push feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
