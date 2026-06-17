## Step-by-Step Implementation Guide

**Step 1: Create an IAM Role for Lambda**
- Go to **IAM** on AWS Console
- Click **Role** - **Create a Role**
  - On Trusted Entity Type: AWS Service
  - Use Case: Select Lambda
- **Add Permissions**:
  - AmazonDynamoDBFullAccess
  - AmazonS3ReadOnlyAccess
- Click **Next**
- **Role Name** for example: *Lambda_DynamoDB_Role*
- Review the **Role**.
- Click **Create Role**

**Step 2: Create an S3 Bucket**
- On the AWS Console; Search for S3
- Click **Create a Bucket**
- Fill in:
  - Bucket Name: *mys3bucket*
  - Object Ownership: *ACL enabled*
  - **Disable**: Block Public Access
- Click **Create Bucket**

**Step 3: Create a DynamoDB Table**
- On the AWS Console, search for AWS DynamoDB.
- Click **Create Table**
- Create a table and use default settings
- Fill in:
  - Table Name: e.g., *MyDynamoDBTable*
  - Partition Key: *unique*
  - Table Settings: Leave as default.
- Click **Create Table**

**Step 4: Create a Lambda Function**

AWS Lambda is a serverless computing services that allows you to run code without provisioning or managing services. 
- On AWS Console, Search for **AWS Lambda**
- Click **Create Function**
- Choose:
  - Author from Scratch
  - Name: *S3ToDynamoFunction*
  - Runtime: *Python 3.10/3.9/3.11*
  - Permissions: Use existing role: select *Lambda_DynamoDB_Role*
- Click **Create Function**

**Step 5: Add the Lambda Code.**

In the Lambda editor, *paste this code:*
''' pthython
import boto3
from uuid import uuid4 
 
s3 = boto3.client('s3') 
dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('S3DynamoDBtable')

#Get the object from the event and show its content type
def lambda_handler(event, context):     
    for record in event['Records']: 
        bucket_name = record['s3']['bucket']['name']         
        object_key = record['s3']['object']['key']         
        event_name = record['eventName']         
        event_time = record['eventTime'] 
 
         #Get object metadata       
         try: 
            meta = s3.head_object(Bucket=bucket_name, Key=object_key)             
            size = meta['ContentLength']         
         except Exception as e: 
            print(f"Failed to get metadata: {e}")             
            size = -1 
         
         #Prepare item for DynamoDB   
         table.put_item(Item={ 
            'unique': str(uuid4()), 
            'Bucket': bucket_name, 
            'Object': object_key, 
            'Size': size, 
            'Event_name': event_name, 
            'Event_time': event_time 
        }) 
Click **Deploy**

**Step 6: Add an S3 Trigger**

On the same **Lambda Function** page, go to *“Configuration → Triggers”*
Click **Add trigger** 





