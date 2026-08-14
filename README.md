PROFESSIONAL TECHNICAL REPORT
Job Fraud Analysis
A Data Analytics Case Study on Online Job Posting Fraud
https://drive.google.com/drive/folders/1ybEVAepRV6OqDb8WkSS1lGreDp_rZgEr?usp=sharing

Project attribute

Documented detail

Project type

Collaborative data analytics, fraud-risk analysis and dashboarding project

Dataset
16,000 online job postings from a public Kaggle dataset
Target
Fraud label: 0 = legitimate, 1 = fraudulent
Tools documented
Python, Microsoft Power BI and Microsoft Excel
Primary outputs
Cleaned/engineered analytical dataset, exploratory analysis, dashboards, findings and recommendations
Individual contribution
Analysis observations, recommendations, and preparation of the technical report
Project status
Analysis and dashboard/report deliverables documented as completed; model-development status is not fully documented in the supplied reports


Portfolio positioning: This report documents the full analytical work of the collaborative project. 

<img width="643" height="286" alt="Dashboard 2" src="https://github.com/user-attachments/assets/ec1c407d-c4de-4886-82a5-c9e02d9572d6" />

Analysis done on PowerBI

<img width="622" height="341" alt="Dashboard 1" src="https://github.com/user-attachments/assets/2e5c4c90-f50c-44c3-990b-3c0ba759cb09" />

Analysis done om Excel

1. Project Overview
1.1 Executive Summary
Online recruitment platforms provide an efficient way for employers and candidates to connect, but the same scale and accessibility can be exploited through fraudulent job postings. This project analyses a public dataset of 16,000 job postings to identify patterns associated with fraudulent listings and translate those patterns into practical verification and risk-monitoring recommendations.
The analysis combines structured job-posting metadata with unstructured text attributes, including job title, company profile, description, requirements and benefits. Key dimensions examined include industry, department, employment type, salary class, job function, geographic distribution and company-logo presence. The dataset was cleaned and transformed to support exploratory analysis and modelling-oriented preprocessing, including text standardisation, categorical treatment of missing values, salary extraction, location parsing, text-length feature engineering, combined-text construction and duplicate removal.
The dashboard analysis identified a reported overall fraud rate of 4.48%, 707 fraudulent listings, strong differences between postings with and without company logos, elevated fraud prevalence in particular industries and salary classes, and geographic concentration in major job-market regions. The strongest recurring signals in the supplied analysis were opacity and incomplete metadata—particularly hidden salary information, missing company branding, generic/unknown categories and certain high-risk industry or job-function combinations.
1.2 Problem Addressed
The project addresses the difficulty of distinguishing legitimate online job opportunities from fraudulent listings using observable attributes of a posting. The practical problem is not simply identifying whether fraud exists, but understanding which characteristics, categories and combinations of attributes are associated with elevated fraud risk so that platforms and job seekers can apply more targeted checks.
1.3 Objectives
Identify industries with elevated fraudulent-posting rates.
Assess how fraud prevalence varies across salary classes and salary disclosure status.
Determine which employment types are most associated with fraudulent postings.
Identify job functions with comparatively high fraud prevalence.
Examine the geographic distribution of fraudulent job postings.
Assess the relationship between company-logo presence and fraud rate.
Prepare the raw job-posting data for reliable exploratory analysis and potential machine-learning workflows.
Translate observed patterns into practical recommendations for job platforms, job seekers and policymakers.
1.4 Scope
The documented scope covers data preparation, exploratory analysis, comparative fraud-rate analysis, dashboard visualisation, interpretation of findings and recommendations. The supplied reports also describe preprocessing choices intended to support machine-learning modelling. However, they do not document a completed model, model name, train/test split results, evaluation metrics or model-performance comparison. Accordingly, this portfolio report does not claim a completed predictive model.
1.5 Individual Contribution
This was a collaborative project. The individual contribution documented for portfolio purposes is limited to the work the user has identified: contributing analytical observations, developing/compiling recommendations, and contributing to the technical report. The dashboards and wider project outputs are therefore presented as team outputs rather than as independently produced work.

2. Problem Context
Fraudulent job postings can imitate legitimate recruitment advertisements closely enough to attract applicants, particularly when a listing uses familiar job categories but provides limited information about the employer, compensation or role. The project therefore treats job-posting fraud as a pattern-recognition and data-quality problem: the available metadata and text may contain signals that differentiate fraudulent from legitimate postings, but those signals must be interpreted carefully because legitimate postings can also be incomplete.

2.1 Stakeholder Context

