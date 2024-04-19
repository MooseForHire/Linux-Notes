# Intro
There are multiple sets of regular expressions. Several different applications use different
types of regex in Linux environments - Java, Perl, Python, sed, gawk, grep, MySQL, PostgreSQL.

A regex is implemented using a regular expression engine. This is the underlying software that interprets the expression.

The two most popular are:

- POSIX Basic Regular Expression (BRE)
- POSIX Extended Regular Expression (ERE)

Gawk uses ERE.

First some examples:

```$ echo "This is a test" | sed -n '/test/p'```      ----> If "test" is found, print the whole line. Output: 
This is a test

```$ echo "This is a test" | sed -n '/trial/p'```   -----> If "trial" is found, print the whole line. Output:

```$ echo "This is a test" | gawk '/test/{print $0}'```  ---> if "test" is found, print whole line. Output:
This is a test

```$ echo "This is a test" | gawk '/trial/{print $0}'``` ---> if "trial" is found, print whole line Output:


- As you can see from above, sed and gawk use different versions of the print command to print any lines matching.
- Note they are case-sensitive. If this were run: '/Test/p' or '/Test/{print $0}', it wouldn’t have matched.

It doesn’t have to match the whole word, it just needs to contain it:


$ echo "The books are expensive" | sed -n '/book/p'
The books are expensive.

It also can contain spaces and numbers:

$ echo "The books are expensive" | sed -n '/books are/p'
The books are expensive.



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




