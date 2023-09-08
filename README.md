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

![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/cf281897-0b69-46f0-af5d-87910d728a33)

Before moving to next step open explorer and check the files by expanding project pane

## Second Step

In this step, I initialized an AWS SAM Quick Start application that deploys a Lambda function and an API Gateway and reviewed the AWS SAM template file to get a better understanding of its differences with AWS CloudFormation.

To initialize a new SAM project, enter the command ```sam init --name DemoApp``` in the terminal.

Select the following choices:

```
1. Which template source would you like to use?: 1-AWS Quick Start Templates
2.Choose an AWS Quick Start application template: 1-Hello World Example
3.Use the most popular runtime and package type? (Python and zip): y
4. Would you like to enable X-Ray tracing on the function(s) in your application?: N
5. Would you like to enable monitoring using CloudWatch Application Insights?: N

```





