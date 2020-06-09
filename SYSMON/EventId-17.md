# Event ID: 17 - PipeEvent (Pipe Created)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               | 
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| PipeName                    | pipe_name                         |
| Image                       | process_path                      |

#### Logstash pipeline

```
if [event_id] == 17 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "PipeName" => "pipe_name"
            "Image" => "process_path"
        }
      }
    }
```