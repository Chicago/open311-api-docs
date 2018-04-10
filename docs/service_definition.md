# Retrieve the Definitions for a Service Request

Define attributes associated with a service code.

| Resource Information |                                    |
|----------------------|------------------------------------|
| Method               | GET services/:service_code.:format |
| Requires API key?    | No                                 |
| Response Formats     | JSON, XML                          |
| HTTP Methods         | GET                                |
| JSONP                | callback=?                         |

## Arguments

|     Argument      | Required |                                     Description                                                 |
|-------------------|----------|-------------------------------------------------------------------------------------------------|
| `jurisdiction_id` | optional | Optional, but if it is included, it must be set to `cityofchicago.org`                          |
| `service_code`    | required | The service_code is specified in the main URL path rather than an added query string parameter. |

## Response Parameters

|     Argument   |                        Description                                     |
|----------------|------------------------------------------------------------------------|
| `service_code`         | Returns the service_code associated with the definition, the same one submitted for this call. |
| `variable`             | 'true' denotes that user input is needed. 'false' means the attribute is only used to present information to the user within the description field. |
| `code`                 | A unique identifier for the attribute. |
| `datatype`             | Denotes the type of field used for user input. |
| `required`             | 'true' means that the value is required to submit service request. 'false' means that the value not required. |
| `datatype_description` | A description of the datatype which helps the user provide their input. |
| `order`                | The sort order that the attributes will be presented to the user. 1 is shown first in the list. |
| `description`          | A description of the attribute field with instructions for the user to find and identify the requested information. |
| `key`                  | The unique identifier associated with an option for singlevaluelist or multivaluelist. This is analogous to the value attribute in an html option tag.|
| `name`                 | The human readable title of an option for singlevaluelist or multivaluelist. This is analogous to the innerhtml text node of an html option tag. |