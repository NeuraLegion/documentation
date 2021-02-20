# Creating an Authentication Object in NexPloit

The NexPloit authentication capabilities allow you to scan all the login-protected resources within your target application or API. If you need to scan an application  or API with some authenticated pages, you first need to configure NexPloit with the correct authentication method(s) and valid credentials, so that it can easily reach each of them when running a scan. 

By creating an authentication object, you enable NexPloit to reach complete scan coverage of the target application or API during the security testing. 

>[!NOTE|label:Note]
The created object is available only for the user who has created it. Other users of the same organization cannot add this specific object to their scans. However, they can run, edit and re-test the existing scans with the authentication objects created by other users.

The authentication setup enables you to test access to the authenticated resources covered by the created object before using it in a scan, easily determine the configuration failures and fix them. 

You can enable NexPloit to get access to an authenticated resource by using any of the following authentication options:
* [**Form authentication**](/guide/np-web-ui/advanced-set-up/authentication/types/form-authentication.md) - the default method of authentication, used for authentication requests with the content type set as ‘application/x-www-form-urlencoded.   
* [**Header authentication**](/guide/np-web-ui/advanced-set-up/authentication/types/header-authentication.md) - the most straightforward method of authentication, used for static header authentication tokens that are generated outside of NexPloit and will not expire during a scan.  
* [**API call**](guide/np-web-ui/scanning/managing-authentications/types/api-call.md) - the most flexible method of authentication, used  for multiple API requests that include customized request bodies. 

### Setup <!-- {docsify-ignore} -->
To create an authentication object in NexPloit by using any of the available authentication options, you will need to get valid parameters and values required for a successful authentication setup, the specific parameters depend on the required authentication flow. You can find them in the browser DevTools of your application. To do that, follow these steps:
1. Open the DevTools in your application.
2. In the DevTools, select the **Network** tab.

    > [!TIP|label:Pro Tip]
Make sure that the **Preserve log** checkbox is selected.

   ![Preserve-log](media/preserve-log.png ':size=45%')

3. Perform a request by submitting the login call.  
4. Use the data of the relevant login request when completing the authentication setup fields.

  >[!NOTE|label:Note]
  It is important to select the actual login request from the overall list to pass the authentication setup successfully. 


