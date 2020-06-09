# Event ID: 15 - FileCreateStreamHash

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      | 
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| TargetFileName              | file_name                         |
| CreationUtcTime             | file_creation_time                |
| Hash                        | sysmon_hash                       |

#### Logstash pipeline

```
if [event_id] == 15 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "TargetFileName" => "file_name"
            "CreationUtcTime" => "file_creation_time"
            "Hash" => "sysmon_hash"
        }
      }
    }
```