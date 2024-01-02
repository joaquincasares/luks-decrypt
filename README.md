# luks-decrypt

```bash
# generate words from a word with possible character substitutions
./bin/generate-words \
    ./word/abca.txt

# generate a phrase file from a group of words
./bin/generate-phrase \
    ./words/abca.txt \
    ./words/joiner.txt \
    ./words/myword.txt

# generate phrases using a phrase file
./bin/generate-phrases \
    ./phrase/abca.joiner.myword.txt

# attempt multiple phrases to decrypt a luks using cryptsetup
./bin/decrypt \
    ./phrases/abca.joiner.myword.txt
```