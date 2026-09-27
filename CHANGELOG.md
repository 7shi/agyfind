# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.5.0] - 2026-09-27

### Changed

- Entries are now dated and sorted by the artifact file's mtime instead of `updatedAt` in its metadata, which is not refreshed when the artifact is edited. This affects the timestamps and order in `agyfind summary`, the index numbers used by `agyfind show N`, and the `updated` header in `agyfind show`.

## [0.4.0] - 2026-09-26

### Added

- `agyfind show --no-rich` prints the content as plain text (the previous default behavior).

### Changed

- `agyfind show` now renders the content as Markdown with rich by default, both through the pager (colors always emitted) and with `--no-pager`.
- `--no-pager` is implied when stdout is piped or redirected; the output is still rendered with rich but without color codes. Use `--no-rich` to get the raw content.

### Removed

- `agyfind show --rich`, which is now the default (use `--no-pager` for the same output).

## [0.3.1] - 2026-09-24

### Changed

- `agyfind show` now encloses its header in `---` lines. `updated` is printed as `YYYY-MM-DD HH:MM:SS+09:00`, and `summary` is omitted when empty instead of printing `-`.
- `agyfind show --rich` draws the header's `---` delimiters as full-width rules.

## [0.3.0] - 2026-09-24

### Added

- `agyfind show --rich` renders the content as Markdown with rich (without a pager).

### Changed

- `agyfind show` now pipes its output through a pager (`$PAGER`, default `less` with `LESS=FRX`) when stdout is a terminal, like `git show`, and prints the whole content by default instead of the first 10 lines. Use `--no-pager` to disable the pager; `-n LINES` still limits the content.

## [0.2.1] - 2026-09-02

### Fixed

- `agyfind summary DIRECTORY` now shows each entry's index from the full, unfiltered list instead of a filtered index, so it can always be passed directly to `agyfind show N`.

## [0.2.0] - 2026-09-01

### Changed

- Discover artifacts by scanning `*.metadata.json` sidecars instead of `*.md` files, so artifacts are no longer limited to the `.md` extension.

## [0.1.1] - 2026-09-01

### Changed

- Use "artifact" terminology consistently in docs and CLI help text.

## [0.1.0] - 2026-09-01

### Added

- `agyfind` CLI to list and inspect Antigravity CLI brain files, with `summary`, `ls`, and `show` subcommands.
