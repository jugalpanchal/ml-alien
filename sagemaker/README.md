## Phases
1. Data Processing: Use EMR notebooks to prepare data for machine learning.
2. Modeling: Then call SageMaker from the notebook to create, train and deploy/host a machine learning model(that estimates the age of abalone based on their physical characteristics)

## Components
### EMR
1. EMR cluster should have permissions to access SageMaker: Add the 'AmazonSageMakerFullAccess' managed policy in the IAM(Core EC2 Instance IAM role) role.    

### SageMaker
- Amazon SageMaker provides managed infrastructure for model training and deployment.    
- Use PySpark to create a regression model that estimates abalone age.     
- Deploy the regression model in Amazon SageMaker and measure the effectiveness of your model.    

1. Create a IAM Role: Allows SageMaker notebook instances, training jobs, and models to access S3 training data, ECR, and CloudWatch on your behalf.    
	
### NoteBook    
To comunicate with SageMaker you need to install the notebook scoped libraries. These libraries are available only during the notebook session. After the session ends, the libraries are deleted.    
We install boto3 (the AWS Python 3 SDK) and the high level SageMaker SDK.	    
sc.install_pypi_package("boto3==1.16.9");    
sc.install_pypi_package('sagemaker==2.16.1');    

### Bucket
- data - source data ex. abalone.csv
- train - train data from the source(75%)
- test - test data from the source(25%) 
- inference - predicated values from the model by using the test data when we run(batch process) the model with the entire test data.
- model - Actual trained model file which can be used to predice values for any input set. We can pickle it even. s3://sagemaker-us-east-2-1234567890123/xgboost-YYYY-MM-DD-HH-mm-ss-mmm/output/model.tar.gz
