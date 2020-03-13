# What are .sortfiles?

a .sortfile is a file format that tells a file manager how to sort the files.

# Schema (still being developed)

```
#comments and blank lines are ignored

[this is a section, and it is ignored]
#lines before the first section are assumed to be
#part of the [sort] section (sane default behaviour)

[metadata]

#metadata is an optional, but important section

#version of .sortfile file format
version = 0.0.1

# which directory is the sortfile targeted at?
# default is the directory containing the sortfile.
root = .

#sort order of files not part of the [sort] section
sort_order = by_type

[sort]
README.md

# one filename per line, \ is the only escape character.
# \ escapes a #(comment) or a \n(for filenames with newlines) or \\(or with a slash), or \[ (files starting with '[' )
# also escape a newline by a backslash at the end.

# trivia: to encode a filename made solely of whitespaces, escape the first whitespace with a \
# to encode a # or \ or [, or a newline, escape it with \

\\file starting with a backslash
\ file starting with a whitespace
\# file starting with a comment

file\
with\
newlines\n and \
\# a #

subdirs/are/sorted
```
