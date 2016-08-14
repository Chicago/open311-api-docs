# GET services/:service_code.:format

Define attributes associated with a service code.

| Resource Information |     |
|----------------------|-----|
| Method Name | Service Definition |
| Requires API key? | No |
| Response Formats | JSON, XML |
| HTTP Methods | GET |
| JSONP | callback=? |

## Arguments

|     Argument      | Required |                        Description                        |
|-------------------|----------|-----------------------------------------------------------|
| `jurisdiction_id` | optional | This is currently optional on Chicago's Open311 endpoint. |
| `service_code`    | required | The service_code is specified in the main URL path rather than an added query string parameter. |
| `extensions`      | optional | The Chicago Open311 endpoint provides supplemental details about Service Requests that are in addition to the ones described in the standard specification. These data are nested in the 'extended_attributes' field in the Service Request response. In order to retrieve the new supplemental details, add the query parameter “extensions=true” to any Open 311 api request. |

## Response Parameters

|     Argument   |              |                        Description                                     |
|----------------|--------------|------------------------------------------------------------------------|
| `service_request_id` | | 	The unique ID of the service request created. |
| `service_code` | | Returns the service_code associated with the definition, the same one submitted for this call. |
| `status` | The current status of the service request. |
| `status_notes` | |Explanation of why status was changed to current state or more details on current status than conveyed with status alone. |
| `service_name` | | The human readable name of the service request type. |
| `service_code` | | The unique identifier for the service request type. |
| `description` | | A full description of the request or report submitted. |
| `agency_responsible` | | The agency responsible for fulfilling or otherwise addressing the service request. | |
| `service_notice` | Information about the action expected to fulfill the request or otherwise address the information reported. |
| `requested_datetime` | | The date and time when the service request was made. |
| `updated_datetime` | Non-standard | TBD: The Chicago implementation uses updated_datetime in a manner that differs from Open311. Documentation is still being compiled. |
| `expected_datetime` | | The date and time when the service request can be expected to be fulfilled. This may be based on a service-specific service level agreement. |
| `address` | | Human readable address or description of location. |
| `address_id` | | The internal address ID used by a jurisdictions master address repository or other addressing system. |
| `zipcode` | | The postal code for the location of the service request. |
| `lat` | | latitude using the (WGS84) projection. |
| `long` | | longitude using the (WGS84) projection. |
| `media_url` | Non-standard | A URL to media associated with the request, eg an image. |
| `channel` | Non-standard | Nested in extended_attributes field (extended_attributes.channel). Describes the method that the Service Request was input into the 311 system (i.e. phone, web). |
| `ward` | Non-standard | Nested in extended_attributes field (extended_attributes.ward). The political boundary where the Service Request is located. |
| `police_district` | Non-standard | Nested in extended_attributes field (extended_attributes.police_district). The police district boundary where the Service Request is located. |
| `duplicate` | Non-standard | Nested in extended_attributes field (extended_attributes.duplicate). Indicates that this Service Request is a duplicate of a Service Request that is already in the system. This can happen when, for example, the same pothole is reported multiple times. Use in conjuntion with extended_attributes.parent_service_request_id to identify duplicates and their assoicated 'master' (aka parent) Service Request records. |
| `parent_service_request_id` | Non-standard | Nested in extended_attributes field (extended_attributes.parent_service_request_id). When a Service Request is a duplicate, this value shows which Service Request (the parent) it is a duplicate of. Use in conjuntion with extended_attributes.duplicate to identify duplicates and their assoicated 'master' (aka parent) Service Request records. |
| `notes` | Non-standard | This fields holds nested and related status details, activities, follow-on case details, for the Service Request. Will generally have a Request Opened activity and a Request closed activity when the request is closed. May also hold other activity types (i.e. Dispatch Work Crew) and notes about Follow-on Service Requests (usually transfer of Service Request ownership from one department to another). Each actiivty in the array of 1 or more activities can have additional properties that are described below. |
| `notes.summary` | Non-standard | Short description of the activity / action described by the note. |
| `notes.type` | Non-standard | Category of the activity / action described by the note (i.e activity / opened / closed). |
| `notes.description` | Non-standard | More detailed description of the activity / action described by the note - usually comes directly from City systems so can be a bit cryptic. |
| `notes.extended_attributes` | Non-standard | For activities that are actual Follow-on (child) Service Requests, this field holds important information about those child service requests. Specifically, you will find service_name, agency_responsible, and service_request_id of the child SR. |
| `notes.datetime` | Non-standard | The human readable title of an option for singlevaluelist or multivaluelist. This is analogous to the innerhtml text node of an html option tag. |