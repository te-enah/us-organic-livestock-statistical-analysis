# Module 01: Hypothesis Formulation & Baseline Metrics

## 1. Experimental Design Framework
To evaluate whether the certified organic livestock sector experienced true growth over a three-year period, a paired experimental framework was established. Because data tracks identical geopolitical boundaries (U.S. States) across two distinct temporal markers, each state acts as its own internal baseline control.

* **Null Hypothesis ($H_0$):** $\mu_{2008} = \mu_{2011}$  
    There is no significant difference in the mean total number of certified organic livestock across U.S. states between 2008 and 2011. Any observed variations are purely due to chance.
* **Alternative Hypothesis ($H_1$):** $\mu_{2008} \neq \mu_{2011}$  
    There is a statistically significant difference in the mean total number of certified organic livestock across U.S. states between 2008 and 2011.

## 2. Statistical Significance Parameters
In a public policy context, declaring an effect as **"statistically significant"** requires empirical proof that the change is highly unlikely to have occurred due to random agricultural variance (e.g., exceptional weather cycles or passing localized trends). 

Setting our alpha threshold at $\alpha = 0.05$ means we accept a maximum 5% probability of rejecting the null hypothesis erroneously. 

## 3. Baseline Summary Statistics
By excluding the national aggregated "U.S." record to maintain structural independence across individual state units, the following baseline parameters were computed:

| Metric | 2008 Total Livestock Counts | 2011 Total Livestock Counts |
| :--- | :--- | :--- |
| **Mean (Average)** | 9,516.58 | 9,847.06 |
| **Standard Deviation (STDEV)** | 19,002.39 | 19,531.06 |

### Implementation Formulas
* **State Average (2008):** `=AVERAGE(H5:H54)`
* **State Standard Deviation (2008):** `=STDEV.S(H5:H54)`
