# Event ID: 14 - RegistryEvent (Key and Value Rename)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| EventType                   | event_type                        |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| TargetObject                | registry_key_path                 |
| NewName                     | registry_key_new_name             |


#### Logstash pipeline

```
if [event_id] == 14 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "EventType" => "event_type"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "TargetObject" => "registry_key_path"
            "NewName" => "registry_key_new_name"
        }
      }
    }
```