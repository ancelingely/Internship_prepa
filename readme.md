# Internship project 
My internship project is part of the APPROCHE(-S) study (CHU Nîmes, department of physical medicine and rehabilitation). The objective of this sudy is to describe predictive factors for the success of rehabilitation programs in chronic low back pain. The study is based on activity limitation and associated factors that can predict the success of rehabilitation programs (psychological, physical, social factors). Evaluation is based on questionnaires, 3D movement evaluation (gait, balance, trunk positioning, trunk flexion, lifting), and accelerometer data.

The project is divided into two parts (described below) :
    - 1 : Precise description of motor comportment : 
    - 2 : Validation of walking data 

## 1 Description of motor comportment
**Objective** : Describe the way in which activity is accumulated or fragmented, temporal organization during the day and week, and eventually the complexity/variability of activity sequences.

### Reference framework 
**LBP and physical activity** : Physical activity is a key factor in management of CLBP. A prospective study on a 71 600 subjects cohort (UK biobank) showed that moderate physical activity and a 60 min/day duration was associated with a lower risk of developing CLBP (1). But, there is a lack of knowledge regarding the distribution of physical activity in patients with CLBP, and the way in which it is accumulated or fragmented.

### Data description 
Accelerometer WGT3-X BT : acceleration + gravitational composante + noise 
Steps : raw signal - quality assesment - preprocessing - 

### Analysis of accelerometer data
#### Wearable-specific indicators of PA behavior (WIPAB)** ?
**Counts** are the most commonly used metric. It is derived from the raw acceleration signal using a proprietary algorithm. However, this method has limitations related to its dependence on the ActiGraph algorithm. Raw data potentially allow extracting richer and more comparable metrics. 

**ENMO** provides a continuous measure of movement intensity derived from raw triaxial accelerometer data (5). Beyond simply calculating the average ENMO over a day, its distribution can be described using percentiles (e.g., P25, P50, P75, P90), which indicate the range and intensity of movement performed by an individual. However, percentiles do not provide information about the temporal organization of activity. To go further, the sequence of ENMO values over time can be studied to determine how activity is accumulated, fragmented, and organized, for example by examining transitions between different intensity levels, bout duration, or the regularity and complexity of activity sequences.

Other methods exists, divided into 3 categories : activity intensity distribution (intensity gradient, MX metric), activity accumulation (power law exponent alpha, median bout lenght, Proportion of total time accumulated in bouts longer than x, Gini index), and temporal correlation and regularity (Scaling exponent alpha, Autocorrelation coefficient at lag k, Fourier analysis, sample entropy, Lempel-Ziv complexity, Permutation Lempel-Ziv complexity, Symbolic dynamics).(4)

## 2 Validation of walking data
A more practical and methodological section dedicated to walking, a potential basis for a future, more detailed data analysis. We have an ActiGraph worn on the hip for 7 days, but it is necessary to validate precisely what we are able to extract from it regarding walking episodes and certain characteristics of this activity.
Pilot phase followed by an independent validation, using the Qualisys laboratory and force platforms as references, as well as a small semi-ecological course filmed (BORIS).

### Reference framework
Activity classification can be done using several methods. Previous study used actigraph to classify different types of physical activity : walking, standing, stair climbing, running, cycling, lying down... The classification was based on three different method classifier : Rule base/cut-point, traditionnal machine learning (decision trees, random forests...), deep learning (CNN, RNN...). Validity was assessed using video - synchronised ground truth, other ground truth, K-folp / loso. Codes are available on github for 16 of these studies. 


### 


## References 
1. Zhu Y, Liu D, Yin X, Wang J, Zhang TJ, Wu N. Accelerometer-measured intensity-specific physical activity, genetic susceptibility, and back pain risk: a UK Biobank cohort study. Spine J. juin 2026;26(6):1070‑82. doi:10.1016/j.spinee.2025.10.021 PubMed PMID: 41106605.

2. Neishabouri A, Nguyen J, Samuelsson J, Guthrie T, Biggs M, Wyatt J, et al. Quantification of acceleration as activity counts in ActiGraph wearable. Sci Rep. 13 juill 2022;12(1):11958. doi:10.1038/s41598-022-16003-x PubMed PMID: 35831446; PubMed Central PMCID: PMC9279376.

3. Sadeghi Janbahan K, Espin-Garcia O. Methods for classifying physical activities using accelerometer data: a scoping review. NPJ Digit Med. 6 mai 2026;9(1):534. doi:10.1038/s41746-026-02694-3 PubMed PMID: 42091626; PubMed Central PMCID: PMC13357583.

4. Backes A, Gupta T, Schmitz S, Fagherazzi G, van Hees V, Malisoux L. Advanced analytical methods to assess physical activity behavior using accelerometer time series: A scoping review. Scand J Med Sci Sports. janv 2022;32(1):18‑44. doi:10.1111/sms.14085 PubMed PMID: 34695249; PubMed Central PMCID: PMC9298329.

5. van Hees VT, Gorzelniak L, Dean León EC, Eder M, Pias M, Taherian S, et al. Separating movement and gravity components in an acceleration signal and implications for the assessment of human daily physical activity. PLoS One. 2013;8(4):e61691. doi:10.1371/journal.pone.0061691 PubMed PMID: 23626718; PubMed Central PMCID: PMC3634007.

