
# The Any Character

`grep -h '.zip' dirlist*.txt`

Output:

```
bunzip2
bzip2
bzip2recover
gunzip
gzip
funzip
gpg-zip
unzip
unzipsfx
```

the `.` metacharacter is the "Any" character. It matches any character in that character position.

The command searches for any line in our files that match the regular expression `.zip` 

The output does not contain `zip` because the match specifies at least 4 characters, and `zip` is 3. 

# Anchors

The caret (`^`) and dollar sign (`$`) characters are treated as anchors in regex.

This means they cause the match to occur only if the regular expression is found at the beginning of the line: `^` or the end of the line `$`.

```
[me@linuxbox ~]$ grep -h '^zip' dirlist*.txt
zip
zipcloak
zipgrep
zipinfo
zipnote

[me@linuxbox ~]$ grep -h 'zip$' dirlist*.txt
gunzip
gzip
funzip
gpg-zip
preunzip
unzip
zip

[me@linuxbox ~]$ grep -h '^zip$' dirlist*.txt
zip
```


# Bracket Expressions and Character Classes

With bracket expressions, we can specify a set of characters (including characters that would otherwise be interpreted as metacharacters) to be matched. 

The following says: "Match `b` or `g` with zip"

```
[me@linuxbox ~]$ grep -h '[bg]zip' dirlist*.txt
bzip2
bzip2recover
gzip
```

Keep in mind, characters between `[ ]` lose their special meanings, with two exceptions:

`-` : This is used to specify a range
`^` : This is used as negation.

```
[me@linuxbox ~]$ grep -h '[^bg]zip' dirlist*.txt
```

This will output lines in the file that do not contain `b` or `g` in the position before `zip`. Note that a negated character **still requires a character in that position**. 




