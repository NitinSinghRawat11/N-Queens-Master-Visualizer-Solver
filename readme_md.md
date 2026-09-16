# 👑 N-Queens Master Visualizer & Solver

An interactive, feature-rich web application built to visualize the classic **N-Queens Puzzle** using backtracking algorithms. Designed with a sleek Amber & Obsidian theme, this self-contained single-file application lets you watch the algorithm explore, prune branches, and place royal crowns in real-time.

![N-Queens Preview](https://img.shields.io/badge/Status-Active-success) ![License](https://img.shields.io/badge/License-MIT-blue.svg) ![Tech Stack](https://img.shields.io/badge/Stack-HTML5%20%7C%20Tailwind%20CSS%20%7C%20JavaScript-orange)

---

## ✨ Key Features

1. **Live Backtracking Visualizer:**
   * Watch the recursive algorithm operate step-by-step.
   * Adjustable simulation speeds: *Relaxed*, *Normal*, *Turbo*, and *Instantaneous*.
   * Live operational counters tracking step counts, active row/column inspections, and total solutions found.
2. **Distinct Solutions Gallery:**
   * Instantly inspect every single valid arrangement for board dimensions ranging from $N = 4$ up to $N = 9$.
   * Clean grid layouts with royal crown graphics and responsive design.
3. **Step-by-Step Tutorial & Documentation:**
   * In-built explanation of how $O(1)$ diagonal and column branch pruning works under the hood.
4. **Zero-Config Single-File Architecture:**
   * Combines HTML, Tailwind CSS, and JavaScript into one seamless file for instant execution anywhere.

---

## 🚀 How to Run the Application

Because this project is built as a **Single-File Web App**, running it requires no complex node environments or backend servers.

### Method 1: Local File (Easiest)
1. Download or copy the complete code into a file named `index.html`.
2. Double-click the file to open it instantly in any modern web browser (Google Chrome, Mozilla Firefox, Microsoft Edge, or Safari).

### Method 2: Local Development Server (Recommended)
If you use Visual Studio Code:
1. Open the project folder in VS Code.
2. Install the **Live Server** extension.
3. Right-click anywhere in `index.html` and choose **"Open with Live Server"**.

---

## 🧠 How the Backtracking Algorithm Works

The core engine uses recursive backtracking with optimized diagonal tracking to avoid checking every single combination ($N^N$):
* **Columns Set (`cols`):** Tracks vertical columns containing a queen.
* **Positive Diagonal (`diag1` calculated as `row - col`):** Prevents downward-right diagonal conflicts.
* **Negative Diagonal (`diag2` calculated as `row + col`):** Prevents downward-left diagonal conflicts.

```javascript
function backtrack(row) {
    if (row === boardSize) {
        // Solution discovered! Save state.
        return;
    }
    for (let col = 0; col < boardSize; col++) {
        if (cols.has(col) || diag1.has(row - col) || diag2.has(row + col)) continue;
        // Place and recurse...
    }
}
```

---

## 📂 Project Structure

```text
├── index.html        # Complete self-contained web app (UI, CSS, and JS engine)
├── guide.md          # In-depth technical architecture and documentation
└── README.md         # Project overview and instructions
```

---

## 🛡️ License

This project is open-source and available under the [MIT License](LICENSE).