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
         
  #### Methods & Results :
  
   1. Data Cleaning :
      
  
         Method\Dataset |  Mammography  | RNA-seq
        ---------------|---------------|----------
        Null values | Replaced categorical with mode.Numerical with mean  | No Null values
        Imbalance  |  N/A  | SMOTE
        Correlation | pandas corr() | ANOVA
        Encoding categorical variables | N/A | keras to_categorical
        Train/Test split- Stratify | Sklearns’s train_test_split | Defined function
        
   2. Models :
      
      Here we are using 4 non-dl algorithms : Decision Trees, Logistic Regression, KNN , SVC.
      Dataset \ Methods | Decision Trees | Logistic Regression | KNN | SVC
      ------------------|----------------|---------------------|-----|-----
      Mammography | 0.7529 | 0.799 |0.6951 | 0.7388
      RNA-seq Gene | 0.9557 | 1.0 | 1.0 | 1.0
      
      Discussion: <br>
      i. RNA-seq Gene dataset performs better with KNN as the dataset was constructed to classify similar aberrations among different cancerous tumors. Thus, there   was some underlying similarities for KNN to group. <br>
     ii. Mammography dataset worked better with Logistic because it was set of metrics and we had to find a relation among them for each sample to predict the output. Hence it worked well. <br>

   
   DL models: <br>
   We have used Fully Connected NN and Conv 1D <br>
   Dataset \ Methods | Fully Connected NN | Conv 1D
   ------------------|--------------------|--------
Mammography | 0.7937 | 0.7977 
RNA-seq Gene | 0.8796 | 0.8984

![accuracy](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo_dl1.png) ![loss](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo_dl1_loss.png)
The above graphs are from Mammography dataset for Fully connected NN, it is a good fit. <br>


![acuracy](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo_dl2_acc.png)  ![loss](https://github.com/Sreeja-coder/Augmenting-Cancer-Detection/blob/main/assets/mamo_dl2_loss.png)

The above graphs are from Mammography dataset for CONV1 D, it is a good fit, but If I run it for more epochs, it might overfit.
