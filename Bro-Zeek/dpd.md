# Bro/Zeek DPD log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| uid                         | event_uid                         | 
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| proto                       | dpd_violation_protocol            |
| analyzer                    | dpd_violation_analyzer            |
| failure_reason              | dpd_failure_reason                |



#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "dpd" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:dpd_violation_protocol}\t%{DATA:dpd_violation_analyzer}\t%{GREEDYDATA:dpd_failure_reason}" 
      }
    }
  }
```