# Event ID: 9 - RawAccessRead

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| Device                      | target_device                     |

#### Logstash pipeline

```
if [event_id] == 9 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "Device" => "target_device"
        }
      }
    }
```