The source report identifies job platforms and recruitment websites, government and regulatory bodies, and the broader recruitment ecosystem as relevant stakeholder groups. The intended value of the analysis is to support stronger verification, greater transparency and better awareness rather than to assert that the analysis alone can eliminate job fraud.

2.2 What Success Means

Job seekers can identify and avoid suspicious listings more effectively.
Employers can use trustworthy recruitment channels with stronger listing verification.
Platforms can use observable risk signals to prioritise listings for review.
Regulators and industry stakeholders can use evidence about recurring fraud patterns to inform monitoring and awareness activities.

3. Data Sources and Dataset

3.1 Source and Dataset Characteristics
The project uses a secondary public dataset retrieved from Kaggle: the Real or Fake Job Posting Prediction dataset. The supplied technical reports describe 16,000 job postings. The dataset combines structured metadata with unstructured text fields and a binary fraud label.
Dataset source: Kaggle – Real or Fake Fake Job Posting Prediction

3.2 Variables Used
Variable group
Fields documented in the reports
Target / outcome
Fraud label / fraudulent indicator
Text fields
Job title, company profile, description, requirements, benefits, final/combined text
Recruitment metadata
Department, employment type, required experience, required education, industry, function
Compensation
Salary range; derived salary value / salary class
Geography
Country, state, city, clean location
Trust / listing signals
Has company logo, has questions, telecommuting
Identifiers / derived measures
Job ID, text length


3.3 Target Definition
The fraud target was validated as a binary variable. A value of 0 represents a legitimate job posting and 1 represents a fraudulent posting. The source reports that the target contained no missing values.

3.4 Quantitative and Categorical Fields
The detailed PDF classifies quantitative measures as including fraudulent, text length, job ID, telecommuting, company-logo presence, questions and salary range, while categorical dimensions include title, department, company profile, description, requirements, benefits, employment type, experience, education, industry, function, final text and geographic fields. For professional analytical terminology, this report treats the fraud label as the target/outcome and the remaining attributes as predictors or descriptive dimensions rather than relying on the original 'dependent/independent values' wording.

4. Pre-Analysis and Analytical Questions

4.1 Initial Dataset Assessment
Initial inspection indicated that the raw dataset could not be interpreted reliably without preprocessing. The source documentation identified widespread missing information across salary, location and company-profile fields; noisy and unstructured text; inconsistent salary and location formats; and duplicate or near-duplicate postings. These issues were treated as analytical risks rather than simply formatting problems.

4.2 Pre-Analysis Expectations
Incomplete job postings could create reputational and user-safety risks and might contain useful fraud signals.
High-volume low-information postings warranted closer inspection.
Lack of salary transparency could be associated with elevated fraud risk, subject to validation.
Certain industries, employment types, countries and job functions could show different levels of fraud prevalence.
Description length could provide a useful differentiating feature.
Company-logo presence could function as a trust-related signal.

4.3 Analysis Questions
Which industries have the highest fraud rates in job postings?
Which countries record the highest number of fraudulent job postings?
How does fraud prevalence vary across salary classes (Low, Medium, High and Unknown)?
What percentage of job postings that hide salary information are fraudulent?
Which employment types are most associated with fraudulent job postings?
Which job functions are most frequently targeted by fraudulent postings?
How does fraud vary between postings with and without company logos?
Which locations contain the largest concentrations of fraudulent postings?


5. Data Preparation and Cleaning
The preprocessing workflow was designed to retain information rather than remove incomplete records indiscriminately. This was particularly important because missing metadata can itself be informative in fraud analysis. The workflow also separated text processing from categorical/metadata processing so that each field type received an appropriate treatment.

5.1 Initial Data Inspection
The dataset was inspected for row and column structure, sample records and data types. This revealed missing values, inconsistent representations and fields requiring transformation.

5.2 Missing-Value Assessment
Missingness was assessed across all columns. Important gaps were identified in location, department, salary range, company profile, required education and required experience. The records were retained rather than discarded because missing information may be associated with fraud risk.

5.3 Target Validation
The fraud target was checked for binary values and confirmed to have no missing entries. It was explicitly treated as numeric, with 0 representing legitimate and 1 representing fraudulent postings.

5.4 Text and Categorical Feature Separation
Text fields included job title, company profile, job description, requirements and benefits. Metadata/categorical fields included location, department, employment type, experience, education, industry and function. This separation enabled different preprocessing strategies.

5.5 Text Standardisation
Missing text values were replaced with empty strings to prevent downstream processing errors. Text was converted to lowercase and unnecessary whitespace was removed.

5.6 Categorical Missing-Value Treatment
Missing categorical values were replaced with the explicit category 'Unknown'. This preserved records and allowed the absence of metadata to remain visible as a potential analytical signal.

