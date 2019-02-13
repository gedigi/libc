[![Travis-CI Status]][Travis-CI] [![Appveyor Status]][Appveyor] [![Cirrus-CI Status]][Cirrus-CI] [![Latest Version]][crates.io] [![Documentation]][docs.rs] ![License]

libc - Raw FFI bindings to platforms' system libraries
====

`libc` provides all of the definitions necessary to easily interoperate with C
code (or "C-like" code) on each of the platforms that Rust supports. This
includes type definitions (e.g. `c_int`), constants (e.g. `EINVAL`) as well as
function headers (e.g. `malloc`).

This crate exports all underlying platform types, functions, and constants under
the crate root, so all items are accessible as `libc::foo`. The types and values
of all the exported APIs match the platform that libc is compiled for.

More detailed information about the design of this library can be found in its
[associated RFC][rfc].

[rfc]: https://github.com/rust-lang/rfcs/blob/master/text/1291-promote-libc.md

## Usage

Add the following to your `Cargo.toml`:

```toml
[dependencies]
libc = "0.2"
```

## Features

* `use_std`: by default `libc` links to the standard library. Disable this
  feature remove this dependency and be able to use `libc` in `#![no_std]`
  crates.

* `extra_traits`: all `struct`s implemented in `libc` are `Copy` and `Clone`.
  This feature derives `Debug, `Eq`, `Hash`, and `PartialEq`.

## Rust version support

The minimum supported Rust toolchain version is **Rust 1.13.0** . APIs requiring
newer Rust features are only available on newer Rust toolchains:

| Feature              | Version |
|----------------------|---------|
| `union`              |  1.19.0 |
| `const mem::size_of` |  1.24.0 |
| `repr(align)`        |  1.25.0 |
| `extra_traits`      |  1.25.0 |
| `core::ffi::c_void`  |  1.30.0 |
| `repr(packed(N))` |  1.33.0 |

## Platform support

[Platform-specific documentation of libc's master branch for all supported platforms][docs.master].

See [`ci/build.sh`](ci/build.sh) for the platforms on which `libc` is
guaranteed to build for each Rust toolchain. The test-matrix at [Travis-CI],
[Appveyor], and [Cirrus-CI] show the platforms in which `libc` tests are run.

### Platform-specific documentation
* [aarch64-linux-android](aarch64-linux-android/libc/index.html)
* [aarch64-unknown-linux-gnu](aarch64-unknown-linux-gnu/libc/index.html)
* [arm-linux-androideabi](arm-linux-androideabi/libc/index.html)
* [arm-unknown-linux-gnueabi](arm-unknown-linux-gnueabi/libc/index.html)
* [arm-unknown-linux-gnueabihf](arm-unknown-linux-gnueabihf/libc/index.html)
* [armv7-linux-androideabi](armv7-linux-androideabi/libc/index.html)
* [armv7-unknown-linux-gnueabihf](armv7-unknown-linux-gnueabihf/libc/index.html)
* [i586-unknown-linux-gnu](i586-unknown-linux-gnu/libc/index.html)
* [i686-linux-android](i686-linux-android/libc/index.html)
* [i686-unknown-freebsd](i686-unknown-freebsd/libc/index.html)
* [i686-unknown-linux-gnu](i686-unknown-linux-gnu/libc/index.html)
* [i686-unknown-linux-musl](i686-unknown-linux-musl/libc/index.html)
* [mips-unknown-linux-gnu](mips-unknown-linux-gnu/libc/index.html)
* [mips-unknown-linux-musl](mips-unknown-linux-musl/libc/index.html)
* [mips64-unknown-linux-gnuabi64](mips64-unknown-linux-gnuabi64/libc/index.html)
* [mips64el-unknown-linux-gnuabi64](mips64el-unknown-linux-gnuabi64/libc/index.html)
* [mipsel-unknown-linux-gnu](mipsel-unknown-linux-gnu/libc/index.html)
* [mipsel-unknown-linux-gnu](mipsel-unknown-linux-gnu/libc/index.html)
* [mipsel-unknown-linux-musl](mipsel-unknown-linux-musl/libc/index.html)
* [powerpc-unknown-linux-gnu](powerpc-unknown-linux-gnu/libc/index.html)
* [powerpc64-unknown-linux-gnu](powerpc64-unknown-linux-gnu/libc/index.html)
* [powerpc64le-unknown-linux-gnu](powerpc64le-unknown-linux-gnu/libc/index.html)
* [s390x-unknown-linux-gnu](s390x-unknown-linux-gnu/libc/index.html)
* [x86_64-unknown-freebsd](x86_64-unknown-freebsd/libc/index.html)
* [x86_64-unknown-linux-gnu](x86_64-unknown-linux-gnu/libc/index.html)
* [x86_64-unknown-linux-musl](x86_64-unknown-linux-musl/libc/index.html)
* [x86_64-unknown-netbsd](x86_64-unknown-netbsd/libc/index.html)
* [arm-unknown-linux-musleabi](arm-unknown-linux-musleabi/libc/index.html)
* [arm-unknown-linux-musleabihf](arm-unknown-linux-musleabihf/libc/index.html)
* [armv7-unknown-linux-musleabihf](armv7-unknown-linux-musleabihf/libc/index.html)
* [sparc64-unknown-linux-gnu](sparc64-unknown-linux-gnu/libc/index.html)
* [wasm32-unknown-emscripten](wasm32-unknown-emscripten/libc/index.html)
* [x86_64-linux-android](x86_64-linux-android/libc/index.html)
* [x86_64-rumprun-netbsd](x86_64-rumprun-netbsd/libc/index.html)
* [aarch64-unknown-linux-musl](aarch64-unknown-linux-musl/libc/index.html)
* [sparcv9-sun-solaris](sparcv9-sun-solaris/libc/index.html)
* [wasm32-unknown-unknown](wasm32-unknown-unknown/libc/index.html)
* [x86_64-sun-solaris](x86_64-sun-solaris/libc/index.html)
* [i586-unknown-linux-musl](i586-unknown-linux-musl/libc/index.html)
* [x86_64-unknown-cloudabi](x86_64-unknown-cloudabi/libc/index.html)
* [aarch64-fuchsia](aarch64-fuchsia/libc/index.html)
* [thumbv6m-none-eabi](thumbv6m-none-eabi/libc/index.html)
* [thumbv7em-none-eabi](thumbv7em-none-eabi/libc/index.html)
* [thumbv7em-none-eabihf](thumbv7em-none-eabihf/libc/index.html)
* [thumbv7m-none-eabi](thumbv7m-none-eabi/libc/index.html)
* [thumbv7neon-linux-androideabi](thumbv7neon-linux-androideabi/libc/index.html)
* [thumbv7neon-unknown-linux-gnueabihf](thumbv7neon-unknown-linux-gnueabihf/libc/index.html)
* [x86_64-fortanix-unknown-sgx](x86_64-fortanix-unknown-sgx/libc/index.html)
* [x86_64-fuchsia](x86_64-fuchsia/libc/index.html)
* [x86_64-unknown-linux-gnux32](x86_64-unknown-linux-gnux32/libc/index.html)
* [x86_64-unknown-redox](x86_64-unknown-redox/libc/index.html)
* [aarch64-apple-ios](aarch64-apple-ios/libc/index.html)
* [armv7-apple-ios](armv7-apple-ios/libc/index.html)
* [armv7s-apple-ios](armv7s-apple-ios/libc/index.html)
* [i386-apple-ios](i386-apple-ios/libc/index.html)
* [i686-apple-darwin](i686-apple-darwin/libc/index.html)
* [x86_64-apple-darwin](x86_64-apple-darwin/libc/index.html)
* [x86_64-apple-ios](x86_64-apple-ios/libc/index.html)

## License

This project is licensed under either of

* [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
  ([LICENSE-APACHE](LICENSE-APACHE))

* [MIT License](http://opensource.org/licenses/MIT)
  ([LICENSE-MIT](LICENSE-MIT))

at your option.

## Contributing

We welcome all people who want to contribute. Please see the [contributing
instructions] for more information.

[contributing instructions]: CONTRIBUTING.md

Contributions in any form (issues, pull requests, etc.) to this project
must adhere to Rust's [Code of Conduct].

[Code of Conduct]: https://www.rust-lang.org/en-US/conduct.html

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in `libc` by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.

[Travis-CI]: https://travis-ci.com/rust-lang/libc
[Travis-CI Status]: https://travis-ci.com/rust-lang/libc.svg?branch=master
[Appveyor]: https://ci.appveyor.com/project/rust-lang-libs/libc
[Appveyor Status]: https://ci.appveyor.com/api/projects/status/github/rust-lang/libc?svg=true
[Cirrus-CI]: https://cirrus-ci.com/github/rust-lang/libc
[Cirrus-CI Status]: https://api.cirrus-ci.com/github/rust-lang/libc.svg
[crates.io]: https://crates.io/crates/libc
[Latest Version]: https://img.shields.io/crates/v/libc.svg
[Documentation]: https://docs.rs/libc/badge.svg
[docs.rs]: https://docs.rs/libc
[License]: https://img.shields.io/crates/l/libc.svg
[docs.master]: https://rust-lang.github.io/libc
