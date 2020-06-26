# Bro/Zeek NTLM log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| uid                         | event_uid                         | 
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| username                    | ntlm_username                     |
| hostname                    | ntlm_client_hostname              |
| domainname                  | ntlm_client_domain_name           |
| server_nb_computer_name     | ntlm_server_netbios_name          |
| server_dns_computer_name    | ntlm_server_dns_name              |
| server_tree_name            | ntlm_server_tree_name             |
| success                     | ntlm_auth_status                  |


#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "ntlm" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:ntlm_username}\t%{DATA:ntlm_client_hostname}\t%{DATA:ntlm_client_domain_name}\t%{DATA:ntlm_server_netbios_name}\t%{DATA:ntlm_server_dns_name}\t%{GREEDYDATA:ntlm_server_tree_name}\t%{GREEDYDATA:ntlm_auth_status}" }
      }
    }
  }
```