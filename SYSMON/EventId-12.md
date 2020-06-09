# Event ID: 12 - RegistryEvent (Object create and delete)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| EventType                   | event_type                        |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| TargetObject                | registry_key_path                 |

#### Logstash pipeline

```
if [event_id] == 12 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "EventType" => "event_type"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "TargetObject" => "registry_key_path"
        }
      }
    }
```