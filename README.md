# AzureFunction-with-SignalR-javascript

Reference

Tutorial Document :
https://docs.microsoft.com/en-us/azure/azure-signalr/signalr-tutorial-authenticate-azure-functions

QuickStart Document:
https://docs.microsoft.com/en-us/azure/azure-signalr/signalr-quickstart-azure-functions-javascript


The QuickStart document Github Repo failed to work without changes, may due to runtime version changes. 

Detailed Steps for local project. 

Prerequisites
Use Function Core Tools v2 
Create runtime v2 function app from Visual Studio Code Extension 
Select Node version 10 LTS

Step1: Configure Connection String for Storage and SignalR Service
configure the local.settings.json for app settings ( AzureWebJobsStorage , AzureSignalRConnectionString,  WEBSITE_NODE_DEFAULT_VERSION) 

Step 2: Create Function negotiate

Add Http Function "/negotiate".  This is necessary function to keep the real-time connection for SignalR Service. 
Copy paste the code for /negotiate/function.json and /negotiate/index.js 

Step 3: Create Function SendMessage

Add Http Function "/SendMessage".  
Copy paste the code for SendMessage/function.json and SendMessage/index.js

Step 4: Add CORS Settings for the sample Static Page to host.json file
This configuration is in the host.json file in the project root folder

    "CORS": "http://localhost:8080,https://azure-samples.github.io",     ( After we deployed to cloud-side function app, we will also need to configure the CORS settings for this sample)
    "CORSCredentials": true


Step 5: Enter "F5" button to run the function app locally with Function Core Tools.  
Then we could go to the sample static site.  https://azure-samples.github.io/signalr-service-quickstart-serverless-chat/demo/chat-v2/

Our locally hosting Function App will be use our SignalR Service configured in the host.json file. 
The source code for the static page could be found here. https://github.com/Azure-Samples/signalr-service-quickstart-serverless-chat/blob/2720a9a565e925db09ef972505e1c5a7a3765be4/docs/demo/chat-with-auth/index.html

This step refers to this particular step.  https://docs.microsoft.com/en-us/azure/azure-signalr/signalr-quickstart-azure-functions-javascript#run-the-web-application

