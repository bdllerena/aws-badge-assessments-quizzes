
## .NET Workloads on AWS Lambda

### Q1. Which AWS .NET tool lets you deploy Lambda functions from the command line? (select two)

- [ ] Amazon.ECS.Tools
- [x] Amazon.Lambda.Templates
- [x] Amazon.Lambda.Tools
- [ ] Amazon.Lambda.TestTool

To deploy AWS Lambda functions from the command line using .NET tools, there are a couple of options:

#### Amazon.Lambda.Templates

This is a set of templates provided by AWS that can be used with the .NET CLI to generate boilerplate code and configurations for your Lambda. To install the templates package, execute:

```
dotnet new --install Amazon.Lambda.Templates
```

After creating a project using these templates, you can deploy using the `deploy-function` command from `Amazon.Lambda.Tools`.

#### Amazon.Lambda.Tools

This is a .NET Core Global Tool that you can install and use from the command line. It's designed to make it easier to deploy and manage Lambda functions. To install the tool, use the following command:

```
dotnet tool install -g Amazon.Lambda.Tools
```

Once installed, you have access to a range of commands, including `deploy-function`, which is used to deploy your Lambda function. The `deploy-function` command has various options that allow you to specify the function name, role, and other configurations. For example, to deploy a function, you would use:

