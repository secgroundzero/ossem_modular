# Event ID: 10 - Sysmon service state changed

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| SourceProcessGuid           | process_guid                      |
| SourceProcessId             | process_id                        |
| SourceThreadId              | thread_id                         |
| SourceImage                 | process_path                      | 
| TargetProcessGuid           | target_process_guid               |
| TargetProcessId             | target_process_id                 |
| TargetImage                 | target_process_path               | 
| GrantedAccess               | process_granted_access            |
| CallTrace                   | process_call_trace                |

#### Logstash pipeline

```
if [event_id] == 10 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "SourceProcessGuid" => "process_guid"
            "SourceProcessId" => "process_id"
            "SourceThreadId" => "thread_id"
            "SourceImage" => "process_path"
            "TargetProcessGuid" => "target_process_guid"
            "TargetProcessId" => "target_process_id"
            "TargetImage" => "target_process_path"
            "GrantedAccess" => "process_granted_access"
            "CallTrace" => "process_call_trace"
        }
      }
    }
```