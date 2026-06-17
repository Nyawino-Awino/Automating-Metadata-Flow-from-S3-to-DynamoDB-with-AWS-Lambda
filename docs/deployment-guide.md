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





