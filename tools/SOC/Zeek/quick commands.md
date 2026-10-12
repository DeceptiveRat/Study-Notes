1. run zeek in docker against sample.pcap in current directory

```sh
sudo docker run -it --rm -v $(pwd):/pcaps -w /pcaps zeek/zeek:lts zeek -C -r sample.pcap
```


2. run docker with zeek installed

```sh
sudo docker run -it --rm -v $(pwd):/pcaps -w /pcaps zeek/zeek:lts bash
```


3. use zeek-cut to format zeek log

```sh
cat conn.log | zeek-cut -d ts id.orig_h id.orig_p id.resp_h id.resp_p service >> text.txt
```


4. output json format logs with docker zeek (for ingesting with filebeat)

```sh
echo "redef LogAscii::use_json=T;" > json-config.zeek
sudo docker run -it --rm -v $(pwd):/pcaps -w /pcaps zeek/zeek:lts \
  zeek -C -r 2025-01-22-traffic-analysis-exercise.pcap json-config.zeek
```
