# Project 1 Objective
 - The project aims to extract data from the City of Vancouver's website. The dataset is uploaded to an AWS cloud platform and a comprehensive data analytics study has been implemented. 
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
- Utilized datasets in Excel Format is as shown below. Insignificant columns have been hidden.
   
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
 - AWS Athena service was utilized. Some queries were performed and tables are made for the analysis.
   
## AWS Services
 - The following AWS Services were used:
    - Storage is done in AWS S3
    - Computation in EC2
    - ETL Pipeline and Processes in AWS Glue
    - Data Analysis in Athena
 
## Data Pipeline Implementation:
 - The process was conducted in AWS Glue by utilizing Visual ETL to perform processes.
 - Multiple transformation operations were perfomred including change schema, aggregation, and join operations.
    - Change Schema Operation: The structure of the 2023 and 2024 dataset has been changed by deleting all the unnecessary columns and giving meaningful names to the required columns.
    - Aggregate Operation: The aggregate function has been used to aggregate the records of the ‘Year’ column within the 2023 and 2024 dataset.
    - Join Operation: To prepare a collective output, join funnction is used to combine the data by taking the type of work as medium for common column.
    - Change Schema: Again this operation was used to delete the unnecesssary columns and giving meaninngful names.
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
 - General Server and Web Server were set up using AWS EC2 service to make the data available for internal and external access.
 - The yearly report has been published for public access to reduce communication time and better accessebility.
   
