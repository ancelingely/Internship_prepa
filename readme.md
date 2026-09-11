# Internship project 
My internship project is part of the APPROCHE(-S) study (CHU Nîmes, department of physical medicine and rehabilitation). The first part of this document describes the study and the second part describes my internship project.

## Project Title: APPROCHE(-S) 

### Objective of the study
Describe predictive Factors for the Success of Rehabilitation Programs in Chronic Low Back Pain. The study is based on activity limitation and associated factors that can predict the success of rehabilitation programs (Psychological, physical, social factors).  

### Methodology
**Population** : 2 groups of patients will be included in the study:
- Group 1: Patients with chronic low back pain who have completed a rehabilitation program 
- Group 2 : Healthy subjects without low back pain (control group)

**Evaluation** : Questionnaires, 3D Movement evaluation (gait, balance, trunck positionning, trunck flexion, lifting), accelerometer

**Data analysis** : movement complexity...

## Interniship project description
### Objective of the internship project
The objective of my internship project is to analyze the accelerometer data collected during the APPROCHE(-S). It is composed of two parts 

**Precise description of motor comportment** : The way in which activity is accumulated or fragmented, temporal organization during the day and week, and eventually the complexity/variability of activity sequences.

**Validation of walking data** : A more practical and methodological section dedicated to walking, a potential basis for a future, more detailed data analysis. We have an ActiGraph worn on the hip for 7 days, but it is necessary to validate precisely what we are able to extract from it regarding walking episodes and certain characteristics of this activity.
Pilot phase followed by an independent validation, using the Qualisys laboratory and force platforms as references, as well as a small semi-ecological course filmed.

#### Data description 
Accelerometer : acceleration + gravitational composante + noise 
Steps : raw signal - quality assesment - preprocessing - 

#### Analysis of accelerometer data
Counts : Counts represent a classical and widely used approach to characterize the volume and intensity of physical activity. However, they have limitations related to their dependence on the ActiGraph algorithm. Raw data potentially allow extracting richer and more comparable metrics. (chatgpt). Counts represent the number of times the acceleration signal crosses a threshold within a given epoch (time window). The algorithm used to calculate counts is proprietary and may vary between different devices and manufacturers. 

Ali Neishabouri et al (1) proposed a method to extract counts from raw accelerometer data, which is implemented in the agcounts python package. The package is available on pypi and can be installed using pip.

**STEP 1 : Understand and be able to use the agcounts package to extract counts from raw accelerometer data.**



## References 
1. Neishabouri A, Nguyen J, Samuelsson J, Guthrie T, Biggs M, Wyatt J, et al. Quantification of acceleration as activity counts in ActiGraph wearable. Sci Rep. 13 juill 2022;12(1):11958. doi:10.1038/s41598-022-16003-x PubMed PMID: 35831446; PubMed Central PMCID: PMC9279376.



