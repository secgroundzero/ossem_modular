# Bro/Zeek HTTP log

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| ts                          | @timestamp                        |
| id.orig.h                   | src_ip_addr                       |
| id.orig_p                   | src_port                          |
| id.resp_h                   | dst_ip_addr                       |
| id.resp_p                   | dst_port                          |
| uid                         | event_uid                         |
| orig_fuids                  | zeek_uid_orig_fuids               |
| username                    | url_user_name                     |
| password                    | url_user_password                 |
| resp_fuids                  | zeek_uid_resp_fuids               |
| host                        | url_host_name                     |
| cookie_vars                 | http_cookie_variables             |
| client_header_names         | http_request_header_names         |
| info_code                   | http_informational_code           |
| info_msg                    | http_informational_message        |
| method                      | http_request_method               |
| orig_filenames              | src_file_path                     |
| orig_mime_types             | src_mime_type                     |
| origin                      | http_header_origin                |
| post_body                   | http_response_body_original       |
| proxied                     | request_proxied                   |
| referrer                    | httpreferrer original             |
| request_body_len            | http_request_body_bytes           |
| response_body_len           | http_response_body_bytes          |
| server_header_names         | http_response_header_names        |
| resp_mime_types             | dst_mime_type                     |
| omniture                    | server_is_omniture                |
| status_code                 | http_status_code                  |
| status_msg                  | http_status_message               |
| trans_depth                 | trans_depth                       |
| version                     | http_version                      |
| resp_filenames              | dst_file_path                     |
| flash_version               | flash_version                     |
| tags                        | tags                              |
| uri                         | url_original                      |
| uri_vars                    | url_vars                          |
| user_agent                  | user_agent_original               |


#### Logstash Grok Expression


```
filter {
  if [fields][zeek_log_name] == "http" {

  grok {
      match => { "message" => "%{NUMBER:@timestamp}\t%{NOTSPACE:event_uid}\t%{IP:src_ip_addr}\t%{INT:src_port}\t%{IP:dst_ip_addr}\t%{INT:dst_port}\t%{INT:trans_depth}\t%{DATA:http_request_method}\t%{DATA:url_host_name}\t%{DATA:url_original}\t%{DATA:httpreferrer_original}\t%{DATA:http_version}\t%{DATA:user_agent_original}\t%{NUMBER:http_request_body_bytes}\t%{NUMBER:http_request_body_bytes}\t%{DATA:http_status_code}\t%{DATA:http_status_message}\t%{DATA:http_informational_code}\t%{DATA:http_informational_message}\t%{DATA:src_file_path}\t%{DATA:tags}\t%{DATA:url_user_name}\t%{DATA:url_user_password}\t%{DATA:request_proxied}\t%{DATA:zeek_uid_orig_fuids}\t%{DATA:src_mime_type}\t%{DATA:zeek_uid_resp_fuids}\t%{DATA:dst_file_path}\t%{DATA:dst_mime_type}" }
      }
    }
  }
```