# Windows DHCP Server Content Pack

Tested with Filebeats 7.17.12.0 / Windows 2022 / Graylog 5.1.4
The Content Pack should be compatible with all Graylog 5.X version.

**Note this was built using filebeats as the log exporter. No inputs extractor were used, only pipeline rules.**

**Do not need additionnal Grok pattern, uses the default like WORD/GREEDYDATA etc..**

## Includes

* Input (Beats/TCP/5044)
* Stream (Filebeat)
* Pipeline Rules w/ 4 stages (grok extractor, opcode_to_op_description, mac_prefix_extractor, mac_prefix_to_mac_vendor)
* Lookup table + Data adapter + data cache
* Dashboard (24h) (Windows DHCP Server)

## Not included

- [macaddress.csv](macaddress_list.csv)
- [dhcpv4_opcode.csv](dhcpv4_opcode.csv)

Add it to your Graylog server in /srv or if different location, modify the content_pack.json to change location path.

## Requirements
* Graylog 5.0 
* Windows DHCP server configured
* A log exporter/collector such as filebeats monitoring the directory path specified: (C:\Windows\system32\dhcp)

## Sidecar configuration file Example (agent side)
- C:\Program Files\Graylog\sidecar\sidecar.yml
```
server_url: "https://graylog.lab.lan/api"
server_api_token: "your_token_server"
node_id: "file:C:\\Program Files\\Graylog\\sidecar\\node-id"
node_name: ""
update_interval: 10
tls_skip_verify: true
send_status: true
tags: 
   - filebeat-windows-server
collector_binaries_accesslist:
   - "C:\\Program Files\\Graylog\\sidecar\\filebeat.exe"
```


## Screenshots

![image](https://github.com/s0p4L1n3/Graylog_Content_Pack_Windows_DHCP_Server/assets/126569468/956d788f-6b51-4c36-be72-6d7f6ddc3392)

