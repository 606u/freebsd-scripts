# Various, useful every-day scripts tailored for FreeBSD


## cfscat -- Cold file-system cataloging

Scans a file-system location to make a list of directories and files
inside.  Gives you the ability to list files or search amongst them
(by name) even when file-system is not available (for example a
detached external USB flash or hard drive).

Usage: mount your storage device and ask `cfscat` to enumerate files
on it:

    $ cfscat scan /mnt/music music-hdd

`cfscat` will cache a list of directories and files in this location
and label them as `music-hdd` volume. Later, when you unmount it, you
can still see a list of files there with

    $ cfscat ls music-hdd
    $ cfscat hier music-hdd | less

or search for your Bach records with

    $ cfscat q bach

To update same volume at a later time mount it on the same place and
run

    $ cfscat update music-hdd

And, finally,

    $ cfscat volumes

Will print a list of your volumes.

Internally `cfscat` uses FreeBSD's `updatedb(8)` and `locate(1)`
facilities, but uses separate databases, usually kept in `~/.cfscat/`.
