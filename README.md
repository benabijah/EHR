# EHR
Diabetes Progression in Electronic Health Records


## 0. Teaser
The primary goal of this "mini" project is to explore handling electronic health records -- from data ingestion
all the way through analyses. Using synthetic healthcare claims data obtained from the 
[Centers for Medicare & and Medicaid Services](https://data.cms.gov/collection/synthetic-medicare-enrollment-fee-for-service-claims-and-prescription-drug-event), 
we track beneficiaries' progression from being diagnosed with prediabetes to diabetes mellitus with/without complications. 
To do this, we use the assistance of AI tools for the ingestion of our data, and then proceed with statistical 
modeling to help us understand the dynamics involved in diabetes disease progression. (See [Abstract](#1-abstract))


## 1. Why Diabetes Progresson?
Diabetes as a chronic disease often progresses if unattended to. For any given population, if we can estimate the
risks involved at every stage of the progression, as well as identify the various factors that drive these risks,
then we can formulate targeted interventions geared toward preventing diabetes progression or delaying the rate 
of progression. 

Motivated by [Li et al., 2024](https://pubmed.ncbi.nlm.nih.gov/39345707/) and 
[Siriwardhana et al., 2018](https://pubmed.ncbi.nlm.nih.gov/29914451/), we will estimate transition probabilities 
between three states: (1) prediabetes, (2) diabetes mellitus without complications, and (3) diabetes mellitus with
complications -- as well as the average time spent in each state. Although this project uses synthetic data, 
the methods herein may be transferable to real applications.


## 2. Cohort
This project only considers Medicare beneficiaries diagnosed with prediabetes in 2022 and follows them through 
2025 for subsequent diagnoses of higher stages of diabetes. Furthermore, we only include beneficiaries who 
progressed from a lower state to higher ones, without any regression at any point during the followup period.

For example, we exclude a beneficiary with observed states, say, `1,2,1` because they regressed from state `2` to 
state `1` -- instead of remaining in state `2` or even advancing to state `3`. 


## 3. Time of Event
Since this is longitudinal modeling of disease progression, for each beneficiary, the time of diagnoses of 
all other condition(s) -- including comorbidities -- is measured relative to the time they were diagnosed with 
prediabetes. Essentially, we track the duration (in months) from when they were diagnosed of prediabetes to the 
time of diagnoses of the two other states.


## 4. Comorbidities
Comorbidities were measured as time dependent, in the sense that they change with time. For example,
a beneficiary may not have hypertension at the time of prediabetes diagnoses, but may be diagnosed with it,
say, 5 months later even when they are still in the prediabetes state or had advanced to a higher state.


## 5. Abstract
Diabetes is a chronic disease that often progresses from a mild stage to a more complicated one, and eventually 
to other chronic diseases like stroke or kidney failure. Understanding the various driving factors of this 
progression is an important step towards policy implementation to mitigate its effects. In this study, we employ a 
data-driven approach to examine the longitudinal paths of diabetes progression among Medicare members. We will 
analyze synthetic claims data obtained from the Centers for Medicare and Medicaid Services (CMS) from 2022 
through 2025 for a cohort of 1821 prediabetes patients diagnosed of prediabetes in 2022 and followed up for their 
transition to diabetes with(out) complications. Transitions between specific states will be modeled using 
Cox proportional hazards model incorporating demographic factors and other comorbidities. Furthermore, a subgroup 
analysis will be performed to delineate differences in progression by sex and specific age categories.

**Keywords**: *Medicare claims, diabetes, disease progression, survival analysis, multistate models*


