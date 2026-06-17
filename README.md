# Automating-Metadata-Flow-from-S3-to-DynamoDB-with-AWS-Lambda
This guide provides a detailed, step-by-step approach to implementing an automated metadata extraction and storage solution using Amazon S, AWS Lambda, and AmazonDynamoDB. This architecture is ideal for scenarios where you need to process newly uploaded files in S3, extract specific metadata, and store it in a highly scalable NoSQL database for quick retrieval and analysis. This pattern is fundamental for building data lakes, content management systems, digital asset management,complianace and auditing and event-driven architectures.

# Architecture Overview
The solution leverages three core AWS services:
- **Amazon S3 (Simple Storage Service)**: Acts as the primary storage for your files. When a new object is uploaded to a designated S3 bucket, it triggers an event.
- **AWS Lambda**: A serverless compute service that executes code in response to events. In this architecture, Lambda is triggered by S3 object creation events. It extracts relevant metadata from the S3 object and prepares it for storage.
- **Amazon DynamoDB**: A fast, flexible NoSQL database service for single-digit millisecond performance at any scale. It will store the extracted metadata, making it easily queryable.

## Architecture

![Architecture Diagram](architecture/aws_metadata_flow.png)

The flow is straightforward: an **S3 Event** (e.g., a new file upload) triggers an **AWS Lambda** function, which then extracts **Metadata** from the S3 object and writes it to an **Amazon DynamoDB table**.

## Deployment

Refer to: ![Documentation](docs/deployment-guide.md)

## Testing

Upload any file into the configured S3 bucket and verify that metadata appears in DynamoDB.

## Conclusion
You have successfully implemented an automated metadata flow from S3 to DynamoDB using AWS Lambda. This serverless architecture provides a scalable, cost-effective, and efficient way to process file uploads and manage their associated metadata. You can extend this solution by extracting more complex metadata, integrating with other AWS services, or building a frontend application to search and display the metadata.

## References
AWS CLI Installation and Configuration: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html
Amazon S3 Documentation: https://docs.aws.amazon.com/s3/index.html
AWS Lambda Documentation: https://docs.aws.amazon.com/lambda/index.html
Amazon DynamoDB Documentation: https://docs.aws.amazon.com/dynamodb/index.html


## Author
Rhoda Ndege
Cloud Engineer
