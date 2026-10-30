## model
- `ollama pull <model>`: download base model (e.g. `ollama pull gemma2:9b`)
- `ollama create <model name> -f <model file>`: build custom model (e.g. `ollama create gemma-claude -f Modelfile)
- `ollama rm <model>`: delete base model (e.g. `ollama rm [gemma2:9b | gemma-claude]`)

## basics
- `ollama launch claude --model gemma-claude`: launch bypassing menu
- `ollama list`: list models