# Bro/Zeek DNS log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| proto                       | network_protocol                  |
| id.orig_h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp.h                   | dst_ip_addr                       | 
| id.resp.p                   | dst_port                          |
| uid                         | event_uid                         |
| AA                          | dns_flags_authoritative           |
| addl                        | dns_additional_name               |
| auth                        | dns_additional_authoritative_name |
| answers                     | dns_response_name                 |
| TTLs                        | dns_response_ttl                  |
| RA                          | dns_flags_recursion_available     |
| RD                          | dns_flags_recursion_desired       |
| rejected                    | dns_rejected                      |
| TC                          | dns_flags_truncated               |
| Z                           | dns_flags_z                       |
| qclass                      | dns_query_class                   |
| qclass_name                 | dns_query_class_name              |
| qtype                       | dns_query_type                    |
| qtype_name                  | dns_query_type_name               |
| query                       | dns_query_name                    |
| rcode_name                  | dns_response_code_name            |
| rtt                         | dns_rtt                           |
| rcode                       | dns_response_code                 |
| trans_id                    | dns_transaction_id                |

#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "dns" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:orig_p}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{WORD:network_protocol}\t%{INT:dns_transaction_id}\t-\t%{GREEDYDATA:dns_query_name}\t%{GREEDYDATA:dns_query_class}\t%{GREEDYDATA:dns_query_class_name}\t%{GREEDYDATA:dns_query_type}\t%{GREEDYDATA:dns_query_type_name}\t%{GREEDYDATA:dns_response_code}\t%{GREEDYDATA:dns_response_code_name}\t%{GREEDYDATA:dns_flags_authoritative}\t%{GREEDYDATA:dns_flags_truncated}\t%{GREEDYDATA:dns_flags_recursion_desired}\t%{GREEDYDATA:dns_flags_recursion_available}\t%{GREEDYDATA:dns_flags_z}\t%{GREEDYDATA:dns_response_name}\t%{GREEDYDATA:dns_response_ttl}\t%{GREEDYDATA:dns_rejected}" 
      }
    }
  }
```