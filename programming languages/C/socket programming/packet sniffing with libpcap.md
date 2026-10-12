### 1. pcap_findalldevs()
- use pcap_if_t types that can contain interfaces

```c
#include <pcap.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(int argc, char **argv)
{
	char errbuf[PCAP_ERRBUF_SIZE];
	pcap_if_t *interface_list;

	if(pcap_findalldevs(&interface_list, errbuf) == PCAP_ERROR)
		pcap_fatal("At findalldevs", errbuf);

	pcap_if_t *interface;

	for(interface = interface_list;interface!=NULL;interface = interface->next)
		printf("Name: %s (%s)\n", interface->name, interface->description);

	pcap_freealldevs(interface_list);
}
```


2. 