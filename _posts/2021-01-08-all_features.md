---
layout: post
title: Rust: Cargo Workspaces add-on
--- 

With my `flow` rust project, I have ended up with a workspace project with eight crates inside it (after moving 
some libraries into the crate of the binary that uses them, it would be ten otherwise).

This works pretty well for me in rust, with cargo handling things nicely.

When combined with cargo's ability to specify a local dependency it can use in-place of
a specific (published) version:
```toml
[dependencies]
flowrstructs = {path = "../flowrstructs", version = "0.33.0"}
```

This work's nicely for development of multiple crates in parallel. Especially in the earlier
days of a project when the interfaces between crates are not clear and are unstable and 
you have to make changes to multiple crates at the same time, and you don't want to be publishing
lots of intermediate versions on crates.io while you work out how the crates fit together.

There are still a few things you can find missing from cargo when using it in a workspace
project. But they are not many, and the number is decreasing over time as cargo developers fill in the gaps.

I have multiple dependencies between crates within the workspace, and I had to separate out some structs into a
new, shared, crate to avoid a cyclic dependency. The crate dependency hierarchy in my project alone
is three or more levels deep.

When publishing crates, and wishing published crates to use the updated version of the other 
crates they depend upon, this became a time consuming manual task, and a real PITA.

For a while I codified the dependency structure into a makefile that took care of publishing
new versions of crates in order.

A much better solution I have found that has been working for me well so far is the
[cargo workspaces](https://crates.io/crates/cargo-workspaces) add-on to cargo.

To quote from it's crates.io entry:
```
A tool that optimizes the workflow around cargo workspaces with git and cargo
by providing utilities to version, publish, execute commands and more.
```

I mainly use the `publish` command, but the others may become useful for me over time.

I checkout `master` branch, type `cargo ws publish`, select the type of bump to the version
numbers I want, check the list of crate to be published matches my expectations and then go
and make a cup of tea, while it works its magic.

When I come back, the crates modified since the last time I published, have had their version
number bumped, committed to git, and published into crates.io - in the order dictated by the 
dependency hierarchy of my workspace project.

The only gotcha I've seen so far, is that you can start to get into a bit of a mess if for some
reason you need to update the versions manually in-between publishing with `cargo workspace`.

But it wasn't too hard to get out of the mess and back on the smooth road.

Kudos to `Pavan Kumar Sunkara` for writing such a useful and time-saving tool for us
rustaceans!