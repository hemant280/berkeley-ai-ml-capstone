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
