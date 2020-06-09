# Event ID: 21 - RegistryEvent (Value Set)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| EventType                   | event_type                        |
| UtcTime                     | event_date_creation               |  
| Operation                   | wmi_operation                     |
| User                        | user_name                         |
| Consumer                    | wmi_consumer_path                 |
| Filter                      | wmi_filter_path                   |

#### Logstash pipeline

```
if [event_id] == 21 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "EventType" => "event_type"
            "UtcTime" => "event_date_creation"
            "Operation" => "wmi_operation"
            "User" => "user_name"
            "Consumer" => "wmi_consumer_path"
            "Filter" => "wmi_filter_path"
        }
      }
    }
```