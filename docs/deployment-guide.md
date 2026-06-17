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