5.7 Salary Range Transformation
Salary information was initially stored as free text with varying formats and currencies. The first numeric value in each salary range was extracted and converted to numeric form. Values that could not be reliably converted remained missing rather than being assigned unsupported values.

5.8 Text-Length Feature Engineering
A text-length feature was created by counting the number of words in the job description. The source analysis treats shorter descriptions as a potentially useful fraud indicator because fraudulent listings may contain less detailed content.

5.9 Combined Text Feature
Multiple text fields were merged into a combined text field so that text-based modelling could use information from the job title, company profile, description, requirements and benefits together.

5.10 Location Parsing
The original location field was highly inconsistent. Values were decomposed into country, state and city using comma delimiters. When more than three components were present, the first was treated as country, the second as state and the remaining components were combined as city. Missing components were padded with empty strings.

5.11 Country Standardisation
Two-letter and three-letter country codes were converted to full country names using an international country-reference library. Codes that could not be resolved were retained to avoid corrupting the original information.
5.12 State and City Standardisation
State and city values were cleaned by removing excess whitespace, filling missing values with empty strings and standardising capitalisation to title case.

5.13 Unified Clean Location
A clean_location field was created by combining non-empty city, state and country components into a readable geographic value for analysis and visualisation.

5.14 Removal of Original Location Field
The original unstructured location field was removed after the structured components and clean location field had been created, reducing redundancy in downstream analysis.

5.15 Duplicate Handling
Duplicate postings were identified using identical combined-text content and removed. This reduced redundancy and limited the risk that repeated templates, particularly fraudulent templates, would bias subsequent analysis or modelling.

5.16 Class Distribution Review
The fraud/legitimate distribution was reviewed and found to be heavily imbalanced, with fraudulent postings representing a small minority. The source documentation notes that this should influence modelling strategy and evaluation metrics.

5.17 Final Sanity Checks
The cleaned data was re-evaluated to confirm that text and categorical fields had been handled, engineered features were present, data types were appropriate and the target remained intact and correctly labelled.


6. Data Quality Issues and Limitations
Severe class imbalance
Fraudulent postings form a small minority of the dataset. A model can therefore appear accurate by favouring the majority class, making accuracy alone potentially misleading.
High volume of missing information
Location, department, salary, company profile, education and experience contain substantial missingness. Missingness may be informative, but it also introduces uncertainty.
Unstructured and noisy text
Descriptions vary widely in length, grammar, punctuation and information quality, increasing preprocessing and feature-extraction complexity.
Inconsistent salary information
Salary values are stored as free text with different currencies, ranges, abbreviations and symbols, and many values are missing.
Ambiguous location values
Entries such as Unknown, Remote and incomplete geographic references reduce the reliability of geographic comparisons.
Potential duplicate/template postings
Highly similar or identical postings can cause leakage-like effects if repeated templates appear in both training and evaluation data.
No clear temporal dimension
The dataset does not provide a clear posting/expiration date structure, limiting time-series, trend and seasonality analysis.
Limited ground-truth documentation
The source dataset contains pre-labelled fraud indicators, but the reports do not document how the original labels were assigned.
Overlap between legitimate and fraudulent postings
Legitimate postings can also have short descriptions, missing salary information or remote-work characteristics, creating potential false positives.
Dataset age
The dataset may not represent current recruitment practices or emerging fraud techniques, particularly given changes in remote and online recruitment.
Interpretation caution: The observed relationships should be treated as associations in this dataset, not proof that a single characteristic causes fraud. For example, a missing salary or logo may be a useful risk signal without being sufficient evidence that a posting is fraudulent.


7. Analytical Methodology
The analytical workflow progressed from data-quality assessment to preprocessing, exploratory analysis, comparative fraud-rate analysis and dashboard visualisation. The project used Python for data preparation/analytical processing, Power BI for interactive dashboarding and Excel for additional analysis and dashboard presentation.

7.1 Analytical Workflow
Inspect the raw dataset and identify structural/data-quality issues.
Validate the fraud target and understand class distribution.
Separate text fields from categorical and metadata fields.
Standardise text and categorical values.
Transform salary and location fields into analytical representations.
Engineer text length and combined-text features.
Remove duplicate combined-text records.
Assess fraud prevalence across key categorical and geographic dimensions.
Compare initial expectations with post-analysis findings.
Build dashboard visualisations to communicate patterns and support interpretation.
Translate the strongest observed patterns into prioritised recommendations.

