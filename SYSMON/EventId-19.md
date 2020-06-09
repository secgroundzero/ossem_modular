# Event ID: 19 -  WmiEvent (WmiEventFilter activity detected)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| EventType                   | event_type                        |
| UtcTime                     | event_date_creation               |
| Operation                   | wmi_operation                     |
| User                        | user_name                         |
| EventNameSpace              | wmi_namespace                     |
| Name                        | wmi_filter_name                   |
| Query                       | wmi_query                         |


#### Logstash pipeline

```
if [event_id] == 19 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "EventType" => "event_type"
            "UtcTime" => "event_date_creation"
            "Operation" => "wmi_operation"
            "User" => "user_name"
            "EventNameSpace" => "wmi_namespace"
            "Name" => "wmi_filter_name"
            "Query" => "wmi_query"
        }
      }
    }
```