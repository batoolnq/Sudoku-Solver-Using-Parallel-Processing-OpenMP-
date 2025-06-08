# 🧩 Sudoku Solver Using Parallel Processing (OpenMP)
A Parallel Computing Course Project

## 📌 Overview
This project explores the use of **parallel programming techniques** to optimize the performance of a Sudoku-solving algorithm. Implemented using **OpenMP**, the solver splits tasks like puzzle validation and grid generation across multiple threads, aiming to reduce execution time and improve scalability. Despite the theoretical benefits of parallelism, our findings highlight the challenges of thread synchronization and race conditions in recursive and stateful computations.

## 🧠 Motivation
Solving Sudoku puzzles computationally is time-consuming due to the recursive and combinatorial nature of the problem. Traditional sequential solvers operate on a single thread, making them inefficient for larger or more complex puzzles. This project was initiated to:

- Accelerate Sudoku solving by parallelizing independent tasks
- Study the effects of race conditions and synchronization overhead
- Compare parallel performance to traditional sequential methods

## 🔍 Key Features
- ✅ Sequential and parallel implementations with performance benchmarking
- 🧵 OpenMP-based parallelization of Sudoku grid filling and validation
- ⚠️ Race condition detection and mitigation using:
  - `#pragma omp critical`
  - `atomic` (limited applicability)
  - `reduction` (for benchmarking, not effective for this case)
- 📊 Comparative analysis over multiple core configurations (1, 2, 4, 8)

## 🛠️ Technical Details
- Language: C++
- Parallel Framework: OpenMP
- Functions Parallelized:
  - `fillDiagonal()` and `isSafe()` inside `solveSudoku()`
- Grid size: Standard 9x9
- Race condition variables:
  - `grid` (shared grid)
  - `isEmpty` (shared flag across threads)

## 📈 Performance Summary

| Method        | Avg. Execution Time |
|---------------|---------------------|
| Sequential    | 0.000146 sec        |
| Parallel (with race conditions) | 0.00363 sec       |
| Parallel (critical sections)    | ~1.7 sec          |

### 🧪 Cores Benchmark

| Cores | Time (s)     | Speedup | Efficiency |
|-------|--------------|---------|------------|
| 1     | 0.00090      | 1.00x   | 100%       |
| 2     | 0.00058      | 1.55x   | 77.5%      |
| 4     | 0.00029      | 3.1x    | 77.5%      |
| 8     | 0.00023      | 3.81x   | 47.6%      |

## 📚 Project Stages
1. **Stage 1** – Proposal & AWS Budget Planning  
2. **Stage 2** – Code Implementation & Race Condition Identification  
3. **Stage 3** – Parallelization using OpenMP  
4. **Final** – Evaluation, Optimization, and Report Writing

## 📊 Insights & Challenges
- **Best performance** came from the sequential version due to lack of synchronization overhead.
- **Critical sections** fixed correctness issues but increased execution time significantly.
- **Reduction & atomic** directives were often unsuitable due to non-aggregative logic.
- Demonstrated **diminishing returns** with more than 4 cores due to synchronization overhead.

## 📷 Screenshots
> *Feel free to upload and link to any diagrams or sample outputs here using the `/images` folder.*

## 🚀 Future Work
- Apply GPU acceleration using CUDA or OpenCL
- Explore task-based parallelism or distributed approaches (e.g., MPI)
- Extend to real-time interactive Sudoku game with UI
- Implement hybrid solvers using constraint propagation + parallelism

## 👩‍💻 Team Contributors
- Batool Alqatari (Team Leader)  
- Amnah Albrahim  
- Lama AlHujaili  
- Ghadeer Alsarrar  
- Maryam Alshakhs  

Supervised by: **Dr. Rabab Alkhalifa**

## 📄 Report & Paper
For full experimental results and literature review, read our paper here:  
[📄 Final Report PDF](./FinalParallel-Group2-Team6.pdf)

---
