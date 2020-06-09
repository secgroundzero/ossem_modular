# Event ID: 13 - RegistryEvent (Value Set)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| EventType                   | event_type                        |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| TargetObject                | registry_key_path                 |
| Details                     | registry_key_details              |


#### Logstash pipeline

```
if [event_id] == 13 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "EventType" => "event_type"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "TargetObject" => "registry_key_path"
            "Details" => "registry_key_details"
        }
      }
    }
```