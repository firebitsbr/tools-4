# Amethyst-CLI

[![Build Status][s1]][tc] [![GPL3 License][s2]][gl]

[s1]: https://api.travis-ci.org/ebkalderon/amethyst_cli.svg
[s2]: https://img.shields.io/badge/license-GPL%20v3-blue.svg

[tc]: https://travis-ci.org/ebkalderon/amethyst_cli
[gl]: https://github.com/ebkalderon/amethyst_cli/blob/master/COPYING

Command-line interface for creating and deploying [Amethyst][am] game projects.
This project is a *work in progress* and very incomplete; pardon the dust!

[am]: https://github.com/ebkalderon/amethyst

## Usage

The CLI interface is intentionally very similar to [Cargo][ca], so it is easily
intelligible to Rustaceans. Unfortunately, it is very limited at the moment in
terms of features. Below are the subcommands ~~hacked together~~ implemented so
far.

[ca]: https://github.com/rust-lang/cargo

#### new

Generates an empty game project, a fresh white canvas for your next masterpiece.
The default directory structure is laid out like this:

```
project/
├── Cargo.toml
├── resources
│   ├── config.yml
│   ├── entities/
│   ├── input.yml
│   └── prefabs/
└── src
    └── main.rs
```

#### build

Compiles the current project. It's currently just a frontend for `cargo build`,
but more features are in the works, like [Lua][lu] or [mruby][mr] script
precompilation and offline GPU shader compilation for APIs that support it.
And no, you're not dreaming. The `--release` flag doesn't work yet.

[lu]: http://www.lua.org/
[mr]: http://mruby.org/

#### clean

Removes the `target` directory. Again, just like in Cargo. One day, this will
have switches whether or not to clear out said precompiled scripts or cached
shader program bytecode.

#### run

Runs the main binary of the project. A frontend to `cargo run`. Proposed extra
features include real-time profiling and debugging, and manual skipping of
levels when playtesting. Oh, and `--release` doesn't work here yet either.

## What's missing?

#### deploy

Performs a clean rebuild of the game and engine, runs any unit and integration
tests if there are any, zips up the `resources` directory, and places it and
the game binary in a directory called `deployed`.

#### module

Grabs forthcoming Amethyst engine modules (e.g. rendering, scripting, physics,
etc.) from either crates.io or GitHub, configures your `Cargo.toml` and
modifies the `resources` directory accordingly. Once a new module is installed
and configured, just drop your assets into the appropriate folders and you can
start writing your game logic.

## Contributing

Amethyst is an open-source project that values community contribution. Pull
requests are welcome!

We assume you have granted non-exclusive right to your source code under the
[GNU General Public License 3.0][gl] and you have processed your code with `rustfmt` prior to
submission. If you want to be known as an author, please add your name to the
AUTHORS.md file in the pull request.
