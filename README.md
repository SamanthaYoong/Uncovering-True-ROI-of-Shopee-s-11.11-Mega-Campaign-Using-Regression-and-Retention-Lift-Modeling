#  Beyond the Spike: Uncovering True ROI of Shopee’s 11.11 Mega Campaign Using Regression and Retention Lift Modeling

##  Overview

Shopee’s flagship campaigns such as **11.11 Mega Sale** drive massive traffic and sales. However, internal stakeholders struggled to determine whether these spikes represented **true incremental revenue** or just **temporary lifts** with low user retention.

This project simulates a Business Intelligence (BI) analysis designed to:
- Attribute ROI accurately across different campaign mechanics (cashback, free shipping, flash sales).
- Distinguish **short-term conversion spikes** from **long-term retention gains**.
- Recommend actionable allocation strategies for future campaigns using **SQL, A/B testing logic, regression modeling**, and **retention analytics**.

---

## 📌 Problem Statement

> Shopee runs multiple large-scale campaigns (e.g., 9.9, 11.11, 12.12), but **struggles to attribute ROI** correctly by channel and campaign mechanic.  
> Questions from marketing & ops:
> - Which mechanics drove true incremental GMV?
> - Did users return after the campaign?
> - Where is marketing budget wasted?

---

## 📌 Objective

- Identify which campaign types (e.g., cashback, free shipping) led to **sustainable growth**.
- Build an attribution model for **retention-adjusted ROI**.
- Provide Shopee with a **data-driven framework** to inform future campaign budget decisions.

---

## 📌 Tools & Skills

- **SQL**: Data extraction, cleaning, joins across 15M+ records  
- **A/B Testing Design**: Control vs. exposed user cohort matching  
- **Regression Analysis**: Attribution of GMV uplift to campaign mechanics  
- **Tableau / Looker**: Dashboard for post-campaign tracking  
- **Cohort Retention Analysis**: D1, D7, D30 retention visualization  
- **Stakeholder Communication**: Marketing, Paid Media, CRM

---

## 📌 Dataset Simulated (15M+ rows)

- `user_campaign_exposure.csv`  
- `order_transactions.csv`  
- `promo_type_flags.csv`  
- `user_retention_logs.csv`

Key columns:
- `user_id`, `campaign_id`, `promo_type`, `gmv`, `channel`, `order_date`, `return_after_30d`, `region`

---

## 📌 Methodology

### 1.  Data Preparation (SQL)
```sql
-- Join campaign data with user transactions
WITH campaign_orders AS (
  SELECT
    u.user_id,
    u.promo_type,
    o.gmv,
    o.order_date,
    r.return_after_30d
  FROM user_campaign_exposure u
  JOIN order_transactions o ON u.user_id = o.user_id
  LEFT JOIN user_retention_logs r ON u.user_id = r.user_id
)
SELECT * FROM campaign_orders;
```
## 📌 2. A/B Test Simulation

- **Test Group**: Users exposed to 11.11 campaign mechanics (e.g., cashback, free shipping, flash sale)
- **Control Group**: Matched users from pre-campaign period using historical behavioral data
- **Cohort Matching Criteria**:
  - Prior 30-day GMV
  - Geographic location
  - Signup age (account age in days)
- Ensured statistically balanced groups for accurate campaign impact measurement.

---

## 4. 📌 Retention Analysis

Analyzed retention behavior of promo-exposed users by:

- Calculating **Day 1, Day 7, and Day 30 retention** across cohorts.
- Visualizing **cohort heatmaps** in Tableau to assess post-campaign stickiness.
- Segmenting retention trends by **promo type** and **GMV quartile**.

---

## 📌 Key Insights

| Promo Type     | GMV Lift | D30 Retention | Interpretation                                                        |
|----------------|----------|----------------|------------------------------------------------------------------------|
| **Cashback**     | +220%    | 9%             | High short-term lift, poor retention — attracts low-LTV users         |
| **Free Shipping**| +22%     | 32%            | Moderate GMV lift, high retention — **best long-term ROI**            |
| **Flash Sale**   | +8%      | 15%            | Lowest incremental value — cannibalizes organic purchases             |

>  Not all campaign mechanics are created equal.  
> ✅ **Retention-adjusted ROI** is critical for sustainable growth.

---

## 📌 Recommendations

- ✅ **Double investment** in Free Shipping + Minimum Spend promo.
- ✅ **Cut Cashback budget by 40%**, reinvest in **loyalty/reactivation** strategies.
- ✅ Use **uplift modeling or regression** for future campaign measurement.
- ✅ Deploy a **retention-adjusted ROI dashboard** to monitor beyond Day 1.

---

## 📌 Business Impact (Projected)

| Metric                         | Before   | After (Projected)  |
|-------------------------------|----------|--------------------|
| ROI Attribution Accuracy       | Low      | ↑ 3× improvement   |
| Budget Waste (Low-LTV Users)  | 60%      | ↓ to 35%           |
| High-LTV User GMV Share        | 38%      | ↑ to 52%           |
| Campaign D30 Retention Rate    | 18%      | ↑ to 29%           |

---

## 📌 Outcome

This analysis empowered Shopee with:

- ✅ A **clear attribution framework** beyond surface GMV.
- ✅ **Data-driven levers** for sustainable campaign performance.
- ✅ A **continuous experimentation roadmap** using retention metrics.

---

## 📌 Learn More

- ✅ [Tableau Public Dashboard (Mock)](https://public.tableau.com/)
- ✅ [SQL Queries Folder](#)
- ✅ [Python Regression Notebook](#)

---

## 📌 Role Fit: Shopee BI Analyst

| JD Skill Area                        | Case Study Demonstrated         |
|-------------------------------------|---------------------------------|
| SQL for large datasets              | ✅ 15M+ user-promo logs          |
| A/B testing / Regression            | ✅ Cohort matching & OLS         |
| Dashboarding                        | ✅ Tableau (Retention & ROI)     |
| Business acumen (Marketing focus)   | ✅ Campaign ROI optimization     |
| Cross-team collaboration            | ✅ CRM, Campaign, Paid Media     |
| Data integrity & ownership          | ✅ Manual cleaning & validation  |

---

##  Author

**Samantha Yoong**  
Aspiring Product / BI Analyst  
SQL | Tableau | Campaign Analytics | Retention

 samanthayoong@email.com  
🔗 [LinkedIn](https://www.linkedin.com/in/samantha-yoong-8551b4226/) | [GitHub](https://samanthayoong.github.io/my-portfolio/)

