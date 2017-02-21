# DynamicsCRMWrapper
A wrapper around the Dynamics 365 and CRM connections using XRM Tools.

##Description
Dynamics CRM/365 SDK exposes XRM tools to work with Dynamics365/CRM. This library uses XRM tools to connect with Dynamics 365/CRM environments.

##Concurrent ExecuteMultiple Calls
Dynamics365/CRM environment will not allow more than two parallel ExecuteMultiple requests to run. In order to avoid errors and running multiple requests seemingly without bothering about the limitation we need to have a mechanism. This DynamicsCRMWrapper library works in such a way that it can execute only certain amount of ExecuteMultiple requests at a time. And the number of parallel request is configurabe.

#Usage:
DynamicsCRMWrapper exposes a singleton class as afacade for CRM named CRMFacade. (This class is a comn=bination of Singleton and Facade pattern).
A CRMConnection class which holds the CrmServiceClient object from XRM tools for a specific organization. And also implements mutual exclusion mechanism to maintain the number of requests.

1. Add DynamicsCRMWrapper reference to your project.
2. Create new Dynamics CRM connection and consume it using the below code,
```
string organizationUrl = @"YourOrgUrl";
if(CRMFacade.CreateCRMConnection(
  AuthenticationProviderType.OnlineFederation,
  new ConnectionCredentials{<Fill your credentials here>}))
  {
    OrganizationResponse response = CRMFacade.Execute(organizationUrl,Your_OrganizationRequest);
  }
```

_You are welcomed to raise issues or feature suggestions._
**This project will be updated often, so check back here often or you can star it.**
