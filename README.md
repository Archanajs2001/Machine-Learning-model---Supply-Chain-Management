# Supply-Chain-Management

## Table of Contents

- [Data Cleaning](#data-cleaning)
- [Data Transformation in Power BI](#data-transformation-in-power-bi)
- [Visualizations](#visualizations)
- [Slicers](#slicers)
- [Instructions](#instructions)
- 
## Introduction

In response to observed mismatches between demand and supply within our Fast Moving Consumer Goods (FMCG) company's instant noodles business, a comprehensive data analysis has been conducted over the past two years. This initiative is driven by the necessity to optimize supply quantity, thereby mitigating excess inventory costs and enhancing operational efficiency.

The primary objective of this analysis is to harness historical data, unveiling patterns and insights that will inform strategic decision-making. By building predictive models, we aim to determine the optimum product shipment weight from each warehouse, aligning our supply with actual demand.

Throughout this exploration, we have delved into key aspects of the data, conducting an in-depth Exploratory Data Analysis (EDA) and developing machine learning models. The outcomes provide actionable recommendations and lay the groundwork for a more streamlined and efficient supply chain. 


## Data Overview

The training and testing datasets both contains 24 columns of valuable information about the instant noodles business that the FMCG has created.

**Data Dictionary**

Ware_house_ID: Unique identifiers for each warehouse.
WH_Manager_ID: Unique identifiers for the warehouse managers.
Location_type: Indicates the type of location where each warehouse is situated.
WH_capacity_size: Represents the capacity or size of each warehouse.
zone: Categorizes the warehouses into specific zones.
WH_regional_zone: Assigns each warehouse to a regional zone.
num_refill_req_l3m: Records the number of refill requests received in the last 3 months.
transport_issue_l1y: Indicates the occurrence of any transport-related issues within the last year.
Competitor_in_mkt: Specifies the presence of competitors in the market.
retail_shop_num: Provides the number of retail shops associated with each warehouse.
wh_owner_type: Describes the ownership type of each warehouse.
distributor_num: Represents the number of distributors associated with each warehouse.
flood_impacted: Indicates whether a warehouse has been impacted by floods.
flood_proof: Specifies whether a warehouse is flood-proof.
electric_supply: Indicates the status of electric supply to each warehouse.
dist_from_hub: Represents the distance of each warehouse from the hub.
workers_num: Provides the number of workers employed at each warehouse.
wh_est_year: Represents the year in which each warehouse was established.
storage_issue_reported_l3m: Indicates whether any storage issues have been reported in the last 3 months.
temp_reg_mach: Specifies the presence of temperature regulation machinery at each warehouse.
approved_wh_govt_certificate: Indicates if each warehouse has an approved government certificate.
wh_breakdown_l3m: Indicates whether any breakdowns have occurred at each warehouse in the last 3 months.
govt_check_l3m: Indicates if government checks have been conducted for each warehouse in the last 3 months.
product_wg_ton: Represents the weight of the product in tons.

The datasets are included in this repository for referance.

## Data Processing

1. **Handling Null Values**

Training Dataset have 3 columns that contains null variables
Testing Dataset have 2 columns that contains null variables 
   - **Method of Handling:**
     **- workers_num**
       - Imputed null values with median.

     Reason:
     - After observing distribution, the data was seen to be slightly positively skewed.
     - Data contains numerical values.

     **- wh_est_year**
       - Imputed null values with mode.

     Reason:
     - Decided to replace null variables eventhough almost half the data contains null values since the column have correlation with Product weight(target variable).
     - Data contains numerical values.

     **- approved_wh_govt_certificate**
       - Imputed null values with mode.

     Reason:
     - After trying other methods like forward and backward fills decided to replace null values with most frequent value since it improved the models evaluation metrics.   

2. **Feature Selection**
   - Dropped two columns namely 'Ware_house_ID' and 'WH_Manager_ID' since it's not relevant to product weight(target variable)
  
3. **Feature Encoding**
   - Transformed Categorical variables into Numerical format using Label Encoding.

4. **Feature Scaling**
   - Standardize features by removing the mean and scaling to unit variance using Standard Scaling.
   - 
## Visualizations

- **Correlation between Target and Feature variables**

![correlation chart](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/620622fe-3df8-4183-a5c6-a51ded10d004)

- **Relationship between Target variables and features it shows correlation with**

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


## Machine Learning Model Evaluation

- **Metrics**

![image](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/a3b9f51f-e6c7-447a-8823-fb348a7e2c5f)

- **Charts**

![charts](https://github.com/Archanajs2001/Machine-Learning-model---Supply-Chain-Management/assets/154094021/e9ddbc17-4fdf-4121-b09a-c5d820b1b4a8)