7.2 Analytical Measures and Comparisons
Overall fraud prevalence.
Fraud rate by industry.
Fraud prevalence by salary class.
Fraud rate for salary-disclosed versus salary-hidden postings.
Fraud rate by company-logo presence.
Fraud distribution by employment type.
Fraud rate by job function.
Fraudulent-posting counts by country and location.
Cross-sectional drill-downs combining industry, salary, employment type, geography, logo status and job function.

7.3 Machine-Learning Readiness
The reports describe preprocessing choices as supporting machine-learning modelling, including combined text construction, text-length engineering, target validation, class-imbalance review and duplicate removal. However, the supplied documents do not specify a trained model, algorithm, train/validation/test split, vectorisation method, hyperparameters, evaluation metrics or model results. Those elements are therefore not represented as completed modelling work in this portfolio version.

8. Analysis and Results


8.1 Overall Fraud Profile
Metric
Source-reported result
Interpretive note
Total job listings
16,000
Dataset size stated in the submitted technical report.
Fraudulent listings
707
Count stated in the post-analysis section.
Overall fraud rate
4.48%
Reported by the source; see data-consistency note below.
Salary-hidden postings
65.14%
Shown in the detailed salary-disclosure visual.
Fraud rate among salary-hidden postings
7.34%
Shown in the detailed salary-disclosure visual.
Fraud rate among salary-disclosed postings
3.93%
Shown in the detailed salary-disclosure visual.
Logo-present fraud rate
1.95%
Reported across the dashboard analysis.
Logo-absent fraud rate
14.42%
Reported across the dashboard analysis.


Data-consistency note: The source reports 707 fraudulent listings out of 16,000 and separately reports a 4.48% overall fraud rate. A direct calculation from 707/16,000 gives approximately 4.42%, so the exact overall rate should be validated against the underlying dataset/dashboard before publication as a definitive KPI. The detailed salary chart supports 65.14% hidden salary, 7.34% fraud rate among hidden-salary postings and 3.93% among disclosed-salary postings; some narrative passages in the source use 3.93% and 7.34% inconsistently.

8.2 Fraud by Industry
Industry analysis identified Ranching as the most extreme category, with a reported 100% fraud rate. Military, Oil & Energy, Animation and Accounting were also highlighted as elevated-risk industries. The more detailed drill-down analysis reported Accounting at 36.09% fraud, with substantial variation by salary class and employment type.

Figure 1. Fraud rate by industry. Ranching is shown at approximately 100%, followed by Military, Oil & Energy, Animation and Accounting.

8.3 Department-Level Fraud
The source analysis found that the largest number of fraudulent postings fell into the Unknown department category (531). Among identifiable departments, Engineering and Oil & Energy were highlighted. The recommendation arising from this result was to review listings without a department and apply additional scrutiny to engineering and energy-related roles.
8.4 Fraud by Salary Class
Salary class analysis showed the strongest fraud prevalence in the Low category, reported at approximately 75% in the detailed drill-down. The dashboard also presents Low salary as accounting for roughly 50% of fraudulent postings by share. The High category was reported at 26.67% fraud prevalence in the detailed drill-down and was the least fraud-prone of the highlighted classes.

Figure 2. Fraud prevalence across salary classes. Low salary has the highest displayed fraud rate, while High salary has the lowest.

Figure 3. Fraudulent postings by salary class in the Excel dashboard. Unknown is the largest count category, followed by Low, Medium and High.

8.5 Salary Disclosure and Fraud
Salary disclosure produced one of the clearest risk signals in the dashboard analysis. The detailed visual reports a 7.34% fraud rate among postings with hidden salary information versus 3.93% among postings with disclosed salary information. The same visual indicates that approximately 65.14% of postings hide salary information. The analysis therefore treated salary transparency as a useful screening signal, while recognising that hidden salary information alone is not proof of fraud.

Figure 4. Salary disclosure versus hidden salary. The visual reports 7.34% fraud for hidden-salary postings and 3.93% for salary-disclosed postings; the hidden-salary segment is labelled 65.14%.


8.6 Fraud by Employment Type
The source material contains two complementary views of employment type. In the detailed dashboard analysis, temporary and part-time categories show high fraud-rate associations, while the post-analysis narrative emphasises full-time postings as the largest share of fraudulent cases. The Excel dashboard reports 429 fraudulent full-time postings, followed by 163 Unknown, 70 Part-time, 33 Contract, 10 Other and 2 Temporary. This distinction matters: a category can have a high fraud rate but a low total number of fraudulent records if relatively few postings exist in that category.

Figure 5. Fraudulent postings by employment type (Excel dashboard). Full-time has the largest count, followed by Unknown and Part-time.


