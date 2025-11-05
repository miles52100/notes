# SSH Notes

## SSH

A standard for secure remote logins and file transfers over untrusted networks. Provides a way to secure the data traffic of any given application using port forwarding, basically tunneling any TCP/IP port over SSH.

## Key Pair Generation

```text
    >> ssh-keygen -t ecdsa -b 521 -f <filename_private_key> -C "Comment to identify key"
```

### Remarks

* This creates a private/public key pair for authentication.
* The filename is the argument to `-f` and is the private key filename, the public key filename has the `.pub` ending added.
* The comment argument is appended to the public key
* It's a good idea to move the key pair to '~/.ssh'
* If you chose a non-default filename (giving the `-f` argument) you need to add it to the ssh-agent:

### SSH agent

See some of the references for useful information on the agent.

You need to start an SSH agent and then add private keys to the agent.
If the keys are password protected, you'll need to enter the password once only to release to the agent. After that the agent should be able to respond to all SSH challenges during connections without you having to re-enter the password, etc.

Agent sockets are usually stored in:

```text
> ls -l /tmp/ssh-*
```

Normally an agent is started in one of the initial user dot files, so that sub-shells, terminals, etc., all have access to the agent.
One of the environment variables set when the agent is started is `SSH_AUTH_SOCK` which typically will be set to one of the agent sockets above.

To add a private key to an already running agent:

```text
> ssh-add <filename_private_key>
```

To see what keys have been added to the ssh-agent run

```text
> ssh-add -l
```

---

## Reading keys

The default format for written keys is `OpenSSH-specific`.
For open-ssh versions >= 6.5 `ssh -V` tells you what version you have.
In the VScode terminal this returns

```text
> OpenSSH_9.9p2, LibreSSL 3.3.6
```

Incidentally, the 'p' stands for patch (somtimes you might see 'pl' standing for patch level). "LibreSSL" is an open source implementation of TLS protocol.
Apparently, the OpenBSD project forked LibreSSL from OpenSSL 1.0.1g in 2014.

The public key is **base64-encoded** and so readable as a string, e.g.,
`cat <pubkey>.pub` works.
The private key is a **binary** file and you need a tool to obtain a human readable output.

Typically you'll need an `openssl` command to do this, which means knowing the **type of private key**. For example if you know it's an RSA key then

```text
    openssl rsa -text -noout -in <path-to-priv-key>
```

To get that key type, run (works with pub or priv)

```text
    ssh-keygen -lf <path-to-key>
```

This shows the type of key at end as well as printing out the key's fingerprint.

For OpenSSH-specific format you can just read it as its base-64 encoded

See the reference for information on the differences between OpenSSH and OpenSSL key formats.

## Validating and comparing keys by value

Two approaches, either compare the key fingerprints or compare their randomart visualisations.

Two typical situations where you might want to compare keys:

  1. You have two, differently named or same filename but located in different directories or systems, public or private keys and you want to check they're actually the same key
  2. You have a public (private) key and you want to check it is paired with a given private (public) key

In both cases, printing the fingerprint or randomart will work.

**NOTE** the fingerprint and the randomart are associated to the key pair. So the fingerpint (randomart) of a public key is **the same** as that for the corresponding private key.

### Key fingerprint

A fingerprint of the public key.

Typically on key generation this will take the form of

```text
    [type:] [hexadecimal encoding of fingerprint] [comment]
    SHA256:k577E0vW1wfUBNIq7gEKCNiTtb5HqjG9hxsMeqe3zYQ my edward curve key
```

To obtain the fingerprint run

`ssh-keygen -l -f <path-to-key>.pub`

### Key randomart

