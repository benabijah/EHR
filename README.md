# EHR
Diabetes Progression in Electronic Health Records


## Content
- [0. Teaser](#0-teaser)
- [1. Why Diabetes Progresson?](#1-why-diabetes-progresson)
- [2. Cohort](#2-cohort)
- [3. Time of Event](#3-time-of-event)
- [4. Comorbidities](#4-comorbidities)
- [5. Abstract](#5-abstract)


## 0. Teaser
The primary goal of this "mini" project is to explore handling electronic health records -- from data ingestion
all the way through analyses. Using synthetic healthcare claims data obtained from the 
[Centers for Medicare & and Medicaid Services](https://data.cms.gov/collection/synthetic-medicare-enrollment-fee-for-service-claims-and-prescription-drug-event), 
we track beneficiaries' progression from being diagnosed with prediabetes to diabetes mellitus with/without complications. 
To do this, we use the assistance of AI tools for the ingestion of our data, and then proceed with statistical 
modeling to help us understand the dynamics involved in diabetes disease progression. (See [Abstract](#5-abstract))


## 1. Why Diabetes Progresson?
Diabetes as a chronic disease often progresses if unattended to. For any given population, if we can estimate the
risks involved at every stage of the progression -- as well as identify the various factors that drive these risks --
then we can formulate targeted interventions geared toward preventing its progression or, possibly, delaying the rate 
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

For example, we exclude beneficiaries with observed states, say, `1,2,1` because they regressed from state `2` to 
state `1` -- instead of remaining in state `2` or even advancing to state `3`. 


## 3. Time of Event
Since this is a longitudinal modeling of disease progression, for each beneficiary, the time of diagnoses of 
all other condition(s) -- including comorbidities -- is measured relative to the time they were diagnosed with 
prediabetes. Essentially, we track the duration (in months) from when they were diagnosed of prediabetes to the 
time of diagnoses of the two other states/comorbidities.


## 4. Comorbidities
Comorbidities were measured as time dependent, in the sense that they vary with time. For example,
a beneficiary may not have hypertension at the time of prediabetes diagnoses, but may be diagnosed with it,
say, 5 months later even when they are still with prediabetes or had advanced to a higher state.
Also, we limit comorbidities to the same indexing time in order to align all beneficiaries at a 
comparable starting point, ie., time of first prediabetes diagnosis in 2022.


## 5. Abstract
Diabetes is a chronic disease that often progresses from a mild stage to a more complicated one. Understanding the various driving factors of this progression is an important step towards policy implementation to mitigate its effects. In this project, we employ a data-driven approach to examine the longitudinal paths of diabetes progression among Medicare members. We analyze synthetic claims data obtained from the Centers for Medicare and Medicaid Services (CMS) from 2022 through 2025 for a cohort of 3,172 prediabetes patients diagnosed of prediabetes in 2022 and followed up for their transition to diabetes mellitus with(out) complications. Transitions between specific states is modeled using continuous-time multi-state models incorporating demographic factors and other comorbidities. Furthermore, we conduct subgroup analysis to delineate differences in progression by sex and specific age categories. Most prediabetic patients develop diabetes with complications without being diagnosed of diabetes without complications. Obesity, hypertension, and heart disease/failure are some of the factors that significantly impact the risk of diabetes progression. Additionally, males and older adults have higher chances of progression than females and younger adults. We observe higher risks for obese females and obese older adults. On the other hand, higher risks are associated with males living with hypertension, heart disease/failure, alcohol disorders, and depressive disorders.


**Keywords**: *Medicare, diabetes, disease progression, survival analysis, multistate models*


