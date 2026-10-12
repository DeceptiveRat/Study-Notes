1. for parsing json

```plain-text
filebeat.inputs:
- type: filestream
  id: fs1
  enabled: false
  paths:
    - /var/log/auth.log
  fields:
    source_type: various logs
  fields_under_root: true

- type: filestream
  id: fs2
  enabled: false
  paths:
    - /var/log/syslog
  fields:
    source_type: system logs
  fields_under_root: true

- type: filestream
  id: fs3
  enabled: true
  paths:
    - /home/remnux/Downloads/*.json

  # This 'parsers' block is the correct, modern way
  parsers:
    - ndjson:
        # Move your settings inside here
        keys_under_root: true
        add_error_key: true
        message_key: "" # This will drop the original 'message' field
  
  
  fields:
    source_type: malicious logs

filebeat.config.modules:
  path: ${path.config}/modules.d/*.yml

  reload.enabled: false

  #reload.period: 10s

setup.template.settings:
  index.number_of_shards: 1

setup.kibana:

output.elasticsearch:
  hosts: ["localhost:9200"]

  preset: balanced
  username: "elastic"
  password: "5ZpVYURf"

processors:
  - add_host_metadata:
      when.not.contains.tags: forwarded
  - add_cloud_metadata: ~
  - add_docker_metadata: ~
  - add_kubernetes_metadata: ~
```
