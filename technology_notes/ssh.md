# SSH Notes

## Key Pair Generation

```
>> ssh-keygen -t ecdsa -b 521 -f <filename_private_key> -C "Comment to identify key"
```

### remarks

  * This creates a private/public key pair for authentication. 

  * The filename is the argument to `-f` and is the private key filename, the public key filename has the `.pub`
ending added.

  * The comment argument is appended to the public key

  * It's a good idea to move the key pair to '~/.ssh'

  * If you chose a non-default filename (giving the `-f` argument) you need to add it to the ssh-agent. `ssh-add <filename_private_key`

