<p align="left"><img align="left" src="meta/logo.png" width="240px"></p>

# Lighthouse

Smart lights control tool and `Rust` crate.

Currently it mainly supports Philips Hue lights. But the back-end crate is
written in a way that allows other smart lights to be added in the future.

That said, the bulk of the codebase and the CLI focuses on Philips Hue as I
don't have any other branded smart light or other smart home tech to integrate.

## Also see:
[lighthouse.el](https://github.com/finnkauski/lighthouse.el) - an Emacs package
wrapping the functionality of `lighthouse`. 

## Installation

As it is under development you will need the `Rust` and `cargo` installed.
Easiest way to do so is to get on board with [rustup](https://rustup.rs).

Once you have the dependencies installed, run the following:

```shell
cargo install lighthouse
```

For latest version:

```shell
cargo install --git https://github.com/finnkauski/lighthouse
```

More manually:

```shell
git clone https://github.com/finnkauski/lighthouse
cd lighthouse
cargo install --path .
```

## Usage

#### Example files

If you would like to see some of the uses for the `crate` side of `lighthouse`,
see the `examples` directory of the repository. They will give you an idea of
how to use the internals of the crate.

#### Example commands

After installing you will have to authenticate to a `Philips Hue` bridge (the
box that controls the lights). All commands with the exception of `discover`
will run you through a Hue authentication flow.

```
lighthouse - light automation from the comfort of your keyboard

USAGE:
    lh [OPTIONS] [SUBCOMMAND]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -i, --ids <IDs>    Comma delimited IDs of lights that will get affected by the command

SUBCOMMANDS:
    bri         Set brightness (turns lights on)
    color       Send colors to lights
    discover    Discover bridges on the network and print them
    help        Prints this message or the help of the given subcommand(s)
    info        Print out useful information about your system
    loop        Set lights to colorloop
    off         Turn hue lights off
    on          Turn hue lights on
    state       Manually send state to hue lights
```

## Contributing

>This repo would benefit in some form of packaging for MAC/WINDOWS/LINUX so people don't need to install rust.

The tool is good enough for me to be able to do most stuff I want to do. It does
have the potential to become much more user friendly. I would love people to
contribute:

- Examples for the repository
- If you have odd setups or things like light groups, even trying it out to see
  if it breaks would be helpful. I don't know much about the API in detail so
  might have missed edge cases
- More CLI commands
- Currently the `reqwest` client is not `async`, would be ideal if we could send
  the lights commands asynchronously rather than in a for loop.
- Tests
