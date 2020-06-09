# Event ID: 16 - Sysmon Config State Changed

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| UtcTime                     | event_date_creation               |
| Configuration               | sysmon_configuration              |
| ConfigurationFilePath       | sysmon_configuration_hash         |

#### Logstash pipeline

```
if [event_id] == 16 {
      mutate {
        rename => {
            "UtcTime" => "event_date_creation"
            "Configuration" => "sysmon_configuration"
            "ConfigurationFilePath" => "sysmon_configuration_hash"  
        }
      }
    }
```