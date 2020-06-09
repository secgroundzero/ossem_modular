# Event ID: 11 - FileCreate

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| TargetFileName              | file_name                         |
| CreationUtcTime             | file_date_creation                |

#### Logstash pipeline

```
if [event_id] == 11 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "TargetFileName" => "file_name"
            "CreationUtcTime" => "file_date_creation"
        }
      }
    }
```