# Bro/Zeek RDP log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                      |
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| uid                         | event_uid                         |
| cert_count                  | cert_count                        |
| cert_permanent              | cert_permanent                    |
| cert_type                   | rdp_cert_type                     |
| client_build                | rdp_client_build                  |
| client_dig_product_id       | rdp_client_product_id             |
| client_name                 | rdp_client_domain_name            |
| cookie                      | rdp_client_cookie                 |
| desktop_height              | rdp_window_height                 |
| desktop_width               | rdp_window_width                  |
| encryption_level            | rdp_encyption_level               |
| keyboard_layout             | rdp_keyboard_layout               |
| requested_color_depth       | rdp_color_depth                   |
| result                      | rdp_connection_status             |
| security_protocol           | rdp_server_security_protocol      |
| ssl                         | ssl_enabled                       |
| client_channels             | rdp_client_channels               |
| encryption_method           | rdp_encryption_method             |


#### Logstash Grok Expression

```
filter {
  if [fields][zeek_log_name] == "rdp" {

  grok {
      match => { "message" => "%{NUMBER:timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{DATA:rdp_client_cookie}\t%{DATA:rdp_connection_status}\t%{DATA:rdp_server_security_protocol}\t%{DATA:rdp_client_channels}\t%{DATA:rdp_keyboard_layout}\t%{DATA:rdp_client_build}\t%{DATA:rdp_client_domain_name}\t%{DATA:rdp_client_product_id}\t%{DATA:rdp_client_window_width}\t%{DATA:rdp_client_window_height}\t%{DATA:rdp_client_color_depth}\t%{DATA:rdp_cert_type}\t%{DATA:rdp_cert_count}\t%{DATA:rdp_cert_permanent}\t%{DATA:rdp_encryption_level}\t%{DATA:rdp_encyption_method}" 
      }
    }
  }
```