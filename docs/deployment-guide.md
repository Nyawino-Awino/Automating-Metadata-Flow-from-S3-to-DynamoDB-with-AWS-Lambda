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
