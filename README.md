# Mobile-Financial-App-
Analysis of Private Mobile Financial Service Apps
# Mobile Financial Service (MFS) User Review & Sentiment Pipeline

## Tools Used
- Python (Google Colab)
- Data Analysis & NLP Libraries (Pandas, Unicode NFKC)
- Inferential Statistics & Lexical Matching ($\chi^2$, Cramer's $V$)

## Business Problem
Mobile Financial Service (MFS) platforms in emerging markets handle millions of daily transactions, yet frequent authentication failures, payment disruptions, and unexpected fee structures severely erode user trust. Traditional feedback mechanisms like periodic surveys offer only an episodic view of customer pain points. This analysis systematically mines large-scale Play Store reviews to convert unstructured user feedback into prioritized product development backlogs.

## The Data
- **Source:** Scraped Google Play Store reviews for major MFS applications in Bangladesh covering April 25, 2018 – August 8, 2026.
- **Dimensions:** 121,013 raw reviews scraped; 121,011 retained post-cleaning across 7 key metadata fields.
- **Key Variables:** Review Text, Rating (1–5 stars), Timestamp, Helpfulness Index, Application Version, Script Group (Latin, Bangla, Code-Mixed), and 10 Keyword-Derived Complaint Categories.

## Methodology
- **Data Cleaning & Standardization:** Applied Unicode NFKC standardization, removed duplicate review IDs, non-printing characters, markup, and URLs.
- **Sentiment & Script Categorization:** Binned ratings into positive (81.62%), negative (15.22%), and neutral tiers. Classified negative reviews across 10 complaint categories via keyword matching and identified scripts (76.76% Latin/Banglish, 19.09% Bangla, 1.39% Code-Mixed) via character-set heuristics.
- **Statistical Inference:** Conducted Bonferroni-corrected longitudinal Chi-Square tests ($\alpha = 0.005$) and Cramer's $V$ effect size calculations to isolate persistent operational defects from random noise.

##  Key Findings & Insights
- **Authentication is the Primary Defect:** Login, OTP, and verification failures represent the largest persistent defect ($\chi^2 = 406.78, V = 0.159$). The top negative review (29,092 helpfulness votes) cited login failure.
- **Shared Industry Bottlenecks:** Sentiment differences across competing platforms yielded a negligible effect size ($V = 0.053$), proving disruptions stem from shared third-party telecom SMS gateways rather than single-app bugs.
- **Deprioritized Noise:** User complaints regarding notification clutter and in-app advertising were statistically insignificant ($p = 0.219$).

##  Recommendations
- **Diversify Authentication Options:** Implement in-app push verification and biometric fallbacks to eliminate single-point dependencies on cellular SMS gateways.
- **Enhance Fee Transparency:** Integrate real-time pre-transaction fee previews directly into payment confirmation screens.
- **Automate Telemetry Alignment:** Link server uptime metrics and gateway status logs directly to real-time negative sentiment spikes.

## Limitations & Challenges
This analysis relies on keyword-assisted lexical categorization rather than full Transformer-based Aspect-Based Sentiment Analysis (ABSA) models. The severe positive rating skew limits qualitative analysis to the ~15% negative review subset[cite: 3], and scraped reviews lack internal backend telemetry to pinpoint exact root causes.

## 🔗 Project Access
👉 **[View Full Jupyter Notebook & Analysis Code](https://github.com/szmaitra-sudo/Mobile-Financial-App-/blob/main/Mobile_Financial_App.ipynb)**
