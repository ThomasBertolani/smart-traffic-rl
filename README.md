# Adaptive Traffic Signal Control using Reinforcement Learning

A comparative study applying **Tabular Reinforcement Learning** and **Deep Reinforcement Learning** to optimize traffic signal control in a non-stationary, stochastic environment. This project demonstrates that RL can outperform static heuristics by adapting to platoon dynamics in real-time.

---

## 🚦 The Problem
Traditional traffic signals rely on **Fixed Cycle** timers (stable but inefficient) or **Reactive Heuristics** (responsive but unstable). Real-world traffic arrives in coordinated platoons, and switching lights too frequently incurs a capacity penalty.

**The Goal:** Train a RL agent to minimize queue lengths while maintaining stability, effectively solving the trade-off between reactivity and throughput.

## 🧩 Custom Environment
I designed a custom Gymnasium environment to model realistic traffic physics:
* **Non-Stationary Inflow:** Traffic arrives in sine-wave gated platoons to simulate upstream signal coordination.
* **Startup Lost Time:** A capacity penalty is applied during phase switches to simulate driver reaction time.
* **Physical Constraints:** Inflow is capped by a safety headway of 1.2s.

## 🧠 Algorithms Implemented
* **Tabular SARSA($\lambda$):** An on-policy method using Eligibility Traces and State Discretization to bridge TD(0) and Monte Carlo returns.
* **Deep Q-Network (DQN):** An off-policy Deep RL method leveraging Experience Replay and Target Networks to handle continuous state spaces.

---

## 📈 View the Full Report

The complete scientific analysis, including hyperparameter sweeps, learning curves and performance benchmarking, is detailed in the project notebook.

### [📄 Click here to view the Report (Jupyter Notebook)](report.ipynb)

---

## 🛠️ Usage & Reproduction

If you are curious about the implementation details or want to test the agents with different seeds/parameters, you can clone the repository and run the experiments locally.

### 1. Clone the Repository
```bash
git clone https://github.com/ThomasBertolani/adaptive-traffic-control-rl.git
cd adaptive-traffic-rl
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the experiments
The entire pipeline is contained in the notebook `report.ipynb`. You can execute it to reproduce all plots and results.

## 📂 Project Structure
```text
.
├── algorithms/
│   ├── agent.py          # Abstract Base Class for agents
│   ├── dqn.py            # Deep Q-Network implementation
│   └── sarsa_lambda.py   # Tabular SARSA(λ) implementation
├── baselines/
│   └── baseline.py       # Static policies (Random, Greedy, Fixed Cycle)
├── envs/
│   ├── traffic_env.py    # Custom Gymnasium Environment (Physics Engine)
│   └── wrappers.py       # Observation wrappers
├── evaluation/
│   ├── callback.py       # Custom Callback for training logs
│   └── experiments.py    # functions to execute experiments and plots
├── report.ipynb          # Main scientific report and visualization
├── requirements.txt      # Python dependencies
└── README.md             # Project documentation
```

## 👤 Author
**Thomas Bertolani** *Artificial Intelligence Engineering student @ UniMoRe* [LinkedIn](https://www.linkedin.com/in/thomasbertolani/)