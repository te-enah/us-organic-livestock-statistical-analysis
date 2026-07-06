# Module 03: Independent Regional Inference Pipeline

## 1. Regional Hypothesis Framework
To determine if geographic location impacts organic livestock production, an independent group analysis was configured comparing the **West** and **South** regions for the year 2011.

* **Null Hypothesis ($H_0$):** $\mu_{\text{West}} = \mu_{\text{South}}$  
    There is no significant difference in the mean 2011 organic livestock numbers between the West and South regions. Any observed difference is due to random chance.
* **Alternative Hypothesis ($H_1$):** $\mu_{\text{West}} \neq \mu_{\text{South}}$  
    There is a statistically significant difference in the mean 2011 organic livestock numbers between the West and South regions.

## 2. Automated Array Extraction Architecture
To avoid manual sorting errors and clean up the workspace, dynamic spreadsheet formulas were engineered to automatically isolate regional metrics while skipping non-numeric blank data rows:

* **West Region Filter Formula (Placed in cell O2):**
  ```excel
  =FILTER('State Organic Livestock'!N5:N54, 'State Organic Livestock'!B5:B54 = "West", ISNUMBER('State Organic Livestock'!N5:N54))


  South Region Filter Formula (Placed in cell P2):Excel=FILTER('State Organic Livestock'!N5:N54, 'State Organic Livestock'!B5:B54 = "South", ISNUMBER('State Organic Livestock'!N5:N54))
3. Data Visualization & Layout ReferenceBelow is the structural setup of the isolated arrays and the corresponding independent test execution in the analytics spreadsheet:Figure 1: Google Sheets dynamic data isolation and independent t-test configuration matrix.4. Inferential Computation & Power LimitationsUsing the cleanly isolated regional columns, a two-tailed Welch’s $t$-test (independent two-sample test assuming unequal variances) was calculated:Excel=T.TEST(O2:O13, P2:P15, 2, 2)
Calculated $p$-value: 0.3705Small-Sample Power EvaluationAt our alpha threshold ($\alpha = 0.05$), a $p$-value of 0.3705 means we fail to reject the null hypothesis.However, because our sample sizes are very small ($n_{\text{West}} = 12$, $n_{\text{South}} = 14$), this test suffers from low statistical power. In plain terms, our statistical "magnifying glass" is too weak to confirm whether the regions are truly identical. While the West looks higher on paper, the high variance and small sample size mean we cannot confidently rule out a Type II error (a false negative).If the underlying population distribution violates normality, a non-parametric alternative like the Mann-Whitney U Test (Wilcoxon Rank-Sum) should be used to evaluate rank medians instead of volatile raw means.

  <img width="1653" height="786" alt="west 2011 vs  south 2011" src="https://github.com/user-attachments/assets/3a92a98e-6586-4bcc-8cbd-ea12db02df00" />
