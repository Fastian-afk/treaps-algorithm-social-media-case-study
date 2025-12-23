# Social Media Feed Manager: Treaps vs. BST Case Study

## 📌 Overview
This project addresses a critical data structure challenge in modern social media feeds: maintaining content that is simultaneously ordered by **Recency (Timestamp)** and **Popularity (Score)**.

We implemented and compared a **Treap (Randomized Search Tree)** against a standard **Binary Search Tree (BST)** using real-world Reddit data. The study demonstrates how Treaps solve the "sorted input" degeneration problem that causes standard BSTs to fail when handling chronologically ordered data.

## 🚀 Key Features
* **Dual-Ordering:** Maintains chronological order (BST property on Timestamps) and popularity order (Heap property on Scores) simultaneously.
* **Stream Processing:** Handles massive datasets (180GB+) using efficient compressed streaming (`zstandard`) with O(1) memory overhead.
* **Performance:** Achieves **O(1)** access to the most popular post (Root node).
* **Advanced Operations:** Includes custom implementation of `split`, `merge`, and `union` operations for Treaps.
* **Visualization:** Includes dynamic tree visualization using Graphviz to verify structural integrity.

## 🧪 The Challenge: BST Failure
When chronologically sorted data (like a social media feed) is inserted into a standard BST, the tree degenerates into a **Linked List**. This results in O(N) complexity for all operations.

**Experimental Results (50,000 Posts):**
* **BST Height:** ~44,688 (Degenerate / Linked List)
* **Treap Height:** ~38 (Balanced / Logarithmic)

## 📊 Results & Analysis
The experiment simulated a feed of **50,000 posts** followed by mixed operations (likes, deletes, searches).

### 1. Most Popular Post Access Time
The Treap allows immediate access to the highest-scoring post because the max-heap property keeps it at the root.
* **Treap:** ~0.3 microseconds (O(1))
* **BST:** ~9,000 microseconds (O(N)) -> **~24,000x Slower**

### 2. Structural Integrity
The Treap utilizes random priorities (scores) and rotations (`_reheapify_up`) to decouple the tree structure from the insertion order. This ensures the tree remains balanced even when the input data is perfectly sorted by time.

## 🛠️ Tech Stack
* **Language:** Python 3.10+
* **Libraries:** `pandas`, `zstandard`, `seaborn`, `matplotlib`, `graphviz`
* **Dataset:** Pushshift Reddit Dataset (Musical Instruments / Electronics subset)

## ⚙️ How to Run
1. **Clone the repository:**

   git clone [https://github.com/YOUR-USERNAME/social-media-feed-treap-vs-bst.git](https://github.com/YOUR-USERNAME/social-media-feed-treap-vs-bst.git)


2. **Install dependencies:**
pip install pandas zstandard matplotlib seaborn graphviz


3. **Get the Dataset:**
* Download a slice of the Pushshift Reddit Dataset (e.g., `RC_2019-04.zst`).
* Place the `.zst` file in the `src/` or `input/` directory.
* Update the `DATA_FILE_PATH` variable in the notebook if necessary.


4. **Run the Experiment:**
* Open `src/main_experiment.ipynb` in Jupyter or VS Code.
* Run all cells to reproduce the ablation study and generate visualizations.



## 📄 Documentation

For a detailed theoretical analysis, complexity proofs, and discussion of the results, please refer to the **Project Report (PDF)** located in the `docs/` folder of this repository.

## 👨‍💻 Author

* **Imaad Fazal** - *Design and Analysis of Algoriths*
