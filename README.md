# 🤖 BaiTap_AI — Bài Tập Trí Tuệ Nhân Tạo

Tập hợp các bài tập thực hành môn **Trí Tuệ Nhân Tạo**, bao gồm mô phỏng tác nhân, giải thuật tìm kiếm, bài toán ràng buộc và trò chơi có đối kháng — triển khai bằng **Python** với giao diện đồ họa **Tkinter**.

---

## 📁 Cấu Trúc Thư Mục

```
BaiTap_AI/
│
├── 📂 images   # Lưu trữ các gif demo
│
├── 📂 simple-reflex-agent/     # Tác nhân phản xạ đơn giản
│   ├── Cleaning_Robot_Simple_Reflex_Agent.ipynb   # Robot hút bụi
│   └── Eight_Puzzle_Simple_Reflex_Agent.ipynb     # Bài toán 8 puzzle
│
├── 📂 model-based-reflex-agent/    # Tác nhân phản xạ có mô hình
│   ├── Cleaning_Robot_Model_Based_Reflex_Agent.ipynb  # Robot hút bụi
│   ├── Eight_Puzzle_Model_Based_Reflex_Agent.ipynb    # Bài toán 8 puzzle
│   └── Eight_Puzzle_Model_Based_Reflex_Agent_BFS.ipynb # 8 puzzle + BFS
│
├── Cleaning_Robot_Visualization.ipynb     # Robot hút bụi + 4 nhóm thuật toán tìm kiếm
├── Coloring_Map.ipynb      # Bài toán tô màu bản đồ TP.HCM (CSP)
├── Tic_Tac_Toe.ipynb       # Trò chơi Tic-Tac-Toe với AI đối kháng
└── README.md
```

---

## 📌 Chi Tiết Từng Bài

---

### 1. 🤖 Tác Nhân Phản Xạ Đơn Giản (Simple Reflex Agent)

**Thư mục:** `simple-reflex-agent/`

Tác nhân **không có bộ nhớ nội bộ**, chỉ dựa vào nhận thức hiện tại để hành động ngay lập tức.

#### Robot Hút Bụi
**File:** `Cleaning_Robot_Simple_Reflex_Agent.ipynb`

- Lưới 3×3, robot di chuyển ngẫu nhiên trong danh sách hướng hợp lệ
- Không lưu lịch sử, không có mục tiêu dài hạn

#### Bài Toán 8 puzzle
**File:** `Eight_Puzzle_Simple_Reflex_Agent.ipynb`

- Trạng thái đích: `[[1,2,3],[4,5,6],[7,8,0]]`
- Robot ngẫu nhiên trượt ô trống, chạy tối đa 50 bước
- Không đảm bảo tìm được lời giải

---

### 2. 🧠 Tác Nhân Phản Xạ Có Mô Hình (Model-Based Reflex Agent)

**Thư mục:** `model-based-reflex-agent/`

Tác nhân **lưu trạng thái nội bộ** (`model`) để tránh lặp lại hành động vừa thực hiện (cơ chế `forbidden`), cải thiện hiệu quả so với Simple Reflex Agent.

#### Robot Hút Bụi
**File:** `Cleaning_Robot_Model_Based_Reflex_Agent.ipynb`

- Cùng cấu hình lưới 3×3 với tác nhân đơn giản
- Có thêm `model["forbidden"]` ngăn robot đi ngược hướng vừa di chuyển

#### Bài Toán 8 puzzle (Phản xạ có mô hình)
**File:** `Eight_Puzzle_Model_Based_Reflex_Agent.ipynb`

- Tương tự Simple, nhưng tránh đi ngược bước trước đó
- Chạy tối đa 100 bước

#### Bài Toán 8 puzzle (Có mô hình + BFS)
**File:** `Eight_Puzzle_Model_Based_Reflex_Agent_BFS.ipynb`

- Dùng **BFS chuẩn** để tìm đường đi tối ưu từ trạng thái hiện tại đến đích
- Xáo trộn bảng bằng 20 bước hợp lệ, đảm bảo luôn có lời giải

---

### 3. 🧹 Robot Hút Bụi — Visualization

**File:** `Cleaning_Robot_Visualization.ipynb`

Giao diện đồ họa Tkinter cho phép chạy và quan sát **toàn bộ các nhóm thuật toán tìm kiếm** trên lưới 3×3, 4x4 hoặc 5x5. Robot cần dọn sạch mọi ô bụi trong khi tránh chướng ngại vật.

| Mã ô | Ý nghĩa |
|------|---------|
| `0`  | Ô sạch |
| `1`  | Bụi |
| `2`  | Robot |
| `3`  | Chướng ngại vật |

#### 4 nhóm thuật toán được triển khai

**🔹 Tìm kiếm mù (Uninformed Search)**
- Breadth-first Search (BFS) — Tìm kiếm theo chiều rộng (2 biến thể)
- Depth-first Search (DFS) — Tìm kiếm theo chiều sâu (2 biến thể)
- Iterative Deepening Search (IDS) — Tìm kiếm sâu dần (2 biến thể)
- Uniform Cost Search (UCS) — Tìm kiếm chi phí đồng nhất

**🔹 Tìm kiếm có thông tin (Informed Search)**
- Greedy Search — Tham lam theo heuristic, sử dụng hàm h(n) = số bụi còn lại
- A\* Search — A sao (heuristic f(n) = Manhattan gần nhất + số bụi còn lại)
- IDA\* Search — Biến thể giới hạn ngưỡng của A\*

**🔹 Tìm kiếm cục bộ (Local Search)**
- Simple Hill Climbing
- Steepest-Ascent Hill Climbing
- Stochastic Hill Climbing
- Random-Restart Stochastic Hill Climbing
- Local Beam Search
- Simulated Annealing