See this [paper](http://users.ece.cmu.edu/~adrian/projects/validation/validation.pdf)

The purpose is to provide a visual alternative to validating keys rather than comparing the fingerprint strings -  the idea being any change is much esaier to spot in the randomart.

To obtain the randomart

`ssh-keygen -lv -f <path-to-key>.pub`

---

## Typical User set-up

### Dot SSH directory

Typically found in `${HOME}/.ssh`, this directory is not created by default, but is created typically when you first run `ssh <somehost>`

Typically `.ssh` will contain the following:

1. *private key* file(s) (default name could be 'id_rsa')
2. *public key* file(s), typically with a '.pub' ending corresponding to the associated private key
3. *authorized_keys*
   A list of the public keys used to authenticate a user logging into the server.
   The user will use their associated private key to authenticate themselves.
   This list is not highly sensitive, but should have read/write for the owner only - not group or world.
4. *known_hosts*
   A list of public keys for all hosts the ssh user has logged into.
   When you try to SSH into a server or service for the first time, then you'll be asked if you trust the server and if you accept then its public key will be added to the list in this file.
   Again, ideally this file should have read/write permissions for the owner only.
5. *config* a per-user configuration file, see details below.
   This file should have read/write permissions for the user only.

#### authorized_keys

Contains a list of public keys that users authenticating with the corresponding private key are authorized to log in to the server. Used to prevent unauthorized users from connecting to the SSH server.
Typically you'll want to store your public key in this file on the remote machine you're trying to configure for ssh conection.

The file can be edited manually, but it's recommended to use `ssh-copy-id` command to add a user's public key.
It copies the public key to the remote server's authorized_keys file, preserving any existing keys and sets correct permissions on the file to enable it to be used for SSH key-based authentication.

The format of each entry is
`ssh-[type] [public key] [comment]`

The file permissions should be set to `600`, i.e., user read and write only.

#### known_hosts

A list of public keys for all hosts the ssh client has logged into.
**check read/write** permissions
A Typical entry:

```text
    bitbucket.tdx.gss.gov.uk ssh-rsa
    AAAAB3NzaC1yc2EAAAADAQABAAABAQCidjBAlZS7Bt8LWaKUGuMjR/
    ...
    TOgTDZeJZdcDZBPh1i188/Vcr    
```

SSH clients store these known host keys for hosts they have ever connected to.
In OpenSSH the collection is stored in `/etc/ssh/known_hosts` and in `.ssh/known_hosts` in each user's home directory.

#### Structure of the '.ssh/config' file

Typical structure will look like

```text
Host hostname1
    SSH_OPTION value
    SSH_OPTION value

Host hostname2
    SSH_OPTION value

Host *
    SSH_OPTION value
```

 It's organised into stanzas (sections). The Host directive can contain a pattern or white-space list of patterns,
 e.g., `10.10.0.[0-9]` matches the obvious IP range, `!10.10.0.5` means not this host, etc.
 The SSH client reads the configuration file stanza by stanza and the **first** matching stanza has precedence. So more host-specific declarations should be at the beginning of the file.

An example file might be as follows.
Suppose you want to connect to a remote serverthen you need the username, hostname and port for the connection. For example,
`ssh john@dev.example.com -p 2322`

If your config file looks like:

```text
Host dev
  HostName dev.example.com
  User john
  Port 2322
```

You can easily connect with the command

`ssh dev`

The following example illustrates a more realistic config file

```text
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
    User oberyn

Host * !martell
    LogLevel INFO

Host *
    User root
    Compression yes
```

With this config file running
`ssh targaryen`
will result in the ssh client reading the config file and applying the options from the first match which, in this example, is `Host targaryen`.

Then it checks the next stanza for a matching pattern. The next matching one is `Host * !martell`, meaning all hosts except `martell`, and it will apply the connection option from this stanza.

The last stanza matching pattern is `Host *`, but the ssh client will take only the Compression option because the User option has already been set from the first matching stanza, `targaryen`.

The ssh client reads its configuration from the following files, ordered by precedence:

1. Options specified on the command line

2. Options defined in `~/.ssh/config`

3. Options defined in `/etc/ssh/ssh_config`

Taking the example config above, if we want to use all the options for Host dev, but want to user to be root instead of john, use `ssh -o "User=root" dev`

The `-F <alternative-config-file>` option cna be used for per-user config files

For full information on `ssh config`, read the man page via `man 5 ssh_config`

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

 ```text
 ssh -L local_port:remote_address:remote_port <username@server.com>
 ```

If the server application you want is running on the same system as the SSH server itself you'll need something like

 ```text
 ssh -L 8888:localhost:1234 bob@ssh.youroffice.com
 ```

When the tunneled data arrives at the SSH server , that server will sent to port '1234' on 'localhost' (meaning the same host as the SSH server - i.e. the remote machine)

### Remote Port Forwarding

The opposite of local port forwarding - less frequently used.
Makes a resource on your local machine available to the remote machine.
For example, you might be running a web server on the local PC you're sitting in front of, but your local machine is behind a firewall that doesn't allow incoming traffic to the server software.

```text
ssh -R remote_port:local_address:local_port username@server.com
```

So if you want your server app at port 1234 on your machine available at port 8888 on the remote SSH server machine then

```text
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

```text
ssh -D local_port username@server.com
```

For example suppose you have access to an SSH server at `ssh.yourhome.com` and your username on the SSH server is `bob`. You want to use dynamic forwarding to open a SOCKS proxy at port 8888 on the current PC. You'd run the command:

```text
ssh -D 8888 bob@ssh.yourhome.com
```

You'd then configure a web browser or another application to use your local IP address (127.0.0.1) and port 8888. All traffic from the application would be redirected through the tunnel.

## SSH Server code and setup

In order to connect to a server using SSH, the server needs to be running some sort of SSH server daemon code.

For OpenSSH, this code program is `sshd` and is located typically in
`/usr/sbin/sshd`

A situation where you will need to install and set this up is when creating a docker container. The server code package will be `openssh-server` that you'll install with the relevant package manager, and you will have to install as **root**.

The `sshd` process is started when the system boots and runs as root.

Here we just want to record some aspects of this SSH server setup.
For more information, see the SSH server academy link, as well as appropriate man pages.

### SSH server configuration files

The SSH server has a configuration file, typically located `/etc/sshd/sshd_config`, which specifies encryption/authentication options, file locations, logging, etc.

In fact the SSH server reads several configuration files.
The `ssh_config` file specifies one or more host key files (mandatory) and the location of the `authorized_keys` files for users, as well as potentially other files.

Within these files you can set configuration options, such as allowing `X11Forwarding`, `PermitRootLogin`, etc.

To set values in the server configuration file for OpenSSH. Read the man page `man 5 sshd_config`
In particular try to avoid editing the `/etc/sshd/sshd_config` file directly.
Instead, create your settings a separate file stored in `/etc/sshd/sshd_config.d/`
It doesn't matter what you call the file as the first line in the system wide config file (the one you should avoid editing directly) is

`Include /etc/ssh/sshd_config.d/*`

For most settings the first key value pair seen is the one used, unless it's a multi-value key such as `HostKey`.

### SSH server logging

Logging - SSH server uses the `syslog` subsystem for logging. Manyways to configure `syslog`. Many enterprises collect syslog data into their centralised SIEM (Security Incident and Event Management) system.
Most systems, `syslog` is configured to log SSH-related messages be default into files under `/var/log/.`
It's strongly advised to set the logging level, in the SSH server config file, to `VERBOSE`, so that fingerprints for SSH key access get properly logged.

### SSH Host keys

Each host (i.e., computer) should have a unique host key. Sharing host keys is strongly not recommended.

In OpenSSH, host keys are usually stored in `/etc/ssh` directory, in files that start `ssh_host_<rsa/dsa/ecdsa/ed25519>_key`

**They are normally generated automatically when OpenSSH is first installed.**

If needed, use `ssh-keygen` to generate them or replace them.

### Host Certificates

Some SSH implementations support using certificates for authenticating hosts.
`Tectia SSH` supports standards-compliant `X.509` certs for host authentication.
This allows the host certs to be generated and managed using normal cert management tools in an enterprise.

OpenSSH only supports its own proprietary certificate format. Using them requires developing and maintaining internal tools to host certs.

The reference to server SSH says using host certs instead of host keys is 'generally strongly recommended'

## References

* [OpenSSH](https://www.openssh.com/)
* [agent-forwarding](https://web.archive.org/web/20210427181202/http://unixwiz.net/techtips/ssh-agent-forwarding.html)

* [OpenSSH_vs_OpenSSL_key_formats](https://coolaj86.com/articles/openssh-vs-openssl-key-formats/)
* [SSH_academy_server](https://www.ssh.com/academy/ssh/server)
* [NIST IR 7966 - SSH key management](https://www.ssh.com/academy/compliance/nist-7966)
