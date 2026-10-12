1. ARGIND
- index in ARGV of current file being processed

2. BINMODE
- specify binary mode for file I/O on non-POSIX systems
- 1 = r => input files should use binary I/O
- 2 = w => output files should use binary I/O
- 3 = wr = rw => all files should use binary I/O

3. ERRNO
- indicates an error when a redirection fails for getline or if close call fails

4. FIELDWIDTHS
- GAWK parses inputs into fields of fixed width, instead of using FS

5. IGNORECASE
- GAWK becomes case-insensitive

6. LINT
- dynamic control of --lint option

7. PROCINFO
- associative array containing information about the process

8. TEXTDOMAIN
- text domain of theAWK program
- used to find localized translations for the program's strings