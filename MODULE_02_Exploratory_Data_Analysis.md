# Module 02: Exploratory Data Analysis & Normality Diagnostics

## 1. Computing The Variances
While a shallow visual inspection shows an increase in the nationwide state mean ($+330.48$), the standard deviation tells a vastly different story. The sample variance approaches $\approx 19,531$—nearly double the absolute value of the mean itself. This signals massive dispersion within the population.

To isolate the structural shifts, a new vector column was calculated:
$$\text{Difference} = \text{Total}_{2011} - \text{Total}_{2008}$$
* **Spreadsheet Formula:** `=N5 - H5` *(dragged down across rows 5 to 54)*

## 2. Testing the Normality Assumption
A parametric Paired $t$-test strictly mandates that the paired differences follow an approximately normal, symmetrical distribution. Three diagnostic steps were taken to test this assumption:

* **Metric Metric Divergence (Mean vs. Median):** The mean paired difference sits at **$+381.89$** (excluding missing records), yet the median difference is only **$+104.00$**. This major divergence is an immediate indicator of a non-normal, right-skewed distribution.
* **Skewness Quantification:** Running the skewness formula returned an extreme value of **$3.599$**. Any value above $1.0$ confirms severe asymmetrical distribution.
    * *Formula:* `=SKEW(O5:O50)`
* **Visual Profiling via Custom Histogram:** Generating a distribution chart with default parameters proved insufficient as an outlier compressed the data. By adjusting the bucket resolution manually, a clear statistical picture emerged.

> **ℹ️ GRAPHIC CAPTURE SUGGESTION:** > <img width="1895" height="739" alt="Distribution of Growth in Certified Organic Livestock (2008 vs  2011)" src="https://github.com/user-attachments/assets/2a770318-23d3-4a55-98a4-3b3170292cc5" /> **Image Title Placeholder:** `[Image Title: Adjusted Bucket Size 1000 Distribution Histogram]`

## 3. Mathematical Verdict
The data strongly showcases a long right tail caused by single-state expansions, primarily driven by **Texas** adding $+36,607$ head of livestock. 

Because the normality assumption is completely violated, running a parametric Paired $t$-test would yield an artificial, unsafe result. **Statistical pivot justified:** The analysis must use the non-parametric **Wilcoxon Signed-Rank Test**, which evaluates median rank shifts and mitigates outlier distortion.
