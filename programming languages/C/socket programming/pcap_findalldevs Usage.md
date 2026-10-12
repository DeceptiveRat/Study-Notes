
```c
char errbuf[PCAP_ERRBUF_SIZE];
pcap_if_t *interface_list;
pcap_t *pcap_handle;

if(pcap_findalldevs(&interface_list, errbuf) == PCAP_ERROR)
	pcap_fatal("At findalldevs", errbuf);

pcap_if_t *interface = interface_list;
for(int i =0;i>-1;++i)
{
	if(interface == NULL)
		break;
	printf("Interface #[%d] Name: %s (%s)\n", i, interface->name, interface->description);
	interface = interface->next;
}

printf("Choose an interface to use:\n");
int interfaceNumber;
scanf("%d", &interfaceNumber);

interface = interface_list;
for(int i = 0;i<interfaceNumber;i++)
{
	if(interface == NULL)
	{
		printf("Choose a correct interface\n");
		exit(0);
	}

	interface = interface->next;
}

printf("Sniffing on device %s (%s)\n", interface->name, interface->description);

pcap_handle = pcap_open_live(interface->name, 16384, 1, 100, errbuf);
if(pcap_handle == NULL)
	pcap_fatal("At handle", errbuf);

pcap_loop(pcap_handle, CAPTURECOUNT, caught_packet, NULL);

pcap_freealldevs(interface_list);
```

