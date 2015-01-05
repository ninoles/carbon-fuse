offline-fuse
============

A persistent filesystem cache, using FUSE.

offline-fuse used two fuse filesystems to allow persistent rw to a
remote filesystem, even if this system is offline, to the limit of the
cached data.  By itself, it is not a filesystem, but by combining the
strengths of other projects, it creates a nice work environment if you
have either a slow, flaky, or costly access to your data, and don't
have the space to replicate everything locally.

offline-fuse used two fuse layer over a source filesystem.  The first
layer is a read-cache, and we used
[backfs](https://github.com/wfraser/backfs) for this.  The second
layer is the write cache, and we used
[unionfs-fused](https://github.com/rpodgorny/unionfs-fuse) for it.

offline-fuse include tools to manage the caching layers, as well as
managing the different the different layers.  With the exception of
the fuse filesystems themself, the tools rely currently only in a
bourne shell scripts, with some basic posix core utilities.  It should
so work on most system supporting fuse correctly.
