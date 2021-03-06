# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Unreleased

Here you can look at what features are coming in the next version.

### Added

- `Face::empty` constructor as a simple way to construct the empty face
- `Feature` struct that wraps `hb_feature_t` and has an easy to use constructor.
- Add `UnicodeBuffer::add_str_item` to allow providing context to the string
  being shaped.
- Add `UnicodeBuffer::preallocate`

### Changed

- removed kerning callbacks from FontFuncs (following the upstream harfbuzz
  change). This also enabled updating to harfbuzz-sys 0.3.
- updated to use Rust 2018
- Further improved docs

## [0.3.0] 2019-01-08

### Added

- constructor for `Blob` from a mutable slice
- `Font::empty` as a simple way to construct the empty font
- support for serializing a `GlyphBuffer`'s contents
- `create_harfbuzz_rusttype_font`: a new way to create a font with Rusttype font
  funcs (the old `SetRustTypeFuncs` trait is deprecated)

### Fixed

- lifetime of slice returned by `Blob::get_data` (could cause UB)

### Changed

- The rustup feature is no longer enabled by default
- `SetRustTypeFuncs` is now deprecated in favor of
  `create_harfbuzz_rusttype_font`
- Internal representation of smart pointers (possibly more safe now)
- Many improvementes to documentation

## [0.3.0] 2018-08-26

### Fixed

- `Font::parent` now returns an option
- `HarfbuzzObject` becomes unsafe to implement

### Changed

- Smart pointers to use `NonNull`

## [0.2.0] 2018-05-01

### Added

- A new enum called TypedBuffer. It contains either a UnicodeBuffer or a GlyphBuffer. This makes reusing hb_buffer_t objects from foreign code possible.
- UnicodeBuffer methods to return its contents
- `from_bytes` function for `Face`

### Fixed

- `Font::set_funcs` adds necessary `Send` and `Sync` bounds
- UnicodeBuffer and GlyphBuffer no longer implement Clone (as they are
  mutable)
-

### Changed

- Naming: `HbArc` to `Shared` and `HbBox` to `Owned`
- internal representation of `Shared` and `Owned`
- `Shared::into_raw` and `Owned::into_raw` into static methods
- Various improvements to documentation
- `shape` becomes a free standing function (it was a method on `UnicodeBuffer`)

## [0.1.0] 2018-01-11

Initial Release