**🔹 Tìm kiếm trong môi trường phức tạp**
- Sensorless BFS — Tìm kiếm không cảm biến (belief-state / mù hoàn toàn)
- Partial Observable BFS — Quan sát một phần
- AND-OR Graph Search — Môi trường có hành động không xác định


#### Demo thực thi chương trình

- BFS cách tiếp cận 1
> ![BFS1](images/BFS1.gif)

- BFS cách tiếp cận 2
> ![BFS2](images/BFS2.gif)

- DFS cách tiếp cận 1
> ![DFS1](images/DFS1.gif)

- DFS cách tiếp cận 2
> ![DFS2](images/DFS2.gif)

- IDS cách tiếp cận 1
> ![IDS1](images/IDS1.gif)

- IDS cách tiếp cận 2
> ![IDS2](images/IDS2.gif)

- UCS
> ![UCS](images/UCS.gif)

- Greedy Search
> ![GS](images/GS.gif)

- A\* Search
> ![Asao](images/Asao.gif)

- IDA\* Search
> ![IDAsao](images/IDAsao.gif)

- Simple Hill Climbing
> ![SimpleHC](images/SimpleHC.gif)

- Steepest-Ascent Hill Climbing
> ![SteepestHC](images/SteepestHC.gif)

- Stochastic Hill Climbing
> ![StocHC](images/StocHC.gif)

- Random-Restart Stochastic Hill Climbing
> ![RandomRestartHC](images/RandomRestartHC.gif)

- Local Beam Search
> ![LocalBeam](images/LocalBeam.gif)

- Simulated Annealing
> ![SimulatedAnnealing](images/SimulatedAnnealing.gif)

- Sensorless BFS
> ![Sensorless](images/Sensorless.gif)

- Partial Observable BFS
> ![PartialObs](images/PartialObs.gif)

- AND-OR Graph Search
> ![AndOr](images/AndOr.gif)

---

### 4. 🗺️ Tô Màu Bản Đồ TP.HCM (CSP)

**File:** `Coloring_Map.ipynb`

Giải bài toán **tô màu bản đồ** 24 quận/huyện TP.HCM (trước khi sáp nhập) sao cho không có hai vùng kề nhau cùng màu, sử dụng các giải thuật **CSP (Constraint Satisfaction Problem)**.

#### Thuật toán CSP

| Thuật toán | Mô tả |
|------------|-------|
| **Backtracking** | Tìm kiếm quay lui cơ bản |
| **Forward Checking** | Loại bỏ sớm các giá trị vi phạm |
| **AC3** | Lan truyền ràng buộc (Arc Consistency 3) |
| **Min-Conflicts** | Tìm kiếm cục bộ, giảm thiểu số xung đột |

- Giao diện Tkinter 1400×900, hiển thị bản đồ và log từng bước
- Trực quan hóa màu sắc thay đổi theo thời gian thực

#### Demo thực thi chương trình
- Backtracking
> ![Backtracking](images/Backtracking.gif)

- Forward Checking
> ![Forwardchecking](images/Forwardchecking.gif)

- AC-3
> ![AC3](images/AC3.gif)

- Min-Conflicts
> ![MinConflicts](images/MinConflicts.gif)

---

### 5. ❌⭕ Tic-Tac-Toe với AI Đối Kháng

**File:** `Tic_Tac_Toe.ipynb`

Trò chơi **Cờ Caro 3×3** — người chơi đấu với AI được trang bị các thuật toán đối kháng. Người chơi là `X`, AI là `O`.

#### Thuật toán AI

| Thuật toán | Mô tả |
|------------|-------|
| **Minimax** | Tìm kiếm toàn bộ cây trò chơi, AI chơi tối ưu |
| **Alpha-Beta Pruning** | Minimax tối ưu, cắt tỉa các nhánh thừa |
| **Expectimax** | Minimax cho môi trường ngẫu nhiên (nước đi có xác suất) |

- Giao diện Tkinter 600×450
- Hiển thị số nút đã đánh giá, thời gian tính toán của AI
- Có thể chọn thuật toán AI trước khi bắt đầu ván

#### Demo thực thi chương trình
- Minimax
> ![Minimax](images/Minimax.gif)

- Alpha-Beta Pruning
> ![AlphaBeta](images/AlphaBeta.gif)

- Expectimax
> ![Expectimax](images/Expectimax.gif)

---

## 🛠️ Công Nghệ Sử Dụng

| Thành phần | Công nghệ |
|------------|-----------|
| Ngôn ngữ | Python 3.x |
| Giao diện đồ họa | Tkinter (built-in) |
| Notebook | Jupyter Notebook / JupyterLab |
| Cấu trúc dữ liệu | `collections.deque`, `heapq` |

---

## ▶️ Hướng Dẫn Chạy

**Yêu cầu:** Python 3.8+ đã cài sẵn.

1. Clone repository:
```bash
git clone https://github.com/DoAnhTuan-24110369/BaiTap_AI.git
cd BaiTap_AI
```

2. Mở notebook bằng JupyterLab hoặc Jupyter Notebook:
```bash
jupyter notebook
```

3. Điều hướng đến file `.ipynb` muốn chạy, chọn **Kernel → Restart & Run All**.

> **Lưu ý:** Các notebook có giao diện Tkinter (`Cleaning_Robot_Visualization`, `coloring_map`, `tic_tac_toe`) sẽ mở cửa sổ riêng khi chạy — cần môi trường có hỗ trợ hiển thị (không chạy được trên server headless).

---

## 👨‍💻 Tác Giả

**Đỗ Anh Tuấn** — MSSV: 24110369  
Trường Đại học Công nghệ Kỹ thuật TP.HCM (HCMUTE)  
Môn học: Trí Tuệ Nhân Tạo