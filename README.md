# expandir

> A personal fork of [espanso](https://github.com/espanso/espanso), the cross-platform text expander written in Rust.

![License](https://img.shields.io/github/license/BrunosGits/expandir)

![Platforms](https://img.shields.io/badge/platforms-Windows%2C%20macOS%20and%20Linux-blue)

## About this project

expandir is my personal fork of [espanso](https://github.com/espanso/espanso), a
privacy-first, cross-platform text expander. I use it every day.

I forked it because I wanted:

* a sandbox to learn and practice on a real Rust and C++ codebase
* a place to prototype features and experiments that don't need to fit the official project

The code is based on the official espanso codebase. It is not an official espanso release
and it is not affiliated with the espanso project in any way.

The name comes from the Portuguese verb expandir, to expand. I chose a name that stands on
its own because I did not want this fork to sound like a premium or paid edition of espanso.
It is neither of those. It is just my personal build.

If you want a stable text expander, use the official project:
**[https://github.com/espanso/espanso](https://github.com/espanso/espanso)**.

## What makes this fork different

Features and experiments I'm adding, all opt-in:

| Feature | Status |
| ------- | ------ |
| Search window opens near the mouse cursor (`search_use_cursor_position`) | Working on macOS. Windows and Linux testing pending |
| Clipboard history and searchable history UI | Planned |
| Temporary copy/paste hotspots (register slots) | Planned |
| AI snippet authoring assistant | Planned |
| Settings panel (GUI for config toggles) | Planned |
| Match editor GUI | Planned |

See [ROADMAP.md](./ROADMAP.md) for the full plan.

## A personal note

espanso is one of my all-time favorite piece of software. I used TextBlaze for years, more than
61K expansions logged with it, and when I discovered espanso I switched and never
looked back. It's fast, private, and works everywhere I do.

This fork is my way of giving back. It's a playground where I can build the features I
wish espanso had, and a place to learn from a codebase I genuinely admire. I can't wait
to see these features land, starting with the search window opening near the cursor.
It already works great on my Mac.

## Getting started

Setup and usage are the same as espanso. The only difference is the binary name, which is
`expandir` instead of `espanso`. Follow the official
[espanso documentation](https://espanso.org/docs/) to install and configure it, and use
`expandir` wherever the docs say `espanso`.

### Building from source

```sh
cargo build --release
```

The built binary is `target/release/expandir`. For a build with the search window (modulo)
UI:

```sh
cargo build --release --no-default-features --features modulo,vendored-tls
```

## Acknowledgments

This project is a fork of espanso, created by [Federico Terzi](https://github.com/federico-terzi)
and maintained by the espanso team. The core work is theirs:

* [espanso repository](https://github.com/espanso/espanso)
* [espanso website](https://espanso.org)
* [espanso hub](https://hub.espanso.org)

Thanks also to the libraries the project uses:
[libxdo](https://github.com/jordansissel/xdotool), [xclip](https://github.com/astrand/xclip),
[libxkbcommon](https://xkbcommon.org/), [wl-clipboard](https://github.com/bugaevc/wl-clipboard),
and [wxWidgets](https://www.wxwidgets.org/).

## License

This project inherits the upstream license and is licensed under the
[GPL-3.0 license](./LICENSE), as is the original espanso project.