8.7 Fraud by Job Function
Job-function analysis identified Other, Administrative, Project Management and Management among the highest-risk categories in the detailed fraud-rate comparison. Engineering and Customer Service showed moderate risk, while Accounting/Auditing was lower on the displayed fraud-rate chart. The detailed drill-down reported Project Management at 66.67% fraud and Administrative at 80.00% fraud.

Figure 6. Fraud rate by job function. Other and Administrative are among the highest displayed categories, with Project Management and Management also elevated.

Figure 7. Top fraudulent job functions by count in the Excel dashboard. Unknown, Engineering and Administrative lead the displayed counts.


8.8 Company Logo Presence
Company-logo presence produced one of the strongest single differences in the analysis. Postings with a company logo were reported to have a 1.95% fraud rate, compared with 14.42% for postings without a logo. The source interprets this as evidence that visual company branding can operate as a trust signal, while the professional interpretation is more cautious: logo presence is an associated screening feature, not independent proof of legitimacy.

Figure 8. Reported fraud rates with and without company logos: 1.95% with a logo versus 14.42% without.

Figure 9. Company-logo presence in the Excel dashboard. The dashboard records the number of postings with and without logos.


8.9 Geographic Distribution
Geographic analysis showed that fraudulent postings are globally distributed but concentrated in major job-market regions. The Power BI map highlights North America, especially the United States, with additional activity across parts of Europe and Asia. The detailed report also notes the United States as the leading country by fraudulent-posting count in the dashboard analysis, with Canada and other countries appearing in the broader distribution.

Figure 10. Geographic distribution of fake postings by country in the Power BI dashboard.

Figure 11. Geographic visual used in the analysis to show where fraudulent job postings are concentrated.


8.10 Top Industries and Fraud Counts
The Excel dashboard provides a complementary count-based view. Unknown industry categories lead the displayed fraudulent-posting counts, followed by Oil & Energy, Accounting, Hospital & Health Care and other industries. This count-based view complements the fraud-rate analysis: high counts do not necessarily mean the highest rate, because the denominator differs across industries.

Figure 12. Top 10 industries by number of fake postings in the Excel dashboard.


9. Cross-Sectional Findings and Drill-Down Analysis
The detailed PDF extends the dashboard analysis by examining how fraud changes when dimensions are considered together. These drill-downs are retained because they demonstrate the project's analytical depth beyond single-variable charts.

9.1 Ranching
Reported industry fraud rate: 100%.
The Unknown salary class was reported at 36.18% fraud in the drill-down, with 100% highlighted for the relevant interaction.
Full-time employment was identified as the prominent employment type in the drill-down, with a reported association value of 0.39 and a highlighted value of 1.00.
The United States accounted for 1 fraudulent posting in the reported geographic drill-down.
The analysis reported 100% fraud for the salary-hidden interaction and highlighted Engineering as a job function with 52.59% fraud, with 100% highlighted for the relevant interaction.
9.2 Accounting
Reported industry fraud rate: 36.09%.
Low-salary postings showed 75% fraud prevalence, with a 76.67% highlighted value in the drill-down.
Medium salary fraud was reported at 43.90%, with 41.67% highlighted; Unknown salary was reported at 36.18%, with 23.53% highlighted.
Temporary employment showed an association value of 1.00; Part-time 0.53; Full-time 0.39; and Other 0.29, with corresponding highlighted values reported in the source.
Geographic drill-downs recorded fraudulent postings in Canada, India and Australia.
Fraud rate with a logo was reported at 10.91%, compared with 53.85% without a logo.
The source reports 28.74% fraud among the relevant salary-hidden postings and 71.26% for the salary-disclosed comparison, alongside the associated posting shares.
Administrative showed an 80% function fraud rate; Customer Service 41.67%; Accounting/Auditing 26.00%.

9.3 Low Salary Class
Reported salary-class fraud prevalence: 75.00%.
Accounting was reported at 76.67% industry fraud and Oil & Energy at 50.00%.
Other and Part-time employment categories were reported with a fraud association of 1.00 each; Full-time was 0.67.
Canada recorded 2 fraudulent postings and Australia 3 in the reported geographic drill-down.
Fraud rate with a logo was 30.00%; without a logo 94.45%.
The source reports 100% of the relevant hidden-salary postings as fraudulent in this drill-down.
Administrative and Finance were reported at 100% function fraud, Customer Service 75%, Unknown 66.67%, and Accounting/Auditing 55.56%.

