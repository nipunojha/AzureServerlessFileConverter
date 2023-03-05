# AzureServerlessFileConverter
Use Azure Functions and Graph API to convert file between different supported formats 
-Coded to download uploaded file as pdf using session upload which can handle large size files
https://learn.microsoft.com/en-us/onedrive/developer/rest-api/api/driveitem_createuploadsession?view=odsp-graph-online
-Can be exteded  based on the formats supported by the graph api - glb, jpg, html
https://learn.microsoft.com/en-us/onedrive/developer/rest-api/api/driveitem_get_content_format?view=odsp-graph-online
-File formats tested: doc, ppt, excel, txt to pdf
-Used fsutil to generate files for large size so format could not be verifed
-Tested using postman to upload and download file
-Loved using graph explorer to get the clientid/secrets etc https://developer.microsoft.com/en-us/graph/graph-explorer

Challenges faced:
-figuring out tenant id, client id/secrets etc for the first time
-assigning api permissions (needed admin access)
https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-configure-permissions?tabs=http%2Cupdatepermissions-azureadgraph-powershell
-not sure about handing potentially infected files (security with using sharepoint/onedrive as upload folder), cost, clean up of abandoned/failed uploads (try/catch/finally maybe?)
-performance was slow but could be due to free tier/using consumption plan for function

Future potential extensions:
-extend to use cognitive-services for text summarization, key phrase and named entity recognition
https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/summarization/how-to/document-summarization
-integration potential for HealthCare to summarize or categorize patient data/charts etc, PII detection
https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/text-analytics-for-health/overview?tabs=ner
https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/personally-identifiable-information/overview
-based on key phrase or named entity recognition using cognitive-services trigger notification alerts 
https://graph.microsoft.com/beta/me/notifications
-potentially use for translation?