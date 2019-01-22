<h1 align="center"> Invoke Lambda With SQS </h1>

<div align="center">
    <img src="https://github.com/Shwetabh1/LambdaWithSQS/blob/master/images/sqs_lambda.png" alt="Lambda with SQS" width="750" height="360"/>
  <br>
</div>


## What is this?
> You can never understand everything but you should push yourself to understand the system.<br/>
> *-Ryan Dahl (creator of Node.JS)*

This repository aims to explain the what, why and how of working with AWS Lambda and SQS, in a simplified manner.

## Table of Contents
1. Why this Combination?
1. Working With SQS.
1. Working with Lambda.
1. Adding Triggers.
1. Optimization and other concerns.
1. Useful Links

### 1. Why this Combination?
Lambda and SQS both are cheap. The first 1 million request for Lambda per month is free. $0.20 per 1 million requests thereafter.<br/>
Lambda also provides automatic scaling and provisioning.
SQS offers resiliency, Durability, Security, at least once delivery and Scalability. <br/>
The cost of Amazon SQS is calculated per request, plus data transfer charges for data transferred out of Amazon SQS (unless data is transferred to Amazon EC2 instances or to AWS Lambda functions within the same region).

### 2. Working With SQS.
<div align="center">
<img src="https://github.com/Shwetabh1/LambdaWithSQS/blob/master/images/aws_sqs.png" alt="AWS SQS" width="450" height="200"/>
</div>
AWS Simple Queue Service can be used as an event source to invoke Lambda Function. SQS offers two types of Queues. <br/>
1. Simple Queue <br/>
2. FIFO Queue <br/>

Keep in mind AWS Lambda can only work with Simple Queue. The queue by default uses short polling but in the case of Lambda long polling is used. What is short polling and long polling? The default short polling returns immediately, even if the message queue being polled is empty, long polling doesn’t return a response until a message arrives in the message queue, or the long poll times out.
You can use the AWS Management Console or the AWS SDKs (in the programming language of your choice) to create and interact with SQS.

### 3. Working with Lambda.
AWS Lambda is a compute service where you can upload your code and create a Lambda function. AWS Lambda takes care of provisioning and managing the servers that you use to run the code. You don't have to worry about operating systems, patching scaling etc.

You need to understand the following to start working with Lambda
1. Attaching Roles (Execution Role)
2. Versioning
3. Concurrency
4. Function Timeout
5. Handler Name
6. Deploying Packages or Editing Inline

### 4. Adding Triggers.
Triggers can be added once your Lambda Function is ready. Choose the function and under Add triggers, choose SQS. Configure the SQS queue and Batch Size. Lambda reads messages in batches and invokes your function once for each batch.<br> Batch Size specifies the maximum number of items to read from the queue and send to your function, in a single invocation. However, if your function returns an error, all items in the batch return to the queue so choose a smaller batch size. 

### 5. Optimization and other concerns.
Handling Concurrency. <br/>
Handling Errors. <br/>
Dead Letter Queue. <br/>

### 6. Useful Links
https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html#events-sqs-eventsource <br/>
https://docs.aws.amazon.com/lambda/latest/dg/java-programming-model.html <br/>
https://read.acloud.guru/event-driven-architecture-with-sqs-and-aws-lambda-cf2ebd529ae3
