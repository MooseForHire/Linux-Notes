# What is an SSH Key?

An access credential, similar to a password, used in the SSH protocol. SSH Keys grant, automate and enable remote access to servers.

These are called Key-Pairs

They include two keys:

## Public Key:

A public key that is copied to the SSH server(s). Anyone with a copy of the public key can encrypt data, which can then only be read by the person who holds the corresponding private key. Once an SSH server receives a public key from a user and considers the key trustworthy, the server marks the key as authorized in its authorized_keys file.

## Private Key:

A private key that remains only with the user. The possession of this key is proof of the users identitiy. Only a user in possession of a private key that corresponds to the public key at the server will be able to authenticate successfully.

### Creation

When generating a key-pair, it is generated in two steps:

1.  Create SSH key on the client side.
2.  Copy it to the server or any remote host.

A key pair consists of Private and Public key files named id_rsa and id_rsa.pub in the ~/.ssh directory.

## Step 1

`ssh-keygen

Create a key pair. No arguments listed, will prompt for the file in which to store keys. SSH keys for user authentication are usually stored in the user's .ssh directory under the home directory. However, in enterprise environments, this may be different.

`ssh-keygen -t ecdsa -b 521

Create a key pair using ECDSA algorithm, with 521 bit size. Will prompt for file in which to store. It'll ask you to enter the filename in which you want to save the key pair

## Step 2

It'll ask you for a passphrase, this will be the password you use to connect to the host ( just an extra security layer). Default is no password

## Step 3

```shell
# start the ssh-agent in the background
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```

You can simply copy the SSH key to the host by running:
ssh-copy-id username@host-ip-adress
