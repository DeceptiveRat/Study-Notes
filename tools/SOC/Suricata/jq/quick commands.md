- view all events

```sh
jq '.' eve.json
```


- view event types found

```sh
jq '.event_type' eve.json | sort | uniq
```


- view dns event record type

```sh
jq 'select(.dns)' eve.json
```


- view rr names in dns

```sh
jq 'select(.dns).dns.queries[]?.rrname' eve.json
```


- view events with host name j.mp

```sh
jq 'select(.http.hostname == "j.mp")' eve.json
```


- view tls subjects

```sh
jq 'select(.tls).tls.subject' eve.json
```


- get alerts and flow where severity is 1 and print signature and dest ip

```sh
jq 'select(.alert.severity==1).alert, select(.alert.severity==1).flow' eve.json | grep -e "\"signature\"" -e "dest_ip"
```


- get signature of alerts with certain dest ip and severity 

```sh
jq 'select(.flow.dest_ip=="31.41.44.49" and .alert.severity==1).alert.signature' eve.json | sort | uniq | awk '{gsub(/\"/, ""); print}'
```


- get all destination ips where severity is 1

```sh
jq 'select(.alert.severity==1).dest_ip' eve.json | sort | uniq | awk '{gsub(/\"/, ""); print}'
```
