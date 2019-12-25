# ssh-keygen
## Intro
A tool for creating new authentication key pairs for SSH. Such key pairs are for automating logins, and for authenticating host.
## Creating an ssh key pair for user authentication
```
[testssh@example ~]$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/testssh/.ssh/id_rsa): 
Created directory '/home/testssh/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/testssh/.ssh/id_rsa.
Your public key has been saved in /home/testssh/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:LSBMoGLVY/kH+BNHA+fLwGAUYYyRV5qnuiYzzUs1npw testssh@example.com
The key's randomart image is:
+---[RSA 2048]----+
|  .+OB*oo+       |
| ..=oO=oo..      |
|o.  =o=++.       |
|o    .o=oo.      |
|     +  So.      |
|    = +  .       |
|  oo E           |
| +.+.            |
|  =o.            |
+----[SHA256]-----+

```
## Choosing an Algorithm and Specifying Key Sizes
```
ssh-keygen -t rsa -b 4096
ssh-keygen -t dsa
ssh-keygen -t ecdsa -b 521
ssh-keygen -t ed25519
```
## Specifying the File Name
```
ssh-keygen -f ~/Identity-WF -t rsa -b 1024
```
## sshd_config file configuration
```shell
vim /etc/ssh/sshd_config
```
the config file shows
```
AuthorizedKeysFile
Specified the file that contains the public keys that can be used for user authentication.
```
