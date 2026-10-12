1. text preprocessing
- convert to text to vectors 
- framework:
   - noise removal
   - tokenization/segmentation/lexical analysis
   - normalization

2. tokenization
- split strings of text into smaller tokens
- remove punctuation marks 
- remove one and two-letter words
- remove stop words (a, the, in, of, ...)

3. normalization
- word stemming:
   - remove prefix, suffix, etc
   - e.g. running -> run, ended -> end, ...
- lemmatization:
   - convert word to canonical form
   - e.g. better -> good, ran -> run, ...
- others:
   - convert to same case
   - remove punctuation
   - convert numbers to words
   - remove stop words

reference:
- Gachon University - Machine learning lecture