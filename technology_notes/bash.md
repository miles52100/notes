# Bash Notes

Documentation on Bash builtin commands

## ls

  Useful options
  
  * `ls -lT` prints full time, by default this is the file's last time of access as opposed to just modification of metadata. This command is equivalent to using the `-u` option with `-l`
  (the `-T` just prints full time incl. seconds)

  * `ls -lTU` prints file's creation time

  * `ls -lTc` prints file's change time, including change to metadata

  * `ls -ld` prints info about a directory instead of its contents so typically you might just see
  output `drwxr-xr-x 8 ... 12:42 .` (note the dot or current dir at end)
  So you could do
  `mkdir -p d1/d2`
  `touch d1/d2/f1 d1/d2/f2`
  Then `ls -al d1/d2` lists 'files' '..', '.', 'f1' and 'f2' but `ls -adl` only lists 'd1/d2'
  (so dir as file and not its contents - f1 and f2)
  
## date

## stat

  * `stat -x <filename>`  display's all the file's stat info in a verbose (and more readable) way.

## Hot Keys

## Applications

## Terminal
  