<kbd> <img src=![Graph Report](https://github.com/user-attachments/assets/6606aea8-71ac-4026-bce9-1d22e1202f0e) /> </kbd>

## Insights and Findings
 - The graph represents the total number of type of work conducted for issued building permits. It can be depicted that some of the work are just conducted rarely but some of them are often and needs the commitment of the labor at all times.
 - This will help in maintaining the number of workers required around the year and give companies analysis of what to expect from next year.

## Cost Estimation
 - Amazon S3: Estimated annual expense of $285.846 for storage across four buckets.
 - AWS Glue DataBrew: Estimated yearly cost of $32.04 for cleaning and restructuring datasets.
 - AWS Glue: Estimated total cost of $13.20 for ETL job runs.
 - Amazon Athena: Estimated annual expense of $35.76 for querying and analysis.
 - EC2: Total yearly cost of $225.96 for hosting general and web servers.

## Conclusion
 - The project demonstrates the showcases the productivity in using the services of AWS cloud for large-scale dataset and highlights the capabilities in automating data workflows and gaining insights for better management.

# Project 2 Objective
 - The objective of this project is to accurately calculate the student graduation rates for the years 2022, 2023 and 2024 at the University Canada West (UCW).
 - By leveraging sample data, such as student records and course completion information, this project seeks to uncover key insights into student performance, identify trends, and offer data-driven recommendations to improve future graduation rates.

## Table of Contents
 - [Data Analytical Question Formulation](#data-analytical-question-formulation)
 - [Dataset Preparation](#dataset-preparation)
 - [Data Pipeline Design](#data-pipeline-design)
 - [AWS Services](#aws-services)
 - [Data Cleaning and Structuring](#data-cleaning-and-structuring)
 - [Data Pipeline Implementation](#data-pipeline-Implementation)
 - [Outcome](#outcome)
 - [Insights and Findings](#insights-and-findings)
 - [Conclusion](#conclusion)

## Data Analytical Question Formulation
 - Delved into the sample data for 2022, 2023 and 2024 to produce a metric called “Student Graduation Rate.” The metric will provide the percentage of student graduated in the years 2022, 2023 and 2024, respectively.
 - Percentage of Students Graduated (SGR) = (Number of Student Enrolled/ Number of Student Graduated) * 100
  
## Dataset Preparation
 - Sample dataset includes two Excel files
    - Sample Student Records Information.
<kbd> <img src="https://github.com/user-attachments/assets/914c6d2a-d87e-43b9-b06e-cde92d67f59c" /> </kbd>
    - Sample Graduation Records Information.<kbd> <img src="https://github.com/user-attachments/assets/73c8cfc3-deb2-4657-a2f5-ee75d2868d7e" /> </kbd>
      
## Data Pipeline Design
 - Designed using draw.io to anlayse data processing stages.

<kbd> <img src="https://github.com/user-attachments/assets/d95b91b5-3d91-4169-8fba-9cd15b5aea17" /> </kbd>
   
## AWS Services
 - AWS Services:
    - Amazon S3 for storage
    - AWS GlueData Brew for Cleaning and Structuring.
    - AWS Glue for Data Pipleline.

## Data Cleaning and Structuring
 - It includes operations such as
    - Checking invalid values in data set such as null rows.
    - Renaming of coloum names.
    - Change of Data Type for columns.
    - Change of Schema (Addition of Coloumn).
    - Creation and publishing of recipe.

<kbd> <img src="https://github.com/user-attachments/assets/db441eb5-0266-48f6-911c-3c06a8b1f9c6" /> </kbd>

## Data Pipeline Implementation:
 - Implemented using AWS Glue for ETL processes.
 - Transformation operations included schema changes, aggregation, and union operations.
   
<kbd> <img src="https://github.com/user-attachments/assets/c5c54041-9b76-4cb8-aac0-682901128319" /> </kbd>

## Outcome
 - Figure shows the determination of metrics as deduced from ETL Glue.
   
<kbd> <img src="https://github.com/user-attachments/assets/ef50dbd0-f11f-42d4-9a3e-7052bb8347e6" /> </kbd>

## Insights and Findings
 - Student Graduation Rate (SGR) for 2023:
    - The graduation rate for the year 2023 is 66.67%.
    - This indicates that approximately two-thirds of the students enrolled in the relevant programs at UCW successfully graduated in 2023.
    - This rate reflects a decrease when compared to the previous year (2022).
      
 - Student Graduation Rate (SGR) for 2024:
    - The graduation rate for the year 2024 is 69.70%.
    - This shows a slight improvement over the 2023 graduation rate, suggesting positive changes in student performance or institutional effectiveness.
    - However, it still falls short of the graduation rate observed in 2022.

 - Trend Analysis:
    - There is a notable fluctuation in the graduation rates over the three years:
    - 2022: 73.53%
    - 2023: 66.67% (a decrease from 2022)
    - 2024: 69.70% (an increase from 2023 but still lower than 2022)
    - This trend highlights potential areas of concern in student retention or program effectiveness that UCW may need to address.

## Conclusion
 - The project effectively uses AWS Glue DataBrew for data cleaning and transformation, and the ETL pipeline is successfully executed to calculate the student graduation rate.
 - The entire workflow, from data preparation to final output generation, is well-organized with clear steps for extracting, transforming, and loading data into an S3 bucket.
 - The project aims to provide insights into university graduation rates by using a systematic data processing approach, and the documented pipeline reflects a comprehensive methodology to achieve the objective.

# Project 3 Objective
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
<kbd> <img src="https://github.com/user-attachments/assets/3f36ebff-925c-4c8e-873b-03a76b642771" /> </kbd>
    - Data Quality Checks: During the data processing phase, AWS Glue performs data quality checks to remove duplicates, fill in missing values, and format the data according to predefined standards.
<kbd> <img src="https://github.com/user-attachments/assets/b1e2a736-8e0e-420a-a01f-f97101d9bee0" /> </kbd>
    - Conditional Routing: Only records that pass data quality checks are moved into the trusted zone, ensuring that the dataset used for analytics is accurate and reliable.
<kbd> <img src="https://github.com/user-attachments/assets/43ab5eeb-80ff-4a7e-9297-b3e02b833755" /> </kbd>
 - Data Privacy Management
    - Encryption and Access Control: Data privacy is enforced by encrypting sensitive data using AWS KMS and restricting access through IAM policies. Only authorized users with the appropriate roles can access and manipulate sensitive data, ensuring that privacy is maintained.
 - Data Versioning: S3 versioning is enabled to maintain a history of changes to the data. This allows for the recovery of previous versions in case of accidental deletions or modifications, supporting data governance by providing data lineage and audit trails.
    - LabRole Implementation: A predefined role ('LabRole') is assigned to manage permissions for encryption keys, data access, and usage within the platform, ensuring consistent governance policies across the platform.
   
### Data Monitoring
 - AWS CloudWatch for Real-Time Monitoring
    - Resource Monitoring: AWS CloudWatch is used to monitor key metrics of AWS resources, such as CPU utilization, memory usage, and network activity. It provides real-time insights into the performance of the data analytics platform.
    - Custom Metrics and Dashboards: CloudWatch allows the creation of custom metrics and dashboards for specific aspects of the data analytics platform. For example, monitoring the status of S3 buckets, ETL pipelines in AWS Glue, and data processing jobs helps track data flow and detect anomalies.
<kbd> <img src="https://github.com/user-attachments/assets/a05efbac-af60-44cd-81da-ab08890589fb" /> </kbd>
    - Alarms and Notifications: CloudWatch Alarms are set up to trigger notifications when certain thresholds are breached (e.g., unusually high data access attempts, resource usage spikes). This proactive monitoring helps in identifying and mitigating potential security incidents or performance issues.
<kbd> <img src="https://github.com/user-attachments/assets/40569bee-8274-4b29-87da-14e4a46eb538" /> </kbd>
 - AWS CloudTrail for Audit Logging
    - Activity Logging: AWS CloudTrail captures and logs all API calls made within the AWS environment. This includes actions performed on data stored in S3, modifications to IAM roles, and operations within AWS Glue.
    - Audit Trails: CloudTrail logs serve as an audit trail, documenting who accessed or modified the data and when these actions occurred. This is crucial for tracking unauthorized access attempts and ensuring compliance with data governance policies.
    - Event History: CloudTrail maintains a history of events for a specified period, allowing for a retrospective analysis of data access and usage patterns. This can be used to detect unusual activity or verify compliance with data privacy regulations.
<kbd> <img src="https://github.com/user-attachments/assets/ebed967a-7e96-4352-8cc4-b166400a284a" /> </kbd>

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
      
## DAP Architectural Anlaysis
 - Operational Excellence
    - Best Practices: The platform implements AWS best practices to enhance operational efficiency, reliability, and scalability. This includes using IAM for fine-grained access control and AWS Glue for structured data processing.
    - Disaster Recovery: S3 bucket replication and versioning are used to implement disaster recovery strategies. Replicated buckets and versioning ensure that data is recoverable in the event of accidental deletion or corruption.
    - Real-Time Monitoring: AWS CloudWatch monitors the performance and health of the platform in real-time, enabling proactive identification of issues through automated alerts for key metrics like CPU usage and memory consumption.
 - Security
    - Comprehensive Security Practices: Security is a core focus of the DAP architecture. IAM roles and policies are used to enforce the principle of least privilege, ensuring that users and applications have only the necessary access rights.
    - Data Encryption: AWS KMS is used to encrypt sensitive data at rest in S3 buckets. Both symmetric and asymmetric encryption techniques are employed to ensure that data remains confidential and protected from unauthorized access.
    - Auditing and Monitoring: AWS CloudTrail is enabled to log and monitor all user activities, providing a comprehensive audit trail. This logging ensures transparency, accountability, and the ability to detect potential security incidents promptly.
 - Reliability
    - Data Redundancy and Versioning: Amazon S3 versioning is enabled to maintain multiple versions of objects, ensuring that previous versions are available in case of accidental deletions or modifications. This supports data integrity and reliability.
    - Regular Backups: The platform employs regular backups of data and applications, facilitated through S3 bucket replication and automated processes in AWS Glue. This allows for quick restoration in the event of a failure.
    - Data Quality and Integrity: AWS Glue is used to automate the data governance process, ensuring completeness, uniqueness, and freshness of data. This automation helps maintain the reliability of the datasets used for analysis.
 - Performance Efficiency
    - Optimized Resource Usage: The platform is designed to use Amazon S3 for storing raw, processed, and curated datasets. This service is chosen for its ability to handle large volumes of data efficiently.
    - Resource Monitoring and Tuning: AWS CloudWatch continuously monitors resource performance, including CPU utilization and memory usage. Performance metrics are tracked in real-time to identify bottlenecks and optimize resources.
    - Right Sizing of Resources: The platform ensures that the instances and storage solutions are right-sized based on performance requirements, ensuring efficient resource allocation and avoiding over-provisioning.
 - Cost Optimization
   - Cost Management: AWS Cost Explorer is used to monitor and analyze cost and usage patterns. This helps identify opportunities for cost savings, such as optimizing storage costs and minimizing redundant data processing.
    - Data Quality Routing: Data quality is enhanced through conditional routing in the ETL pipeline, where only records passing quality checks are processed further. This reduces costs by avoiding storage of outdated, null, or redundant data.
    - Elastic Resource Allocation: The platform adjusts the number of running instances based on the current needs. For example, it uses a general server during standard operations and scales to a web server when publishing data to the internet, optimizing resource costs.
 - Sustainability
    - Long-Term Efficiency and Scalability: The architecture is designed to ensure long-term sustainability by focusing on efficient resource utilization. Services like Amazon S3 and Glue are used in a manner that allows for scalability while minimizing resource wastage.
    - Resource Efficiency: By rightsizing instances and optimizing storage, the platform minimizes its carbon footprint and operational costs, supporting sustainable data management practices.

## Insights and Findings
 - Secure Data Analytics Platform: The project successfully implements a secure data analytics platform for the City of Vancouver using AWS services. Data protection is ensured through encryption (using AWS KMS) and access control (via IAM), safeguarding data confidentiality and integrity.
 - Effective Data Governance: The platform enforces data governance using AWS Glue for ETL processes and data quality checks, ensuring that only high-quality, clean data is used for analysis. IAM policies and S3 bucket structuring further support privacy and compliance.
 - Comprehensive Data Monitoring: Real-time monitoring using AWS CloudWatch and CloudTrail tracks resource usage, API activities, and data access. This continuous monitoring helps maintain operational transparency and swiftly detect anomalies or security issues.
 - Scalability and Cost Optimization: The architecture leverages AWS services like S3 and Glue to create a scalable platform capable of handling large datasets. Cost optimization is managed through AWS Cost Explorer, ensuring efficient resource usage.
 - Enhanced Data Security and Privacy: Encryption techniques and role-based access control ensure data privacy and compliance, critical for handling sensitive city data. Versioning in S3 maintains data integrity, allowing for recovery of previous data versions.

## Conclusion
 - The AWS Data Analytics Platform for the City of Vancouver successfully establishes a secure, scalable, and efficient environment for managing and analyzing city datasets. By leveraging a combination of AWS services, including IAM, KMS, S3, Glue, CloudWatch, and CloudTrail, the platform ensures robust data protection, governance, and real-time monitoring. This approach not only safeguards sensitive data through encryption and access controls but also enhances data quality and integrity through meticulous ETL processes and data governance practices.
 - The platform is designed to adapt to varying data volumes and analytical needs, demonstrating both scalability and cost efficiency. It sets a strong foundation for data-driven decision-making while adhering to privacy and compliance standards. This project showcases how cloud-based solutions can be effectively utilized to meet the complex data management needs of public sector entities. Moving forward, the platform can be further enhanced with advanced analytics and automated governance to provide deeper insights and continuous optimization.
