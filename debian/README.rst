Notes for myself how to update this package.
============================================


Update upstream version
-----------------------

    $ git pull --origin motiejus git@github.com:Motiejus/piqi-deb.git && cd piqi-deb
    $ git checkout -b upstream motiejus/upstream

Update 'upstream' from alavrik:
    $ git pull git://github.com/alavrik/piqi.git
    $ git push motiejus HEAD:motiejus/upstream

Change to debian-ish working directory (with debian/ folder in it):
    $ git checkout -b motiejus/debian/snapshot motiejus/motiejus/debian/snapshot
    
Update changelog:
    $ dch -i
    
Push updated debian version:
    $ git push motiejus HEAD:motiejus/upstream
    
Generate archives for Ubuntu
----------------------------

Put something like this to changelog:

    piqi (0.6.5-lucid1) lucid; urgency=low

      * Bump upstream version

     -- Motiejus Jakštys <desired.mta@gmail.com>  Thu, 07 Nov 2013 08:23:34 +0100

Create 'orig' archive:
    $ git archive --prefix=piqi_0.6.5/ -o ../piqi_0.6.5.orig.tar.gz upstream

Generate source package:

    $ debuild -i -S -k0xYOURKEY1

You can build the source package now:

    $ debuild -k0xYOURKEY

And upload it.
