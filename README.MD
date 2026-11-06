# Rust Password Generator

I wrote this little command-line tool because I got tired of coming up with passwords that were both strong and impossible to forget. You tell it how long you want the password and how complex it should be, and it spits out a random string. Nothing is saved, nothing is sent anywhere, and it runs entirely in your terminal.

## What it does

You pick a length and a complexity level from 1 to 4. Lower levels give you plain letters, and higher levels add capitals, numbers, and symbols.

## Before you start

You'll need Rust installed, version 1.70 or newer. If you don't have it yet, the [official install guide](https://www.rust-lang.org/tools/install)

## Getting it running

Clone the project and step into its folder:

```bash
git clone https://github.com/your-username/rust-password-generator.git
cd rust-password-generator
```

The program uses the `rand` crate. If your `Cargo.toml` doesn't already list it, add this:

```toml
[dependencies]
rand = "0.9"
```

Then start it up:

```bash
cargo run --release
```

## Using it

The program asks two questions. First, how long do you want the password?
The minimum is 6 (anything 5 or below will exit the program).
The second question is, how complex should it be? Which scales like so:

| Level | What goes into the password | Example characters |
|-------|-----------------------------|--------------------|
| 1 | Lowercase letters | `e` |
| 2 | Lowercase and uppercase letters | `e`, `E` |
| 3 | Letters and digits | `e`, `E`, `0` |
| 4 | Letters, digits, and symbols | `e`, `E`, `0`, `!` |

## Included fail safes / errors

A few things to note before using this program: 

- Typing something that isn't a number for the length will close the program. (exit code 1)
- A complexity outside 1 to 4 or a length under 6 also makes the program close.
- The values for length cannot be negative (Negative numbers for complexity results in the default).
- If the complexity value is not 1-4 but still works it will default to lower and uppercase (complexity - 2)

## On security

The random numbers come from the `rand`'s generator, which is cryptographically secure. Still, this does mean the number is still not truly random and should be used with caution. Maybe dont use it for your bank or email, a proper password manager will probably be the safer bet.

## Project layout

```
.
├── Cargo.toml
├── README.md
└── src
    └── main.rs
```

## Contributing

Ideas, bug reports, and pull requests are all welcome.

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
