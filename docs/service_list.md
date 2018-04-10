# List Available Open311 Services

Provide a list of acceptable 311 service request types and their associated service codes.

| Resource Information |                      |
|----------------------|----------------------|
| Method               | GET services.:format |
| Requires API key?    | No                   |
| Response Formats     | JSON, XML            |
| HTTP Methods         | GET                  |
| JSONP                | callback=?           |

## Arguments

|     Argument      | Required |                        Description                        |
|-------------------|----------|-----------------------------------------------------------|
| `jurisdiction_id` | optional | This is currently optional on Chicago's Open311 endpoint. |

## Response Parameters

|     Argument   |                        Description                                     |
|:---------------|:-----------------------------------------------------------------------|
| `service_code` | The unique identifier for the service request type.                    |
| `service_name` | The human readable name of the service request type.                   |
| `description`  | A brief description of the service request type.                       |
| `metadata`     | Determines whether there are additional form fields for this service type. |
| `type`         | Explains how this deals with the Open311 service request ID dance.             |
| `keywords`     | A comma separated list of tags or keywords to help users identify the request type. This can provide synonyms of the service_name and group. |
| `group`        | A category to group this service type within. This provides a way to group several service request types under one category such as 'sanitation'. |