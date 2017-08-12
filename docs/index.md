# Open311 API Documentation

## Authentication

You may need an API Key in order to call some endpoints in Chicago's Open311 system. This is indicated in the documentation by a field labeled **"Requires API Key?"**.

## Testing

The City of Chicago has a separate environment and URL for testing developer applications before connecting them to the Live Open311 system. The API key developers use in Test will be different than the one used in production. The standard developer workflow would work like this:

1. Developer requests an API key from the Test Open311 system
2. Using the Test API key, developer codes and tests their app against the Test environment
3. Developer requests an API key from the Live Open311 system
4. Developer's application is deployed/released using Live system API key and is coded against the Live environment

## Requesting an API key

### Test
[Request test API keys](http://test311api.cityofchicago.org/open311/v2/apps/new) must be requested first.

Visit the above URL to request an API key from the test Open311 system. Your request will be automatically provisioned so you can get started immediately developing against the test Open311 system.

### Production
[Request production API key](http://311api.cityofchicago.org/open311/v2/apps/new) may be requested after successfully using a test API key.

!!! tip
    All requests for API keys must first be tested in the development environment.
    Use the same application name as used with the test key to ensure quick turn-around
    for your request. When testing, ensure that your application can successfully write
    and retrieve service requests.

Production API keys may only be requested after successfully testing with a test API key. The API Key application you submit will need to be reviewed and approved by City of Chicago Staff to ensure compliance with the [Terms of Service](tos/).

## Service Request Meta Data

Methods that expose data related to how Service Requests will be exposed in the API.

|               Method                | Description |
|-------------------------------------|-------------|
| GET services.:format | **Service List**: Provide a list of acceptable 311 service request types and their associated service codes. |
| GET services/:service_code.:format | **Service Definition**: Define attributes associated with a service code. |

## Service Request

Methods that allow for reading and writing of Service Requests to the City database.

|               Method                | Description |
|-------------------------------------|-------------|
| GET requests/:service_request_i d.:format| **Service Request**: Query the current status of an individual request. |
| GET requests.:format | **Service Requests**: Query the current status of multiple requests. Because the Chicago endpoint may return service requests with no token and no service_reqeust_id in calls to GET service_requests while recently submitted SRs are still being processed by City systems, users of the GET service_requests method should ignore any service requests returned by the API until they have a service_request_id. |
| POST requests.:format | **Post Service Request**: Create a service request in the City's database. Once a service request has been processed by the City (this can take an undetermined amount of time), you should be able to call the GET service_request_id method (tokens/:token_id.:format) to get back the service_request_id for a SR. Therefore, it is nesseary to poll the GET service_request_id method until an SR id is returned. Because the Chicago endpoint may return service requests with no token and no service_reqeust_id in calls to GET service_requests while recently submitted SRs are still being processed by City systems, users of the GET service_requests method should ignore any service requests returned by the API until they have a service_request_id. |