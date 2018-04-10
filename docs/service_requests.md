# GET requests.:format

Query the current status of multiple requests. Because the Chicago endpoint may return service requests with no token and no service_reqeust_id in calls to GET service_requests while recently submitted SRs are still being processed by City systems, users of the GET service_requests method should ignore any service requests returned by the API until they have a service_request_id.

| Resource Information |     |
|----------------------|-----|
| Method Name | Service Definition |
| Requires API key? | No |
| Response Formats | JSON, XML |
| HTTP Methods | GET |
| JSONP | callback=? |

## Arguments

|     Argument         | Required |              |                       Description                        |
|----------------------|----------|--------------|----------------------------------------------------------|
| `jurisdiction_id`    | optional |              | This is currently optional on Chicago's Open311 endpoint. |
| `service_request_id` | optional |              | To call multiple Service Requests at once, multiple service_request_id can be declared; comma delimited. |
| `service_code`       | optional |              | Specify the service type by calling the unique ID(s) of the service_codes you wish to query. This defaults to all service codes when not declared; can be declared multiple times, comma delimited (no spaces). |
| `start_date`         | optional |              | Earliest datetime to include in search. When provided with end_date, allows one to search for requests which have a requested_datetime that matches a given range. Must use w3 format, eg 2010-01-01T00:00:00Z. |
| `end_date`           | optional |              | Latest datetime to include in search. When provided with start_date, allows one to search for requests which have a requested_datetime that matches a given range. Must use w3 format, eg 2010-01-01T00:00:00Z. |
| `status`             | optional |              | Allows for search of requests which have a specific status. This defaults to all statuses; can be declared multiple times, comma delimited (no spaces); Options: open, closed. |
| `extensions`         | optional | Non-standard | The Chicago Open311 endpoint provides supplemental details about Service Requests that are in addition to the ones described in the standard specification. These data are nested in the 'extended_attributes' field in the Service Request response. In order to retrieve the new supplemental details, add the query parameter “extensions=true” to any Open 311 api request. |
| `page_size`          | optional | Non-standard | Controls the maximum amount of results a single call will return. The default value is 50. The maximum value is 500. |
| `page`               | optional | Non-standard | For calls that logically include more records than the page size, the page parameter can be use to page through the results. Use in combination with page_size and with multiple calls to download all data in a logical set of records. |
| `updated_before`     | optional | Non-standard | TBD. This field is experimental and documentation is still being compiled |
| `updated_after`      | optional | Non-standard | TBD. This field is experimental and documentation is still being compiled. |
| `q`                  | optional | Non-standard | Query: TBD. This field is experimental and documentation is still being compiled |


## Response Parameters

|     Argument   |              |                        Description                                     |
|----------------|--------------|------------------------------------------------------------------------|
| `service_request_id` | | 	The unique ID of the service request created. |
| `service_code` | | Returns the service_code associated with the definition, the same one submitted for this call. |
| `status` | | The current status of the service request. |
| `status_notes` | |Explanation of why status was changed to current state or more details on current status than conveyed with status alone. |
| `service_name` | | The human readable name of the service request type. |
| `service_code` | | The unique identifier for the service request type. |
| `description` | | A full description of the request or report submitted. |
| `agency_responsible` | | The agency responsible for fulfilling or otherwise addressing the service request. | |
| `service_notice` | | Information about the action expected to fulfill the request or otherwise address the information reported. |
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