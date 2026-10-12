1. functions return an integer
	- -1 for error and 0 for success by default
	- the global variable *error_message* should be set to the error message on error
	- the error is propagated down the stack, with each function cleaning up resources if necessary
	- the propagation stops when a function can handle the error (try again, do something else, etc)
	- termination should only be done at the top-level function unless:
		- the error is unrecoverable
		- proceeding could cause data corruption
	- *perror* should be used to print the name of the function where the error occurred

2. 