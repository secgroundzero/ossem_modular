# Event ID: 6 - Driver Loaded

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ImageLoaded                 | driver_loaded                     |
| Hashes                      | sysmon_hash                       |
| Signed                      | driver_is_signed                  |
| Signature                   | driver_signature                  |
| SignatureStatus             | driver_signature_status           |

#### Logstash pipeline

```
if [event_id] == 6 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ImageLoaded" => "driver_loaded"
            "Hashes" => "sysmon_hash"
            "Signed" => "driver_is_signed"
            "Signature" => "driver_signature"
            "SignatureStatus" => "driver_signature_status"
        }
      }
    }
```