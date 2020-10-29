# Vaulttool Drop-In Version

A SkotOS game, like most [DGD](https://chattheatre.github.io/lpc-doc)-based apps, has a lot of in-memory data objects. [Shentino](https://github.com/shentino) wrote a useful tool to dump SkotOS's particular flavour of them.

See [Exploring SkotOS](https://chattheatre.github.io/SkotOS-Doc/Exploring_SkotOS.html) for full documentation on the Vault Tool.

## Installing the Vault Tool

SkotOS games have a DGD root directory, often called "skoot". The vault tool should be copied into usr/System/sys/vault.c. And you'll need a directory for the objects. Something like this:

    cp vault.c skoot/usr/System/sys/
    mkdir -p skoot/data/vault

Then you'll need to log in via the wiztool port and compile it:

    cd /usr/System/sys/
    compile vault.c

After that it should be possible to dump objects from memory into skoot/data/vault normally:

    code "/usr/System/sys/vault"->save_subdir("")

This should write out a lot of XML files to skoot/data/vault and possibly show various errors on your network connection and/or the DGD console.

It can take awhile for the whole object dump to finish. You can check if it's still adding files in many ways. Here's my favourite to use from the Unix command prompt:

    find skoot/data/vault -print | wc -l

If the number keeps going up, it's still writing files.
