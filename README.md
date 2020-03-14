# What are .sortfiles?

a .sortfile is a file format that tells a file manager how to sort files and directories.

# Format (still being developed)

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
LICENSE

#i.e. README appears before the LICENSE.

#paths are relative to `root` variable in [metadata]

# one filename/dirname (name) per line, \ is the only escape character.
# to encode a # or \ or [, or a newline, escape it with \ (or use \n)
# \ escapes a # or a \n(for names with newlines) or \\(or with a slash), or \[ (names starting with '[' )
# also escape a newline by a backslash at the end.

# trivia: to encode a name made solely of whitespaces, escape the first whitespace with a \

\\name starting with a backslash
\ name starting with a whitespace
\# name starting with a hashtag

file\
with\
newlines\n and \
\# a #

subdirs/are/sorted
```
# .sortfile search path

a file manager plugin searchs the current directory and all parent directories for a .sortfile.
