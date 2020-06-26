# Bro/Zeek Conn log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| proto                       | network_protocol                  |
| id.orig_h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp.h                   | dst_ip_addr                       |
| id.resp.p                   | dst_port                          |
| vlan                        | network_outer_vlan_id             |
| inner_vlan                  | network_inner_vlan_id             |
| tunnel_parents              | zeek_connection_tunnel_parents    |
| uid                         | event_uid                         |
| orig_bytes                  | src_bytes                         |
| orig_ip_bytes               | src_ip_bytes                      |
| orig_l2_addr                | src_mac                           |
| orig_pkts                   | src_packets                       |
| local_orig                  | zeek_connection_local_src         |
| local_resp                  | zeek_connection_local_dst         |
| duration                    | event_duration                    |
| history                     | network_connection_history        |
| conn_state                  | network_connection_state          |
| missed_bytes                | network_missed_bytes              |
| service                     | network_application               |
| resp_bytes                  | dst_bytes                         |
| resp_ip_bytes               | dst_ip_bytes                      |
| resp_l2_addr                | dst_mac                           |
| resp_pkts                   | dst_packets                       |


#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "conn" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{WORD:network_protocol}\t%{GREEDYDATA:network_application}\t%{NUMBER:event_duration}\t%{NUMBER:src_bytes}\t%{NUMBER:dst_bytes}\t%{GREEDYDATA:network_connection_state}\t%{GREEDYDATA:zeek_connection_local_src}\t%{GREEDYDATA:network_missed_bytes}\t%{GREEDYDATA:network_connection_history}\t%{GREEDYDATA:src_packets}\t%{GREEDYDATA:src_ip_bytes}\t%{GREEDYDATA:dst_packets}\t%{GREEDYDATA:dst_ip_bytes}\t%{GREEDYDATA:zeek_connection_tunnel_parents}" }
      }
    }
  }
```