## Notes on Project Materials

The PDF included in this repository was originally prepared for project presentation. Although it may reflect the presentation style and documentation standards of the time, it preserve the technical design, analytical process, and modeling decisions behind the project.

It provide an overview of the end-to-end modeling workflow, including:
- Problem definition
- Data exploration and processing
- Feature engineering
- Model design and development
- Offline evaluation

For a broader overview, please also refer to the project description below.

For more projects and technical discussions, visit my LinkedIn:  
https://www.linkedin.com/in/qinluu

I'm always happy to connect and exchange ideas.

---

## Demand Forecasting for Rémy Products on JD.com

### Project Overview

This project explored monthly sales forecasting for Rémy products on JD.com using consumer review data, business logic, mathematical estimation, and machine learning.

As reliable ground-truth sales data was unavailable, the project was positioned as an exploratory forecasting initiative, with data limitations communicated to and approved by the client before development.

The objective was to estimate calendar-month sales volumes from review activity, developing a forecasting framework that could support marketing and inventory planning despite significant data limitations.

### Technical Challenges

- **Sparse and Noisy Data:** Platform migration and inconsistent historical records created substantial data cleaning and validation challenges.
- **Dynamic Product Identifiers:** Product IDs and their associated information could change over time, requiring careful validation before records could be used for modeling.
- **Long-Tail Distribution:** Sales patterns varied considerably across products, making it difficult to develop a consistent forecasting approach.
- **Uncertain Review-to-Sales Relationships:** Review timestamps did not necessarily correspond to transaction dates, making simple review-count-to-sales conversion unreliable.
- **Data and Concept Drift:** Changes in platform data distributions and underlying patterns affected model reliability over time.

### Methodology

Rather than estimating sales from review-count differences using a fixed conversion coefficient, the approach combined mathematical estimation with LightGBM-based forecasting.

Key components included:

- **Data Preparation:** Cleaned, validated, and transformed review data to address inconsistencies and improve feature quality.
- **Cumulative Review Forecasting:** Predicted cumulative review counts at multiple future timestamps to capture temporal patterns.
- **Mathematical Estimation:** Applied linear algebraic formulations to translate predicted review activity into sales estimates.
- **Dynamic Parameter Optimization:** Used threshold-search strategies to estimate monthly weighting parameters, accommodating changes in business conditions and consumer behavior.
- **Drift-Aware Adaptation:** Introduced drift-sensitive features and shortened the model retraining cycle from quarterly to monthly to improve adaptability.

### Business Value

The project demonstrated the feasibility of extracting useful sales signals from publicly accessible e-commerce review data, even when reliable sales records were unavailable.

The resulting framework achieved an offline R² score of 0.86 and provided the client with an additional reference for sales estimation and business planning.

The project also highlighted the importance of data quality, explicit assumptions, mathematical reasoning, and model adaptability when developing forecasting solutions under real-world data constraints.

### Key Takeaways

- **Mathematical Modeling:** Translated a business problem with limited direct observations into a structured estimation framework.
- **Data Engineering:** Addressed inconsistent records, sparse observations, and data quality issues before model development.
- **Forecasting Under Uncertainty:** Combined business assumptions, mathematical estimation, and machine learning to address the absence of reliable ground-truth data.
- **Model Adaptability:** Recognized the impact of data and concept drift and adjusted feature engineering and retraining strategies accordingly.
