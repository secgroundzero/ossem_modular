# Bro/Zeek DCE RPC log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| uid                         | event_uid                         | 
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| rtt                         | request_rtt                       |
| named_pipe                  | rpc_server_named_pipe             |
| endpoint                    | rpc_server_pipe_name              |
| operation                   | rpc_pipe_action                   |

#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "dce_rpc" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:request_rtt}\t%{GREEDYDATA:rpc_server_named_pipe}\t%{DATA:rpc_server_pipe_name}\t%{GREEDYDATA:rpc_pipe_action}" } 
      }
    }
  }
```