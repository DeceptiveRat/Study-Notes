## etc
- check sources and values
``` sh
for INDEX in {0..6}; do
export FIELDNAME="tool_calls[$INDEX].args.ReplacementContent";
echo -e "\navailable sources:";
jq "select(.$FIELDNAME != null) | .source" transcript_full.jsonl | sort | uniq | tr "\n" ", " | awk -F"," -v OFS=, "{NF--; print}"
echo -e "\navailable values:";
jq "select(.$FIELDNAME != null) | .$FIELDNAME" transcript_full.jsonl | sort | uniq | head -c 1000 | tr "\n" ", " | awk -F"," -v OFS=", " "{NF--; print}";
done
```

- check for conditions
``` sh
for INDEX in {0..6}; do
export FIELDNAME="tool_calls[$INDEX].args.Overwrite";
jq -c "select(.$FIELDNAME != null) | walk(if type == \"string\" and length > 100 then .[0:100] + \"...\" else . end)" transcript_full.jsonl | head -n 10 | jq .;
done
```

- find conditions
``` sh
for ITEM in $(jq -r "select(.tool_calls[0].name != null) | .tool_calls[0].name" transcript_full.jsonl | sort -u); do
	echo "--- $ITEM ---"
	jq --arg name "$ITEM" 'select(.tool_calls[0].name == $name) | .tool_calls[0].args | paths | select(all(type == "string")) | join(".")' transcript_full.jsonl | sort -u;
done
```

- view value
``` sh
export FIELDNAME="tool_calls[]?.args.WaitMsBeforeAsync";
jq "select(.$FIELDNAME != null) | .$FIELDNAME | walk(if type == \"string\" and length > 100 then .[0:100] + \"...\" else . end)" transcript_full.jsonl
```

- truncate long data
``` sh
walk(if type == "string" and length > 100 then .[0:100] + "..." else . end)
```

- get keys
``` sh
paths | map(if type == "number" then "[]" else tostring end) | join(".")
```