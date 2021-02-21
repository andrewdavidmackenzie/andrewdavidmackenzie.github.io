---
layout: post
title: Rust - Cargo udeps add-on
--- 

As your rust project evolves, adding or changing the dependencies you use is quite common.

After a while it's easy to get to a point where (especially on a larger project) it's hard to know 
which dependencies are still being used, and if the entries in your `Cargo.toml` file are all actually
being used in your code.

Building those extra dependencies takes time in your local builds and in CI and unnecessarily slows everything
down. Also, people installing/compiling your crate will also be downloading, installing and building those
dependencies unnecessarily.

You can manually scan your `Cargo.toml` file and either search for the reference in your code, or try emoving it
and see if everything still compiles (and tests!) successfully. 

But that's a laborious process.

There is a `cargo` add-on called `udeps` that can help you out here.

Here is it's [crates.io entry](https://crates.io/crates/cargo-udeps)
```aidl
Find unused dependencies in Cargo.toml.

While compilation of this tool also works on Rust stable, it needs Rust nightly to actually run.
```

and you use it as described there:
```bash
cargo +nightly udeps
```

It's unfortunate it still requires nightly to run (on my `flow` project I stick to stable, and so a `udeps`
check requires a complete compile from scratch on `nightly` but I don't run it so often...)

If there are no unused dependencies then the output will end with:
```bash
All deps seem to have been used
```

It there are any unused dependencies then they will be reported like this:
```bash
unused dependencies:
`flowr v0.34.3 (/Users/andrew/workspace/flow/flowr)`
└─── dependencies
     ├─── "ctrlc"
     └─── "toml"
Note: These dependencies might be used by other targets.
      To find dependencies that are not used by any target, enable `--all-targets`.
Note: They might be false-positive.
      For example, `cargo-udeps` cannot detect usage of crates that are only used in doc-tests.
      To ignore some of dependencies, write `package.metadata.cargo-udeps.ignore` in Cargo.toml.
```

You can then remove them from your list of dependencies in `Cargo.toml` and run again to check. 

Not recursive
==
I am not sure if it does the check recursively on crates that you depend on, I suspect 
not. That is less useful as you couldn't find the problem directly, you would have to raise an issue or a PR with 
the crate provider, but it still might be useful to raise awareness of unused dependencies in crates in general
either to the author or others who can help remove them with issues or PRs...


Workspace projects
==
When running thus:
```bash
cargo +nightly udeps 
```

in a workspace project, it seems to only check the crates in the `default-members` list in the `Cargo.toml` file
in the workspace root.

Check the entire workspace for unused dependencies using:
```bash
cargo +nightly udeps --workspace
```

This reports unused dependencies by crate in a tree view:
```bash
unused dependencies:
`flowr v0.34.3 (/Users/andrew/workspace/flow/flowr)`
└─── dependencies
     ├─── "ctrlc"
     └─── "toml"
`flowsamples v0.34.0 (/Users/andrew/workspace/flow/samples)`
└─── dependencies
     └─── "flowr"
`flowstdlib v0.34.3 (/Users/andrew/workspace/flow/flowstdlib)`
└─── build-dependencies
     └─── "flowc"
Note: These dependencies might be used by other targets.
      To find dependencies that are not used by any target, enable `--all-targets`.
Note: They might be false-positive.
      For example, `cargo-udeps` cannot detect usage of crates that are only used in doc-tests.
      To ignore some of dependencies, write `package.metadata.cargo-udeps.ignore` in Cargo.toml.
```

Once you have fixed all your unused dependencies, the output will return to the clean:
````bash
All deps seem to have been used.
````

Other Targets
==
If you have any dependencies that are only used on specific targets, as described in the output above
you can check for them using the `--all-targets` option to `cargo`:
```bash
```

Optional Dependencies
==
The unused dependency check works correctly for optional dependencies, that are only used (or made dependencies)
when specific `features` are enabled in `Cargo.toml`