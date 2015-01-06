carbon-fuse
============

A persistent filesystem cache, using FUSE.

The goal of carbon-fuse is to carbon-copy every access you made to
an underlying filesystem, so that you don't need to access it later,
even when it's offline.  Right now, in the environmental spirit of
open-source software, carbon-fuse recycle must of its electron by
using two already existing user-space filesystems which, combined
together, create a nice work environment if you have either a slow, 
costly or even flaky access to your data, and don't have the space
to replicate everything locally.

offline-fuse used two fuse layers over a source filesystem.  The first
layer is a read-cache, and we used
[backfs](https://github.com/wfraser/backfs) for this.  The second
layer is the write cache, and we used
[unionfs-fuse](https://github.com/rpodgorny/unionfs-fuse) for it.
If required, different features would be added to either of them when
necessary, when the possibility to merging both features into a single
filesystem later on.

carbon-fuse include tools to manage the caching layers, as well as
managing the different the different layers.  With the exception of
the fuse filesystems themself, the tools rely currently only in a
bourne shell scripts, with some basic posix core utilities.  It should
so work on most system supporting fuse correctly.
