# Bro/Zeek SSL log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| uid                         | event_uid                         | 
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| version                     | tls_version                       |
| cipher                      | tls_cipher                        |
| curve                       | tls_curve                         |
| server_name                 | dst_host_name                     |
| resumed                     | tls_resumed                       |
| last_alert                  | tls_last_alert                    |
| next_protocol               | tls_next_protocol                 |
| established                 | tls_established                   |
| cert_chain_fuids            | zeek_uid_cert_chain_fuids         |
| client_cert_chain_fuids     | zeek_uid_client_cert_chain_fuids  |
| subject                     | dst_certificate_subject_name      |
| issuer                      | dst_certificate_issuer_name       |
| client_subject              | certificate_subject               |
| client_issuer               | certificate_issuer                |
| validation_status           | tls_certificate_validation_status |


#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "ssl" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:tls_version}\t%{DATA:tls_cipher}\t%{DATA:tls_curve}\t%{DATA:dst_host_name}\t%{DATA:tls_resumed}\t%{DATA:tls_last_alert}\t%{DATA:tls_next_protocol}\t%{DATA:tls_established}\t%{DATA:zeek_uid_cert_chain_fuids}\t%{DATA:zeek_uid_client_cert_chain_fuids}\t%{DATA:dst_certificate_subject_name}\t%{DATA:dst_certificate_issuer_name}\t%{DATA:certificate_subject}\t%{DATA:certificate_issuer}\t%{GREEDYDATA:tls_certificate_validation_status}" }
      }
    }
  }
```