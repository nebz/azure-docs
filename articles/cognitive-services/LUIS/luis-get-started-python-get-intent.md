---
title: Tutorial learning how to call a Language Understanding (LUIS) app using Python | Microsoft Docs
description: In this tutorial, you learn to call a LUIS app using Python.
services: cognitive-services
author: v-geberr
manager: kaiqb
ms.service: cognitive-services
ms.component: language-understanding
ms.topic: tutorial
ms.date: 12/13/2017
ms.author: v-geberr
#Customer intent: As a developer new to LUIS, I want to query the endpoint of a published model using Python. 
---

# Tutorial: Call a LUIS endpoint using Python
Pass utterances to a LUIS endpoint and get intent and entities back.

<!-- green checkmark -->
> [!div class="checklist"]
> * Create LUIS subscription and copy key value for later use
> * View LUIS endpoint results from browser to public sample IoT app
> * Create Visual Studio C# console app to make HTTPS call to LUIS endpoint

For this article, you need a free [LUIS][LUIS] account in order to author your LUIS application.

## Create LUIS subscription key
You need a Cognitive Services API key to make calls to the sample LUIS app used in this walkthrough. 

To get an API key, follow these steps: 

1. You first need to create a [Cognitive Services API account](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-apis-create-account) in the Azure portal. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.

2. Log in to the Azure portal at https://portal.azure.com. 

3. Follow the steps in [Creating Subscription Keys using Azure](./luis-how-to-azure-subscription.md) to get a key.

4. Go back to the [LUIS](luis-reference-regions.md) website and log in using your Azure account. 

    [![](media/luis-get-started-node-get-intent/app-list.png "Screenshot of app list")](media/luis-get-started-node-get-intent/app-list.png)

## Understand what LUIS returns

To understand what a LUIS app returns, you can paste the URL of a sample LUIS app into a browser window. The sample app is an IoT app that detects whether the user wants to turn on or turn off lights.

1. The endpoint of the sample app is in this format: `https://westus.api.cognitive.microsoft.com/luis/v2.0/apps/df67dcdb-c37d-46af-88e1-8b97951ca1c2?subscription-key=<YOUR_API_KEY>&verbose=false&q=turn%20on%20the%20bedroom%20light` Copy the URL and substitute your subscription key for the value of the `subscription-key` field.
2. Paste the URL into a browser window and press Enter. The browser displays a JSON result that indicates that LUIS detects the `HomeAutomation.TurnOn` intent and the `HomeAutomation.Room` entity with the value `bedroom`.

    ![JSON result detects the intent TurnOn](./media/luis-get-started-node-get-intent/turn-on-bedroom.png)
3. Change the value of the `q=` parameter in the URL to `turn off the living room light`, and press enter. The result now indicates that the LUIS detected the `HomeAutomation.TurnOff` intent and the `HomeAutomation.Room` entity with value `living room`. 

    ![JSON result detects the intent TurnOff](./media/luis-get-started-node-get-intent/turn-off-living-room.png)


## Consume a LUIS result using the Endpoint API with Python

You can use Python to access the same results you saw in the browser window in the previous step.

1. Copy one of the following code snippets:

   [!code-python[Console app code that calls a LUIS endpoint for Python 2.7](~/samples-luis/documentation-samples/endpoint-api-samples/python/quickstart-call-endpoint-2-7.py)]

   [!code-python[Console app code that calls a LUIS endpoint for Python 3.6](~/samples-luis/documentation-samples/endpoint-api-samples/python/quickstart-call-endpoint-3-6.py)]


2. Replace the value of the `Ocp-Apim-Subscription-Key` field with your LUIS subscription key.

3. Run the script. It displays the same JSON that you saw earlier in the browser window.
<!-- 
![Console window displays JSON result from LUIS](./media/luis-get-started-python-get-intent/console-turn-on.png)
-->

## Clean up resources
The two resources created in this tutorial are the LUIS subscription key and the C# project. Delete the LUIS subscription key from the Azure portal. Close the Visual Studio project and remove the directory from the file system. 

## Next steps
> [!div class="nextstepaction"]
> [Add utterances](luis-get-started-python-add-utterance.md)

[LUIS]: https://docs.microsoft.com/azure/cognitive-services/luis/luis-reference-regions#luis-website