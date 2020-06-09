# Event ID: 20 - WmiEvent (WmiEventConsumer activity detected)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| EventType                   | event_type                        |
| UtcTime                     | event_date_creation               |
| Operation                   | wmi_operation                     |
| User                        | user_name                         |
| Name                        | wmi_consumer_name                 |
| Type                        | wmi_consumer_type                 |
| Destination                 | wmi_consumer_destination          |

#### Logstash pipeline

```
if [event_id] == 20 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "EventType" => "event_type"
            "UtcTime" => "event_date_creation"
            "Operation" => "wmi_operation"
            "User" => "user_name"
            "Name" => "wmi_consumer_name"
            "Type" => "wmi_consumer_type"
            "Destination" => "wmi_consumer_destination"
        }
      }
    }
```