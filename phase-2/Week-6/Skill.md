Context:
As a Senior developer create strictly HTML page for User Story Review Agent with customized UI not embedding/without Langflow CDN

Instructions:
1. Strictly DO NOT use below Langflow CDN for chat.
<script src="https://cdn.jsdelivr.net/gh/langflow-ai/langflow-embedded-chat@v1.0.8/dist/build/static/js/bundle.min.js"></script>

2. Mandatorily UI should be Custom one calling the Langflow API.

3. Strictly Postman API details should be configurable in the script file no hardcoing in the HTML.

3. Strictly Connect to Jira and Fetch the user stories details Story Title *, Description, Acceptance Criteria *, Additional Information. Use below curl for more details

postman request POST 'https://mahirgce03.atlassian.net//rest/api/3/search/jql' \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Basic bWFoaXJnY2UwM0BnbWFpbC5jb206QVRBVFQzeEZmR0YwSk9XVjNzdzBtOS1vVjdDYngtVVFraGgwTXVmV3l3cmdPcFY2NWVESUszSVVCSGdVM0w3TkNNbG0tdTlIRC10Q1c5aDdsUUFKUzhRY2VMREJ5cy1ScC0zek90X0lhUXJsUG5CcDFkU0ZEQVE4bFFnOUVUUlhNTlFXSzFScnQ2Y0hTLUdha1U3VVJJLUQtZlhhRXJNekFtQ21TRmZzS0U1OVVjUTNjdEJCc0lRPUUyODU2NjY3' \
  --header 'Cookie: atlassian.xsrf.token=37a0da61e0e6fd9e58141d4bd8335d6e947e5b14_lin' \
  --body '{
    "jql": "key = \"SCRUM-5\"",
    "fields": [
        "key",
        "summary",
        "description",
        "customfield_10110",
        "status",
        "reporter"
    ],
    "maxResults": 1
}' \
  --auth-basic-username 'mahirgce03@gmail.com' \
  --auth-basic-password 'ATATT3xFfGF0JOWV3sw0m9-oV7Cbx-UQkhh0MufWywrgOpV65eDIK3IUBHgU3L7NCMlm-u9HD-tCW9h7lQAJS8QceLDBys-Rp-3zOt_IaQrlPnBp1dSFDAQ8lQg9ETRXMNQWK1Rrt6cHS-GakU7URI-D-fXaErMzAmCmSFfsKE59UcQ3ctBBsIQ=E2856667'

  4. Strictly all values Story Title*, Description, Acceptance Criteria*, Additional Information fetches and populated in UI.

  5. Refer the attached langflow workflow and evaulate the user story score  conditions defined in langflow prompt template file. Attached langflow workflow json file "Userstory-score.json" for detail reference.

6. Use the below API - Endpoint, BaseUrl, Flow ID, API Key and the model should be configurable in the script file no hardcoing in the HTML.

HTTP Method -Post
Endpoint -http://localhost:7860/api/v1/run/b4d3d7cd-0cbf-4290-b844-ecb73e297111
BaseUrl-http://localhost:7860/api/v1/run
Flow ID-b4d3d7cd-0cbf-4290-b844-ecb73e297111
API Key- sk-z-rs5yXdAI1vC8nmy6Q8vEK7Btbp9CT5mfb3RQWytAs 

Request Body:
{
		           "output_type": "chat",
		           "input_type": "chat",
		           "tweaks": {
		             "APIRequest-Jf9P2": {
		               "body": [
		                 {
		                   "key": "jql",
		                   "value": "key=\"SCRUM-5\""
		                 },
		                 {
		                   "key": "fields",
		                   "value": "[\"key\", \"summary\", \"description\", \"status\", \"reporter\"]"
		                 }
		               ]
		             },
		             "ChatInput-WXAgy": {
		               "input_value": "Evaluate the user story and provide the score"
		             }
		           },
		           "session_id": "YOUR_SESSION_ID_HERE"
		         }

7. Toogle for Dark and light theme.

8. Mandatorily add Generate score button. When user click "Generate score" button user story score should generated with Overall Quality Score, Specific Improvement Recommendations and Improvement Summary

9. cmd to lanuch app
Run this from the project folder:

node proxy-server.js

If you want it to keep running in the background in PowerShell, use:
Start-Process node -ArgumentList "proxy-server.js"

Then open:
http://localhost:3001