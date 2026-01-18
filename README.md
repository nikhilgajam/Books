<div align="center">

# 📖 Nikhil's Library

**A premium, web-based PDF reader and digital bookshelf built for the modern user.**

[![Tech Stack](https://img.shields.io/badge/Built%20With-PDF.js%20%7C%20Vanilla%20JS-yellow)](https://mozilla.github.io/pdf.js/)

<h3>
<a href="https://nikhilgajam.github.io/Books/">🚀 Launch the App</a>
</h3>

App URL: https://nikhilgajam.github.io/Books

</div>

---

## ⚡ Overview

Nikhil's Library is a serverless Single Page Application (SPA) that transforms a GitHub repository into a personal streaming service for books. Unlike standard GitHub file viewing, this application provides a **custom rendering engine** that offers a distraction-free reading experience similar to commercial e-readers.

## ✨ Application Features

### 🧠 Smart Library Management
* **Auto-Sync:** Dynamically fetches the file list from the repository using the GitHub REST API.
* **Progress Tracking:** Uses `LocalStorage` to automatically save your page number. Pick up exactly where you left off, even after closing the browser.
* **Smart Sorting:** Automatically bubbles your "Currently Reading" books to the top of the grid.
* **Instant Search:** Real-time filtering to find specific notes or books instantly.

### 🎨 Premium UI/UX
* **Glassmorphism Design:** A modern aesthetic featuring deep blacks (`#0a0a0a`), frosted glass effects, and silver accents.
* **Responsive Layout:** Fully optimized for desktop, tablet, and mobile touch interactions.
* **Theme Engine:** Includes a dedicated "Night Mode" for the PDF renderer (inverts colors intelligently for eye comfort) and a standard day mode.

### 🛠 Technical Capabilities
* **Custom PDF Engine:** Built on top of **PDF.js (v3.11)** for high-fidelity rendering directly in the browser canvas.
* **Offline Fallback:** Includes a "Local Folder" mode. If the GitHub API rate limit is reached, users can manually load a local folder of PDFs to use the reader interface. And also can read from your Local System with the load local PDF button.
* **Keyboard Shortcuts:**
    * `Left/Right Arrows`: Navigate pages.
    * `Enter`: Jump to a specific page number.

---

## 🏗️ Architecture

The application is built with a minimalist, dependency-free approach (Vanilla JS + CSS Variables) to ensure high performance.

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Core** | HTML5 / JS (ES6+) | No frameworks (React/Vue) used; pure DOM manipulation for maximum speed. |
| **Rendering** | [PDF.js](https://mozilla.github.io/pdf.js/) | Mozilla's vector-based PDF rendering engine. |
| **Styling** | CSS3 Variables | Premium monochrome theme with `backdrop-filter` for glass effects. |
| **Icons** | [RemixIcon](https://remixicon.com/) | Lightweight, neutral-style vector icons. |
| **Data** | GitHub API | Fetches tree structure recursively to build the library grid. |

---

## 🚀 How to Run Locally

Since this is a static web application, you do not need a backend server (Node/Python) to run it.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/nikhilgajam/Books.git](https://github.com/nikhilgajam/Books.git)
    ```
2.  **Open the App:**
    Simply double-click `index.html` to open it in your browser.
    * *Note: Due to CORS policies, some features (like GitHub API fetching) might behave differently when opening as a file (`file://`). It is recommended to use a simple local server:*
    ```bash
    # If you have Python installed:
    python3 -m http.server (or) python -m http.server
    # Then visit http://localhost:8000
    ```

---

<div align="center">
  <p><i>"The more we know, the more we grow."</i></p>
</div>
