 # Augmenting-Cancer-Detection
 
 ####  Problem Statement :
  In this project we are trying to explore and analyze two different datasets, one collected by doing biopsy and another using X-ray images to see if we can get almost     the same accuracy in detecting cancer using data with and without biopsy.

 ####  Introduction :
  Every cell in the human body has a DNA, which is responsible for building and maintaining the organism. DNA does this by sending out the code for producing certain      kinds of proteins necessary for cell growth and division. DNA cannot directly send out this information to the nucleus; it uses RNA (m-RNA, t-RNA, r-RNA) for this   communication. So, at times the DNA mutates and sends signals to divide and grow cell uncontrolled. This causes the cell to mutate and grow, invading other tissues.
Thus, this disease of controlled cell division is called Cancer.

![Cancer](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/cancer_cell.jpg)


  ####  Literature Review :
   In this project we are exploring two datasets.
   * Mammography Dataset from UCI
   * RNA-seq Gene Dataset from UCI
  
  #### Descriptive Statistics :
   1. ##### Mammography dataset:
      1. Shape :
         The dataset has recorded information for 961 patients. <br>
         Captured 6 attributes for each patient. <br>
           * BI-RADS assessment: 1 to 5 (ordinal, non-predictive!)  <br>
           * Age: patient's age in years (integer)  <br>
           * Shape: mass shape: round=1 oval=2 lobular=3 irregular=4 (nominal)  <br>
           * Margin: mass margin: circumscribed=1 microlobulated=2 obscured=3 ill-defined=4 spiculated=5 (nominal)  <br>
           * Density: mass density high=1 iso=2 low=3 fat-containing=4 (ordinal)  <br>
           * Severity: benign=0 or malignant=1 (binominal, goal field!)  <br>
           
           
      2. Imbalance:
         The Target Label we are predicting is Severity. The pie chart shows a Balanced Dataset. <br>
         ![pie chart](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo1.png)
      
      
      3. Correlation: 
         The correlation matrix, indicates.
         * margin and “shape” are positively correlated. <br>
         * margin” and “age” are positively correlated. <br>
         * Other attributes do not have high correlation.  <br>
         ![matrix](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo2.png)
         
         ![detailed correlation](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo3.png)
         
         The above plot gives us a more detailed knowledge about the correlation between the attributes. <br>
         let us take x-axis "shape" and y-axis "age”: <br>
         An age group of 20 to 40 even if the shape of the tumor increases the cancer is benign. <br>
         But as we grow older the shape of the tumor does signify a malignant tumor. <br>
      
      4. Missing Values:
         The dataset had 162 missing values, since we have less samples already, we are not dropping them, we are instead replacing categorical features with mode and          numerical ones with mean.
         
         
   2. ##### RNA-seq gene expression dataset :
      1. Shape:
         * The dataset has biopsy data for 801 patients. Each recording 20532 gene information.
         * The target label we are trying to predict is “Class” , they are:
         * Breast invasive carcinoma - BRCA
         * Colon adenocarcinoma - COAD
         * Kidney renal clear cell carcinoma - KIRC
         * Lung adenocarcinoma - LUAD
         * Prostate adenocarcinoma - PRAD
      2. Imbalance:
         The dataset is imbalanced we will be using SMOTE to rectify this.
         ![imbalance](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/ran1.png)
         
      3. Correlation:
         We have 20532 features, hence drawing a correlation matrix is not a feasible solution to understand correlation.
         ![correlation](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/rna2.png)
         
      4. Missing Values:
         This dataset had no missing or null values.
         
     
