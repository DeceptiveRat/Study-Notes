
```sh
#!/bin/bash

while getopts "f:h:c:l:s" opt; do
	case $opt in
		f) FILE="$OPTARG";;
		h)
			HEADERDIRECTORY="$OPTARG"
			cd "$HEADERDIRECTORY"
			find . -name "*.h" | while read -r header_file; do
				header_file=${header_file#./}
				c_file="${header_file%.h}.c"
				if [[ -f "$c_file" ]]; then
					o_file="${c_file%.c}.o"
					set -x
					gcc -c "$c_file" -o "$o_file" $COMPILEOPTION
					set +x
				else
					echo "warning: No matching .c file for $header_file"
				fi
			done
			cd "$STARTDIR" ;;
		c) COMPILEOPTION="$OPTARG" ;;
		l) LINKOPTION="$OPTARG" ;;
		s) LINKOPTION+=" -static" ;;
	esac
done
```
