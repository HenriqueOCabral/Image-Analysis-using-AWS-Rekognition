<!--
title: 'AWS NodeJS Example'
description: 'This template demonstrates how to deploy a NodeJS function running on AWS Lambda using the traditional Serverless Framework.'
layout: Doc
framework: v2
platform: AWS
language: nodeJS
priority: 1
authorLink: 'https://github.com/serverless'
authorName: 'Serverless, inc.'
authorAvatar: 'https://avatars1.githubusercontent.com/u/13742415?s=200&v=4'
-->

# Image Analysis Using AWS Rekognition

### Serverless Framework AWS NodeJS Example

The project starts with this template demonstrates how to deploy a NodeJS function running on AWS Lambda using the traditional Serverless Framework. The deployed function does not include any event definitions as well as any kind of persistence (database). For more advanced configurations check out the [examples repo](https://github.com/serverless/examples/) which includes integrations with SQS, DynamoDB or examples of functions that are triggered in `cron`-like manner. For details about configuration of specific `events`, please refer to our [documentation](https://www.serverless.com/framework/docs/providers/aws/events/).

## Usage

Starting from the AWS NodeJs Example and move forward to build an application that will read an image using AWS Rekognition to retrieve it's labels and return the data translated to brazilian portuguese. Awesome, right?!!

** Project based on one of many classes in the a AWS Serverless Course developed by <a href="https://github.com/erickwendel">Erick Wendel</a> **

### Deployment

In order to deploy the example, you need to run the following command:

```
$ sls deploy
```

After running deploy, you should see output similar to:

```bash
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Creating Stack...
Serverless: Checking Stack create progress...
........
Serverless: Stack create finished...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service aws-node.zip file to S3 (711.23 KB)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
.................................
Serverless: Stack update finished...
Service Information
service: aws-node
stage: dev
region: us-east-1
stack: aws-node-dev
resources: 6
functions:
  api: aws-node-dev-hello
layers:
  None
```

### Invocation

After successful deployment, you can invoke the deployed function by using the following command:
* Using the request.json file we achive some freedom to test/manage the application requests whithout needing to use Jumpman or other any third party testing solution...

```bash
# See Functions Logs
sls invoke -f img-analysis --path request.json --log
# Call via AWS/Serverless Framework
sls invoke -f img-analysis --path request.json
```

Which should result in response similar to the following:

```json
{
    "statusCode": 200,
    "body": "A imagem tem\n  \n        94.43% de ser do tipo Cachorro-quente\n      \n \n        94.43% de ser do tipo alimentos\n      \n \n        84.39% de ser do tipo sanduíche\n      \n \n        82.45% de ser do tipo tigela\n      "
}
```

### Local development

You can invoke your function locally by using the following command:

```bash
sls invoke local -f img-analysis --path request.json
```

Which should result in response similar to the following:

```
{
    "statusCode": 200,
    "body": "A imagem tem\n  \n        94.43% de ser do tipo Cachorro-quente\n      \n \n        94.43% de ser do tipo alimentos\n      \n \n        84.39% de ser do tipo sanduíche\n      \n \n        82.45% de ser do tipo tigela\n      "
}
```

### Terminate

```bash
sls remove
```

