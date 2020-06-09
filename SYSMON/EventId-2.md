# Event ID: 2 - A process changed a file creation time

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| TargetFileName              | file_name                         |
| CreationUtcTime             | file_date_creation                |
| PreviousCreationUtcTime     | file_previous_date_creation       |

#### Logstash pipeline

```
if [event_id] == 2 {
      mutate {
        rename => {
          "RuleName" => "tag"
          "UtcTime" => "event_date_creation"
          "ProcessGuid" => "process_guid"
          "ProcessId" => "process_id"
          "Image" => "process_path"
          "TargetFileName" => "file_name"
          "CreationUtcTime" => "file_date_creation"
          "PreviousCreationUtcTime" => "file_previous_date_creation"
        }
      }
    }
```