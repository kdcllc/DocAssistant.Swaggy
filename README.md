# DocAssistant.Swaggy

Try yourself: https://hack-togather-wa.azurewebsites.net/

This project was developed for the Microsoft hackathon, Hack Together: The AI Chat App Hack, leveraging the DocAssistant app and integrating the Retrieval-Augmented Generation (RAG) pattern for OpenAPI specification files.

Technologies utilized include Semantic Kernel, Kernel Memory, OpenAPI, Swagger, Azure OpenAI, Azure Search, Azure Storage, Blazor, ASP.NET, and .NET 8.
  
The project allows users to call any API with their voice or through chat. It involves the following steps:  
   
1. **Uploading Swagger Documents**: The journey begins with the upload of Swagger documents that contain information about the user's API. These documents can be generated on the server by adding comments to the endpoints and payloads, more details here with support of any language: https://swagger.io/tools/open-source/open-source-integrations/.   
  
2. **Viewing and Uploading Status**: The user interface allows viewing the status of recent uploads, and users can upload Swagger documents either from a file or directly via a URL. An API token can be provided if required by the Web API. Also while uploading you can view which operation of uploading swagger api to memory happen.
   
4. **Uploading Knowledge to AI Memory**: The process of uploading knowledge to our AI memory unfolds in three main steps. First, documents are uploaded to Azure storage. Then, the large open API file is chunked into smaller parts, with each endpoint and necessary information being retrieved. Finally, Azure Open AI Ada model is used to create embeddings for each chunk, which are stored in Azure Search for retrieving the best matching endpoints for a request.   
  
5. **Testing the API**: Once the document is uploaded, the endpoints are previewed and questions or commands can be posed to execute the API.

6. **Multiple API Interaction**: The RAG pattern implementation in this project allows working with not just one API, but multiple ones. For instance, the application 'DocAssistent.Swaggy' allows interaction with the AI through typing as well as voice commands and responses.  
   
The project aims to provide an AI helper designed to redirect human queries to the appropriate API. However, it's important to note that the success of the results is highly dependent on the functionality of the web API on the server.  

**Process Flow Diagram**:

  ![image](https://github.com/YuriyMorozyuk95/DocAssistant.Swaggy/assets/27745979/fb2bb1a1-fefb-467d-a990-60298894a7a3)

 A diagram is used to illustrate the process flow. Upon uploading a Swagger document, it's broken down into small chunks. These chunks are used to create embeddings for the uploaded JSON and a corresponding embedding representation of the JSON for Azure Search. When a user initiates a request, Azure Search uses a vector type of search to identify the most suitable endpoint. All located JSONs are then merged into a new, lighter Swagger file. The Open AI GPT model then uses this Swagger file and the user's request to generate an HTTP request to the server. Based on the server's response, the Open AI GPT model generates a user-friendly answer.  
