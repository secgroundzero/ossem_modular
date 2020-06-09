# Event ID: 23 - FileDelete (A file delete was detected)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      | 
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| User                        | user_name                         |
| TargetFileName              | file_name                         |
| Hashes                      | sysmon_hash                       |
| IsExecutable                | file_is_executable                |
| Archived                    | file_is_archived                  |


#### Logstash pipeline

```
if [event_id] == 23 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "User" => "user_name"
            "TargetFileName" => "file_name"
            "Hashes" => "sysmon_hash"
            "IsExecutable" => "file_is_executable"
            "Archived" => "file_is_archived"
        }
      }
    }
```