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
