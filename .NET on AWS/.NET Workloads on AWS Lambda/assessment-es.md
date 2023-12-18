## .NET Workloads on AWS Lambda

### Q1. Which AWS .NET tool lets you deploy Lambda functions from the command line? (select two)

- [ ] Amazon.ECS.Tools
- [x] Amazon.Lambda.Templates
- [x] Amazon.Lambda.Tools
- [ ] Amazon.Lambda.TestTool

Para implementar funciones de AWS Lambda desde la línea de comandos utilizando herramientas .NET, existe un par de opciones:

#### Amazon.Lambda.Templates

Es un conjunto de templates proporcionadas por AWS que se pueden utilizar con la CLI de .NET para generar codigo generico y configuraciones de la lambda. Para instalar el paquete de templates, se debe ejecutar
```
dotnet new --install Amazon.Lambda.Templates
```
Después de crear un proyecto utilizando estos templates, se puede desplegar utilizando el comando `deploy-function` desde `Amazon.Lambda.Tools`.

#### Amazon.Lambda.Tools

Es una herramienta global .NET Core que se puede instalar y utilizar desde la línea de comandos. Está diseñada para facilitar el despliegue y la gestión de las funciones Lambda. Para instalar la herramienta, se utiliza el siguiente comando:

```
dotnet tool install -g Amazon.Lambda.Tools
```

Una vez instalado, tendrá acceso a una serie de comandos, incluido `deploy-function`, que se utiliza para desplegar la función Lambda. El comando `deploy-function` tiene varias opciones que permiten especificar el nombre de la función, el rol y otras configuraciones. Por ejemplo, para desplegar una función, se utilizaría:
```
dotnet lambda deploy-function MyFunction --function-role role
```
[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/csharp-package-asp.html)

### Q2. What command do you use to deploy a Lambda function from the command line? (select one)

- [ ] donet aws deploy-function
- [ ] lambda deploy-function
- [x] dotnet lambda deploy-function
- [ ] dotnet lambda upload-function

