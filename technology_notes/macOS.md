# Mac OS Notes

Documentation on miscellaneous MacOS tricks and tips

## Finder

  - Seeing dot files in `Finder`, simply type `CMD + SHIFT + .` to reveal all the dot files in a dir that were previously hidden (it's a toggle).

## Notes

## Hot Keys

## Applications

## Terminal
  
### SHELL
  
   Default shell is ZSH.
   I customised by using the `oh_my_zsh` community project (got link [here](https://www.sitepoint.com/zsh-tips-tricks/))
   
   Ran command 

   `sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`
   
   Seemed to have run nicely


## APFS
The **Apple File System**
Their proprietary FS.

By default the access timestamp of a file is only updated on read if the currently stored timestamp is prior the the file's modification timestamp.

This can be verified as follows.

Create a new file `touch foo`

Check access, modify and birth time's
`stat -x foo`

Alter metadata only `chmod 664 foo` and check time's `stat -x foo`. You should see Change time is different but modify and access the same (contents not changed).

Now change contents `echo "boo" >> foo` and check 
`stat -x foo`. All 3 times (but not Birth) should read the updated change. In particular access time is updated because otherwise it would be older than mtime. 

This behaviour makes sense as a default behaviour for filesystems (see [here](https://superuser.com/questions/464290/why-is-cat-not-changing-the-access-time)). But in a nutshell do you want to be writing inode data to disk just because you read a file (maybe even from cache)?

Note when you first create a file and immediately
do `stat -x` on it, all 3 times show the same, then after a short (~10s) delay, the mtime and atime are changed and different from each other so all 3 look different but are with 10s of each other. Then it stabilises - not sure but suspect it's some kernel cache  cleanup thing?

## Apple Time value
The timestamp on Apple systems is the **CF Absolute Time value** (aka **Mac Absolute Time**)
a 32-bit integer calculated by the number of seconds since 01/01/2001 00:00:00 UTC.
At least that was what I was able to find online.
Experimenting with this machine it seems I can do
`touch -t 190001010000.00 foo` (1st Jan 1900)
But not 
`touch -t 189912310000.00 foo` (1st Jan 1900)

Amusingly 
`touch -t 189912312359.60 foo` (1st Jan 1900)
works
but 
`touch -t 189912312359.59 foo` (1 sec before 1st Jan 1900 00:00:00)
doesn't, so down to the last second of 19th century is no good.

Note the `-t` option changes access time not creation time of file.

The final time I seem to be able to create is
Sat Apr 12 00:47:16 2262

So is that Apple's 32 bit clock counter problem date?


To get (Unix) Epoch time

`date -j -f "%a %b %d %T %Z %Y" "$(LC_ALL=C date)" "+%s"`