9.4 High Salary Class
Reported salary-class fraud prevalence: 26.67%.
Oil & Energy was reported at 33.33% industry fraud.
Full-time employment had a reported fraud association of 0.27.
The United States recorded 7 fraudulent postings and the United Kingdom 1 in the reported geographic drill-down.
Fraud rate with a logo was 25.93%; without a logo 33.33%.
The source reports 100% of the relevant hidden-salary postings in this drill-down, with 26.67% fraudulent.
Other and Unknown functions were each reported at 100% function fraud.

9.5 Project Management
Reported fraud rate: 66.67%.
Military was reported at 100% industry fraud within this function; Oil & Energy at 63.64%.
Medium salary showed 100% fraud prevalence; Unknown salary 63.64%.
Unknown employment type had an association value of 1.00; Full-time 0.67; Contract 0.50.
The United States recorded 8 fraudulent postings in the reported geographic drill-down.
Fraud rate with a logo was 55.56%; without a logo 100%.
The source reports 38.89% fraud among the relevant hidden-salary postings and 61.11% in the salary-disclosed comparison.

9.6 Administrative
Reported fraud rate: 80.00%.
Animation was reported at 100% industry fraud, Oil & Energy at 80.00%, and Accounting at 78.79%.
Low salary was reported at 100% fraud in the drill-down; Unknown 70.83%; Medium 66.67%.
Other employment type had an association value of 1.00; Full-time 0.79; Part-time 0.75.
The United States recorded 31 fraudulent postings in the reported geographic drill-down, with Greece, Germany and the United Kingdom also represented.
Fraud rate with a logo was 30.00%; without a logo 96.67%.
The source reports 43.04% fraud among the relevant hidden-salary postings and 56.96% for the salary-disclosed comparison.

10. Pre-Analysis Expectations vs. Post-Analysis Findings
Dimension
Initial expectation
Post-analysis result
Assessment
Overall fraud
Fraud might be a majority/high-impact problem.
4.48% was reported across 16,000 jobs; 707 fraudulent listings were reported.
Expectation not matched; fraud is a minority but material.
Industry
Certain industries and Unknown/Other categories might carry higher risk.
Ranching, Military, Oil & Energy, Animation and Accounting were highlighted.
Partially confirmed; specific high-risk sectors became clearer.
Employment type
Temporary, part-time and freelance roles might be riskier than full-time.
Full-time represented the largest count of fraudulent postings; temporary had the highest displayed rate/association in one dashboard view.
Initial expectation only partially supported; rate and count tell different stories.
Salary
Hidden or extreme salary levels might be associated with fraud.
Low salary had the highest prevalence; hidden salary also showed elevated fraud rate.
Partially confirmed; low/unknown pay was more prominent than high pay.
Job function
Generic functions such as Admin/Customer Service/Unknown might be higher risk.
Other, Administrative, Project Management and Management were elevated.
Largely confirmed.
Logo
No-logo postings would likely be riskier.
1.95% with logo vs. 14.42% without.
Strongly confirmed.
Geography
Fraud might cluster in high-volume markets.
North America, especially the U.S., plus parts of Europe and Asia showed higher concentrations.
Broadly confirmed.
Combined risk profile
Multiple weak signals together might identify high-risk listings.
Hidden/low salary, no logo, generic function and high-risk industry repeatedly appeared together.
Supported by the dashboard analysis; not a validated predictive score.


11. Technical Implementation and Visual Analytics

11.1 Python
Python was documented as the processing and analytical tool. The workflow attributed to the Python stage includes dataset inspection, missing-value assessment, target validation, text standardisation, categorical treatment, salary parsing, text-length feature engineering, combined-text construction, location standardisation, duplicate removal and class-distribution review.
11.2 Power BI
Power BI was used to communicate the analytical findings through an interactive dashboard. The Word report documents interactive visualisations, key metrics/KPIs, dynamic labels and annotations, filters, slicers and drill-down capabilities. The dashboard focused on industry fraud rate, salary-class prevalence, employment-type association, salary disclosure, job-function risk and geographic distribution.

Figure 13. Power BI dashboard. The dashboard consolidates the major fraud KPIs and analytical views.

11.3 Microsoft Excel
Excel was used for detailed analysis and an additional dashboard view incorporating charts and pivot-table-oriented analysis. The documented Excel outputs include fraudulent postings by employment type, company-logo presence, salary class, country, job function and top industries.

Figure 14. Excel dashboard documented in the submitted report.

