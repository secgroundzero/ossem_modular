# Event ID: 5 - Process Terminated

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |

#### Logstash pipeline

```
if [event_id] == 5 {
      mutate {
        rename => {
          "RuleName" => "tag"
          "UtcTime" => "event_date_creation"
          "ProcessGuid" => "process_guid"
          "ProcessId" => "process_id"
          "Image" => "process_path"
        }
      }
    }
```