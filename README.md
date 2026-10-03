# Unified GitHub Butler OS 🪐

> A single-file, client-side Developer Cockpit and Agentic Workspace powered by Google Gemini, Web Crypto AES-GCM security, and a bulletproof React sandbox.

---

## 📖 Overview

**Unified GitHub Butler OS** transforms the browser into an agentic developer operating system. It merges GitHub repository navigation, Git source control, a synchronized dual-layer code editor, real-time iframe transpilation, and specialized Gemini AI engineering tools into a single cohesive interface.

Whether running as an embedded standalone React application or connected to a local daemon bridge, Butler OS provides a cockpit experience designed for fast prototyping, code auditing, refactoring, and conversational pair programming.

---

## ⚡ Key Highlights & Architecture

### 1. 🛡️ Enterprise Security & Keyring
* **Web Crypto API AES-GCM 256-bit Encryption**: Personal Access Tokens (PATs) are encrypted locally using PBKDF2 salt derivation before reaching browser storage.
* **Localhost Daemon Bridge Support**: Route API calls through an external local daemon (`http://localhost:8080/api`) so tokens never reside in browser memory.
* **Pre-Commit Secret Scanner**: Halts commits upon detecting unencrypted credentials, AWS keys, GitHub PATs, JWTs, private keys, or database connection strings across staged files.

### 2. 🤖 Centralized AI Transport & Job System
* **Unified Transport Engine (`aiRequest`)**: Centralized gateway managing `gemini-3-flash-preview`, `gemini-3.1-flash-image`, and `gemini-2.5-flash-preview-tts` with automated exponential backoff and rate-limit mitigation.
* **AbortController Cancellation**: Every AI request binds to an active job controller, allowing you to stop long-running operations immediately via the **[STOP]** drawer button.
* **Floating Job Monitor**: Real-time background task drawer tracking operational status, progress telemetry, and timestamps.

### 3. 🛠️ Interactive Cockpit Modals Suite
* **Structured Security & Health Audit**: Evaluates OWASP vulnerabilities, memory leaks, and performance traps; renders a 0–100 health gauge, severity badges (`critical`, `warning`, `info`), and surgical one-click patch replacement.
* **Search-Grounded Dependency & CVE Radar**: Scans dependencies against live Google Search intelligence, displaying verified external CVE advisory badge links.
* **Automated PR & Semantic Release Drafter**: Generates structured PR pull requests, risk assessments, interactive verification checklists, and one-click Markdown clipboard export.
* **Solo Audio Walkthrough (TTS)**: Synthesizes a 90-second developer briefing using `gemini-2.5-flash-preview-tts` with voice selection (`Kore`, `Puck`, `Zephyr`, `Fenrir`) and an HTML5 audio scrubber.
* **Dual-Architect Debate Podcast**: Stages a technical debate between *Fenrir* (Pragmatic Tech Lead) and *Aoede* (Clean Code Purist) with multi-speaker audio playback and synchronized transcript feeds.
* **Smart Diff Refactoring Inspector**: Displays side-by-side red/green code hunk comparisons with selective "Apply Patch" or bulk "Apply All" merging.
* **Cross-Repository Codebase Intelligence ("Ask Repo")**: Multi-file architectural reasoning across the repository file tree.
* **Gemini Live Voice Pair Programmer**: Real-time microphone streaming, 24-bar frequency waveform HUD, and live transcription log with "Push Code State".
* **Multimodal Screenshot to Code**: Converts UI wireframes, sketches, and screenshots directly into responsive Tailwind/React components.
* **Asset Studio**: Generates OpenGraph social banners (16:9), logos (1:1), and documentation graphics using `gemini-3.1-flash-image`.
* **Autonomous Autopilot Loop**: Automatically diagnoses, designs a multi-step execution plan, generates surgical patches, and produces companion test suites.

### 4. 💻 Pro Editor & Bulletproof Preview Sandbox
* **Synchronized Dual-Layer Editor**: Fast syntax highlighting, line numbers, indentation handling, and in-editor search (`Ctrl+F` / `⌘F`).
* **Bulletproof Recursive Proxy (`createDeepProxy`)**: An intelligent JavaScript Proxy inside the preview iframe that absorbs missing imports, SCSS modules, images, and functions without crashing the sandbox.
* **Command Palette (`Ctrl+K` / `⌘K`)**: Instant keyboard-driven access to commands, cockpit modals, and workspace files.
* **Git Staging & Version Control**: Staging, unstaging, snapshot checkpoints, and simulated terminal execution (`npm test`, `git status`, `scan secrets`).

### 5. 🎨 7-Theme Visual Environment Engine
Switch the entire application workspace instantly between 7 themes:
1. **Cyberpunk 2077** (Electric yellow `#fcee0a`, neon cyan, dark HUD)
2. **Neon Dark** (Carbon black, emerald neon `#00ff88`, cyan glow)
3. **Synthwave Purple** (Midnight purple, neon magenta, violet glow)
4. **Pink Magenta** (Velvet noir, hot pink, vivid fuchsia)
5. **Amber Gold CRT** (Retro amber CRT warmth, phosphor glow)
6. **Clean Light Studio** (Crisp daylight slate, indigo focus)
7. **Obsidian Dark** (Classic GitHub dark / carbon palette)
* *Plus an Easter-egg **Matrix Mode** phosphor override.*

---

## 📂 Project Structure

```
.
├── UnifiedGitHubButler.jsx          # Self-contained Master React Application
├── master_restoration_plan.md       # Architecture & Restoration Blueprint
├── lost_features_audit.md           # Forensic Feature Comparison Report
└── README.md                        # Documentation & Developer Guide
```

---

## 🚀 Getting Started

### Prerequisites
* Node.js 18+ (if bundling in a local Vite/Next/CRA setup) or a web browser supporting ES Modules.
* A GitHub Personal Access Token (`repo` and `read:user` scopes recommended).
* A Google Gemini API Key (handled automatically in Canvas environments or passed to the transport layer).

### Dependencies
Ensure the following packages are available in your environment:
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.292.0"
  }
}
```

### Installation & Execution

#### Option A: Inside an existing React / Vite project
1. Copy `UnifiedGitHubButler.jsx` into your source directory (e.g., `src/App.jsx`).
2. Ensure Tailwind CSS is included in your index HTML or CSS entry point:
   ```html
   <script src="https://cdn.tailwindcss.com"></script>
   ```
3. Run your development server:
   ```bash
   npm run dev
   ```

#### Option B: Standalone Web Container
Mount `UnifiedGitHubButler.jsx` directly as the default export of your root component tree.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `⌘ + K` or `Ctrl + K` | Open Universal Command Palette |
| `⌘ + S` or `Ctrl + S` | Save file to in-memory workspace |
| `⌘ + F` or `Ctrl + F` | Toggle In-Editor Search Bar |
| `Tab` | Indent code by 2 spaces |
| `Esc` | Close Active Modal / Command Palette |

---

## 🔒 Security Best Practices

1. **Client Storage**: Tokens are encrypted using AES-GCM prior to `localStorage` writes. Do not export raw browser storage to untrusted environments.
2. **Localhost Daemon**: For production or sensitive private enterprise repositories, toggle the **Local Daemon Proxy** in the Keyring view to avoid exposing PATs in the browser context.
3. **Secret Gatekeeper**: Always review pre-commit warnings; the pre-commit scanner rejects commits containing matched regex patterns for API credentials.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for details.
