# Event ID: 7 - Sysmon service state changed

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      | 
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| ImageLoaded                 | module_loaded                     |
| FileVersion                 | file_version                      |
| Description                 | file_description                  |
| Product                     | file_product                      |
| Company                     | file_company                      |
| OriginalFileName            | file_name_original                |
| Hashes                      | sysmon_hash                       |
| Signed                      | module_is_signed                  |
| Signature                   | module_signature                  | 
| SignatureStatus             | module_signature_status           |

#### Logstash pipeline

```
if [event_id] == 7 {
      mutate {
        rename => {
            "RuleName" => "tag"
            "UtcTime" => "event_date_creation"
            "ProcessGuid" => "process_guid"
            "ProcessId" => "process_id"
            "Image" => "process_path"
            "ImageLoaded" => "module_loaded"
            "FileVersion" => "file_version"
            "Description" => "file_description"
            "Product" => "file_product"
            "Company" => "file_company"
            "OriginalFileName" => "file_name_original"
            "Hashes" => "sysmon_hash"
            "Signed" => "module_is_signed"
            "Signature" => "module_signature"
            "SignatureStatus" => "module_signature_status"
        }
      }
    }
```