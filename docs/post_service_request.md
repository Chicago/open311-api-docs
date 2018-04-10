# Create a New Service Request

Create a service request in the City's database. Once a service request has been processed by the City (this can take an undetermined amount of time), you should be able to call the GET service_request_id method (tokens/:token_id.:format) to get back the service_request_id for a SR. Therefore, it is nesseary to poll the GET service_request_id method until an SR id is returned. Because the Chicago endpoint may return service requests with no token and no service_reqeust_id in calls to GET service_requests while recently submitted SRs are still being processed by City systems, users of the GET service_requests method should ignore any service requests returned by the API until they have a service_request_id.

| Resource Information |                       |
|----------------------|-----------------------|
| Method               | POST requests.:format |
| Requires API key?    | Yes                   |
| Response Formats     | JSON, XML             |
| HTTP Methods         | POST                  |

## Arguments

|     Argument       | Required |                       Description                         |
|--------------------|----------|-----------------------------------------------------------|
| `jurisdiction_id`  | optional | This is currently optional on Chicago's Open311 endpoint. |
| `service_code`     | required | This is obtained from GET Service List method.            |
| `attribute`        | required | This takes the form of attribute[code]=value where multiple code/value pairs can be specified as well as multiple values for the same code in the case of a multivaluelist datatype (attribute[code1][]=value1&attribute[code1][]=value2&attribute[code1][]=value3) - see example. - This is only required if the service_code requires a service definition with required fields. |
| `lat`              | required | lat &amp; long both need to be sent even though they are sent as two separate parameters. lat &amp; long are required. |
| `long`             | required | lat &amp; long both need to be sent even though they are sent as two separate parameters. lat &amp; long are required. |
| `address_string`   | required | This should be written from most specific to most general geographic unit, eg address number or cross streets, street name, neighborhood/district, city/town/village, county, postal code.  |
| `address_id`       | optional | The internal address ID used by a jurisdiction's master address repository or other addressing system. |
| `email`            | optional | The email address of the person submitting the request.   |
| `device_id`        | optional | The unique device ID of the device submitting the request. This is usually only used for mobile devices. |
| `account_id`       | optional | The unique ID for the user account of the person submitting the request. |
| `first_name`       | optional | The given name of the person submitting the request.      |
| `last_name`        | optional | The family name of the person submitting the request.     |
| `phone`            | optional | The phone number of the person submitting the request.    |
| `description`      | optional | A full description of the request or report being submitted. |
| `media_url`        | optional | A URL to media associated with the request, eg an image.  |

## Response Parameters

| Argument |                        Description                                     |
|----------|------------------------------------------------------------------------|
| `token`  | If returned, use this to call GET service_request_id from a token to discover what the service_request_id is after it is created by the City system. |