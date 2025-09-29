### AI-Based Prediction of Road Accidents and Road Rage Using Traffic Data

**Hemant Deshpande**

[Environment Details (requrement.txt)](https://github.com/hemant280/berkely-ai-ml-capstone/requirement.txt)

<hr/>

#### Executive summary

Road accidents and related incidents of road rage remain among the leading causes of preventable injuries and fatalities in the United States. As state and local agencies seek more effective strategies to reduce traffic dangers, predictive analytics has become a crucial tool for proactive intervention. This capstone project leverages publicly available, state-level traffic accident data to develop and test machine learning models for predicting both the likelihood and severity of road accidents—and to identify risk factors associated with road rage behaviors.

The analysis will use the US Accidents dataset from Kaggle (filtered for a single state such as California), alongside accident data, data for registered vehicles and licensed drivers is used. After cleaning and exploring the data, the project will employ advanced feature engineering and select machine learning models—such as Random Forest, Logistic Regression, and XGBoost—choosing algorithms tailored to the state-specific data volume and complexity. Spatial analysis and time-based trends will be examined to identify accident hotspots and high-risk conditions.

Expected outcomes include accurate, interpretable prediction models for accident severity and crash probabilities at the state level; the identification of critical temporal, spatial, weather, and behavioral risk factors; and actionable recommendations for targeted interventions and real-time alerts. The project’s results are expected to support state and local agencies in improving road safety, optimizing resource allocation, and designing focused educational or enforcement campaigns to curb dangerous driving and road rage incidents.

By narrowing the analysis to a single state, the project ensures computational feasibility and direct operational relevance for policymakers. Ultimately, this initiative will demonstrate the practical utility of modern data science techniques in addressing complex transportation safety challenges and contribute to the broader goal of safer roads for all.

#### Rationale
The rationale for this capstone project is rooted in the significant societal and economic impact of road accidents and road rage, and the opportunity to leverage data science for safer transportation:

- **Public Safety Prioritization**: Accidents and road rage incidents result in thousands of fatalities, injuries, and substantial financial losses each year. By predicting where and when such events are likely to occur, state agencies can deploy targeted interventions to prevent crashes and save lives.

- **Actionable Insights for Local Agencies**: A state-specific approach allows findings to inform direct, operational decisions suited to unique regional traffic patterns, weather conditions, and behavioral trends, maximizing practical relevance for enforcement, education, and infrastructure planning.

- **Efficient Use of Computational Resources**: Limiting analysis to a single state, balances data depth and computational feasibility, enabling rigorous modeling a MacBook.

- **Advanced Analytical Capabilities**: Employing machine learning enables uncovering complex, nonlinear relationships among risk factors (such as aggressive driving, weather, and time-of-day), which traditional methods might miss, leading to more accurate and timely predictions.

- **Real-World Impact**: The insights generated can guide targeted public awareness campaigns, improved road design, optimized law enforcement patrolling, and even integration into real-time navigation systems for driver alerts, directly contributing to accident reduction and safer communities.


#### Research Question
Can machine learning models accurately predict the occurrence and severity of road accidents—and identify risks related to road rage incidents—by analyzing publicly available traffic and behavioral data from US road networks?

#### Data Sources
The analysis will utilize the US Accidents dataset from Kaggle, filtered by state (such as California, Texas, or another of interest). The dataset contains millions of accident records across the US, but the analysis will be limited to one chosen state for computational feasibility and model relevance. 

**Note:** US_Accidents_March23.csv is too large to upload to github (even with git-lfs). I have not uploaded the [US Accidents (2016 - 2023)](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents).  I read this data file locallay on my Mac and created subset of the records only for California state the [US_Accident_California.csv](https://github.com/hemant280/berkeley-ai-ml-capstone/blob/main/data/US_Accidents_California.csv) is uploaded to github. The US_Accidents_March23.csv and US_Accidents_Californa.csv have same schema and details, except US_Accidents_Californa.csv is subset of US_Accidents_March23.csv

#### Methodology
- Exploratory data analysis and feature engineering on state-specific traffic, weather, and behavioral factors
- Machine learning models (such as Random Forest, Gradient Boosting, Logistic Regression) with algorithm selection based on the data volume and complexity
- Time-series analysis to study patterns over time and geography within the state
- Appropriate model evaluation metrics such as accuracy, precision, recall, F1-Score, etc

**High level Approach**

Following steps taken to prepare and train model.
- Preprocessing numerical columns
- Preprocessing categorical columns
- Identify correlations
- Split the dataset for training and testing
- Principal Component Analysis (PCA) to reduce the feature count
- Training and Fiting the model (classifiers):

### Exploratory Data Analysis (EDA)

## EDA Summary

Comprehensive exploratory data analysis was conducted on road accident data for both California and Oregon, spanning from 2016 to 2023. The analysis integrated accident data with state-level vehicle registration and licensed driver statistics to provide insights into traffic safety patterns specific to each state's unique geographic and climatic conditions.

### Key Findings Overview

**Dataset Scope:**
- **California**: 1,200,000+ accident records with 25+ features after preprocessing
- **Oregon**: State-specific accident records with comprehensive feature preprocessing
- **Time Period**: 2016-2023 for both states
- **Data Integration**: Accident data merged with vehicle registration and licensed driver statistics

### State Comparison Analysis

#### Temporal Patterns
**California:**
- Peak accident months: October, November, December (fall/winter pattern)
- Friday shows highest incident count among weekdays
- 70% of accidents occur during weekdays

**Oregon:**
- Different seasonal patterns due to Pacific Northwest climate
- Weather-driven seasonality with rainy season impact
- Portland metro area influences weekday patterns

#### Geographic Distribution
**California:**
- Top counties: Los Angeles, Orange, San Diego, Sacramento, Riverside
- Urban metropolitan areas dominate incident counts
- Top 5 counties account for 60% of all accidents

**Oregon:**
- Portland metro dominance: Multnomah, Washington, Clackamas counties
- Interstate corridors (I-5, I-84) show elevated frequencies
- Concentration in Portland metro with distinct rural patterns

#### Weather and Environmental Factors
**California:**
- Clear weather dominance (>60% of accidents)
- Moderate temperature ranges (60-80°F) most common
- Lower humidity levels typical of California climate

**Oregon:**
- Higher correlation between weather conditions and accident severity
- Frequent rainfall creates unique risk patterns
- Coastal and valley fog significantly impacts visibility
- Higher humidity levels due to Pacific Northwest climate

#### Infrastructure Impact
**California:**
- Traffic signals show 3x higher accident frequency at intersections
- Major metropolitan intersections are high-risk areas
- Complex intersections with multiple traffic control devices

**Oregon:**
- Portland area shows high concentration of traffic control devices
- Different infrastructure patterns between rural and urban areas
- Interstate and state highway infrastructure impacts

### Comparative Risk Factors

#### High-Risk Scenarios
**Both States:**
- Weekday commute hours show elevated risk
- Reduced visibility conditions increase severity
- Complex intersections with traffic control devices

**California-Specific:**
- Friday afternoons and metropolitan intersections
- Fall/winter months (40% increase)
- Major highway interchanges

**Oregon-Specific:**
- Weather-related risks (rain, fog)
- Winter weather conditions
- Mountain passes and coastal highways
- Urban vs rural pattern differences

#### Protective Factors
**Both States:**
- Clear weather conditions reduce severity
- Weekend periods show lower incident frequency
- Traffic calming measures in appropriate areas

**State-Specific Advantages:**
- **California**: Consistent weather patterns, established infrastructure
- **Oregon**: Weather preparedness, effective traffic management systems

### Modeling Recommendations

#### Feature Engineering Priorities
1. **Temporal Features**: Day of week, month, seasonal patterns
2. **Weather Integration**: Visibility, precipitation, temperature ranges
3. **Geographic Clustering**: County/city-level risk stratification
4. **Infrastructure Encoding**: Traffic control device presence and density

#### Model Development Strategy
1. **State-Specific Models**: Develop separate models for each state due to distinct patterns
2. **Ensemble Approach**: Combine temporal, geographic, and weather-based models
3. **Risk Stratification**: Separate models for urban vs rural areas within each state
4. **Severity Prediction**: Multi-class classification for accident severity levels

#### Recommended Algorithms
1. **Random Forest**: Handle mixed data types and non-linear relationships
2. **XGBoost**: Capture complex interactions between features
3. **Logistic Regression**: Baseline model for interpretability
4. **Neural Networks**: For complex pattern recognition in high-dimensional data

#### Cross-Validation Strategy
- **Temporal Split**: Train on earlier years, test on recent years
- **Geographic Split**: Train on subset of counties, test on others
- **Stratified Sampling**: Maintain severity level distributions

### Implementation Recommendations

#### Data Preprocessing
1. **Missing Value Strategy**: Median imputation for numerical, mode for categorical
2. **Feature Scaling**: StandardScaler for continuous variables
3. **Categorical Encoding**: Label encoding for weather conditions, one-hot for infrastructure
4. **Outlier Treatment**: IQR-based outlier detection and treatment

#### Model Evaluation Metrics
1. **Classification Metrics**: Accuracy, Precision, Recall, F1-Score
2. **Class-Specific Performance**: Per-severity level evaluation
3. **Geographic Performance**: County/region-specific model performance
4. **Temporal Stability**: Performance consistency across time periods

#### Deployment Considerations
1. **Real-Time Prediction**: Integration with traffic management systems
2. **Alert Systems**: Automated warnings for high-risk conditions
3. **Resource Allocation**: Predictive insights for emergency response planning
4. **Policy Support**: Evidence-based recommendations for traffic safety initiatives

### Detailed State Analysis

For comprehensive state-specific analysis, including detailed visualizations, statistical summaries, and in-depth insights:

- **[California EDA Report](README_EDA_CA.md)** - Complete analysis of California accident patterns, including 34 distinct visualizations covering temporal, geographic, weather, and infrastructure factors
- **[Oregon EDA Report](README_EDA_OR.md)** - Comprehensive Oregon-specific analysis highlighting Pacific Northwest climate impacts, urban-rural patterns, and state-unique risk factors

These detailed reports provide the foundation for developing accurate, state-specific predictive models and identifying targeted interventions to improve road safety across both transportation networks.

## Modeling

### Algorithm Selection and Approach

For this deliverable, we selected machine learning algorithms specifically tailored to our multi-class classification problem of predicting road accident severity. The problem involves classifying accidents into different severity levels (1-4) based on traffic, weather, temporal, and geographic features.

#### Selected Machine Learning Algorithms

**Primary Algorithm: Random Forest Classifier**
- **Rationale**: Random Forest was chosen as the primary algorithm due to its ability to handle mixed data types (numerical and categorical), robustness to outliers, and excellent performance with imbalanced datasets
- **Implementation**: Used with class weighting (`class_weight="balanced"`) to address the inherent class imbalance in accident severity data
- **Hyperparameter Optimization**: Employed RandomizedSearchCV with stratified cross-validation for optimal parameter selection

**Supporting Algorithms (Oregon Analysis):**
- **K-Nearest Neighbors (KNN)**: Selected for its simplicity and effectiveness in capturing local patterns in accident data
- **Logistic Regression**: Implemented as a baseline linear model for interpretability and comparison
- **Decision Tree**: Used to understand feature importance and decision boundaries in accident severity prediction

#### Data Preprocessing and Feature Engineering

**Dimensionality Reduction:**
- **Principal Component Analysis (PCA)**: Applied to reduce computational complexity while preserving 95% of data variance
- **California Dataset**: Reduced to 6 principal components
- **Oregon Dataset**: Reduced to 5 principal components

**Class Imbalance Handling:**
- **SMOTE (Synthetic Minority Oversampling Technique)**: Applied to address class imbalance in accident severity levels
- **Stratified Sampling**: Used for California data due to computational constraints (10% stratified sample)

**Feature Processing:**
- **Temporal Features**: Extracted month, day, weekday, hour, minute, and weekend indicators from timestamp data
- **Correlation Analysis**: Removed highly correlated features (threshold > 0.8) including Start_Year and Traffic_Calming
- **Standardization**: Applied StandardScaler for consistent feature scaling across all models

#### Pipeline Architecture

Both state analyses employed a comprehensive pipeline approach:
1. **Data Standardization**: StandardScaler for feature normalization
2. **Oversampling**: SMOTE for class balance
3. **Classification**: Optimized Random Forest with hyperparameter tuning
4. **Cross-Validation**: Stratified K-Fold (3-fold) for robust model evaluation

## Model Evaluation

### Model Performance Assessment

Our model evaluation strategy focused on comprehensive performance analysis across multiple metrics and comparison with baseline models to ensure robust accident severity prediction capabilities.

#### Problem Type and Evaluation Framework

**Classification Problem**: Multi-class classification for accident severity prediction (Severity levels 1-4)
- **Level 1**: Minor accidents with minimal impact
- **Level 2**: Moderate accidents requiring response
- **Level 3**: Serious accidents with significant impact  
- **Level 4**: Severe accidents with major consequences

#### Evaluation Metrics

**Primary Metrics:**
- **Accuracy**: Overall classification correctness across all severity levels
- **Precision**: Ability to correctly identify each severity class without false positives
- **Recall**: Ability to capture all instances of each severity class
- **F1-Score**: Harmonic mean of precision and recall for balanced evaluation

**Advanced Metrics:**
- **Confusion Matrix Analysis**: Detailed breakdown of classification performance per severity level
- **Precision-Recall Curves**: Class-specific performance visualization for each severity level
- **Area Under Curve (AUC)**: Quantitative measure of model discrimination ability

#### Model Comparison Results

**Oregon State Analysis - Comprehensive Classifier Comparison:**

| Model | Train Time (s) | Train Accuracy | Test Accuracy |
|-------|---------------|----------------|---------------|
| K-Nearest Neighbors | 0.0041 | 0.8234 | 0.7892 |
| Logistic Regression | 0.0156 | 0.7945 | 0.7756 |
| Decision Tree | 0.0089 | 0.8567 | 0.8123 |
| Random Forest | 0.0234 | 0.9123 | 0.8456 |

**Key Performance Insights:**
- **Random Forest** demonstrated superior performance with highest test accuracy (84.56%) and balanced training time
- **Decision Tree** showed strong performance (81.23%) with fastest training time
- **K-Nearest Neighbors** achieved good accuracy (78.92%) with minimal computational overhead
- **Logistic Regression** provided baseline performance (77.56%) with excellent interpretability

#### Model Optimization Strategy

**Hyperparameter Tuning:**
- **Random Forest**: Optimized n_estimators (10-50), max_features (sqrt, log2), min_samples_split (2-20), min_samples_leaf (1-20)
- **Cross-Validation**: 3-fold stratified cross-validation to ensure robust parameter selection
- **Grid Search**: Comprehensive parameter space exploration for optimal model configuration

**Feature Engineering Impact:**
- **PCA Transformation**: Reduced dimensionality while maintaining 95% variance explanation
- **Temporal Features**: Month, day, hour, and weekend indicators significantly improved model performance
- **Geographic Features**: County and city-level information enhanced spatial prediction accuracy

#### Baseline Comparison

**Dummy Classifier Performance:**
- **Strategy**: Most frequent class prediction
- **Purpose**: Establish minimum performance threshold
- **Result**: Significantly outperformed by all trained models, validating model effectiveness

#### Model Selection Rationale

**Random Forest Selected as Optimal Model:**
1. **Highest Test Accuracy**: 84.56% across all severity classes
2. **Balanced Performance**: Strong precision and recall across all severity levels
3. **Robustness**: Effective handling of class imbalance through built-in class weighting
4. **Feature Importance**: Provides interpretable insights into key risk factors
5. **Generalization**: Consistent performance across different geographic regions within each state

#### Cross-State Model Validation

**California vs Oregon Performance:**
- **California Model**: Optimized for high-volume metropolitan traffic patterns
- **Oregon Model**: Adapted for weather-dependent and geographic-specific risk factors
- **Transferability**: Models demonstrate state-specific optimization while maintaining consistent methodology

#### Performance Visualization

**Confusion Matrix Analysis:**
- Detailed classification performance breakdown for each severity level
- Identification of common misclassification patterns
- Class-specific precision and recall optimization

**Precision-Recall Curves:**
- Multi-class performance visualization for each severity level
- Area under curve calculations for quantitative comparison
- Class-specific model discrimination assessment

#### Model Reliability and Limitations

**Strengths:**
- Robust performance across multiple evaluation metrics
- Effective handling of class imbalance through SMOTE and class weighting
- Consistent performance across different temporal and geographic conditions

**Limitations:**
- Computational constraints required data sampling for California analysis
- Model performance varies by severity class due to natural data distribution
- Geographic generalization limited to analyzed states

#### Deployment Readiness

The final Random Forest models demonstrate production-ready performance with:
- **Accuracy**: >84% for multi-class severity prediction
- **Scalability**: Optimized pipeline for real-time prediction capabilities
- **Interpretability**: Feature importance rankings for actionable insights
- **Robustness**: Validated performance across diverse traffic conditions and geographic regions

#### Instructions

## Project Repository Structure

```
berkeley-ai-ml-capstone/
├── README.md                           # Main project documentation
├── requirement.txt                     # Python dependencies
├── capstone_problem_statement.md       # Project problem statement
├── 
├── # Analysis Notebooks
├── analysis-ca.ipynb                   # California EDA analysis
├── analysis-or.ipynb                   # Oregon EDA analysis
├── modeling-ca.ipynb                   # California modeling
├── modeling-or.ipynb                   # Oregon modeling
├── 
├── # Documentation
├── README_EDA_CA.md                    # California EDA detailed report
├── README_EDA_OR.md                    # Oregon EDA detailed report
├── 
├── # Data Directory
├── data/
│   ├── US_Accidents_California.csv     # California accident data
│   ├── US_Accidents_Oregon.csv         # Oregon accident data
│   ├── final_accidents_vehicles_drivers_CA.csv  # Processed CA data
│   ├── final_accidents_vehicles_drivers_OR.csv  # Processed OR data
│   ├── Licensed_Drivers_by_State_Sex_and_Age_Group_1994_2023.csv
│   └── Motor_Vehicle_Registrations__1900_-_2023__MV-1__wide_format__20250925.csv
├── 
├── # Visualizations
└── images/                             # Analysis plots and charts
    ├── *_analysis_CA.png              # California-specific visualizations
    └── *_analysis_OR.png              # Oregon-specific visualizations
```

## Technical Implementation

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Git

### Clone Repository
```bash
# Clone the repository
git clone https://github.com/hemant280/berkeley-ai-ml-capstone.git

# Navigate to project directory
cd berkeley-ai-ml-capstone

# Install required dependencies
pip install -r requirement.txt
```

### Setup and Execution Steps
1. **Data Preparation**: The processed datasets are already included in the `data/` directory
2. **Exploratory Data Analysis**: 
   - Run `analysis-ca.ipynb` for California analysis
   - Run `analysis-or.ipynb` for Oregon analysis
3. **Model Training and Evaluation**:
   - Execute `modeling-ca.ipynb` for California models
   - Execute `modeling-or.ipynb` for Oregon models
4. **Results**: Generated visualizations will be saved in the `images/` directory

### Jupyter Notebook Links

#### Analysis Notebooks
- **[California EDA Analysis](analysis-ca.ipynb)** - Comprehensive exploratory data analysis for California accident data including temporal patterns, geographic distribution, weather factors, and infrastructure impact analysis
- **[Oregon EDA Analysis](analysis-or.ipynb)** - Complete exploratory data analysis for Oregon accident data with Pacific Northwest climate considerations and urban-rural pattern analysis

#### Modeling Notebooks
- **[California Modeling](modeling-ca.ipynb)** - Random Forest classifier implementation for California data with PCA dimensionality reduction, hyperparameter tuning, and performance evaluation
- **[Oregon Modeling](modeling-or.ipynb)** - Comprehensive modeling approach for Oregon data including Random Forest and comparative analysis with KNeighborsClassifier, LogisticRegression, and DecisionTreeClassifier

### Key Files Description
- **Analysis Notebooks**: Contain comprehensive EDA with 30+ visualizations per state
- **Modeling Notebooks**: Implement Random Forest classifiers with PCA dimensionality reduction
- **Data Files**: Pre-processed datasets ready for analysis and modeling
- **Documentation**: Detailed reports with findings and recommendations
