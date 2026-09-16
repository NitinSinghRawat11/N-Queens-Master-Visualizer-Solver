# N-Queens Interactive Visualizer: Guide & Documentation

This guide covers how the application works under the hood and how you can run and interact with it.

---

## Part 1: How to Run the Application

Because this application is built as a **Single-File Web App** (combining HTML, CSS, and JavaScript in one file), running it is extremely simple and requires no backend server installation or complex node environment.

### Method 1: Local File (Easiest)
1. Save the code into a file named index.html on your computer.
2. Double-click the file to open it in any modern web browser (Google Chrome, Mozilla Firefox, Microsoft Edge, or Safari).

### Method 2: Local Development Server (Recommended for Live Reloading)
If you use a code editor like Visual Studio Code:
1. Open the file in VS Code.
2. Install the **Live Server** extension.
3. Right-click anywhere in the editor and choose **"Open with Live Server"**.

---

## Part 2: How It Works (Step-by-Step Architecture)

The application combines a backtracking solver with a dynamic state-machine simulation engine and a modern responsive user interface.

### 1. The Backtracking Algorithm Engine
The core mathematical engine uses recursive backtracking with optimized diagonal tracking. Instead of checking every single combination ($N^N$), it places queens row by row and prunes invalid branches instantly:
* **Columns Set (`cols`):** Tracks which vertical columns already have a queen.
* **Positive Diagonal (`diag1` calculated as `row - col`):** Prevents diagonal conflicts sloping downward-right.
* **Negative Diagonal (`diag2` calculated as `row + col`):** Prevents diagonal conflicts sloping downward-left.

```javascript
function backtrack(row) {
    if (row === boardSize) {
        // Solution found! Save the state.
        return;
    }
    for (let col = 0; col < boardSize; col++) {
        if (cols.has(col) || diag1.has(row - col) || diag2.has(row + col)) continue;
        // Place and recurse...
    }
}
```

### 2. Simulation Step Recorder
Unlike a standard solver that outputs answers instantly, this application's engine records **every single decision point** into a chronological array of steps (`try`, `conflict`, `place`, and `remove`). 
* This allows users to press **"Run Simulation"**, **"Pause"**, or **"Step Forward"** to witness the computer exploring and backtracking in real-time.

### 3. Dynamic DOM Renderer & Styling
* **Tailwind CSS:** Provides the sleek dark-mode aesthetic, grid layouts, and glassmorphism styling.
* **CSS Grid (`board-grid`):** Adapts dynamically to any board size from $N = 4$ up to $N = 10$, recalculating cell dimensions and font sizes instantly.
* **CSS Keyframes Animation (`animate-queen`):** Gives queens a pop-in spring effect whenever they are placed on the interactive board.

---

## Part 3: Features Overview

1. **Solver & Visualizer Tab:** Watch live backtracking simulation with adjustable speeds (Fast, Normal, Turbo, Instant) and real-time operation counters.
2. **All Solutions Gallery Tab:** Explore every distinct valid arrangement for board sizes $N = 4$ through $N = 9$ laid out in clean grid cards.
3. **Interactive Controls:** Easily change $N$ on the fly using the slider to see how the complexity and solution count scale exponentially.