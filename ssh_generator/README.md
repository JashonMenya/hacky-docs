# SSH Documentation

This document describes the steps necessary to generate SSH keys, update SSH config, add known hosts and SSH keys, and set appropriate permissions to the private and public keys.

## Table of Contents
- [Generate SSH Keys](#generate-ssh-keys)
- [Update SSH Config](#update-ssh-config)
- [Add Known Hosts](#add-known-hosts)
- [Set Appropriate Permissions](#set-appropriate-permissions)

## Generate SSH Keys

To generate SSH keys, run the following command:

```bash
ssh-keygen -t rsa -b 4096 -C "youremail@domain.com" -f ~/.ssh/name_your_key
```

This will create two files in your home directory: id_rsa (the private key) and id_rsa.pub (the public key).

## Update SSH Config

The SSH config file is located at `~/.ssh/config`. This file contains a list of hosts that you can connect to using SSH, as well as the options for connecting to those hosts.

To update the SSH config file, follow these steps:

- Open the SSH config file in a text editor.

- Add the following lines to the SSH config file:

```plaintext
Host example.com
    HostName example.com
    User your_username
    IdentityFile ~/.ssh/id_rsa
```

- Save the file and exit the text editor.

Replace example.com with the hostname of the host you want to connect to, and your_username with your username on that host.


By adding these lines to the SSH config file, you can now connect to the specified host using the defined options by simply running:


## Add Known Hosts


The known hosts file is located at `~/.ssh/known_hosts`. This file contains a list of hosts that you have previously connected to, as well as their public keys.

To add a host to the known hosts file, run the following command:

```bash
ssh-keyscan example.com >> ~/.ssh/known_hosts
```

The private key should be kept secret. You should only share the public key with the hosts that you want to connect to.

To set the appropriate permissions to the private and public keys, run the following commands:


## Set Appropriate Permissions
```bash
chmod 400 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```
These commands ensure that the private key is readable only by you and that the public key is readable by others.

