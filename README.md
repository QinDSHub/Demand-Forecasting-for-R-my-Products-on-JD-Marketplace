## Notes on Project Materials

The PDFs included in this projects were originally created for presentations at the time and have been preserved since then.  
While they may now appear somewhat preliminary, they capture a valuable process focused on underlying technical design and system thinking.

They provide a full-picture view of the end-to-end modeling workflow, including:
- Problem definition  
- Data exploration  
- Data cleaning  
- Model architecture design  
- Model development  
- Model offline evaluation  

These materials may be particularly helpful for anyone seeking a deeper understanding of the complete modeling pipeline and the technical reasoning behind it. You can also gain a solid overview by reviewing the README sections below for each project.

For a complete overview of my projects, feel free to visit my LinkedIn:  
### https://www.linkedin.com/in/qinluu  

I’m always happy to connect, share, and discuss.

---

## Demand Forecasting for Rémy Products on JD Marketplace

📂 Project Overview

This project was initiated as a high-stakes feasibility study for a VIP client in the luxury spirits sector (Rémy Cointreau). The objective was to infer monthly sales volumes on the JD.com platform using unstructured consumer comment metadata as a proxy.
Despite significant data constraints and high noise levels, this "impossible task" resulted in a mathematical framework that the client successfully adopted to inform their marketing strategies and inventory management with R2 score at 0.86.

________________________________________
📂 Technical Challenges & Complexity

Predicting sales from comment data presents several non-trivial hurdles:

•	Sparse & Noisy Data: Fragmented datasets due to system migrations, with some products having only 1–3 data points per month.

•	Dynamic Entity Mapping: Product "Keys" on JD.com are non-static; a single ID might represent Red Wine for one quarter and be repurposed for White Wine the next.

•	Long-Tail Distribution: Highly imbalanced data across the alcoholic beverage category.

•	Signal Uncertainty: Determining if a correlation exists between the timing of a comment and the timing of a transaction.

________________________________________
📂 Methodological Innovation: Mathematical Decomposition

To solve the lack of direct sales data, we developed a logic to derive Sales Volume ($V$) from Incremental Comments ($C$).

☑ The Core Hypothesis
The relationship was modeled as a weighted sum of current and lagged comment activities:
V_april = w1 * C1 + w2 * C2 + w3 * C3
Where $w_n$ represents the conversion ratio of users who purchased in month $n$ but commented in April.

☑ Formula Optimization & Simplification
Through continuous derivation and assumption testing, I simplified the complex multi-lag model into a more robust Dual-Variable Model:
V_april = alpha1 * C1 + alpha2 * C2
Testing proved that this Formula (B) significantly outperformed simpler single-variable models by capturing the "lagged" nature of consumer feedback while maintaining model stability.

☑ Dynamic Parameter Search
Instead of static weights, I leveraged a parameter search approach using limited ground-truth sales samples to identify the optimal $\alpha_1$ and $\alpha_2$ for each specific month. This accounted for seasonal variations in consumer behavior (e.g., Chinese New Year or 6.18 shopping festivals).
________________________________________

📂 Business Impact & Client Adoption

While initially framed as an exploratory experiment, the model's ability to capture sales trends from public-facing metadata provided the client with a unique competitive advantage:

•	Strategic Pivot: Enabled the client to adjust marketing spend based on the "engagement-to-sales" lag identified by the model.

•	Inventory Heuristics: Provided a reference point for stock replenishment in regions where direct sales data was delayed.

•	Success out of "Impossibility": The client ultimately moved this from a "test case" to a production-referenced tool for internal decision-making.

________________________________________
📂 Key Takeaways

☑ Mathematical Intuition: Ability to decompose business problems into solvable linear equations.

☑ Client Management: Managed expectations for a "practically infeasible" project while delivering a "practically useful" outcome.

☑ Data Scarcity Strategy: Expert at extracting signal from noisy, small, and long-tail datasets.