11.4 Visualisation Inventory
Analytical question
Visualisation documented
Primary purpose
Which industries have the highest fraud rates?
Bar chart
Compare fraud prevalence across industries.
How does fraud vary by salary class?
Column/bar chart
Compare Low, Medium, High and Unknown salary categories.
Which employment types are associated with fraud?
Bar chart
Compare employment-type fraud associations and counts.
What proportion of hidden-salary postings are fraudulent?
Doughnut chart
Compare salary disclosure status and associated fraud rates.
Which job functions are most frequently targeted?
Bar chart
Compare function-level fraud prevalence/counts.
Which countries have the highest fraud counts?
Map
Show geographic concentration.
Does logo presence relate to fraud?
KPI/comparison visual and donut
Compare fraud rates and logo availability.
Which industries have the most fake postings?
Top-10 bar chart
Show count-based concentration by industry.



12. Insights, Implications and Recommendations
The recommendations below preserve the substantive recommendations in the supplied reports while organising them by stakeholder and risk theme. They are presented as evidence-informed actions rather than guaranteed outcomes.

12.1 Recommendations for Job Platforms
Enhance employer verification by requiring evidence such as business registration/licensing, website validation or other employer-verification checks before listings are approved.
Use logo verification or verified-company indicators as an additional screening signal, given the large difference reported between postings with and without logos.
Improve fraud-detection workflows by prioritising postings that combine multiple observed risk signals, including hidden salary information, no company logo, generic/Unknown function or department, and elevated-risk industries.
Monitor geographic concentrations and apply additional review to listings originating from high-volume/high-risk regions identified through platform data.
Promote salary transparency and flag listings without salary information for additional review rather than treating missing salary as automatic proof of fraud.
Highlight verified postings so job seekers can distinguish listings that have passed platform checks.
Provide users with practical fraud-detection guidance and encourage reporting of suspicious listings to improve the platform's feedback loop.

12.2 Risk-Specific Recommendations
Risk area
High-priority action
Medium/longer-term action
Ranching
Apply strict verification to all postings; verify employer identity and scrutinise hidden-salary and relevant engineering listings.
Monitor the pattern over time and develop targeted awareness for job seekers.
Accounting
Review temporary/part-time and low-salary postings; scrutinise no-logo and Administrative listings.
Use periodic audits and industry/regulatory awareness around salary transparency.
Low salary
Increase review of low-salary postings and scrutinise no-logo, Administrative and Finance listings.
Use ongoing analytics and job-seeker education to monitor recurring patterns.
High salary
Review Oil & Energy and relevant full-time/no-logo listings; validate salary claims.
Continue monitoring rather than treating high salary as the primary fraud signal.
Project Management
Verify Military and Oil & Energy listings and scrutinise no-logo and medium/Unknown salary combinations.
Monitor contract roles and geographic concentration.
Administrative
Verify Animation, Oil & Energy and Accounting listings; scrutinise no-logo and low/Unknown salary postings.
Monitor part-time/medium-salary patterns and develop targeted alerts.


12.3 Recommendations for Job Seekers

Scrutinise listings that provide little employer information or lack a company logo.
Treat vague salary information as a reason to verify the employer rather than as automatic evidence of fraud.
Research the employer independently through its official website and reputable professional sources before sharing sensitive information.
Prefer recruitment platforms with visible verification and reporting mechanisms.
Report suspicious listings so platforms can investigate and protect other applicants.
Be particularly cautious when multiple risk signals occur together, such as a generic role, hidden/low salary, missing logo and limited employer information.
12.4 Recommendations for Policymakers and Regulators
Strengthen penalties and enforcement mechanisms for fraudulent online job advertising.
Encourage information sharing between regulators and recruitment platforms to improve fraud detection.
Support public awareness campaigns on common job-fraud indicators.
Promote standards that improve transparency and employer verification in online recruitment.

13. Project Outputs and Deliverables

Processed job-posting dataset with cleaned text and categorical fields.
Structured geographic fields and unified clean-location representation.
Derived salary representation and salary-class analysis.
Text-length and combined-text features.
Exploratory fraud analysis across industry, salary, employment type, function, geography and logo presence.
Power BI interactive dashboard with KPIs, filters/slicers and analytical visuals.
Excel dashboard and supporting chart-based analysis.
Analytical observations and recommendations.
Technical report documenting methodology, results, insights, limitations and recommendations.

14. Challenges and Limitations of the Analysis

The main analytical challenge was the combination of severe class imbalance, missing metadata, noisy text and inconsistent geographic/salary representations. The preprocessing workflow reduced these issues but did not remove the underlying uncertainty. In particular, the dataset's pre-existing labels, lack of a clear time dimension and age of the dataset limit how confidently the findings can be generalised to current job-market fraud.
A second limitation is interpretive: several risk indicators are associated with fraud but are not exclusive to fraudulent postings. A legitimate employer may omit a salary, use a remote location, have no uploaded logo or provide a short description. The analysis therefore supports prioritised review and risk screening rather than automatic rejection based on any single attribute.

