# Event ID: 22 - DNSEvent (DNS query)

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| QueryName                   | dst_host_name                     |
| QueryStatus                 | dns_query_status                  |
| QueryResults                | dns_query_results                 |
| Image                       | process_path                      |


#### Logstash pipeline

```
if [event_id] == 22 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "QueryName" => "dst_host_name"
            "QueryStatus" => "dns_query_status"
            "QueryResults" => "dns_query_results"
            "Image" => "process_path"
        }
      }
    }
```