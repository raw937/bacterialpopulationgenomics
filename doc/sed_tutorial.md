## Stream Editor -> sed
### Man's best friend

### Basic syntax
```sed [-n] [-e] 'command(s)' files``` 

- -n, --quiet, --silent: Same as standard -n option.
- -e script, --expression=script: Same as standard -e option.
- -f script-file, --file=script-file: Same as standard -f option.
- --follow-symlinks: If this option is provided, the SED follows symbolic links while editing files in place.
- i[SUFFIX], --in-place[=SUFFIX]: This option is used to edit file in place. If suffix is provided, it takes a backup of the original file, otherwise it overwrites the original file.
- -l N, --line-lenght=N: This option sets the line length for l command to N characters.
- --posix: This option disables all GNU extensions.
- -r, --regexp-extended: This option allows to use extended regular expressions rather than basic regular expressions.
- -u, --unbuffered: When this option is provided, the SED loads minimal amount of data from the input files and flushes the output buffers more often. It is useful for editing the output of "tail -f" when you do not want to wait for the output.
- -z, --null-data: By default, the SED separates each line by a new-line character. If NULL-data option is provided, it separates the lines by NULL characters.

### String replacement
```sed -i 's/Ham/Cheese/g' file.txt```
- replaces all strings "Ham" with "Cheese"

```sed -i 's/T/U/g' file.txt```
- replaces all strings "U" with "T"

### Show only lines 12-18 of file.txt
```sed -n 12,18p file.txt```

### Show all of file.txt except for lines from 12 to 18
```sed 12,18d file.txt```

### Double-space file.txt
```sed G file.txt```

### Write all commands in script.sed and execute them
```sed -f script.sed file.txt```

### Delete the last line
```sed '$d' file.txt```

### Print only lines with three consecutive digits
```sed '/[0-9]\{3\}/p' file.txt``` 

### Unless boom is found replace aaa with bb
```sed '/boom/!s/aaa/bb/' file.txt``` 


### Useful ones

#### Convert csv to tsv
```sed -E 's/("([^"]*)")?,/\2\t/g' file.csv >> file.tsv```
- converts column separate file to tab delim

#### Add a tab after the first space
```sed 's/^[ ]([^ ]) /\1\t/' file.txt >New_file.txt```
