# Event ID: 1 - Process Creation

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      | 
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| FileVersion                 | file_version                      |
| Description                 | file_description                  |
| Product                     | file_product                      |
| Company                     | file_company                      |
| OriginalFileName            | file_name_original                |
| CommandLine                 | process_command_line              |
| CurrentDirectory            | file_current_directory            |
| User                        | user_name                         |
| LogonGuid                   | user_logon_guid                   |
| LogonId                     | user_logon_id                     |
| TerminalSessionId           | user_session_id                   |
| IntegrityLevel              | process_integrity_level           |
| Hashes                      | sysmon_hash                       |
| ParentProcessGuid           | process_parent_guid               |
| ParentProcessId             | process_parent_id                 |
| ParentImage                 | process_parent_path               |
| ParentCommandLine           | process_parent_command_line       |

#### Logstash pipeline

```
if [event_id] == 1 {
      mutate {
        rename => {
          "RuleName" => "tag"
          "UtcTime" => "event_date_creation"
          "ProcessGuid" => "process_guid"
          "ProcessId" => "process_id"
          "Image" => "process_path"
          "FileVersion" => "file_version"
          "Description" => "file_description"
          "Product" => "file_product"
          "Company" => "file_company"
          "OriginalFileName" => "file_name_original"
          "CommandLine" => "process_command_line"
          "CurrentDirectory" => "file_current_directory"
          "User" => "user_name"
          "LogonGuid" => "user_logon_guid"
          "LogonId" => "user_logon_id"
          "TerminalSessionId" => "user_session_id"
          "IntegrityLevel" => "process_integrity_level"
          "Hashes" => "sysmon_hash"
          "ParentProcessGuid" => "process_parent_guid"
          "ParentProcessId" => "process_parent_id"
          "ParentImage" => "process_parent_path"
          "ParentCommandLine" => "process_parent_command_line"
        }
      }
    }
```