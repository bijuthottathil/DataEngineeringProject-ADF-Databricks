# DataEngineeringProject-ADF-Databricks

![image](https://github.com/user-attachments/assets/3bb67de5-990b-4c2d-80a3-5885468b61ff)



# Intend of this project is to move tables from Adventureworks Postgress DB from  on-Prem to  migrate ADLS in Azure , then transform to visualization using Databricks, Synapse and Power BI
. Part 1 Environment Setup
. Part 2  Data Ingestion
. Part 3  Data Transformation
. Part 4  Data Loading
. Part 5  Data Reporting
. Part 6 End to End Pipleline Testing



1 . Local PostgresDB in your laptop
![image](https://github.com/user-attachments/assets/6323dab6-445c-465e-a2a7-14b0cb58df41)


2 . Setup self hosted runtime to push data from PostgresDB to cloud ( This can be done while creating linked service in Azure Data Factory)
![image](https://github.com/user-attachments/assets/22dc5bed-4341-426c-9c18-5ce450cd9723)

3 Create Key Vault to keep posgress credentials

![image](https://github.com/user-attachments/assets/de3193e8-6531-4d92-81e1-551ed08357c6)
4  Store Posgres credentials in 2 secrets

![image](https://github.com/user-attachments/assets/e1135c65-2bbe-4451-bf5b-ca400f6b7974)

5 Create new Azure Data Factory and open the studio




ADF to copy data

ADLS Gen 2- to store , it is cheap
Azure Databricks- to transform raw data to curated data
medallion architecture followed

Synapse- Gold layer data will be loaded in Synapse
Power BI--
Azure active directory- identity access management tool
kv for storing securities
