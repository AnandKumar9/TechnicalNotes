#### GnuPG

GnuPG (06:29 PM) $ sudo gpg2 --gen-key
gpg (GnuPG) 2.2.17; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

You selected this USER-ID:
"Anand Kumar <anand.kumar3@capitalone.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? O

We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 6DFE6B36576620B4 marked as ultimately trusted
gpg: directory '/Users/sou543/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/Users/sou543/.gnupg/openpgp-revocs.d/F89DC7EC4CE8391090C5058D6DFE6B36576620B4.rev'
public and secret key created and signed.

pub   rsa2048 2019-10-06 [SC] [expires: 2021-10-05]
F89DC7EC4CE8391090C5058D6DFE6B36576620B4
uid                      Anand Kumar <anand.kumar3@capitalone.com>
sub   rsa2048 2019-10-06 [E] [expires: 2021-10-05]

*******

GnuPG (06:33 PM) $ sudo gpg2 --list-keys
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: next trustdb check due at 2021-10-05
/Users/sou543/.gnupg/pubring.kbx
--------------------------------
pub   rsa2048 2019-10-06 [SC] [expires: 2021-10-05]
F89DC7EC4CE8391090C5058D6DFE6B36576620B4
uid           [ultimate] Anand Kumar <anand.kumar3@capitalone.com>
sub   rsa2048 2019-10-06 [E] [expires: 2021-10-05]

*******

Desktop (06:34 PM) $ sudo gpg2 --export --armor anand.kumar3@capitalone.com > publickey.asc

gpg2 --import publickey.asc

Desktop (06:37 PM) $ sudo gpg2 --encrypt --recipient Anand\ Kumar TestFile.txt
Desktop (06:38 PM) $ ls -l
-rw-r--r--   1 sou543  staff    45 Oct  6 18:36 TestFile.txt
-rw-r--r--   1 root    staff   388 Oct  6 18:38 TestFile.txt.gpg

Desktop (06:38 PM) $ sudo gpg2 --decrypt TestFile.txt.gpg
gpg: encrypted with 2048-bit RSA key, ID 75D35DAF3386EB87, created 2019-10-06
"Anand Kumar <anand.kumar3@capitalone.com>"
The actual content after decryption.

*******

Cleartext
Ciphertext
Symmetric key encryption
Public key cryptography (Asymmetric key encryption)
Digital Signature (source and protects tampering)

PGP (compression, session key)
GnuPG

https://www.youtube.com/watch?v=GSIDS_lvRv4
https://medium.com/@hashelse/cryptography-for-absolute-beginners-3e274f9d6d66
https://medium.com/@hashelse/how-to-sign-and-verify-a-document-or-file-using-pgp-gpg-401d013d2405

*******

Allegheny83!
