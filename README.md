cmdg - A command line client to Gmail.

TODO: copyright

https://github.com/ThomasHabets/cmdg

Introduction
============

cmdg is a commandline client to Gmail that provides a UI more similar
to Pine.

It uses the Gmail API to interact with your mailbox. This has several
benefits over IMAP
------------------
* No passwords stored on disk. (application-specific passwords are
  also passwords, and can be used for more than Gmail). OAuth2 is used
  instead, and cmdgs access can be revoked
  [here](https://security.google.com/settings/security/permissions).
  cmdg can only access your Gmail, and cannot lose your password even
  if the machine it runs on gets hacked.
* The "labels" model is native in the cmdg UI, unlike IMAP clients
  that try to map Gmail labels onto IMAP.
* TODO: others

The benefits cmdg has over the Gmail web UI
-------------------------------------------
* Emacs keys. (or compose emails in Vim, if you prefer)
* Proper quoting. The Gmail web UI encourages top-posting. Ugh.
* It uses 100% keyboard navigation. Gmail web UI has very good
  keyboard navigation for a web app, but still requires mouse for
  a few things.
* cmdg works without a graphic terminal.
* cmdg uses less bandwidth (citation needed), and much less memory.

A security difference
---------------------
* Gmail web UI uses username and password to log in, which means they
  can be stolen. You should be using [U2F
  Yubikeys](https://www.yubico.com/products/yubikey-hardware/fido-u2f-security-key/),
  so that losing the password isn't as big of a deal. The user has to
  re-type the password every now and then, which is an opportunity for
  the attacker to steal the password.
* OAuth token in cmdg.conf can be copied, and the thief would be
  able to access the users Gmail until the key is revoked. The
  access does not expire on its own.

Installing
==========
```
$ mkdir go
$ cd go
$ GOPATH=$(pwd) go get github.com/ThomasHabets/cmdg.git
$ GOPATH=$(pwd) go build github.com/ThomasHabets/cmdg
$ cp cmdg /usr/local/bin
```

Configuring
===========
TODO: Create a client ID for people to use.
```
$ cmdg -configure
Client ID: <your client ID here>
Client Secret: <your client secret here>
Cut and paste this URL into your browser:
  https://long-url....
Returned code: <paste code here>
$
```

Running
=======
```
$ cmdg
```
For keyboard shortcuts, see the manpage, or press '?' in most screens.

To quit, press Ctrl-C.
(TODO: implement '?' inline help)
