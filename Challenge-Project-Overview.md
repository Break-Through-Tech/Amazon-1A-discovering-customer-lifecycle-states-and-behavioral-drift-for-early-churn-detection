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
In this project, you will use public e-commerce customer transaction and event-behavior data and machine learning techniques including time-series feature engineering, clustering, classification, behavioral drift detection, explainable AI, and generative AI to build a system that detects early behavioral changes in customers before they churn and generates interpretable customer-risk summaries. This will help us address the business problem of identifying at-risk customers earlier, improving retention strategies, and reducing revenue loss from preventable customer churn.

### Success Criteria
Success will be measured using both predictive performance and early-warning usefulness. The team will evaluate churn prediction using accuracy, precision, recall, F1 score, and ROC-AUC. Since the project focuses on early detection, the team will also measure early-warning horizon, defined as how many days or weeks before churn the system can identify meaningful behavioral drift. The lifecycle-state approach will be evaluated by whether the discovered customer states are interpretable and whether transitions into at-risk states improve early churn detection compared with standard churn models. The GenAI component will be evaluated qualitatively based on whether it produces accurate, clear, and useful summaries grounded in the model’s features and explanations. A successful December outcome would be a reproducible Python/Google Colab pipeline that ingests public e-commerce datasets, creates customer-time features, discovers lifecycle states, predicts churn risk, explains the drivers of risk, and generates plain-English risk summaries for at-risk customers.

### Stretch Goals
If the team progresses quickly, stretch goals could include building customer behavior embeddings using autoencoders or sequence models, comparing lifecycle-state discovery across multiple datasets, adding a lightweight dashboard using Streamlit or Gradio, improving the GenAI component with prompt templates or retrieval-augmented generation over customer history, or developing retention recommendation logic based on the type of behavioral drift detected.

### Project Milestones
Use these milestones to guide your work. Your team will create a GitHub Projects board to track tasks within each milestone.
| Month | Milestone | Key Activities |
|-------|-----------|----------------|
| **September** | Business Understanding & Data Exploration | The team will focus on understanding the business problem, exploring public datasets, and building the foundational data pipeline. Fellows will review open-source e-commerce datasets such as Online Retail II and RetailRocket, clean the data, define a practical churn label, and create the first version of a customer-time feature table. Initial features may include purchase frequency, activity count, revenue, unique items, average order value, and days since last activity. By the end of September, the team should have a reproducible Google Colab notebook that converts raw public data into modeling-ready customer behavior features. |
| **October** | Modeling | The team will build baseline models and begin analyzing customer behavior changes over time. Fellows will train traditional churn prediction models such as Logistic Regression, Random Forest, and XGBoost, then evaluate them using metrics such as precision, recall, F1 score, and ROC-AUC. The team will also create behavioral drift features that compare a customer’s current behavior with their previous behavior, such as changes in purchase frequency, revenue, activity count, and unique items. By the end of October, the team should have baseline churn models and an initial behavioral drift scoring approach. |
| **November** | TBD | The team will develop the advanced lifecycle-state, explainability, and GenAI components. Fellows will apply clustering methods such as K-Means, Gaussian Mixture Models, or HDBSCAN to discover latent customer lifecycle states, such as active buyer, occasional buyer, declining customer, and at-risk customer. The team will compare the lifecycle-state and behavioral-drift approach against baseline churn models, measure how early churn risk can be detected, and use explainability methods such as SHAP or feature attribution to identify the strongest drivers of risk. As a final layer, the team will add a lightweight Generative AI component that converts model outputs into plain-English customer-risk summaries and possible retention recommendations. By the end of November, the team should have a final end-to-end demo, evaluation results, and explainable GenAI-generated summaries for at-risk customers. |

> **Note for the team:** Please create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → Choose **Board** → Add columns for each month.

---

## 📊 Dataset
**Name and Source:** Publicly accessible via Kaggle/UCI  
**Format:** CSV/TSV and Excel  
**Size:** under 1gb  
**Location:** https://archive.ics.uci.edu/dataset/502/online%2Bretail%2Bii, https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset

### Key Details
- Publicly available e-commerce data (Online Retail II and RetailRocket datasets), including numerical, categorical, text, and time-series data in CSV/TSV and Excel formats.
- Preprocessing must account for temporal sequencing, handle high-cardinality categorical variables, and normalize transactional volume across different customer segments.

---

## 🛠️ Suggested Approach

**ML Problem Type:** Classification, Clustering, and NLP (Generative AI)  

**Recommended Libraries:**
- [e.g., pandas, scikit-learn, TensorFlow, Hugging Face]

**Evaluation Metrics:**
- [e.g., Accuracy, Precision/Recall, RMSE, BLEU score]

---

## 📚 Resources to Get Started

The following resources will help your team understand the problem space and potential technical approaches for this project:

**Background Reading:**
- [e.g., Link to an article or blog post about the problem domain]
- [e.g., Link to an industry report or case study]

**Technical Tutorials:**
- [e.g., Link to a free tutorial on the ML technique(s) involved]
- [e.g., Link to documentation for a key library or tool]

**Code Examples:**
- [e.g., Link to a relevant GitHub repo]
- [e.g., Link to a sample implementation or starter code]

**Other:**
- [Links to any additional resources — e.g., papers, videos, podcasts, etc.]

*Feel free to explore beyond these, and share anything interesting you find with me!*

---

## 🤝 How We'll Work Together

**Official check-ins:** During our biweekly 45-minute AI Studio Lab Section meeting block (2nd and 4th week of every month)

 **Other ways to reach out to me with questions:** 
* [e.g., Your team's channel within Break Through Tech’s Discord space]
* [e.g., Email; please copy your teammates and AI Studio Coach]
* [e.g., Request a team check-in on Zoom]
* [Note: I will aim to respond within 48 hours. Please reach out to your AI Studio Coach with urgent questions.]

> 💡 **Challenge Advisor: Please update the above based on your availability and preference. If you are not able to answer questions or meet with fellows outside of the biweekly Lab Section check-ins, simply write in "N/A (only available during the official check-in times)"**

**Recommended free coding / collaboration tools**
* […]
* […]

---

## 🚀 Getting Started

1. **Review this overview document** and note any questions for our first meeting
2. **Begin reviewing the dataset** using the link above
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects)

I’m excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of August 24th (Break Through Tech’s Bridge to Studio - Session C). 
