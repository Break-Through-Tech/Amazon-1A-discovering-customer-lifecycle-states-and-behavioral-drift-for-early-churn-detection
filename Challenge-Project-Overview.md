---

> ## Challenge Advisor: Update & Finalize Your Project Overview
>
> > 💡 **These grey text instructions are just for you, the team's Challenge Advisor; please delete them once you have completed the steps below.**
>
> We've pre-populated this Challenge Project Overview page — which is what will be shared with your Break Through Tech student team in August — using the details from your submission form. You should have received an email inviting you to join this repo as a Collaborator, enabling you to add files and make edits.
> 
> In order for your project to be finalized and assigned to a team, please:
> 1. **Review all sections below** and update or expand any content as needed, making sure to address the SME Feedback in the section immediately below. Look for square brackets to find the places below that require additional inputs from you (e.g., "About [Company / Org Name]").
> 2. **Add your dataset** to the [data folder](data) in this repo.
> 3. **Close the Issue assigned to you in this repo** to let us know that you have made your edits and the overview page is ready for final review. You can do this by going to the _Issues_ tab in the top left section of the menu above, add a comment that says "CA review complete", and click the button to Close the Issue. 
>
> If you're unfamiliar with how to edit a page like this in GitHub, check out [this tutorial](https://ubc-lib-geo.github.io/gis-workshop-waml-template/content/handson/edit-readme.html) for a quick overview (start with step 2 and only edit this page), and [this guide](https://ubc-lib-geo.github.io/gis-workshop-waml-template/content/markdown.html) on how to use Markdown to compose text.
>
>
> ❌ Remember that this is a public repo. Do NOT include: Proprietary data, PII, API keys, credentials, or anything confidential.

---

## 📋 BTT Internal Evaluation Notes
*(This section is for BTT staff and CAs only — remove before sharing with students)*

### Technical Vetting
| Check | Status | Notes |
| :--- | :--- | :--- |
| Python Compatibility | 🟢 | Stack aligns perfectly with scikit-learn, pandas, and SHAP. GenAI component must be limited to local HuggingFace transformers or OpenAI API with strict usage limits. |
| Data Readiness | 🟡 | Public retail datasets are well-documented but require significant feature engineering to construct time-series windows and label churn. |
| Resource Check | 🟢 | Dataset size is well within Google Colab limits. No requirement for proprietary hardware. |

### Internal Scores
- **Student Fit Score:** 7/10
- **Technical Depth Score:** 8/10
- **Overall Recommendation:** REVISE

### Advisor Feedback Draft
This project offers a compelling synthesis of classical ML and Generative AI, providing students with high-value exposure to explainable systems. To ensure success within the 12-week window, I suggest: (1) Standardize the 'Churn' definition early to avoid ambiguity during the modeling phase, and (2) Replace complex LLM integrations with a deterministic template-based generation approach to minimize API dependency issues. Streamlining the scope will help to ensure the core classification pipeline is robust before layering on GenAI features (which could be the stretch goal for the Fellows).

---

# Discovering Customer Lifecycle States and Behavioral Drift for Early Churn Detection Using Explainable AI and Generative AI

**Company / Org:** Amazon.com  
**Challenge Advisor:** Aryyama Kumar Jana, Lakshmi Prasanna Kachireddy, janaaryyama@gmail.com  
**Program:** Break Through Tech AI Studio - Fall 2026  

---

## 🏢 About Amazon.com
Amazon is a global leader in e-commerce, cloud computing, and digital streaming, operating at the intersection of retail innovation and logistics efficiency. This project team will refine customer retention strategies by applying advanced machine learning to large-scale transactional datasets.

---

## 🎯 The Challenge
### Project Summary
This project tasks the team with building an end-to-end churn detection system that integrates time-series feature engineering, customer lifecycle clustering, and behavioral drift detection. By leveraging both Explainable AI (XAI) and Generative AI, the team will create a system that not only predicts customer churn but also provides human-readable summaries of underlying risk factors to inform business decision-making.

### Success Criteria
Predictive performance (accuracy, precision, recall, F1 score, ROC-AUC), early-warning horizon (days/weeks before churn), interpretability of discovered customer states, and qualitative evaluation of GenAI summaries.

### Project Milestones
Use these milestones to guide your work. Your team will create a GitHub Projects board to track tasks within each milestone.
| Month | Milestone | Key Activities |
|-------|-----------|----------------|
| **September** | Data Exploration & Preprocessing | Ingesting the Online Retail II/RetailRocket datasets, conducting exploratory data analysis, and developing robust data-cleaning pipelines to handle missing values and outliers. |
| **October** | Feature Engineering & Baseline Modeling | Constructing time-series windows for behavioral tracking, engineering churn-predictive features, and training initial baseline models such as Logistic Regression and Random Forest. |
| **November** | Model Optimization & Evaluation | Performing rigorous hyperparameter tuning on XGBoost/ensemble models, evaluating model performance against success metrics, and validating the robustness of the clustering architecture. |
| **December** | Insights, Deliverables & Presentation | Integrating SHAP for model interpretability, deploying GenAI for risk report generation, and finalizing the documentation of business recommendations. |

> **Note for the team:** Please create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → Choose **Board** → Add columns for each month.

---

## 📊 Dataset
**Name and Source:** Online Retail II and RetailRocket datasets (Publicly accessible via Kaggle/UCI)  
**Format:** CSV/TSV and Excel  
**Size:** under 1gb  
**Location:** Internal data repository or provided web links via project Slack channel  

### Key Details
- Publicly available e-commerce data (Online Retail II and RetailRocket datasets), including numerical, categorical, text, and time-series data in CSV/TSV and Excel formats.
- Preprocessing must account for temporal sequencing, handle high-cardinality categorical variables, and normalize transactional volume across different customer segments.

---

## 🛠️ Suggested Approach
**ML Problem Type:** Classification, Clustering, and NLP (Generative AI)  
**Recommended Libraries:**
- Python
- Google Colab
- Logistic Regression
- Random Forest
- XGBoost
- K-Means
- Gaussian Mixture Models
- HDBSCAN
- SHAP
- GenAI
**Evaluation Metrics:** F1-score, Precision-Recall AUC, time-to-churn horizon, and qualitative readability/accuracy scores for GenAI summaries.

---

## 📚 Resources to Get Started
The following resources will help your team understand the problem space and potential technical approaches for this project:
**Background Reading:**
- Industry documentation on "Customer Churn Prediction in Retail" and "Explainable AI for Risk Management."
**Technical Tutorials:**
- Scikit-learn documentation for time-series splits and SHAP library tutorials for feature importance visualization.
**Code Examples:**
- Baseline repository templates for tabular classification and K-means clustering patterns.

---

## 🤝 How We'll Work Together
**Check-ins:** During our biweekly 60-min AI Studio Lab Section meeting block (2nd and 4th week of every month)  
**Communication:** Official Studio Slack channel and team-designated email threads.  
**Response time:** 24-48 hours during business days.  
**Recommended Tools:**
- **Coding:** Google Colab Free Tier  
- **Collaboration:** GitHub, Notion  
- **Virtual Meetings:** Zoom, Google Meet  

---

## 🚀 Getting Started
1. **Review this overview document** and note any questions for our first meeting.
2. **Begin reviewing the dataset** using the link provided in the Dataset section.
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).

I'm excited to work with you!

---

## ❓ Questions?
Please bring any questions to our first meeting during the week of August 24th (Break Through Tech's Bridge to Studio - Session B).
