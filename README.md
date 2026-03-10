# Optimization of Café Operations ☕️

An operations research and analytics project aimed at optimizing seating arrangements and operational policies for 'Cafe Ann' using queueing theory, simulation, and linear programming.

## 📌 Overview
This project tackles real-world congestion and profitability issues in a 24-hour university café. By analyzing actual customer transaction and arrival data, the project is divided into two main tasks:
1. **Seating Optimization:** Determining the most profitable ratio of 1-person to 2-person seating.
2. **Policy Optimization:** Deriving the best operational actions (e.g., giving out free cookies or implementing time limits) based on varying levels of café congestion.

## 🛠 Methodology & Modeling

### Task 1: Seating Capacity Optimization
* [cite_start]**Queueing Model:** Modeled the café as an $M/M/K/K$ queueing system (Erlang Loss system) where capacity equals the number of servers[cite: 91, 179].
* **Simulation:** Evaluated different combinations of seating arrangements using Python.
* [cite_start]**Outcome:** Identified the optimal configuration (20 single-person seats, 7 two-person seats), which mathematically projected an increase in monthly expected revenue compared to the existing layout[cite: 274, 277].

### Task 2: State-Based Policy Optimization
* [cite_start]**State Definition:** Categorized the café's environment into 5 distinct states (State 0 to 4) based on the congestion level ($\rho$)[cite: 284, 286, 287].
* **Decision Variables:** Evaluated three specific actions: 
    1. Do Nothing 
    2. Free Cookie Service (for customer retention in low states) 
    3. [cite_start]3-Hour Time Limit (to reduce balking in high states)[cite: 291].
* [cite_start]**Mathematical Approach:** * Applied a truncated exponential distribution to accurately model the updated service rate ($\mu$) when the 3-hour limit is active[cite: 300, 301, 690].
    * [cite_start]Formulated a Linear Programming (LP) model to maximize the Net Profit ($NP_{ik}$) across all states[cite: 528, 558].
* **Outcome:** Solved the LP to find the optimal policy sequence (1, 2, 1, 1, 3). [cite_start]The optimal strategy proved to be "Do Nothing" for states 0, 2, and 3; offering a "Cookie Service" during state 1; and enforcing a "3-Hour Limit" during the highly congested state 4[cite: 656, 657, 658, 659].

## 💻 Tech Stack & Tools
* [cite_start]**Languages:** Python [cite: 206]
* **Operations Research:** Queueing Theory ($M/M/K/K$), Truncated Exponential Distributions, Markov Decision Process Concepts
* [cite_start]**Optimization:** Linear Programming, Excel Solver [cite: 558, 573]

## 💡 Key Takeaways
This project bridges the gap between theoretical operations research and practical business application. It demonstrates how rigorous mathematical modeling—handling shifting service rates and capacity constraints—can directly translate into actionable, data-driven business decisions that maximize revenue.
