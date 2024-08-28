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

5 Create new Azure Data Factory and open the studio. Navigate to runtimes. I had created selfhosted runtime before, so it is listing there

![image](https://github.com/user-attachments/assets/fd2d0616-1b14-41bc-98ad-2af76a33b2bb)


![image](https://github.com/user-attachments/assets/c9091ac5-59b8-4f67-bd0d-05c84e1f04ca)


![image](https://github.com/user-attachments/assets/73185713-1439-4380-ad72-9b7d72c5ba41)


Now creating link to ADLS storage account
![image](https://github.com/user-attachments/assets/730e5a32-6a14-4ec6-8745-6178f5217133)

Products table copied to ADLS storage account after running pipeline

![image](https://github.com/user-attachments/assets/cbbab31f-9761-40a7-b24a-e7080a5fe9c9)
check Paraquet file in Bronze folder
![image](https://github.com/user-attachments/assets/5890f3fc-4d73-4052-b489-b2b938758ee3)


created new pipeline to move data from 2 tables 

![image](https://github.com/user-attachments/assets/350eb7d8-d66f-4b29-bfda-4c5f9f20f75c)

iterating multiple tables using lookup and copy each activities in ADF
![image](https://github.com/user-attachments/assets/3222ade3-1e73-4540-b436-1c1a51a97dac)

Execution of postgress DB tables from onPrem to Bronze 

![image](https://github.com/user-attachments/assets/b93ebd83-7fc6-4584-a3fb-dd4e243bf86c)

![image](https://github.com/user-attachments/assets/6e5c1311-ca0c-426b-87ef-bbdfaa4a85ad)

Piple line executed and table data stored in proper folder structure

![image](https://github.com/user-attachments/assets/4a97bf2f-ee25-41fc-a724-5563c4a99769)

![image](https://github.com/user-attachments/assets/5c05b442-7e65-4057-b897-8aa644ca9fbb)


Mounting ADLS in Databricks notebook after creatingcluster
![image](https://github.com/user-attachments/assets/640913b3-f772-4058-985f-7a5732794807)

Bronze to Silver notebook
![image](https://github.com/user-attachments/assets/b27cc4c7-cfb4-43ec-88de-46ea363b4b0f)
Silver to Gold after joining dimension and fact tables using Broadcast join
![image](https://github.com/user-attachments/assets/1a8e287d-12f4-4b25-990d-38ebf8716814)

![image](https://github.com/user-attachments/assets/27c83782-19ac-4c7c-9542-1ed00bcae438)


To access databricks cluster in adf, please make sure to create access token

![image](https://github.com/user-attachments/assets/b0be33f8-33ea-47ef-bde3-983ec09364da)

add additional databricks control in the pipeline and choose bronze to silver note book

![image](https://github.com/user-attachments/assets/eda79f86-bba0-449e-bbba-9ba31cfdea7e)

Before running pipeline, making sure that only folders are available, without data

![image](https://github.com/user-attachments/assets/9e176787-e576-4296-8fd5-2efdeff48a89)


![image](https://github.com/user-attachments/assets/375e4201-63d4-4664-8444-57744c0c24b5)
![image](https://github.com/user-attachments/assets/457a82a8-38ca-46b9-9ab8-527fca08053a)

All jobs completed 
![image](https://github.com/user-attachments/assets/3e520b99-1620-45af-bd2c-feef057cbbe8)

You can see cleansed parquet file loaded in Gold adls storage

![image](https://github.com/user-attachments/assets/0cb4bcca-14c7-4438-a726-c60aca3c9a57)

Silver to Gold transformation in Databricks cluster is here

![image](https://github.com/user-attachments/assets/26487e5b-fd7a-40ce-b661-670f9d2ff090)


ADF to copy data

ADLS Gen 2- to store , it is cheap
Azure Databricks- to transform raw data to curated data
medallion architecture followed

Synapse- Gold layer data will be loaded in Synapse
Power BI--
Azure active directory- identity access management tool
kv for storing securities
