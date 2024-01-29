# Supply Chain Management

## Table of Contents

- [Introduction](#introduction)
- [Data Overview](#data-overview)
- [Data Processing](#data-processing)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Model Evaluation](#model-evaluation)
- [Insights and Recommendations](#insights-and-recommendations)
- [Next Steps and Improvements](#next-steps-and-improvements)
  
## Introduction

In response to observed mismatches between demand and supply within a Fast Moving Consumer Goods (FMCG) company's instant noodles business, a comprehensive data analysis has been conducted over the past two years. This initiative is driven by the necessity to optimize supply quantity, thereby enhancing operational efficiency.

The primary objective of this analysis is to harness historical data, unveiling patterns and insights that will inform strategic decision-making. By building predictive models, we aim to determine the optimum product shipment weight from each warehouse, aligning our supply with actual demand.

Throughout this exploration, we have delved into key aspects of the data, conducting an in-depth Exploratory Data Analysis (EDA) and developing Machine Learning models. The outcomes provide actionable recommendations and lay the groundwork for a more streamlined and efficient supply chain. 


## Data Overview

The training and testing datasets both contains 24 columns of valuable information about the instant noodles business that the FMCG has created.

**Data Dictionary**

- Ware_house_ID: Unique identifiers for each warehouse.
- WH_Manager_ID: Unique identifiers for the warehouse managers.
- Location_type: Indicates the type of location where each warehouse is situated.
- WH_capacity_size: Represents the capacity or size of each warehouse.
- zone: Categorizes the warehouses into specific zones.
- WH_regional_zone: Assigns each warehouse to a regional zone.
- num_refill_req_l3m: Records the number of refill requests received in the last 3 months.
- transport_issue_l1y: Indicates the occurrence of any transport-related issues within the last year.
- Competitor_in_mkt: Specifies the presence of competitors in the market.
- retail_shop_num: Provides the number of retail shops associated with each warehouse.
- wh_owner_type: Describes the ownership type of each warehouse.
- distributor_num: Represents the number of distributors associated with each warehouse.
- flood_impacted: Indicates whether a warehouse has been impacted by floods.
- flood_proof: Specifies whether a warehouse is flood-proof.
- electric_supply: Indicates the status of electric supply to each warehouse.
- dist_from_hub: Represents the distance of each warehouse from the hub.
- workers_num: Provides the number of workers employed at each warehouse.
- wh_est_year: Represents the year in which each warehouse was established.
- storage_issue_reported_l3m: Indicates whether any storage issues have been reported in the last 3 months.
- temp_reg_mach: Specifies the presence of temperature regulation machinery at each warehouse.
- approved_wh_govt_certificate: Indicates if each warehouse has an approved government certificate.
- wh_breakdown_l3m: Indicates whether any breakdowns have occurred at each warehouse in the last 3 months.
- govt_check_l3m: Indicates if government checks have been conducted for each warehouse in the last 3 months.
- product_wg_ton: Represents the weight of the product in tons.

The datasets are included in this repository for referance.

## Data Processing

1. **Handling Null Values**

Training Dataset and Testing Dataset both have 3 columns that contains null variables.

   - **Method of Handling:**
     
     **workers_num**
       - Imputed null values with median.

     Reason:
     - After observing distribution, the data was seen to be slightly positively skewed.
     - Data contains numerical values.

     **wh_est_year**
       - Imputed null values with mode.

      Reason:
      - Decided to replace null variables eventhough almost half the data contains null values since the column have correlation with Product weight(target variable).
      - Data contains numerical values.

     **approved_wh_govt_certificate**
       - Imputed null values with mode.

     Reason:
     - After trying other methods like forward and backward fills decided to replace null values with most frequent value since it improved the models evaluation metrics.   

2. **Feature Selection**
   - Dropped two columns namely 'Ware_house_ID' and 'WH_Manager_ID' since it's not relevant to product weight(target variable)
  
3. **Feature Encoding**
   - Transformed Categorical variables into Numerical format using Label Encoding.

4. **Feature Scaling**
   - Standardized features by removing the mean and scaling to unit variance using Standard Scaling.

     
## Exploratory Data Analysis

- **Correlation between Target and Feature variables**

![correlation chart](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/620622fe-3df8-4183-a5c6-a51ded10d004)

- **Relationship between Target variables and Features it shows correlation with**

![1](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/44f0b2fa-fcef-4ed6-8883-d5f0dfd4fb73)

**As the quantity of products stored in warehouses increases, the likelihood of facing storage issues also increases.**

![2](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/97f97c0a-5425-4336-aa03-d5b17fb43d13)

**As the product weight increases, the number of breakdowns faced by the warehouse also tends to increase.**
  
![3](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/3d0787aa-ce45-49fe-b277-0aa7327f97c3)

**Warehouses with temperature regulation capabilities tend to have higher average product weights.**
 
![year](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/f65af83d-5974-48ba-b600-8b9344152014)


**Recently established warehouses tend to have lower product weights compared to warehouses established in earlier years.**

![5](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/27dbd5bd-b8b8-40cc-90de-8b0f517a1bb3)

**Warehouses with fewer reported transport issues tend to have higher average product weights.**

![6](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/d2b05d33-18cb-4514-9c67-305685591676)

**Warehouses with higher levels of government approval (e.g., 'A+' or 'A') tend to have higher average product weights compared to warehouses with lower levels of approval.**

![7](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/5c715a47-a7cc-4aad-8c62-4e98eb01b59a)

**Warehouses located in urban areas tend to have higher average product weights**

![pie](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/c829d806-a844-4d8f-9d61-e778ade92870)

**Majority of the Warehouses are situated in Rural areas.**

**North zone has the highest number of Warehouses.**


## Model Evaluation

- **Metrics**

![image](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/75407475-df91-4053-bcde-436074d88552)




- **Charts**

![CHARTS!!!!!](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/f6be6cfd-d18b-44e1-a536-97c54ecfff71)



**Best Machine Learning Model**

- **Gradient Boosting Regressor**

Evaluation Metrics:

- **R2 Score : 0.994199**

- **Mean Absolute Values : 0.058168**

- **Root Mean Squared Value : 0.076167**


**Gradient Boosting Regressor is the Best Model. By utilizing this Machine Learning Model, we can make highly accurate predictions making it the preferred and most effective machine learning model for our task.**

## Insights and Recommendations

**Insights:**

1. **Warehouses in the North:**
   
Warehouses located in the North exhibit a higher storage capacity, leading to a larger volume of stored products.

2. **Product Weight and Operational Challenges:**
   
There is a correlation between higher product weights and increased occurrences of storage issues and warehouse breakdowns, indicating a need for strategic management of heavier products.

3. **Distribution Across Areas:**
   
Rural areas host the majority of warehouses, accounting for over 90% of the warehouses.

4. **Product Storage Discrepancy:**
   
Despite the predominance of warehouses in rural areas, urban warehouses store a larger quantity of products. This suggests a potential disparity in the distribution of products across different geographical areas.

5. **Temperature Regulator Influence:**
    
Warehouses equipped with temperature regulators tend to handle higher product weights. But majority of warehouses are not equipped with one. Therefore, it is recommended to consider equipping more warehouses with temperature-regulating facilities.

6. **Transport Issues and Product Weight:**
    
A negative correlation is observed between the occurrence of transport issues and the average product weight. Hence, addressing and minimizing transport issues may contribute to an increase in product weight.

**Recommendations:**

- **Expand Urban Warehouses:**
Given the higher demand for storage in urban areas, it is recommended to consider expanding warehouse facilities in these regions to meet the growing storage requirements resulting in a more balanced distribution across both rural and urban areas.

- **Optimize North Storage:**
Considering the higher capacity in the North and since higher product weight means increased storage issues and warehouse breakdown, it is advisable to assess and optimize the amount of products stored in this region. This may involve redistributing products across other zones to achieve a more balanced distribution.

- **Equip Warehouses with Temperature Regulators:**
Enhance the capabilities of warehouses by equipping them with temperature regulators to support the storage of higher amount of products and improve overall operational efficiency.

- **Mitigate Transport Issues:**
Implement measures to reduce transport issues, as this has shown to positively impact the average product weight. This may involve improving transport infrastructure, logistics, or optimizing supply chain processes.



These recommendations aim to enhance operational efficiency, address storage needs in high-demand areas, and ensure a more equitable distribution of products across geographical zones, while also optimizing warehouse capabilities based on observed correlations.

## Next steps and Improvements

**Next Steps:**

- **Hyperparameter Tuning:**
Delve into the fine-tuning of hyperparameters for machine learning models such as Random Forest and SVM. Employ advanced optimization techniques like grid search or randomized search to extract the best possible model configurations.

- **Model Ensembles:**
Investigate the potential benefits of crafting an ensemble model by synergizing the strengths of multiple models. Ensemble methods can elevate overall performance and enhance predictive accuracy.

**Improvements:**

- **Feature Selection:**
Enhance model efficiency by carefully evaluating and reducing the number of features. If certain features prove to be irrelevant, their removal can lead to improved performance, particularly for boosting models.

- **Data Quality Enhancement:**
Elevate the performance and representativeness of the dataset by reassessing the strategy for imputing missing values. A meticulous review of the imputation process ensures a more robust and reliable dataset representation.


Thank you for your attention. If you have any further questions or require additional insights, please do not hesitate to reach out.

Contact Info: archanaganga585@gmail.com
