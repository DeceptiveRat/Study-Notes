
```c
	while((opt = getopt(argc, argv, ":htc:")) != -1)
	{
		switch(opt)
		{
			case 'h':
				printHelp(argv[0]);
				break;
			case 't':
				mode = 1;
				break;
			case 'c':
				train_iteration  = atoi(optarg);
				break;
			case '?': 
				printf("unknown option: %c\n", optopt);
				break;
		}
	}
```


reference:
- geeksforgeeks: <https://www.geeksforgeeks.org/c/getopt-function-in-c-to-parse-command-line-arguments/>