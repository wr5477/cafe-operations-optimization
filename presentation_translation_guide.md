# Presentation Translation Guide
**Title: Optimization in "Cafe" Operations (Operations Research II Team Project)**

*Note: This guide provides English translations and contextual explanations for each slide in the original Korean presentation (`cafe_optimization_final_presentation.pdf`).*

## [Slide 1-4] Introduction & Research Background
* **Slide 1:** Project Title: Optimization in "Cafe" Operations. Team members listed.
* **Slide 2:** Table of Contents: 01 Research Background, 02 Task 1, 03 Task 2, 04 Limitations & Suggestions.
* **Slide 3 (Task 1):** The goal is to determine the optimal ratio of 1-person to 2-person tables to increase seat utilization, improve customer satisfaction, and enhance overall operational efficiency.
* **Slide 4 (Task 2):** The goal is to derive the optimal operational policy for different congestion states to increase profitability, improve customer satisfaction, and allow for flexible management.

## [Slide 5-8] Task 1: Data Collection
* **Slide 5:** Introduction to Task 1: Determining the optimal seating ratio.
* **Slide 6 (Arrival Data):** Team members collected primary data by observing customer arrivals at 'Cafe Ann' (a cafe mainly used by university students for studying) over a 24-hour period. The calculated arrival rate (lambda) is 7.17.
* **Slide 7 (Sales Data):** Collected actual daily sales data to estimate the expected profit per customer (avg. 5,247.5 KRW). It assumes all transactions lead to cafe usage, as take-out orders were rarely observed.
* **Slide 8 (Usage Time Data):** Conducted a survey targeting university students who study in cafes. The survey determined that the average usage time is about 3.48 hours. When asked about an acceptable time limit, 48.1% of respondents chose 3 hours.

## [Slide 9-11] Task 1: System Definition & Markov Properties
* **Slide 9:** Defined the system as an M/M/K/K Queueing Model (Erlang Loss System). The number of servers (s) equals the cafe's maximum capacity (K). No queue exists; if the cafe is full, customers leave.
* **Slide 10-11:** Performed Kolmogorov-Smirnov (K-S) tests to verify if the collected time-interval data follows an exponential distribution. The p-values were > 0.05, failing to reject the null hypothesis, confirming the data follows an exponential distribution.

## [Slide 12-15] Task 1: M/M/K/K Modeling & Evaluation Metrics
* **Slide 12:** Defined model parameters based on collected data: lambda = 43/6 (arrivals per hour), mu = 1/3.48 (service rate per hour), s = 34 (number of 2-person tables), and Profit = 5,300 KRW per person.
* **Slide 13-14:** Explained the mathematical derivation of the Erlang-B formula to calculate the blocking probability (B(E,m)). Revenue is calculated based on the number of customers served.
* **Slide 15:** Showed the Python simulation code used to calculate the blocking probability and estimate the monthly revenue, which closely matched the actual cafe sales data.

## [Slide 16-17] Task 1: Seating Optimization Results
* **Slide 16:** Defined assumptions for optimization: 1 person occupies one full table; groups of 2+ use 2-person tables; groups spend more money on average than solo customers. The current layout has 28 single seats and 3 two-person seats.
* **Slide 17:** Ran a Python loop to find the seating combination that maximizes expected revenue. 
    * **Result:** The optimal layout is 20 single-person seats and 7 two-person seats, which mathematically increases the expected monthly revenue compared to the existing layout.

## [Slide 18-23] Task 2: State Definition & Decisions
* **Slide 18:** Introduction to Task 2: Deriving the optimal policy combination by situation.
* **Slide 19:** Defined 5 "States" (0 to 4) based on the cafe's congestion level (utilization rate, rho). State 0 is low congestion; State 4 is extremely high congestion (over 140%).
* **Slide 20:** Defined 3 Decision options (k): 1. Do Nothing; 2. Offer Free Cookies (to attract/retain customers in low states); 3. Implement a 3-Hour Time Limit (to reduce balking in high states).
* **Slide 21-23:** Explained the mathematical adjustment needed for Decision 3 (Time Limit). Modeled the new service time using a truncated exponential distribution (cut off at 3 hours), increasing the service rate (mu) from 0.29 to 0.7769 per hour.

## [Slide 24-28] Task 2: Transition Probabilities (P_ij(k))
* **Slide 24:** Probabilities for k=1 (Do Nothing): Assumed the cafe is most likely to stay in its current state or shift to adjacent states.
* **Slide 25:** Probabilities for k=2 (Free Cookies): Based on survey data, providing cookies has a 33.3% chance of positively influencing future visits (moving to a higher state) and a 66.7% chance of having no effect (staying in the same state).
* **Slide 26-28:** Probabilities for k=3 (Time Limit): Based on survey data, 40% of customers would not visit if a 3-hour limit were enforced. Adjusted the transition probabilities for States 3 and 4 accordingly to reflect this drop in arrival rate.

## [Slide 29-31] Task 2: Net Profit (NP_ik) Calculation
* **Slide 29-31:** Calculated the Net Profit for each state and decision combination.
    * **k=1 (Do Nothing):** Based on expected hourly customers and average spend. For high states (3 & 4), throughput is limited by the service rate.
    * **k=2 (Free Cookies):** Subtracted the fixed cost of purchasing cookies from the revenue.
    * **k=3 (Time Limit):** With the increased service rate (mu=0.77), the cafe can handle more customers per hour in high states, leading to higher revenue despite the loss of some customers.

## [Slide 32-35] Task 2: Linear Programming Model & Optimal Policy
* **Slide 32:** Formulated the problem as a Linear Programming (LP) model to maximize total expected Net Profit, subject to steady-state probability constraints.
* **Slide 33-34:** Showed the setup and results using Excel Solver.
* **Slide 35:** Final Optimal Policy sequence: **(1, 2, 1, 1, 3)**.
    * State 0, 2, 3: Do Nothing (k=1).
    * State 1: Free Cookie Service (k=2).
    * State 4: 3-Hour Time Limit (k=3).

## [Slide 36-39] Limitations & Conclusion
* **Slide 36:** Acknowledged limitations: Reliance on some survey data/assumptions due to limited access to the cafe's complete historical data, and the somewhat arbitrary assignment of initial probabilities for the "Do Nothing" scenario.
* **Slide 37-39:** Team photos, behind-the-scenes moments, and a concluding "Thank You."
