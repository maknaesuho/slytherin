# 📉 Vanguard Digital Onboarding A/B Test

An end-to-end data analytics project evaluating a digital onboarding UI redesign for Vanguard, measuring its impact on user retention, session duration, and completion rates to drive a commercial rollout decision.

---

## 🎯 Project Overview & Business Context
* **Client / Brand:** Vanguard (Digital Client Onboarding)
* **Objective:** Determine if the new digital interface ("Test" variation) significantly outperforms the legacy workflow ("Control" variation) in driving completion rates while minimizing user friction.
* **Final Outcome / Recommendation:** **Deploy the Test Variation**. The redesign achieved a highly significant completion lift (+8.69% overall), successfully exceeding Vanguard's 5% business threshold, particularly driven by high-value Diamond-tier clients.

---

## ⚙️ Key Analysis Parameters
The feasibility study evaluated the digital experiment across three core pillars:
1. **Completion Rate Lift (Z-Test):** Measured the absolute percentage point increase in completed sessions between the Control and Test groups, aiming to exceed a 5% commercial growth target.
2. **Session Duration (Mann-Whitney U Test):** Evaluated whether the new UI increased cognitive load. Because duration data is heavily right-skewed by inactive sessions, non-parametric median testing was used.
3. **Funnel Friction & Backtracking:** Tracked milestone abandonment (Start $\to$ Step 1 $\to$ Step 2 $\to$ Step 3 $\to$ Confirm) and compared the furthest step reached against the literal exit step to identify repetitive loops and friction points.

---

## 🛠️ Tech Stack & Data Pipelines
* **Language & Libraries:** Python 3, Pandas (Data Wrangling), Matplotlib & Seaborn (EDA), SciPy & Statsmodels (Hypothesis Testing).
* **Visualization:** Interactive Tableau Dashboard mapping step-by-step dwell times, age cohort performance, and funnel drop-offs.
* **Data Wrangling Highlights:** 
  * Merged demographic client profiles with raw web event logs.
  * Resolved fragmented sessions by sorting strictly on `visit_id` and timestamp (`mergesort`).
  * Calculated chronological step durations using `.shift(-1)` to measure exact dwell times, dropping extreme inactivity outliers (>1800s) to prevent skewed averages.

---

## 📊 Major Findings & Strategic Insights
* **The Overall Lift:** The new design successfully passed the 5% business growth target. Overall completion rates climbed from **49.89% (Control)** to **58.58% (Test)**—an **+8.69% absolute lift**.
* **Massive Diamond Tier Success:** High-value Diamond clients experienced the most dramatic benefit, surging from 48.04% to 63.35% completion (**+15.31% lift**).
* **Frictionless Efficiency:** The Test variation streamlined complex decision-making. Users completed Step 2 and Step 3 much faster, with the total median session duration increasing by only a negligible 5 seconds (188s vs. 193s).
* **The "Step 3" Cliff:** While the overall design improved, Step 3 remains the largest abandonment point across both variations (driving ~84% of drop-offs at that stage), requiring targeted UX review for validation errors.
* **Age Cohort Friction:** Younger clients (<35) drove a strong +5.09% lift with zero added time penalty. Older clients (55+), however, experienced adaptation friction, taking 21 seconds longer to navigate the new interface.

---

## 🚀 Further Questions & Next Steps
Based on the dashboard and statistical findings, the following actions are recommended:
* **Full Rollout:** Proceed with a global deployment of the Test variation due to its substantial revenue implications for Diamond-tier clients and overall statistical significance.
* **Segmented UX Support:** Implement targeted onboarding guidance (e.g., brief tooltips or guided tours) specifically tailored for the 55+ legacy cohort to ease their adaptation to the new interface.
* **Optimize Step 1 & 3:** Focus engineering efforts exclusively on Step 3 form validation errors, and investigate why Test users backtrack from Step 1 more frequently than Control users (19.21% vs. 9.35%).

---

## 📂 Deliverables & Project Files
* **[Jupyter Notebook (Wrangling, EDA, & Hypothesis Testing)](./vanguard_ab_test_clean.ipynb)**
* **[Tableau Dashboard Data Sources](./tableau_outputs/)**
* **[Executive Presentation (Google Slides)](#)**
* **[Trello Kanban Board](#)**