15. Project Status and Future Development

The supplied documentation demonstrates a completed analytical/reporting workflow and two dashboard outputs. The individual contribution identified for this portfolio is completed: observations, recommendations and technical report work. Because the supplied reports do not contain model-training results, predictive-model performance should be treated as an area for future development rather than a completed deliverable.

15.1 Recommended Future Development

Build and document a reproducible fraud-classification model using the engineered text and metadata features.
Use imbalance-aware evaluation, prioritising precision, recall, F1-score, PR-AUC or other appropriate metrics rather than relying on accuracy alone.
Use leakage-resistant train/test splitting, particularly because duplicate or template-based postings can inflate performance.
Document the text vectorisation approach and compare suitable text-classification methods.
Introduce a time dimension if newer data becomes available to evaluate changes in fraud patterns.
Validate model performance on newer or independently labelled job postings.
Develop a transparent risk-scoring framework that combines multiple signals while preserving human review.
Track dashboard KPIs over time when temporal data becomes available.

16. Conclusion

The job-fraud analysis demonstrates how a mixed structured-and-text dataset can be transformed into an interpretable fraud-risk analysis through systematic cleaning, feature engineering, exploratory analysis and dashboard visualisation. Across the documented results, fraud was not uniformly distributed: the analysis highlighted particular industries, salary categories, employment types, job functions, geographic markets and listing characteristics as areas of elevated risk.
The strongest recurring signals were associated with transparency and specificity. Postings without company logos showed a reported 14.42% fraud rate compared with 1.95% for postings with logos, while hidden-salary postings showed a reported 7.34% fraud rate compared with 3.93% for salary-disclosed postings. Ranching was the most extreme industry example in the detailed analysis, while Administrative and Project Management were among the elevated job-function categories.
The project therefore provides a practical basis for prioritised verification rather than a simplistic rule that any one feature identifies fraud. Its next logical stage would be to validate the observed patterns with a reproducible predictive model, stronger ground-truth documentation and more recent time-based data.

17. Information Requiring Validation or Additional Input

1. Overall fraud-rate inconsistency: The report states 707 fraudulent listings out of 16,000 and also reports a 4.48% overall fraud rate. 707/16,000 calculates to approximately 4.42%. The final portfolio KPI should be validated against the underlying data/dashboard.
2. Salary-disclosure wording: Some narrative sections state that 3.93% of postings hide salary information, while the detailed visual labels the hidden-salary share as 65.14%, with 7.34% fraud among hidden-salary postings and 3.93% among disclosed-salary postings. The visual is internally more coherent, but the underlying dashboard/data should be checked.
3. Employment-type interpretation: The detailed employment-type visual shows very high fraud-rate association for Temporary, while the Excel dashboard shows Full-time as the largest number of fraudulent postings (429). The final portfolio should distinguish fraud rate from fraud count, as this report does.
4. Modelling status: The reports repeatedly reference machine-learning modelling/readiness, but no algorithm, train/test split, vectorisation method, model metrics or model results are documented. Please confirm whether a model was actually trained and evaluated.
5. Exact software workflow: Python, Power BI and Excel are explicitly documented. If specific Python libraries, notebooks, Power BI data-modeling steps, DAX measures or Excel transformations were used and should be credited, they need to be supplied separately.
6. Individual contribution detail: The report now reflects the contribution stated by the user: observations, recommendations and technical report work. If specific charts, sections or analyses were personally authored, those can be added to make the contribution statement more granular.
7. Dashboard versions: The supplied Word report contains both Power BI and Excel dashboard documentation. If there are final dashboard files/links or updated versions after submission, they should replace placeholders in the GitHub/portfolio materials.
Appendix A. Source-Derived Technical Notes
The following technical details were retained from the supplied reports because they materially document the analytical process: missing text was replaced with empty strings; categorical missing values were represented as 'Unknown'; salary extraction used the first numeric value in the salary-range field; location strings were split into country/state/city; country codes were standardised using an international country reference library; state/city formatting was normalised; clean_location was created; identical combined-text duplicates were removed; class imbalance was reviewed; and final sanity checks were performed.

The project documentation also identifies job ID, telecommuting, company-logo presence and questions among quantitative/binary analytical fields and includes text length as a derived measure. These fields should remain available in the project repository if the corresponding cleaned dataset and notebook are included.


Appendix B. Reference

Public dataset: Kaggle – Real or Fake Fake Job Posting Prediction

