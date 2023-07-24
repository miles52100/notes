# SSH Notes

## SSH
A standard for secuer remote logins and file transfers over untrusted networks. Provides a way to secure the data traffic of any given application using port forwarding, basically tunneling any TCP/IP port over SSH.

## Key Pair Generation

```
>> ssh-keygen -t ecdsa -b 521 -f <filename_private_key> -C "Comment to identify key"
```

### Remarks

  * This creates a private/public key pair for authentication. 

  * The filename is the argument to `-f` and is the private key filename, the public key filename has the `.pub`
ending added.

  * The comment argument is appended to the public key

  * It's a good idea to move the key pair to '~/.ssh'

  * If you chose a non-default filename (giving the `-f` argument) you need to add it to the ssh-agent:
  
  ```
  ssh-add <filename_private_key
  ```

---

## Dot SSH directory
  Typically found in `${HOME}/.ssh`, this directory is not created by default, but typically when you first run `ssh <somehost>`

Typically `.ssh` will contain the following:

1. *private key* file (default name could be 'id_rsa')

2. *public key* file, typically with a '.pub' ending corresponding to the associated private key

3. *authorized_keys* A list of the public keys that can be used for logging in as this user (not highly sensitive, but should have read/write for the owner only - not group or world)

4. *known_hosts* A list of public keys for all hosts the ssh user has logged into. Again ideally should have read/write permissions for the owner only

5. *config* a per-user configuration file - see below - again with read/write permissions for this user only.

### Strucutre of the '.ssh/config' file

Typical structure will look like

```
Host hostname1
    SSH_OPTION value
    SSH_OPTION value

Host hostname2
    SSH_OPTION value

Host *
    SSH_OPTION value
```
 It's organised into stanzas (sections). The Host directive can contain a pattern or white-space list of patterns

 e.g. `10.10.0.[0-9]` matches the IP range, `!10.10.0.5` means not this host.
 The SSH client reads the configuration file stanza by stanza and the first matching stanza has precedence. So more host-specific declarations should be at the beginning of the file.


An example file might be, suppose as is typical, that you want to connect to a remote server, you need the username, hostname and port so you might use
`ssh john@dev.example.com -p 2322` for example

With a config file set up as

```
Host dev
  HostName dev.example.com
  User john
  Port 2322
```

You can then simply use `ssh dev`

The following example illustrates a more realistic config file

```
Host targaryen
    HostName 192.168.1.10
    User daenerys
    Port 7654
    IdentityFile ~/.ssh/targaryen.key

Host tyrell
    HostName 192.168.10.20

Host martell
    HostName 192.168.10.50

Host *ell
    user oberyn

Host * !martell
    LogLevel INFO

Host *
    User root
    Compression yes
```

When you type ssh targaryen, the ssh client reads the file and apply the options from the first match, which is Host targaryen. 

Then it checks the next stanzas one by one for a matching pattern. The next matching one is Host * !martell (meaning all hosts except martell), and it will apply the connection option from this stanza. 

The last definition Host * also matches, but the ssh client will take only the Compression option because the User option is already defined in the Host targaryen stanza.


The ssh client read its configuration in the following precedence order:

1. Options specified on the command line

2. Options defined in `~/.ssh/config`

3. Options defined in `/etc/ssh/ssh_config`

Taking the example config above, if we want use all the options for Host dev, but want to user to be root instead of john, use `ssh -o "User=root" dev`

The `-F <alternative-config-file>` option cna be used for per-user config files

---
---
## SSH Client and Server

 * SSH server - a program using the **Secure Shell Protocol** to accept connections from remote computers

 * SSH client - a program that allows the establishment of secure and authenticated SSH connections to SSH servers.

 There are many SSH client programs available: 'WinSCP', 'OpenSSH', 'PuTTY', 'iTerm 2' etc.


 ## SSH Tunnels and Port Forwarding
 A method of transporting arbitray networking data over an encerypted SSH connection.
 Can be used to add encryption to legacy applications, implement VPNs and access intranet services across firewalls

 ### Local Port Forwarding
 Access (remote) local network resources that aren't exposed to the internet.
 For example, say you want to access a database server attached to your office from your home.
 For security purposes the db is only configured to accept connections from the local office network.

 To do this, suppose you have established an SSH connection with the SSH server on the remote machine. You need to your SSH client to forward traffic rom a specific port, say 1234, to the address of the db's server and its port on the office network.

 To do this you need the `-L` option to `ssh`

 ```
 ssh -L local_port:remote_address:remote_port <username@server.com>
 ```

 If the server application you want is running on the same system as the SSH server itself you'll need something like

 ```
 ssh -L 8888:localhost:1234 bob@ssh.youroffice.com
 ```
 When the tunneled data arrives at the SSH server , that server will sent to port '1234' on 'localhost' (meaning the same host as the SSH server - i.e. the remote machine)

### Remote Port Forwarding
The opposite of local port forwarding - less frequently used.
Makes a resource on your local machine available to the remote machine.
For example, you might be running a web server on the local PC you're sitting in front of, but your local machine is behind a firewall that doesn't allow incoming traffic to the server software.

```
ssh -R remote_port:local_address:local_port username@server.com
```

So if you want your server app at port 1234 on your machine available at port 8888 on the remote SSH server machine then

```
ssh -R 8888:localhost:1234 bob@ssh.youroffice.com
```

### Dynamic port forwarding
This works similarly to a proxy or VPN.
The SSH client will create a 'SOCKS proxy' you can condifure applications to use.
All the traffic sent through the proxy would be sent through the SSH server. 
Similar to local forwarding - it takes local traffic sent to a specific port on your PC and sends it over the SSH connection to a remote location.

Suppose you're using a public WiFi network and you want to browse securely without being snooped on.
If you have access to an SSH server at home, you could connect to it and use dynamic port forwarding. The SSH client will create a SOCKS proxy on your PC. All traffic sent to that proxy will be sent over the SSH server connection.
From the perspective of any website you visit it will appear as if you were sitting in front of your PC at gome.

Another example, you may want to access a media server you have on your home network. For security reasons you may only have an SSH server exposed to the Internet. You don't allow incoming connections from the Internet to your media server. You could set up dynamic port forwarding, configure a web browser to use the SOCKS proxy and then access servers running on your home network through the web browser as if you were sitting in front of your SSH system at home.

E.g. if your media server is located at port 192:168:1.123 on your home netowkr, you could plug that address into any application using the SOCKS proxy and you'd access the media server as if you were on your home network.

To use dynamic forwarding, use the `-D` flag

```
ssh -D local_port username@server.com
```

For example suppose you have an access to an SSH server at `ssh.yourhome.com` and username on the SSH server is `bob`. You want to sue dynamic forwarding to open SOCKS proxy at port 8888 on the current PC. You'd run the command:

```
ssh -D 8888 bob@ssh.yourhome.com
```

You'd then configure a web browser or another application to use your local IP address (127.0.0.1) and port 8888. All traffic from the application would be redirected through the tunnel.

