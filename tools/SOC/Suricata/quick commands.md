1. start Suricata

```sh
sudo systemctl start suricata
sudo systemctl status suricata
```


2. view log information

```sh
sudo tail /var/log/suricata/eve.json | jq
```


3. reload suricata rules

```sh
sudo suricatasc -c reload-rules
```


4. replay pcap

```sh
suricata -c /etc/suricata/suricata.yaml -k none -r $PCAP_FILE --runmode=autofp -l "$LOG_LOCATION"
```
