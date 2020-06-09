# Event ID: 3 - Network Connection

|Native field name            |OSSEM Field Name                   |
|:----------------------------|:----------------------------------|
| RuleName                    | tag                               |
| UtcTime                     | event_date_creation               |
| ProcessGuid                 | process_guid                      |
| ProcessId                   | process_id                        |
| Image                       | process_path                      |
| User                        | user_name                         |
| Protocol                    | network_protocol                  |
| Initiated                   | network_connection_initiated      |
| SourceIsIpv6                | src_is_ipv6                       |
| SourceIp                    | src_ip_addr                       |
| SourceHostname              | src_host_name                     |
| SourcePort                  | src_port                          |
| SourcePortName              | src_port_name                     |
| DestinationIsIpv6           | dst_is_ipv6                       |
| DestinationIp               | dst_ip_addr                       |
| DestinationHostname         | dst_host_name                     |
| DestinationPort             | dst_port                          |
| DestinationPortName         | dst_port_name                     |


#### Logstash pipeline

```
if [event_id] == 3 {
      mutate {
        rename => {
          "RuleName" => "tag"
          "UtcTime" => "event_date_creation"
          "ProcessGuid" => "process_guid"
          "ProcessId" => "process_id"
          "Image" => "process_path"
          "User" => "user_name"
          "Protocol" => "network_protocol"
          "Initiated" => "network_connection_initiated"
          "SourceIsIpv6" => "src_is_ipv6"
          "SourceIp" => "src_ip_addr"
          "SourceHostname" => "src_host_name"
          "SourcePort" => "src_port"
          "SourcePortName" => "src_port_name"
          "DestinationIsIpv6" => "dst_is_ipv6"
          "DestinationIp" => "dst_ip_addr"
          "DestinationHostname" => "dst_host_name"
          "DestinationPort" => "dst_port"
          "DestinationPortName" => "dst_port_name"
        }
      }
    }
```