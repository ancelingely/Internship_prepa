# Internship project 
My internship project is part of the APPROCHE(-S) study (CHU Nîmes, department of physical medicine and rehabilitation). The objective of this sudy is to describe predictive factors for the success of rehabilitation programs in chronic low back pain. The study is based on activity limitation and associated factors that can predict the success of rehabilitation programs (psychological, physical, social factors). Evaluation is based on questionnaires, 3D movement evaluation (gait, balance, trunk positioning, trunk flexion, lifting), and accelerometer data.

The project is divided into two parts (described below) :
    - 1 : Precise description of motor comportment : 
    - 2 : Validation of walking data 

## 1 Description of motor comportment
From raw accelerometer data over 7 days to a multi-scale characterization of motor behavior and walking in real-life settings.

### Reference framework 
**LBP and physical activity** : Physical activity is a key factor in management of CLBP. A prospective study on a 71 600 subjects cohort (UK biobank) showed that moderate physical activity and a 60 min/day duration was associated with a lower risk of developing CLBP (1). But, there is a lack of knowledge regarding the distribution of physical activity in patients with CLBP, and the way in which it is accumulated or fragmented.

**Problematic** :  What can be described in a defensible way from 7 days of raw accelerometry at the hip?

**Objective** : Describe the way in which activity is accumulated or fragmented, temporal organization during the day and week, and eventually the complexity/variability of activity sequences.

**2 ways** : 

    - Whole week movement behavior : 
        Question : How does the person organize his/her whole motor behavior over the week?
        Analysis level : Sujet / jour / séquences d’états
        Ouput : volume, intensity, accumulation, fragmentation, temporality, repertoire/complexity, data-driven states

    - free living gait. 
        Question : when does the person walk, how much, in which contexts, and how is his/her gait organized?
        Analysis level : Sujet / jour / walking bout / foulée   
        Outuputs : Walking bouts, cadence, stride timing, macro-gait, regularity/spectral, SampEn, RQA, HKp, LDS/ACI, DFA conditionnel.

### Data description 
Accelerometer WGT3-X BT : acceleration + gravitational composante + noise 
Sampling frequency : 60 Hz ?
Duration : 7 days 
Epochs = 5 sec ?

### Analysis of accelerometer data
#### Preprocessing 

