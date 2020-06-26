# Bro/Zeek SMB Mapping log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| uid                         | event_uid                         |
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| path                        | share_name                        |
| service                     | smb_service_type                  |
| native_file_system          | file_system_type                  |
| share_type                  | share_type                        |


#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "smb_mapping" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:share_name}\t%{DATA:smb_service_type}\t%{DATA:file_system_type}\t%{DATA:share_type}" } 
      }
    }
  }
```