
# Code
## Refer ML service deployed as online endpoint  [here](../../code/ml-as-service/question-answering-online-endpoint.ipynb) # Online Endpoint

## sample qa service invocation  [here](../../code/ml-as-service/simple-qa-model.ipynb) # sample qa service invocation
## Sample Code
Replace and substitute `subscription_id`, `workspace`, `resource_group` with appropriate values

```Python
from azure.ai.ml import MLClient
from azure.identity import (
    DefaultAzureCredential,
    InteractiveBrowserCredential,
    ClientSecretCredential,
)
from azure.ai.ml.entities import AmlCompute
import time

try:
    credential = DefaultAzureCredential()
    credential.get_token("https://management.azure.com/.default")
except Exception as ex:
    credential = InteractiveBrowserCredential()

# connect to a workspace
workspace_ml_client = None
try:
    workspace_ml_client = MLClient.from_config(credential)
    subscription_id = workspace_ml_client.subscription_id
    workspace = workspace_ml_client.workspace_name
    resource_group = workspace_ml_client.resource_group_name
except Exception as ex:
    print(ex)
    
    # Enter details of your workspace
    # subscription_id="<SUBSCRIPTION_ID>",
    # resource_group ="<RESOURCE_GROUP>",
    # workspace = "<WORKSPACE_NAME>",
    
    workspace_ml_client = MLClient(
        credential, subscription_id, resource_group, workspace
    )
# Connect to the HuggingFaceHub registry
registry_ml_client = MLClient(credential, registry_name="HuggingFace")
print(registry_ml_client)
```
# Understand the Azure Machine Learning service
1. To create an Azure Machine Learning service, you'll have to:

2. Get access to Azure, for example through the Azure portal.

3. Sign in to get access to an Azure subscription.

4. Create a `resource group` within your subscription.

5. Create an `Azure Machine Learning` service to create a `workspace`.

6. When a workspace is provisioned, Azure will automatically create other Azure resources within the same resource group to support the workspace:

7. `Azure Storage Account`: To store files and notebooks used in the workspace, and to store metadata of jobs and models.

8. `Azure Key Vault`: To securely manage secrets such as authentication keys and credentials used by the workspace.

9. `Application Insights`: To monitor predictive services in the workspace.

10. `Azure Container Registry`: Created when needed to store images for Azure Machine Learning environments.

# Follow Steps for creation of ML Workspace in Azure
![Alt text](1.jpg "a title")

![Alt text](2.jpg "a title")

![Alt text](3.jpg "a title")

![Alt text](4.jpg "a title")

![Alt text](5.jpg "a title")

![Alt text](6.jpg "a title")

![Alt text](7.jpg "a title")

![Alt text](8.jpg "a title")

![Alt text](9.jpg "a title")

![Alt text](10.jpg "a title")