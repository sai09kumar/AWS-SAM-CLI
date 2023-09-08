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
![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/ca1c7d63-bce4-46a0-bc85-a15eb10c60ba)



![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/7ade620c-3d49-4010-99f9-b9db62ffd4f8)

The app template you selected is cloned from the aws-sam-cli-app-templates repository and appears under DemoApp in the Project pane.

Now, to begin exploring the project's template.yaml file. With AWS SAM,  notice the stack templates closely follow the format of an AWS CloudFormation template file. This next section will highlight the subtle differences between the two types of template files.

Double click on template.yaml to explore:

![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/67a71096-a3b0-4c76-9c9e-11bab51538a0)

An AWS SAM template file must have the transform declaration, AWS::Serverless-2016-10-31. This identifies the template file as a SAM template, enabling the use of SAM resource definitions and global properties.

The Globals section is unique to SAM template files and defines property values that apply to all of the serverless functions and APIs within your application. The Function global consists of a Timeout value of 3 seconds and a MemorySize of 128.


![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/2f233e0d-af16-4b55-9a4f-3f1097b4dcef)

The HelloWorldFunction is an AWS::Serverless::Function type and is defined similarly to a CloudFormation AWS::Lambda::Function. The CodeUri property, points to the hello_world/ directory within DemoApp, with the Handler property pointing at the specific file and entry point app.lambda_handler. In the hello_world directory, you'll find a file named app.py with the lambda_handler function defined.

As mentioned previously, this stack deploys a Lambda function and an API endpoint that triggers it. In the AWS SAM template, will find the API defined as an Events property. The API, HelloWorld contains a single GET method call. When the GET request is made to the API, this function will be triggered. This implicit creation of an API reduces the amount of code needed to define a single endpoint.


![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/fee4cc3b-0f64-4bb8-9ed9-b289a3e4098c)

The Outputs section of SAM template files correspond directly with the Outputs section of a CloudFormation template. The HelloWorldApi value can be used to call the API once it is deployed to trigger the function.

Now, Below the HelloWorldFunction resource definition, add the following IAM Role property, ensuring it is indented at the same level as the existing properties:

```Role: arn:aws:iam::477763416030:role/LambdaBasicRole```

And now, Below the Outputs section, delete the following three lines of code that make up the HelloWorldFunctionIamRole output:
```
  HelloWorldFunctionIamRole:
  Description: "Implicit IAM Role created for Hello World function"
  Value: !GetAtt HelloWorldFunctionRole.Arn
```
The IAM Role or Policies of a Lambda function's execution role are implicitly configured with AWS SAM. These two changes allow you to provide a preconfigured IAM Role that permits the appropriate actions.

Now,
Open the hello_world/app.py file in the editor:
Check the code gives the message or not

![image](https://github.com/sai09kumar/AWS-SAM-CLI/assets/124625853/a14f72e8-5066-4c22-ba85-40f43ed20d0e)

The function in this quick start application does not perform any SDK actions. When this API is deployed and called, this function should return a simple hello, world message.










