# Event ID: 4 - Sysmon service state changed

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| UtcTime                     | event_date_creation               |
| State                       | service_state                     |
| Version                     | file_version                      |
| SchemaVersion               | sysmon_schema_version             |


#### Logstash pipeline

```
if [event_id] == 4 {
      mutate {
        rename => {
          "UtcTime" => "event_date_creation"
          "State" => "service_state"
          "Version" => "file_version"
          "SchemaVersion" => "sysmon_schema_version"
        }
      }
    }
```