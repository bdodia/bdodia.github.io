---
layout: post
title: Preparing Mac for Big Data Stack
---

Some steps to take prior to installing a Big Data stack on Mac OS X

1. Check Java installation
2. Install Homebrew
3. SSH Setup

1. Check Java Installation
 Open up a Terminal session and check that Java version 1.6.* is installed.

```bash
$ java -version
java version "1.6.0_65"
Java(TM) SE Runtime Environment (build 1.6.0_65-b14-462-11M4609)
Java HotSpot(TM) 64-Bit Server VM (build 20.65-b04-462, mixed mode)
```

If the message you get is similar to the above then you are good to go. If java is not installed then you will need to install version 1.6.* , for instructions on installing see *[r.2]*. 

2. Install Homebrew
Installing Homebrew is not a mandatory step; you can download the software components directly and install, however Homebrew (or a suitable alternative) will generally make the process of software pull/get, installation and removal cleaner see *[r.1]*. 

3. Secure Shell SSH Setup
SSH will be used to secure the connection to your Mac. Firstly enable Remote Login under System Preferences / Sharing; you might choose to enable remote login for a specific user account(s) only so as to avoid opening up your Mac to unknown attacks, in which case choose the account to allow access for, again under Preferences / Sharing. Now we need to set-up the private and public keys for SSH to function. At the Terminal command prompt from your $HOME directory enter:

```bash
$ ssh-keygen -t rsa -P ""  
```

Accept the default storage path offered at the prompt1. Now we need to copy (cat) the public key to the $HOME/.ssh/authorized_keys file2. 

```bash
$ cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys
```

Test the secure shell connection using

```bash
$ ssh localhost
```

You'll receive a prompt asking whether you want to allow this, accept the request. If all is well you'll now have an SSH session open.
Now we have the basics in place to continue exploring Big Data.

### Notes:

1. If you want to create a passphrase to encrypt your private key, then use $ ssh-keygen -t rsa instead.

2. Ordinarily the $HOME/.ssh/authorized_keys file would reside on the remote server/server which you want to connect to. If it did not happen by default, you'll also need to set the permissions on the $HOME/.ssh/authorized_keys file so that you (owner) have read+write access to it. Entering chmod u+rw authorized_keys or chmod 0600 authorized_keys at the Terminal command prompt from within your $HOME/.ssh directory will work.

### *References:*

r.1. brew.sh 

r.2. Official Java package for OS X
