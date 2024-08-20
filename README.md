# DataEngineeringProject-ADF-Databricks

![image](https://github.com/user-attachments/assets/3bb67de5-990b-4c2d-80a3-5885468b61ff)



Intend of this project is to move tables from Adventureworks Postgress DB from  on-Prem to  migrate ADLS in Azure , then transform to visualization using Databricks, Synapse and Power BI

Pre Requisites
1 . Local PostgresDB in your laptop
![image](https://github.com/user-attachments/assets/6323dab6-445c-465e-a2a7-14b0cb58df41)


2 . Setup self hosted runtime to push data from PostgresDB to cloud
![image](https://github.com/user-attachments/assets/22dc5bed-4341-426c-9c18-5ce450cd9723)


ADF to copy data

ADLS Gen 2- to store , it is cheap
Azure Databricks- to transform raw data to curated data
medallion architecture followed

Synapse- Gold layer data will be loaded in Synapse
Power BI--
Azure active directory- identity access management tool
kv for storing securities
