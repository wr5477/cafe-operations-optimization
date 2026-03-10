# Optimization of Café Operations ☕️

*This research is based on real-world operational and transaction data from 'Cafe Ann', located in Anam, Seoul, South Korea.*

An operations research and analytics project aimed at optimizing seating arrangements and operational policies for a 24-hour university café using queueing theory, simulation, and linear programming.

## 📌 Overview
This project tackles real-world congestion and profitability issues. By analyzing actual customer transaction and arrival data, the project is divided into two main tasks:
1. **Seating Optimization:** Determining the most profitable ratio of 1-person to 2-person seating.
2. **Policy Optimization:** Deriving the best operational actions (e.g., giving out free cookies or implementing time limits) based on varying levels of café congestion.

## 🛠 Methodology & Modeling

### Task 1: Seating Capacity Optimization
* **Queueing Model:** Modeled the café as an M/M/K/K queueing system (Erlang Loss system) where capacity equals the number of servers.
* **Simulation:** Evaluated different combinations of seating arrangements using Python.
* **Outcome:** Identified the optimal configuration (20 single-person seats, 7 two-person seats), which mathematically projected an increase in monthly expected revenue compared to the existing layout.

### Task 2: State-Based Policy Optimization
* **State Definition:** Categorized the café's environment into 5 distinct states (State 0 to 4) based on the congestion level (rho).
* **Decision Variables:** Evaluated three specific actions: 
    1. Do Nothing 
    2. Free Cookie Service (for customer retention in low states) 
    3. 3-Hour Time Limit (to reduce balking in high states).
* **Mathematical Approach:** * Applied a truncated exponential distribution to accurately model the updated service rate (mu) when the 3-hour limit is active.
    * Formulated a Linear Programming (LP) model to maximize the Net Profit (NP_ik) across all states.
* **Outcome:** Solved the LP to find the optimal policy sequence (1, 2, 1, 1, 3). The optimal strategy proved to be "Do Nothing" for states 0, 2, and 3; offering a "Cookie Service" during state 1; and enforcing a "3-Hour Limit" during the highly congested state 4.

## 💻 Tech Stack & Tools
* **Languages:** Python
* **Operations Research:** Queueing Theory (M/M/K/K), Truncated Exponential Distributions, Markov Decision Process Concepts
* **Optimization:** Linear Programming, Excel Solver

## 💡 Key Takeaways
This project bridges the gap between theoretical operations research and practical business application. It demonstrates how rigorous mathematical modeling—handling shifting service rates and capacity constraints—can directly translate into actionable, data-driven business decisions that maximize revenue.
