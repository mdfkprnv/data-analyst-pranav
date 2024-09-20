# Project 1 Objective
 - The project aims to extract data from the City of Vancouver's website. The dataset is uploaded to an AWS cloud platform, and a comprehensive data analytics study has been implemented. 
 - The goal is to streamline data processing, analysis, and visualization for various building permits, ensuring scalability, security, and efficiency in data management.

## Table of Contents
 - [Methodology](#methodology)
 - [AWS Services](#aws-services)
 - [Data Pipeline Implementation](#data-pipeline-implementation)
 - [Data Analysis](#data-analysis)
 - [Outcome](#outcome)
 - [Insights and Findings](#insights-and-findings)
 - [Cost Estimation](#cost-estimation)
 - [Conclusion](#conclusion)

## Methodology

### Data Analytical Question Formulation
 -	Researched on the data given for the years 2023 and 2024. A metric is generated “Percentage change Year-on-Year.” The metric will give details on the changes experienced in issued building permits from the year 2023 to 2024.
 -	Percentage change Y-o-Y = (Number of permits issued in 2023/ Number of permits issued in 2024) * 100
   
   <kbd> <img src=![Screenshot 2024-08-27 182055](https://github.com/user-attachments/assets/c8e5488b-9547-4aca-944f-d0b2a2db7e83) /> </kbd>

### Data Discovery
- Focussed on the procedure ‘Issued Building Permits’ in the Property and Development department for the city of Vancouver. [Data Source Link](https://opendata.vancouver.ca/explore/dataset/issued-building-permits/export/?refine.issuedate=2023)
- Utilized datasets in Excel format are shown below. Insignificant columns have been hidden.
   
  <kbd> <img src=![Screenshot 2024-09-18 194221](https://github.com/user-attachments/assets/28024c5d-1dea-4620-953a-0441f101a285) /> </kbd>
  
  
### Dataset Preparation
 - The following things have been performed in AWS:
    - Data Gathering
    - ETL Pipeline
    - Data Cleaning using AWS Glue DataBrew.

### Data Pipeline Design
 - Designed using draw.io to automate data processing stages.

   <kbd> <img src=![Screenshot 2024-08-27 210913](https://github.com/user-attachments/assets/3179c3ef-2c18-4fad-b9d5-5e1548e9e5a1)
 /> </kbd>

   <kbd> <img src=![Screenshot 2024-08-27 210859](https://github.com/user-attachments/assets/2634bb5f-7f1b-44d6-b8ba-f45e12cd5f3f) /> </kbd>
### Data Analysis
 - AWS Athena service was utilized. Some queries were performed, and tables were made for the analysis.
   
## AWS Services
 - The following AWS Services were used:
    - Storage is done in AWS S3
    - Computation in EC2
    - ETL Pipeline and Processes in AWS Glue
    - Data Analysis in Athena
 
## Data Pipeline Implementation:
 - The process was conducted in AWS Glue by utilizing Visual ETL to perform processes.
 - Multiple transformation operations were performed, including change schema, aggregation, and join operations.
    - Change Schema Operation: The structure of the 2023 and 2024 datasets has been changed by deleting all the unnecessary columns and giving meaningful names to the required columns.
    - Aggregate Operation: The aggregate function has been used to aggregate the records of the ‘Year’ column within the 2023 and 2024 datasets.
    - Join Operation: To prepare a collective output, the join function is used to combine the data by taking the type of work as a medium for the common column.
    - Change Schema: Again, this operation was used to delete the unnecessary columns and give meaningful names.
    - Derived Column: This operation is utilized to handle the mathematical equation part. An equation is created and formulated using this.
  
   <kbd> <img src=![Screenshot 2024-08-27 114123](https://github.com/user-attachments/assets/687ffe67-501e-4c63-a0a9-f811e043d661) /> </kbd>

## Data Analysis
 - Data analysis was performed using AWS Athena.
 - SQL database was utilized to analyze the content of the dataset.
 - Table DDL

sql
  --Contact Centre Table --
CREATE EXTERNAL TABLE `project1_pad_table_pranav`(
  `year` string, 
  `percent_change_yoy` string)
ROW FORMAT DELIMITED 
  FIELDS TERMINATED BY ',' 
STORED AS INPUTFORMAT 
  'org.apache.hadoop.mapred.TextInputFormat' 
OUTPUTFORMAT 
  'org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat'
LOCATION
  's3://project1-pad-pranav-dataset/Property and Development Domain/Curated/Yearly Report'
TBLPROPERTIES (
  'classification'='csv', 
  'skip.header.line.count'='1', 
  'transient_lastDdlTime'='1724308959')

 - Table creation from AWS Athena Database is as shown below:
   
<kbd> <img src=![step 11](https://github.com/user-attachments/assets/3a660dfc-581c-4f87-9c14-51c60014c888) /> </kbd>

## Results
 - The general Server and Web Server were set up using AWS EC2 service to make the data available for internal and external access.
 - The yearly report has been published for public access to reduce communication time and improve accessibility.
   
<kbd> <img src=![Graph Report](https://github.com/user-attachments/assets/6606aea8-71ac-4026-bce9-1d22e1202f0e) /> </kbd>

## Insights and Findings
 - The graph represents the total number of types of work conducted for issued building permits. It can be depicted that some of the work is conducted rarely, but some of it is often and requires commitment from the laborer at all times.
 - This will help maintain the number of workers required around the year and give companies an analysis of what to expect from next year.

## Cost Estimation
 - Amazon S3: Estimated annual expense of $285.846 for storage across four buckets.
 - AWS Glue DataBrew: Estimated yearly cost of $32.04 for cleaning and restructuring datasets.
 - AWS Glue: Estimated total cost of $13.20 for ETL job runs.
 - Amazon Athena: Estimated annual expense of $35.76 for querying and analysis.
 - EC2: Total yearly cost of $225.96 for hosting general and web servers.

## Conclusion
 - The project showcases the productivity in using the services of AWS cloud for large-scale datasets and highlights the capabilities in automating data workflows and gaining insights for better management.

# Project 2 Objective
 - To develop and deploy a secure, efficient, and scalable Data Analytics Platform (DAP) for the City of Vancouver leveraging AWS cloud services. This platform will support the seamless migration, storage, processing, and analysis of city datasets, enabling enhanced data-driven decision-making while ensuring robust data protection, governance, and compliance with privacy regulations.

## Table of Contents
 - [ETL Workflow](#etl-workflow)
 - [Data protection](#data-protection)
 - [Data Governance](#data-governance)
 - [Data Monitoring](#data-monitoring)
 - [AWS Services Used](aws-services-used)
 - [DAP Architectural Analysis](#dap-architectural-analysis)
 - [Insights and Findings](#insights-and-findings)
 - [Conclusion](#conclusion)

### ETL Workflow
 - Implemented using AWS Glue for ETL processes.
<kbd> <img src="https://github.com/user-attachments/assets/da29dd8c-171f-42ce-89d8-6081de44a800" /> </kbd>
  
### Data Protection
- Identity and Access Management (IAM)
  - Access Control: IAM is utilized to create users, groups, and roles for managing access to AWS resources. Specific roles, like "LabRole," are assigned to ensure that only authorized individuals have the appropriate permissions.
  - Policy Creation: Policies are designed to follow the principle of least privilege, granting users or groups only the minimal permissions required to access necessary resources.

- Encryption and Decryption
  - AWS Key Management Service (KMS):
  - Symmetric Key: A single key is used for both encryption and decryption. This key is applied to encrypt data in Amazon S3 buckets, ensuring only authorized users can access the stored data.
  - Asymmetric Key: A pair of public and private keys is used for encryption and decryption. This method is employed for highly sensitive data, enabling encryption with one key and decryption with another.

- Data Storage Security in Amazon S3
  - Bucket Policies and Access Controls: IAM roles and bucket policies restrict access to S3 buckets, ensuring only authorized users and services can interact with the data.
  - ETL Pipeline Security: AWS Glue processes data within an encrypted ETL pipeline, protecting data during transformation.

- Techniques for Integrity Protection
  - Data Integrity Checks: Encryption and decryption mechanisms safeguard data, ensuring it remains unaltered during storage and transmission.
  - Versioning in S3: Amazon S3 versioning is enabled to maintain previous versions of objects, preventing accidental data loss or changes.
    <kbd> <img src="https://github.com/user-attachments/assets/8df47c88-d485-4442-a7c7-7e1bd763a642" /> </kbd>

- Monitoring and Auditing
  - Replication: Replication enhances data protection by automatically creating multiple copies of the data in different S3 buckets, either within the same region or across different regions.
<kbd> <img src="https://github.com/user-attachments/assets/558156f8-dd5c-4588-bc80-ba3b10c346da" /> </kbd>

### Data Governance
 - Data Quality Management
    - AWS Glue: ETL Pipeline - The ETL (Extract, Transform, Load) pipeline using AWS Glue is designed to clean, process, and structure the data before it is stored in the "Trusted" zone. This ensures that the data used for analytics is of high quality, complete, and ready for analysis.
    - Data Quality Checks: During the data processing phase, AWS Glue performs data quality checks to remove duplicates, fill in missing values, and format the data according to predefined standards.
    - Conditional Routing: Only records that pass data quality checks are moved into the trusted zone, ensuring that the dataset used for analytics is accurate and reliable.
 - Data Privacy Management
    - Encryption and Access Control: Data privacy is enforced by encrypting sensitive data using AWS KMS and restricting access through IAM policies. Only authorized users with the appropriate roles can access and manipulate sensitive data, ensuring that privacy is maintained.
 - Data Versioning: S3 versioning is enabled to maintain a history of changes to the data. This allows for the recovery of previous versions in case of accidental deletions or modifications, supporting data governance by providing data lineage and audit trails.
    - LabRole Implementation: A predefined role ('LabRole') is assigned to manage permissions for encryption keys, data access, and usage within the platform, ensuring consistent governance policies across the platform.
   
### Data Monitoring
 - AWS CloudWatch for Real-Time Monitoring
    - Resource Monitoring: AWS CloudWatch is used to monitor key metrics of AWS resources, such as CPU utilization, memory usage, and network activity. It provides real-time insights into the performance of the data analytics platform.
    - Custom Metrics and Dashboards: CloudWatch allows the creation of custom metrics and dashboards for specific aspects of the data analytics platform. For example, monitoring the status of S3 buckets, ETL pipelines in AWS Glue, and data processing jobs helps track data flow and detect anomalies.
    - Alarms and Notifications: CloudWatch Alarms are set up to trigger notifications when certain thresholds are breached (e.g., unusually high data access attempts, resource usage spikes). This proactive monitoring helps in identifying and mitigating potential security incidents or performance issues.
<kbd> <img src="https://github.com/user-attachments/assets/4cd98b72-9926-4883-8790-b7caaa13f956" /> </kbd>
 - AWS CloudTrail for Audit Logging
    - Activity Logging: AWS CloudTrail captures and logs all API calls made within the AWS environment. This includes actions performed on data stored in S3, modifications to IAM roles, and operations within AWS Glue.
    - Audit Trails: CloudTrail logs serve as an audit trail, documenting who accessed or modified the data and when these actions occurred. This is crucial for tracking unauthorized access attempts and ensuring compliance with data governance policies.
    - Event History: CloudTrail maintains a history of events for a specified period, allowing for a retrospective analysis of data access and usage patterns. This can be used to detect unusual activity or verify compliance with data privacy regulations.
<kbd> <img src="https://github.com/user-attachments/assets/801ab0df-9cc8-4351-8f9f-5e2b9ec535e7" /> </kbd>

## AWS Services Utilised
 - AWS Services:
    - IAM: Access control and user management.
    - KMS: Encryption and key management.
    - S3: Data storage and management with encryption and versioning.
    - AWS Glue: Data integration, ETL, and data quality management.
    - CloudWatch: Real-time monitoring and alerting.
    - CloudTrail: Audit logging and activity tracking.
    - S3 Access Logs: Data access monitoring and auditing.
    - Cost Explorer: Cost tracking and optimization.
      
## DAP Architectural Analysis

  - Operational Excellence
    - Best Practices: The platform follows AWS best practices to boost operational efficiency, reliability, and scalability. This includes leveraging IAM for granular access control and using AWS Glue for structured data processing.
    - Disaster Recovery: S3 bucket replication and versioning are in place to support disaster recovery. These ensure that data is recoverable in the event of accidental deletion or corruption.
    - Real-Time Monitoring: AWS CloudWatch provides real-time monitoring of platform performance and health, allowing for proactive issue detection through automated alerts for key metrics like CPU and memory usage.

  - Security
    - Comprehensive Security Practices: Security is a cornerstone of the DAP architecture. IAM roles and policies enforce the principle of least privilege, ensuring users and applications only have the access rights necessary.
    - Data Encryption: AWS KMS is utilized to encrypt sensitive data at rest within S3 buckets. Both symmetric and asymmetric encryption methods are employed to protect data confidentiality and prevent unauthorized access.
    - Auditing and Monitoring: AWS CloudTrail is enabled to log and track all user activity, creating a thorough audit trail. This enables transparency, accountability, and swift detection of potential security incidents.

  - Reliability
    - Data Redundancy and Versioning: Amazon S3 versioning is enabled to preserve multiple object versions, ensuring previous versions are available in case of accidental deletion or modification, supporting data reliability.
    - Regular Backups: The platform regularly backs up data and applications using S3 bucket replication and automated AWS Glue processes, allowing for quick recovery in case of failure.
    - Data Quality and Integrity: AWS Glue automates data governance to ensure completeness, uniqueness, and data freshness. This automation helps maintain the reliability of datasets used in analysis.

  - Performance Efficiency
    - Optimized Resource Usage: The platform efficiently uses Amazon S3 for storing raw, processed, and curated datasets, handling large volumes of data seamlessly.
    - Resource Monitoring and Tuning: AWS CloudWatch continuously tracks resource performance, including CPU and memory usage. Bottlenecks are identified in real-time to optimize resource utilization.
    - Right Sizing of Resources: The platform allocates resources, like instances and storage, based on performance needs, ensuring optimal resource allocation and avoiding over-provisioning.

  - Cost Optimization
    -Cost Management: AWS Cost Explorer monitors and analyzes cost and usage trends, identifying cost-saving opportunities by optimizing storage and minimizing redundant data processing.
    - Data Quality Routing: Conditional routing in the ETL pipeline ensures that only records meeting quality checks are processed, reducing costs by preventing the storage of outdated or redundant data.
    - Elastic Resource Allocation: The platform adjusts instance counts based on real-time demand. For example, it uses a general server for standard operations and scales to a web server for data publication, optimizing resource costs.
  
  - Sustainability
    - Long-Term Efficiency and Scalability: The architecture is built for sustainability, focusing on efficient resource use. Services like Amazon S3 and Glue support scalability while minimizing resource waste.
    - Resource Efficiency: Rightsizing instances and optimizing storage helps the platform reduce its carbon footprint and operational costs, promoting sustainable data management practices.

## Insights and Findings
 - Secure Data Analytics Platform: The project has successfully implemented a secure data analytics platform for the City of Vancouver using AWS services. Data protection is achieved through encryption (using AWS KMS) and access control (via IAM), ensuring the confidentiality and integrity of the data.
 - Effective Data Governance: AWS Glue is utilized for ETL processes and data quality checks, ensuring that only high-quality, clean data is used for analysis. IAM policies and structured S3 buckets further enhance privacy, governance, and compliance.
 - Comprehensive Data Monitoring: AWS CloudWatch and CloudTrail enable real-time monitoring of resource usage, API activities, and data access. This continuous monitoring maintains operational transparency and facilitates the quick detection of anomalies or security issues.
 - Scalability and Cost Optimization: By leveraging AWS services like S3 and Glue, the architecture provides a scalable platform capable of handling large datasets. AWS Cost Explorer helps optimize resources, ensuring cost-effective operations.
 - Enhanced Data Security and Privacy: Data privacy is ensured through encryption techniques and role-based access control, which are crucial for managing sensitive city data. S3 versioning maintains data integrity by allowing recovery of previous versions when needed.

## Conclusion
 - The AWS Data Analytics Platform for the City of Vancouver successfully delivers a secure, scalable, and efficient solution for managing and analyzing city datasets. It leverages a range of AWS services, such as IAM, KMS, S3, Glue, CloudWatch, and CloudTrail, to ensure strong data protection, governance, and real-time monitoring. This approach safeguards sensitive data through encryption and access control while enhancing data quality and integrity through rigorous ETL processes and data governance.
 - The platform is designed to scale with fluctuating data volumes and diverse analytical requirements, ensuring both flexibility and cost efficiency. It lays a solid foundation for data-driven decision-making, adhering to strict privacy and compliance standards. Moving forward, the platform can be enhanced with advanced analytics and automated governance features to offer deeper insights and continuous improvement. This project highlights the effectiveness of cloud-based solutions in addressing the complex data management needs of public sector organizations.

# Project 3 Objective
 - The objective of this project is to accurately calculate the successful policies developed for the years 2023 and 2024 at the University of Canada West (UCW).

## Table of Contents
 - [Dataset Preparation](#dataset-preparation)
 - [AWS Services](#aws-services)
 - [Data Cleaning and Structuring](#data-cleaning-and-structuring)
 - [Data Pipeline Implementation](#data-pipeline-implementation)
 - [Outcome](#outcome)
 - [Insights and Findings](#insights-and-findings)
 - [Conclusion](#conclusion)

## Dataset Preparation
 - Sample dataset includes two Excel files
    - Sample Student Records Information.
<kbd> <img src="https://github.com/user-attachments/assets/c62aede6-ba88-4d1d-b983-60fa152a3620" /> </kbd>
   
## AWS Services
 - AWS Services:
    - Storage in Amazon S3
    - Cleaning and Structuring in AWS GlueData
    - Data Pipeline in AWS Glue 

## Data Cleaning and Structuring
  - The process includes the following operations:
    - Identifying and handling invalid values, such as null entries in the dataset.
    - Renaming column headers for consistency and clarity.
    - Modifying data types for columns as needed.
    - Altering the schema, including adding new columns.
    - Creating and publishing data-cleaning recipes.
 
<kbd> <img src="https://github.com/user-attachments/assets/79760bfc-1eea-4858-9209-e6b07352cbfd" /> </kbd>

## Data Pipeline Implementation:
 - Implemented using AWS Glue for ETL processes.
 - Transformation operations included schema changes, aggregation, and union operations.
   
<kbd> <img src="https://github.com/user-attachments/assets/9ab2a6db-7845-42eb-9669-c8e9e186ee8b" /> </kbd>

## Outcome
 - Figure shows the determination of metrics as deduced from ETL Glue.
   
<kbd> <img src="https://github.com/user-attachments/assets/1ed47fbf-bea2-49b3-a7cf-d259b0935279" /> </kbd>

## Insights and Findings
 - Approved Policy Rate (APR) for 2023:
    - The approval rate for the year 2023 is 96.55%.
    - This indicates that most of the policies were reliant and accepted by the stakeholders in 2023.
      
 - Approved Policy Rate (APR) for 2024:
    - The approval rate for the year 2024 is 23.80%.
    - This shows a depreciation over the 2023 approval rate, suggesting bad decisions from the board and stakeholders.


## Conclusion
  - The project efficiently leverages AWS Glue DataBrew for data cleaning and transformation, executing the ETL pipeline to successfully calculate the policy approval rate.
  - The workflow is structured, with well-defined steps for extracting, transforming, and loading data into an S3 bucket, ensuring smooth data processing from preparation to final output generation.
  - The project’s goal is to analyze university-developed policies using a systematic data processing approach, and the documented pipeline outlines a thorough methodology to achieve this objective.
