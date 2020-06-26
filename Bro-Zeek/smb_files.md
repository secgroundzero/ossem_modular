# Bro/Zeek SMB Files log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| uid                         | event_uid                         | 
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| fuid                        | event_fuid                        |
| action                      | file_action                       |
| path                        | share_path                        |
| name                        | share_relative_target_name        |
| size                        | file_size                         |
| prev_name                   | file_previous_name                |
| times.modified              | file_modified_time                |
| times.accessed              | file_accessed_time                |
| times.created               | file_creation_time                |
| times.changed               | file_changed_time                 |


#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "smb_files" {

  grok {
      match => { "message" => "%{NUMBER:timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:event_fuid}\t%{DATA:event_action}\t%{DATA:share_path}\t%{DATA:share_relative_target_name}\t%{DATA:file_size}\t%{DATA:file_previous_name}\t%{DATA:file_modified_time}\t%{DATA:file_accessed_time}\t%{DATA:file_creation_time}\t%{DATA:file_changed_time}" 
      }
    }
  }
```