---
title: "Quickstart: Azure management client library for Java"
description: In this quickstart, get started with the Azure management client library for Java.
services: cognitive-services
author: PatrickFarley
manager: nitinme
ms.service: cognitive-services
ms.topic: include
ms.date: 06/04/2021
ms.author: pafarley
---

[Reference documentation](/java/api/com.microsoft.azure.management.cognitiveservices) | [Library source code](https://github.com/Azure/azure-sdk-for-java/tree/main/sdk/cognitiveservices/azure-resourcemanager-cognitiveservices/src/main/java/com/azure/resourcemanager/cognitiveservices) | [Package (Maven)](https://mvnrepository.com/artifact/com.microsoft.azure/azure-mgmt-cognitiveservices)

## Java prerequisites

* A valid Azure subscription - [Create one for free](https://azure.microsoft.com/free/).
* The current version of the [Java Development Kit(JDK)](https://www.oracle.com/technetwork/java/javase/downloads/index.html)
* The [Gradle build tool](https://gradle.org/install/), or another dependency manager.
* [!INCLUDE [contributor-requirement](./contributor-requirement.md)]
* [!INCLUDE [terms-azure-portal](./terms-azure-portal.md)]


[!INCLUDE [Create a service principal](./create-service-principal.md)]

[!INCLUDE [Create a resource group](./create-resource-group.md)]

## Create a new Java application

In a console window (such as cmd, PowerShell, or Bash), create a new directory for your app, and navigate to it. 

```console
mkdir myapp && cd myapp
```

Run the `gradle init` command from your working directory. This command will create essential build files for Gradle, including *build.gradle.kts* which is used at runtime to create and configure your application.

```console
gradle init --type basic
```

When prompted to choose a **DSL**, select **Kotlin**.

From your working directory, run the following command:

```console
mkdir -p src/main/java
```

### Install the client library

This quickstart uses the Gradle dependency manager. You can find the client library and information for other dependency managers on the [Maven Central Repository](https://mvnrepository.com/artifact/com.azure/azure-ai-formrecognizer).

In your project's *build.gradle.kts* file, include the client library as an `implementation` statement, along with the required plugins and settings.

```kotlin
plugins {
    java
    application
}
application {
    mainClass.set("FormRecognizer")
}
repositories {
    mavenCentral()
}
dependencies {
    implementation(group = "com.microsoft.azure", name = "azure-mgmt-cognitiveservices", version = "1.10.0-beta")
}
```

### Import libraries

Navigate to the new **src/main/java** folder and create a file called *Management.java*. Open it in your preferred editor or IDE and add the following `import` statements:

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_imports)]

## Authenticate the client

Add a class in *Management.java*, and then add the following fields and their values inside of it. Populate their values, using the service principal you created and your other Azure account information.

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_constants)]

Then, in your **main** method, use these values to construct a **CognitiveServicesManager** object. This object is needed for all of your Azure management operations.

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_auth)]

## Call management methods

Add the following code to your **Main** method to list available resources, create a sample resource, list your owned resources, and then delete the sample resource. You'll define these methods in the next steps.

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_calls)]

## Create a Cognitive Services resource (Java)

To create and subscribe to a new Cognitive Services resource, use the **create** method. This method adds a new billable resource to the resource group you pass in. When creating your new resource, you'll need to know the "kind" of service you want to use, along with its pricing tier (or SKU) and an Azure location. The following method takes all of these as arguments and creates a resource.

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_create)]

### Choose a service and pricing tier

When you create a new resource, you'll need to know the "kind" of service you want to use, along with the [pricing tier](https://azure.microsoft.com/pricing/details/cognitive-services/) (or SKU) you want. You'll use this and other information as parameters when creating the resource. You can find a list of available Cognitive Service "kinds" by calling the following method:

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_list_avail)]

[!INCLUDE [cognitive-services-subscription-types](../../../../includes/cognitive-services-subscription-types.md)]

[!INCLUDE [SKUs and pricing](./sku-pricing.md)]

## View your resources

To view all of the resources under your Azure account (across all resource groups), use the following method:

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_list)]

## Delete a resource

The following method deletes the specified resource from the given resource group.

[!code-java[](~/cognitive-services-quickstart-code/java/azure_management_service/quickstart.java?name=snippet_delete)]

If you need to recover a deleted resource, see [Recover deleted Cognitive Services resources](../../manage-resources.md).

## See also

* See **[Authenticate requests to Azure Cognitive Services](../../authentication.md)** on how to securely work with Cognitive Services.
* See **[What are Azure Cognitive Services?](../../what-are-cognitive-services.md)** to get a list of different categories within Cognitive Services.
* See **[Natural language support](../../language-support.md)** to see the list of natural languages that Cognitive Services supports.
* See **[Use Cognitive Services as containers](../../cognitive-services-container-support.md)** to understand how to use Cognitive Services on-prem.
* See **[Plan and manage costs for Cognitive Services](../../plan-manage-costs.md)** to estimate cost of using Cognitive Services.
* See **[Azure Management SDK reference documentation](/java/api/com.microsoft.azure.management.cognitiveservices)** for more details on the management SDK.
