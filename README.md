# Instructions to run Microsoft Azure TTS Talking Avatar sample code

## Pre-requisites

* Follow [Text to speech quickstart](https://learn.microsoft.com/azure/ai-services/speech-service/get-started-text-to-speech?pivots=programming-language-python#set-up-the-environment) to set up the environment for running Speech SDK in python.

## Chat Sample

This sample demonstrates the chat scenario, with integration of Azure speech-to-text, Azure OpenAI, and Azure text-to-speech avatar real-time API.

* Step 1: Open a console and navigate to the folder containing this README.md document.
    * Run `pip install -r requirements.txt` to install the required packages.
    * Set below environment variables:
        * `SPEECH_REGION` - the region of your Azure speech resource, e.g. westus2.
        * `SPEECH_KEY` - the API key of your Azure speech resource.
        * `SPEECH_PRIVATE_ENDPOINT` - the private endpoint of your Azure speech resource. e.g. https://my-speech-service.cognitiveservices.azure.com. This is optional, and only needed when you want to use private endpoint to access Azure speech service. This is optional, which is only needed when you are using custom endpoint. For more information about private endpoint, please refer to [Enable private endpoint](https://learn.microsoft.com/azure/ai-services/speech-service/speech-services-private-link).
        * `SPEECH_RESOURCE_URL` - the URL of your Azure speech resource, e.g. /subscriptions/6e83d8b7-00dd-4b0a-9e98-dab9f060418b/resourceGroups/my-resource-group/providers/Microsoft.CognitiveServices/accounts/my-speech-resource. To fetch the speech resource URL, go to your speech resource overview page on Azure portal, click `JSON View` link, and then copy the `Resource ID` value on the popped up page. This is optional, which is only needed when you want to use private endpoint to access Azure speech service.
        * `USER_ASSIGNED_MANAGED_IDENTITY_CLIENT_ID` - the client ID of your user-assigned managed identity. This is optional, which is only needed when you want to use private endpoint with user-assigned managed identity to access Azure speech service. For more information about user-assigned managed identity, please refer to [Use a user-assigned managed identity](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/how-to-use-vm-token?tabs=azure-cli).
        * `AZURE_OPENAI_ENDPOINT` - the endpoint of your Azure OpenAI resource, e.g. https://my-aoai.openai.azure.com/, which can be found in the `Keys and Endpoint` section of your Azure OpenAI resource in Azure portal.
        * `AZURE_OPENAI_API_KEY` - the API key of your Azure OpenAI resource, which can be found in the `Keys and Endpoint` section of your Azure OpenAI resource in Azure portal.
        * `AZURE_OPENAI_DEPLOYMENT_NAME` - the name of your Azure OpenAI model deployment, which can be found in the `Model deployments` section of your Azure OpenAI resource in Azure portal.
    * Set below environment variables if you want to use customized ICE server:
        * `ICE_SERVER_URL` - the URL of your customized ICE server.
        * `ICE_SERVER_URL_REMOTE` - the URL of your customized ICE server for remote side. This is only required when the ICE address for remote side is different from local side.
        * `ICE_SERVER_USERNAME` - the username of your customized ICE server.
        * `ICE_SERVER_PASSWORD` - the password of your customized ICE server.
    * Run `python -m flask run -h 0.0.0.0 -p 5000` to start this sample.

* Step 2: Open a browser and navigate to `http://localhost:5000/chat` to view the web UI of this sample.

* Step 3: Click `Open Avatar Session` button to setup video connection with Azure TTS Talking Avatar service. If everything goes well, you should see a live video with an avatar being shown on the web page.

* Step 5: Click `Start Microphone` button to start microphone (make sure to allow the microphone access tip box popping up in the browser), and then you can start chatting with the avatar with speech. The chat history (the text of what you said, and the response text by the Azure OpenAI chat API) will be shown beside the avatar. The avatar will then speak out the response of the chat API.

# Additional Tip(s)

* If you want to enforce the avatar to stop speaking before the avatar finishes the utterance, you can click `Stop Speaking` button. This is useful when you want to interrupt the avatar speaking.

* If you want to clear the chat history and start a new round of chat, you can click `Clear Chat History` button. And if you want to stop the avatar service, please click `Close Avatar Session` button to close the connection with avatar service.

* If you want to type your query message instead of speaking, you can check the `Type Message` checkbox, and then type your query message in the text box showing up below the checkbox.