Al desplegar, normalmente se navega al directorio del proyecto y se ejecuta el comando `dotnet lambda deploy-function`. La CLI pedirá información necesaria, como la región de AWS y el nombre de la función. Para una función existente, actualizará el código. Si se trata de una función nueva, la creará e informará de que se ha creado una nueva función Lambda una vez que se haya desplegado correctamente.[Referencia](https://docs.aws.amazon.com/sdk-for-net/v3/developer-guide/deploying-lambda.html)

### Q3. Which AWS IDE Toolkit(s) lets you invoke Lambda functions with sample requests from other services? (select one)

- [ ] Visual Studio Code
- [ ] Visual Studio
- [ ] Rider
- [x] All of these

Los Toolkits de AWS IDE permite invocar funciones de Lambda con solicitudes de otros servicios. Cada uno de estos toolkits proporciona funcionalidad para interactuar con los servicios de AWS, invocar funciones de Lambda y pasar los parámetros necesarios para ver los responses.[Referencia](https://aws.amazon.com/developer/language/net/badges-and-training/aws-lambda/module-two/)

### Q4. When using the Runtime Interface Emulator, how many function handlers can you test at a time? (select one)

- [ ] 1
- [ ] 2
- [ ] 3
- [x] More than 3

Cuando se utiliza el Runtime Interface Emulator, se puede probar más de 3 handlers de la función a la vez, pero se probaría cada uno por turno.Esto se debe a que cuando se inicia el contenedor, pasa el handler de la función apropiado cada vez que se ejecuta. El Runtime Interface Emulator lo utiliza para ejecutar el método apropiado en la aplicación. Así, mientras que se puede tener múltiples handlers de la función en el código, cada invocación puede dirigirse a un handler de función específico. [Referencia](https://aws.amazon.com/developer/language/net/badges-and-training/aws-lambda/module-five/) 

### Q5. What are the two types of concurrency supported by Lambda functions? (select two)

- [ ] Optimistic
- [x] Reserved
- [x] Provisioned
- [ ] Pessimistic

Los dos tipos de controles de concurrencia disponibles en AWS Lambda son la concurrencia reservada (Reserved) y la concurrencia aprovisionada(Provisioned).La concurrencia reservada es el número máximo de instancias concurrentes que se asignan a una función específica, lo que garantiza que la función siempre pueda procesar hasta el número especificado de ejecuciones concurrentes.Esta concurrencia reservada está dedicada exclusivamente a la función y no puede ser utilizada por otras funciones.Por otro lado, la concurrencia aprovisionada es el número de entornos de ejecución que están pre-inicializados y siempre listos para responder inmediatamente a las invocaciones de la función, evitando así los arranques en frío y garantizando menor latencia para la ejecución de la función.[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html)

### Q6. Which one of the following can you specify when deploying a Lambda function? (select one)

- [ ] The network bandwidth allocation
- [x] The memory allocation
- [ ] The CPU speed
- [ ] File IO capacity

Al desplegar una función Lambda, se puede especificar la asignación de memoria para la función. Esta asignación determina indirectamente los recursos de CPU y ancho de banda de red asignados a la función. AWS Lambda asigna la CPU linealmente en proporción a la cantidad de memoria configurada. La asignación de ancho de banda de red también aumenta con el tamaño de memoria que especifique para la función. Por lo tanto, aunque no se configure directamente la velocidad del CPU o el ancho de banda de red, estos son escalados por AWS en función de la asignación de memoria que se proporcione. Es importante tener en cuenta que AWS Lambda no permite definir explícitamente la velocidad de la CPU o el ancho de banda de la red, ni la capacidad de I/O de archivos, ya que AWS Lambda los administra en función de la configuración de la memoria y el entorno de ejecución.[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html)

### Q7. True or False: You can create your own types to pass to Lambda function handlers.

- [x] True
- [ ] False

Puedes crear tus propios tipos para pasarlos a los handlers de la función Lambda. Esta es una práctica común, especialmente en lenguajes tipados como TypeScript, donde se puede definir tipos personalizados para los objetos de evento y contexto que recibe la función Lambda, así como para el tipo de retorno de la función handler. Esto mejora la seguridad tipográfica y puede ayudar a prevenir errores al habilitar funciones de comprobación de tipos y autocompletado en el entorno de desarrollo.[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/csharp-handler.html)

### Q8. What AWS infrastructure do you need to create before you can deploy a Lambda function based on a serverless template? (select one)

- [ ] An S3 bucket
- [x] A cloud formation stack
- [ ] A CodeBuild project
- [ ] A SAM template

AWS CloudFormation permite modelar toda la infraestructura en un template de archivo de texto, que luego se puede utilizar para aprovisionar y administrar recursos de AWS, incluidas las funciones de Lambda, como una única unidad denominada stack. Al implementar una función Lambda con un template sin servidor (serverless) como el modelo de aplicación sin servidor (SAM) de AWS, CloudFormation se utiliza para implementar los recursos definidos en el template SAM.[Referencia](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/quickref-lambda.html)

### Q9. What are two reasons you might use a .NET custom runtime? (select two)

- [x] You want to use a version of .NET that is not available as a managed runtime
- [ ] You want to use ahead of time compilation
- [ ] You want control over minor and patch versions of version of .NET that is available as a managed runtime
- [x] You want to include less popular NuGet packages in your application

#### You want to use a version of .NET that is not available as a managed runtime

AWS Lambda actualiza periódicamente los entornos de ejecución que admite, pero puede haber un desfase entre el lanzamiento de una nueva versión de .NET y el momento en que AWS Lambda proporciona un entorno de ejecución administrado para ella. Si se desea utilizar una versión más reciente de .NET que aún no es compatible con los entorn de ejecución administrados por AWS Lambda, se deberá crear un entorno de ejecución personalizado. Por ejemplo, si AWS Lambda admite .NET 6 como entorno de ejecución administrado pero se desea utilizar .NET 7, deberá utilizar un entorno de ejecución personalizado.[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html) 

#### You want to include less popular NuGet packages in your application

Los entorno de ejecución administrados de AWS Lambda ofrecen compatibilidad con una versión principal específica de .NET, como .NET 6, pero es posible que necesite una versión menor o de parche específica debido a dependencias o características concretas. Un entorno de ejecución personalizado permite especificar la versión exacta de .NET que se desea utilizar, hasta el nivel menor y de parche, y actualizarla según su propio calendario. Esto puede ser fundamental para mantener la coherencia con otras partes de la infraestructura o garantizar la compatibilidad con determinadas bibliotecas.[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html)

### Q10. Where can you find the .NET type to handle incoming S3 events for your function handler? (select one)

- [ ] You don't need a specific type
- [x] In the AWSSDK.Lambda.S3Events NuGet package
- [ ] In the AWSSDK.S3.package
- [ ] In the AWSSDK.Lambda package

El type .NET para manejar eventos S3 entrantes para el handler de funciones se puede encontrar en el paquete AWSSDK.Lambda.S3Events NuGet. Este paquete contiene los type necesarios para gestionar las notificaciones de eventos de S3 en una función .NET Lambda, lo que permite trabajar con los detalles del evento, como el nombre del bucket y la clave de objeto implicados en el evento. Está diseñado específicamente para trabajar con funciones Lambda que responden a triggers de eventos de S3.[Referencia](https://www.nuget.org/packages/Amazon.Lambda.S3Events)

### Q11. When working with a Lambda function based on a serverless.* template, what do you need to change to handle different event types? (select one)

- [ ] the NuGet packages referenced in the csproj file
- [ ] what CreateHostBuilder returns
- [ ] the base class a controller inherits from
- [x] the type LambdaEntryPoint inherits from

Cuando se necesita manejar diferentes tipos de eventos, a menudo se necesita modificar el LambdaEntryPoint porque determina cómo se procesan y enrutan los eventos entrantes dentro de la aplicación. Este tipo corresponde al método que AWS Lambda llama cuando se invoca la función. Por ejemplo, si se está gestionando un evento de S3, el LambdaEntryPoint puede heredar de una clase capaz de procesar cargas útiles de eventos de S3.[Referencia](https://docs.aws.amazon.com/toolkit-for-visual-studio/latest/user-guide/lambda-build-test-severless-app.html)

### Q12. For Lambda functions based on the serverless templates, in which file is the function handler configured? (select one)

- [x] serverless.template
- [ ] lambda.csproj
- [ ] aws-lambda-tools-defaults.json

Este es el archivo de template de AWS CloudFormation que se utiliza para definir los recursos de AWS, incluida la función de Lambda. El handler se define en la sección Properties del recurso AWS::Serverless::Function. Define el nombre de la función y el método del handler (por ejemplo, "Handler": "Namespace.ClassName::MethodName"), que AWS Lambda puede llamar cuando se invoca la función.
[Referencia](https://docs.aws.amazon.com/toolkit-for-visual-studio/latest/user-guide/lambda-build-test-severless-app.html)

### Q13. If you want your Lambda function to handle Kinesis events, what NuGet package contains the type that represents a Kinesis event? (select one)

- [ ] Amazon.Lambda.Core
- [x] Amazon.Lambda.KinesisEvents
- [ ] Amazon.Lambda.Tools
- [ ] Amazon.Lambda.AspNetCoreServer

El paquete NuGet correcto es Amazon.Lambda.KinesisEvents. Este paquete incluye los type necesarios para manejar fuentes de eventos de Amazon Kinesis en funciones de AWS Lambda, lo que permite a los desarrolladores trabajar con eventos de Kinesis directamente dentro de del código .NET.[Referencia](https://www.nuget.org/packages/Amazon.Lambda.KinesisEvents/)

### Q14. True or False: Lambda functions support the C# async keyword. (select one)

- [x] True
- [ ] False

Las funciones de AWS Lambda admiten la palabra clave `async` de C#. Esto permite escribir handlers de funciones asíncronas, lo que hace posible realizar operaciones de I/O sin bloqueo, esperar llamadas a métodos asíncronos y mejorar la escalabilidad de la función Lambda.El tiempo de ejecución de Lambda para C# admite métodos asíncronos que devuelven `Task` o `Task<T>`, que son esperados por el propio tiempo de ejecución al invocar el handler de la función. Esta es una característica clave de C#, y AWS Lambda es totalmente compatible con los paradigmas modernos de programación asíncrona.[Referencia](https://docs.aws.amazon.com/lambda/latest/dg/csharp-handler.html)

### Q15. What takes place using a cold start? (select all that apply)

- [ ] Downloading the Lambda code/image
- [ ] Deploying the function
- [x] Creating the execution environment
- [x] Running the initialization code
- [ ] Executing the function handler

Durante el arranque en frío de una función de AWS Lambda, se llevan a cabo las siguientes acciones:

Creating the execution environment:AWS Lambda prepara un nuevo entorno de ejecución, que incluye el aprovisionamiento de un contenedor y la configuración del tiempo de ejecución necesario.

Running the initialization code: Se ejecuta cualquier código de inicialización de la función Lambda, como constructores estáticos o variables globales.

Los arranques en frío no implican la descarga del código/imagen de Lambda, el despliegue de la función ni la ejecución del handler de la función. Estas acciones forman parte del proceso de despliegue de la función o de la fase de invocación, no del proceso de arranque en frío. El handler de la función se ejecuta una vez que el proceso de arranque en frío ha finalizado y la función Lambda es realmente invocada.[Referencia](https://docs.aws.amazon.com/lambda/latest/operatorguide/execution-environments.html)


### Q16. When adding permissions to the role a Lambda function will run under, should you? (select one)

- [ ] Grant every possible permission
- [x] Grant the fewest permissions possible

Cuando se añada permisos al rol bajo el que se ejecutará una función Lambda se debe considerar el principio de Grant the fewest permissions possible.
Este principio se conoce como el principio del menor privilegio, y es una de las mejores prácticas de seguridad. Significa dar sólo los permisos necesarios para realizar las tareas requeridas.
[Referencia](https://docs.aws.amazon.com/wellarchitected/latest/framework/sec_permissions_least_privileges.html)
