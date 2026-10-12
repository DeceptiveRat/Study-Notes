1. fine-tuning
![unnamed_d2ece4e757624a81b54a9f56f9a57c74](unnamed_d2ece4e757624a81b54a9f56f9a57c74.png)
- transforms generalist created after pre-training to specialist
- high performance despite low training cost

2. downstream tasks
- text classification
- Named Entity Recognition(NER)
- Question Answering(QA)
- summarization

3. Parameter Efficient Fine Tuning(PEFT)
- full fine-tuning requires separate management of multiple models
- freeze generalist model and only add a few core parameters
- LoRA is a widely used standard
![unnamed_1aa8834d23bb47a69a4d4391d59e1cf6](unnamed_1aa8834d23bb47a69a4d4391d59e1cf6.png)

reference:
- 가천대 인공지능입문 Lecture 5 강의 자료 