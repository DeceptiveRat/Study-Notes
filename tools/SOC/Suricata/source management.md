1. print enabled sources

```sh
suricata-update list-enabled-sources
```


2. print all sources

```sh
suricata-update list-sources
```

- name of rule is used to enable/disable
- some rules are commercial only

3. update sources

```sh
suricata-update update-sources
```

- downloads index.yaml file from openinfosecfoundation
- checks if rule sources matches most recent version

4. enabling new rule source

```sh
suricata-update enable-source -h
suricata-update enable-source <source name>
suricata-update
```


5. disabling rule source

```sh
suricata-update disable-source <source name>
suricata-update
```


6. adding new rule sources

```sh
suricata-update add-source -h
```