The processing of raw accelerometer data will follow several main steps. First, the raw triaxial acceleration signals (X, Y and Z) will be extracted from the ActiGraph files and checked for data quality and non-wear periods. The signals will then be calibrated to correct for potential measurement biases and, if required, filtered (not ENMO and MAD (6) and resampled according to the selected processing pipeline. 

Two open-source approaches can be considered for the pre-processing of the raw accelerometer data: **actipy**, a Python-based toolbox that provides access to ActiGraph raw data and includes gravity-based calibration and signal processing, and **GGIR**(7), an R package widely used for processing raw accelerometer data and implementing automatic calibration.

#### Wearable-specific indicators of PA behavior (WIPAB)** ?
Counts are the most commonly used metric. It is derived from the raw acceleration signal using a proprietary algorithm. However, this method has limitations related to its dependence on the ActiGraph algorithm. Raw data potentially allow extracting richer and more comparable metrics. 

**A. Exposition / quantité**
How much and at what intensity does the person move?
ENMO, MAD, intensity gradient, MX metrics,temps par niveaux d’intensité.

ENMO : Euclidean Norm Minus One (6), 
    A measure of acceleration intensity derived from raw triaxial accelerometer data. It is calculated by taking the square root of the sum of the squares of the three axes, subtracting 1g (the gravitational component), and setting negative values to zero. ENMO provides a continuous measure of movement intensity, allowing for the assessment of physical activity levels throughout the day. 

$$
ENMO = \max(\sqrt{x^2 + y^2 + z^2} - 1g, 0)
$$

    Results are expressed in milligravity (mg) units, where 1 mg = 0.001 g.

    For the main analysis, the ENMO calculation will be implemented directly in **Python** in order to maintain control and transparency over each step of the computation. The resulting ENMO values will then be compared with those obtained using **GGIR in R** on the same raw ActiGraph data. This comparison will provide a reference check for the Python implementation and help assess the consistency and reproducibility of the processing pipeline.

    An epoch can be defined to aggregate the ENMO values over a specific time window (e.g., 1 second, 1 minute) to facilitate further analysis and interpretation of physical activity patterns.It is calculated as the average of the ENMO values within the epoch.
   
    The ENMO values can be used to classify physical activity into different intensity levels (e.g., sedentary, light, moderate, vigorous) based on established cut-points or thresholds.

MAD : Mean Absolute Deviation (6), 
    A measure of the average absolute difference between each data point and the mean. It is used to assess the variability of the acceleration signal. It is calculated by taking the absolute difference between each data point and the mean, summing these differences, and dividing by the total number of data points. MAD provides insight into the variability of movement intensity over time.

$$
MAD = \frac{1}{n} \sum_{i=1}^{n} \left|x_i - \bar{x}\right|
$$


Intensity gradient : 
    A measure that describes the distribution of physical activity intensity across different levels, providing insight into how much time is spent at various intensities. It necessarily requires a continuous measure of intensity such as ENMO. The intensity of each epoch is calculated, and the time spent at each intensity level is determined. The intensity gradient is then derived by plotting the cumulative time spent at each intensity level against the corresponding intensity values. 
    
    The gradient (slope) of this regression describes the distribution of activity intensity: a more negative gradient indicates that time is more strongly concentrated at lower intensities, whereas a less negative gradient indicates a more even distribution of time across the intensity spectrum. 

    Rather than classifying physical activity using predefined intensity cut-points, the Intensity Gradient describes the continuous relationship between activity intensity and the time accumulated at each intensity.

Exemple : 
| Participant | Typical activity pattern | ENMO | MAD | Intensity Gradient (IG) |
|---|---|---|---|---|
| **Older active adult** | Very active throughout the day, with many low-intensity movements and short trips | Could be similar to the other participants | **Relatively low** if movements are regular and smooth | **More negative** — most time is accumulated at low intensities |
| **30-year-old office worker** | Mostly sedentary during working hours, followed by ~2 h of vigorous exercise | Could be similar to the other participants | **Variable**, depending on the activity | **Less negative** — more time is accumulated at higher intensities |
| **Delivery worker** | Frequent transitions, walking, carrying parcels and short periods of faster movement | Could be similar to the other participants | **Relatively high** due to frequent changes in acceleration | **Less negative** — activity is distributed across a wider range of intensities |

**B. Accumulation / fragmentation** 
Comment le mouvement et les périodes de faible mouvement sont-ils accumulés ? Durées de bouts, proportion en bouts longs, fragmentation, transitions.

**C. Organisation temporelle**
Quand l’activité survient-elle et à quel point lepr ofil est-il stable d’un jour à l’autre ?
Profils horaires, variabilité interjour, weekday/weekend, similarité de profils.

**D. Répertoire / complexité** 
Combien d’états différents sont utilisés et comment s’enchaînent-ils ?
Occupancy, entropies, Lempel-Ziv, états HSMM, transitions.




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

6. Bakrania K, Yates T, Rowlands AV, Esliger DW, Bunnewell S, Sanders J, et al. Intensity Thresholds on Raw Acceleration Data: Euclidean Norm Minus One (ENMO) and Mean Amplitude Deviation (MAD) Approaches. PLoS One. 2016;11(10):e0164045. doi:10.1371/journal.pone.0164045 PubMed PMID: 27706241; PubMed Central PMCID: PMC5051724.

7. van Hees VT, Fang Z, Langford J, Assah F, Mohammad A, da Silva ICM, et al. Autocalibration of accelerometer data for free-living physical activity assessment using local gravity and temperature: an evaluation on four continents. J Appl Physiol (1985). 1 oct 2014;117(7):738‑44. doi:10.1152/japplphysiol.00421.2014 PubMed PMID: 25103964; PubMed Central PMCID: PMC4187052.
