# resource-allocation-text-semantic-S-SE

This is the source code of the paper "Resource allocation for text semantic communications".

L. Yan, Z. Qin, R. Zhang, Y. Li and G. Y. Li, "Resource Allocation for Text Semantic Communications," in IEEE Wireless Communications Letters, doi: 10.1109/LWC.2022.3170849.

# Hungarian Algorithm and Semantic-aware Resource Allocation Simulation

This repository provides:
- An implementation of the **Hungarian Algorithm** for solving the Minimum Cost Assignment Problem.
- A simulation framework for evaluating **semantic-aware channel assignment** in wireless networks using precomputed semantic utility tables.

---

## 📦 Requirements

Install the required Python packages:

```bash
pip install numpy matplotlib tqdm
```

---

## 📌 Hungarian Algorithm

### Description

The Hungarian algorithm solves the minimum cost matching (assignment) problem. Given a cost matrix `Perf`, it finds the optimal binary matching matrix `Matching` that minimizes the total cost of matched pairs.

### Function

```python
matching, cost = Hungarian(Perf)
```

### Arguments

- `Perf (numpy.ndarray)`  
  A 2D matrix of shape `(M, N)` representing the cost (or performance) of assigning row `i` to column `j`.  
  - Use `np.inf` for disallowed assignments.
  - For **maximum performance matching**, use `-Perf` before calling the function.

### Returns

- `Matching (numpy.ndarray)`  
  A binary matrix (0 or 1) of shape `(M, N)`, where `Matching[i, j] = 1` means task `i` is assigned to resource `j`.

- `Cost (float)`  
  The total cost of the assignment (sum of matched `Perf[i, j]` values).  
  For maximization problems, return `-Cost` after inputting `-Perf`.

### Example

```python
import numpy as np
from my_hungarian import Hungarian

Perf = np.array([[4, 1, 3],
                 [2, 0, 5],
                 [3, 2, 2]], dtype=float)

matching, cost = Hungarian(Perf)

print("Matching:\n", matching)
print("Cost:", cost)
```

**Output:**

```
Matching:
[[0 1 0]
 [1 0 0]
 [0 0 1]]
Cost: 5.0
```

---

## 📊 Simulation: Semantic-aware Resource Allocation

### Overview

This simulation evaluates spectral efficiency (S-SE) under two scenarios:

1. **Ideal System**: Uses Shannon-based throughput and Hungarian matching.
2. **Proposed System**: Uses precomputed semantic utility (`sem_table`) and Hungarian matching.

### Key Features

- Rayleigh fading and large-scale path loss based on 3GPP LTE macro-cell model
- Hungarian algorithm-based channel assignment
- Symbol-based semantic efficiency selection using lookup table
- Comparison plots of S-SE for ideal vs. proposed schemes


### Notes

- Make sure your semantic utility table is located at:
  ```
  /content/drive/MyDrive/sem_table.csv
  ```
  and formatted as a tab-delimited `.csv`.

- You can modify the following simulation parameters:
  - `n_devices`: number of users
  - `channel`: number of channels (default: 9)
  - `t_factor`: bits per word
  - `p_values`: transmit power(s) in dB
  - `episode`: number of iteration 
  - 
---


---

## 🔧 Future Extensions

- Add support for dynamic channel availability
- Integrate reinforcement learning-based feature selection
- Real-time semantic feature compression

---
### 📚 References

- Hungarian Algorithm Python Implementation by [UserName](https://github.com/username/repo-name)
  - Adapted or referenced in parts of `hungarian algorithm` for matching logic.
  - sem_table can be referenced at the following link: https://github.com/YL12345/semantic-resource-allocation-S-SE-
  - This is the source code of the paper "Resource allocation for text semantic communications".
    L. Yan, Z. Qin, R. Zhang, Y. Li and G. Y. Li, "Resource Allocation for Text Semantic Communications," in IEEE Wireless Communications Letters, doi: 10.1109/LWC.2022.3170849.


---

## 📄 License

This project is available for academic and research use. For commercial applications, please contact the author.

---