```
dotnet lambda deploy-function MyFunction --function-role role
```
[Reference](https://docs.aws.amazon.com/lambda/latest/dg/csharp-package-asp.html)

### Q2. What command do you use to deploy a Lambda function from the command line? (select one)

- [ ] donet aws deploy-function
- [ ] lambda deploy-function
- [x] dotnet lambda deploy-function
- [ ] dotnet lambda upload-function

When deploying, you typically navigate to your project directory and execute the `dotnet lambda deploy-function` command. The CLI will prompt you for the necessary information such as the AWS region and the function name. For an existing function, it will update the code. For a new function, it will create it and report "New Lambda function created" once successfully deployed.[Reference](https://docs.aws.amazon.com/sdk-for-net/v3/developer-guide/deploying-lambda.html)

### Q3. Which AWS IDE Toolkit(s) lets you invoke Lambda functions with sample requests from other services? (select one)

- [ ] Visual Studio Code
- [ ] Visual Studio
- [ ] Rider
- [x] All of these

The AWS IDE Toolkits allow invoking Lambda functions with requests from other services. Each of these toolkits provides functionality to interact with AWS services, invoke Lambda functions, and pass necessary parameters to view the responses.[Reference](https://aws.amazon.com/developer/language/net/badges-and-training/aws-lambda/module-two/)

### Q4. When using the Runtime Interface Emulator, how many function handlers can you test at a time? (select one)

- [ ] 1
- [ ] 2
- [ ] 3
- [x] More than 3

When using the Runtime Interface Emulator, you can test more than 3 function handlers at a time, but you would test each in turn. This is because when you start the container, you pass the appropriate function handler each time you run it. The Runtime Interface Emulator then uses this to execute the appropriate method in your application. So while you can have multiple function handlers in your code, each invocation can target a specific function handler. [Reference](https://aws.amazon.com/developer/language/net/badges-and-training/aws-lambda/module-five/) 

### Q5. What are the two types of concurrency supported by Lambda functions? (select two)

- [ ] Optimistic
- [x] Reserved
- [x] Provisioned
- [ ] Pessimistic

The two types of concurrency controls available in AWS Lambda are Reserved Concurrency and Provisioned Concurrency. Reserved Concurrency is the maximum number of concurrent instances allocated to a specific function, ensuring that the function can always process up to the specified number of concurrent executions. This reserved concurrency is dedicated exclusively to the function and cannot be used by other functions. On the other hand, Provisioned Concurrency refers to the number of execution environments that are pre-initialized and always ready to immediately respond to function invocations, thereby avoiding cold starts and ensuring lower latency for function execution.[Reference](https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html)

### Q6. Which one of the following can you specify when deploying a Lambda function? (select one)

- [ ] The network bandwidth allocation
- [x] The memory allocation
- [ ] The CPU speed
- [ ] File IO capacity

When deploying a Lambda function, you can specify the memory allocation for the function. This allocation indirectly determines the CPU resources and network bandwidth allocated to the function. AWS Lambda allocates CPU linearly in proportion to the amount of memory configured. Network bandwidth allocation also increases with the memory size you specify for the function. Therefore, although not directly configurable, the CPU speed and network bandwidth are scaled by AWS based on the memory allocation provided. It's important to note that AWS Lambda does not allow explicit definition of CPU speed, network bandwidth, or file I/O capacity, as these are managed by AWS based on the memory configuration and execution environment.[Reference](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html)

### Q7. True or False: You can create your own types to pass to Lambda function handlers.

- [x] True
- [ ] False

You can create your own types to pass to Lambda function handlers. This is a common practice, especially in typed languages like TypeScript, where you can define custom types for the event and context objects received by the Lambda function, as well as for the function handler's return type. This enhances type safety and can help prevent errors by enabling type-checking features and autocomplete in the development environment.[Reference](https://docs.aws.amazon.com/lambda/latest/dg/csharp-handler.html)

### Q8. What AWS infrastructure do you need to create before you can deploy a Lambda function based on a serverless template? (select one)

- [ ] An S3 bucket
- [x] A cloud formation stack
- [ ] A CodeBuild project
- [ ] A SAM template

AWS CloudFormation allows modeling the entire infrastructure in a text file template, which can then be used to provision and manage AWS resources, including Lambda functions, as a single unit called a stack. When deploying a Lambda function with a serverless template such as AWS's Serverless Application Model (SAM), CloudFormation is used to deploy the resources defined in the SAM template.[Reference](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/quickref-lambda.html)

### Q9. What are two reasons you might use a .NET custom runtime? (select two)

- [x] You want to use a version of .NET that is not available as a managed runtime
- [ ] You want to use ahead of time compilation
- [ ] You want control over minor and patch versions of version of .NET that is available as a managed runtime
- [x] You want to include less popular NuGet packages in your application

#### You want to use a version of .NET that is not available as a managed runtime

AWS Lambda periodically updates the execution environments it supports, but there might be a lag between the release of a new .NET version and when AWS Lambda provides a managed runtime environment for it. To use a more recent version of .NET not yet supported by AWS Lambda's managed execution environments, a custom runtime is required. For instance, if AWS Lambda supports .NET 6 as a managed runtime but you wish to use .NET 7, a custom runtime is needed.[Reference](https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html) 

#### You want to include less popular NuGet packages in your application

Managed runtimes of AWS Lambda offer support for a specific major version of .NET, like .NET 6, but you might need a specific minor or patch version due to dependencies or particular features. A custom runtime allows specifying the exact version of .NET you wish to use, down to the minor and patch level, and updating it on your own schedule. This can be crucial for maintaining consistency with other parts of the infrastructure or ensuring compatibility with certain libraries.[Reference](https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html)

### Q10. Where can you find the .NET type to handle incoming S3 events for your function handler? (select one)

- [ ] You don't need a specific type
- [x] In the AWSSDK.Lambda.S3Events NuGet package
- [ ] In the AWSSDK.S3.package
- [ ] In the AWSSDK.Lambda package

The .NET type to handle incoming S3 events for the function handler can be found in the `AWSSDK.Lambda.S3Events NuGet package`. This package contains the necessary types to manage S3 event notifications in a .NET Lambda function, enabling work with event details such as the bucket name and object key involved in the event. It is specifically designed to work with Lambda functions that respond to S3 event triggers.[Reference](https://www.nuget.org/packages/Amazon.Lambda.S3Events)

### Q11. When working with a Lambda function based on a serverless.* template, what do you need to change to handle different event types? (select one)

- [ ] the NuGet packages referenced in the csproj file
- [ ] what CreateHostBuilder returns
- [ ] the base class a controller inherits from
- [x] the type LambdaEntryPoint inherits from

To handle different types of events, you often need to modify the `LambdaEntryPoint` because it determines how incoming events are processed and routed within the application. This type corresponds to the method AWS Lambda calls when the function is invoked. For example, if you are handling an S3 event, `LambdaEntryPoint` may inherit from a class capable of processing S3 event payloads.[Referencia](https://docs.aws.amazon.com/toolkit-for-visual-studio/latest/user-guide/lambda-build-test-severless-app.html)

### Q12. For Lambda functions based on the serverless templates, in which file is the function handler configured? (select one)

- [x] serverless.template
- [ ] lambda.csproj
- [ ] aws-lambda-tools-defaults.json

The serverless.template is the AWS CloudFormation template file used to define AWS resources, including the Lambda function. The handler is defined in the Properties section of the `AWS::Serverless::Function` resource. It defines the function name and the handler method (e.g., `"Handler": "Namespace.ClassName::MethodName"`), which AWS Lambda can call when the function is invoked.
[Reference](https://docs.aws.amazon.com/toolkit-for-visual-studio/latest/user-guide/lambda-build-test-severless-app.html)

### Q13. If you want your Lambda function to handle Kinesis events, what NuGet package contains the type that represents a Kinesis event? (select one)

- [ ] Amazon.Lambda.Core
- [x] Amazon.Lambda.KinesisEvents
- [ ] Amazon.Lambda.Tools
- [ ] Amazon.Lambda.AspNetCoreServer

The correct NuGet package is `Amazon.Lambda.KinesisEvents`. This package includes the necessary types to handle Amazon Kinesis event sources in AWS Lambda functions, allowing developers to work directly with Kinesis events within their .NET code.[Reference](https://www.nuget.org/packages/Amazon.Lambda.KinesisEvents/)

### Q14. True or False: Lambda functions support the C# async keyword. (select one)

- [x] True
- [ ] False

AWS Lambda functions support the C# async keyword. This allows writing asynchronous function handlers, enabling non-blocking I/O operations, awaiting asynchronous method calls, and enhancing the scalability of the Lambda function. The Lambda runtime for C# supports asynchronous methods that return `Task` or `Task<T>`, which are awaited by the runtime itself when invoking the function handler. This is a key feature of C#, and AWS Lambda fully supports modern asynchronous programming paradigms.[Reference](https://docs.aws.amazon.com/lambda/latest/dg/csharp-handler.html)

### Q15. What takes place using a cold start? (select all that apply)

- [ ] Downloading the Lambda code/image
- [ ] Deploying the function
- [x] Creating the execution environment
- [x] Running the initialization code
- [ ] Executing the function handler

During a cold start of an AWS Lambda function, the following actions occur:

#### Creating the execution environment
AWS Lambda prepares a new execution environment, which includes provisioning a container and setting up the required runtime.

#### Running the initialization code
Any Lambda function initialization code, such as static constructors or global variables, is executed.

Cold starts do not involve downloading the Lambda code/image, deploying the function, or executing the function handler. These actions are part of the function deployment process or the invocation phase, not the cold start process. The function handler is executed once the cold start process has completed, and the Lambda function is actually invoked.

[Reference](https://docs.aws.amazon.com/lambda/latest/operatorguide/execution-environments.html)


### Q16. When adding permissions to the role a Lambda function will run under, should you? (select one)

- [ ] Grant every possible permission
- [x] Grant the fewest permissions possible

When adding permissions to the role under which a Lambda function will run, you should adhere to the principle of granting the fewest permissions possible. This principle is known as the principle of least privilege, and it is one of the best practices in security. It means granting only the permissions necessary to perform the required tasks.[Reference](https://docs.aws.amazon.com/wellarchitected/latest/framework/sec_permissions_least_privileges.html)
