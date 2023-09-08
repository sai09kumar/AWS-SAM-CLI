# AWS-SAM-CLI

## Lab Description

The AWS Serverless Application Model (SAM) CLI is a tool to build serverless applications that are defined using AWS SAM templates. The CLI consists of commands that allow you to define, test, and deploy your serverless applications.
In this lab, I worked with the AWS SAM CLI in an IDE environment that is configured to an AWS account. The IDE environment will allowed initialize, configure, and deploy a quick start application to AWS, without using the AWS console directly. I deployed a simple Hello World application to experience the easy-to-use commands provided by the AWS SAM CLI.

## Learning objectives

1. Initialize an AWS SAM project
2. Deploy a simple API and Lambda function using the SAM CLI

## Prerequsites

1. AWS Serverless Application Model (SAM)
2. AWS Lambda
3. Amazon API Gateway

Enviornment Before
![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/099b19d6-8f25-4267-8471-28ffcc082b21)

Enviornment After

![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/dc2ed516-4229-4434-b3dd-98b7e3372a9b)

## First Step

In this step, I configured the AWS credentials needed to use the AWS SAM CLI.

In the IDE editor opwn the terminal and select new terminal and run following commands:
```
aws configure set aws_access_key_id AKIAW6PHLF7PNX2T5CI3 &&
aws configure set aws_secret_access_key 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 &&
aws configure set default.region us-west-2
```
Enter ``` aws configuration list``` to confirm credentials



