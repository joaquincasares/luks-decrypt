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

A word file named `abca.txt` would look something like this:

```
abca
a,x
c,x
```

A words file would contain multiple words for a part of a phrase, including empty lines if it's possible the word may not exist in a phrase.

```
==> words/abca.txt <==
abca
abcx
abxa
abxx
xbca
xbcx
xbxa
xbxx

==> words/joiner.txt <==
&


==> words/myword.txt <==
this
that
somethingelse
```

Phrase files collect words and separate them with a `===`:

```
abca
abcx
abxa
abxx
xbca
xbcx
xbxa
xbxx
===
&

===
this
that
somethingelse
```

Each line a phrases file is used to attempt to decrypt a luks encrypted device via cryptsetup:

```
abca&this
abca&that
abca&somethingelse
abcathis
abcathat
abcasomethingelse
abcx&this
abcx&that
abcx&somethingelse
abcxthis
abcxthat
abcxsomethingelse
abxa&this
abxa&that
abxa&somethingelse
abxathis
abxathat
abxasomethingelse
abxx&this
abxx&that
abxx&somethingelse
abxxthis
abxxthat
abxxsomethingelse
xbca&this
xbca&that
xbca&somethingelse
xbcathis
xbcathat
xbcasomethingelse
xbcx&this
xbcx&that
xbcx&somethingelse
xbcxthis
xbcxthat
xbcxsomethingelse
xbxa&this
xbxa&that
xbxa&somethingelse
xbxathis
xbxathat
xbxasomethingelse
xbxx&this
xbxx&that
xbxx&somethingelse
xbxxthis
xbxxthat
xbxxsomethingelse
```